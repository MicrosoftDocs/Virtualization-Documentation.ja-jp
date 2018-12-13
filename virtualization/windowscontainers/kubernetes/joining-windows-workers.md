---
title: Windows ノードへの参加
author: daschott
ms.author: daschott
ms.date: 11/02/2018
ms.topic: get-started-article
ms.prod: containers
description: Kubernetes v1.12 を使用するには、Windows ノードを結合できます。
keywords: kubernetes、1.12、windows、作業の開始
ms.assetid: 3b05d2c2-4b9b-42b4-a61b-702df35f5b17
ms.openlocfilehash: 8051270cac6178bad9adf9a8ef9e2324932f7d01
ms.sourcegitcommit: 8e9252856869135196fd054e3cb417562f851b51
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/08/2018
ms.locfileid: "6179072"
---
# <a name="joining-windows-server-nodes-to-a-cluster"></a>Windows Server ノード クラスターへの参加 #
[Kubernetes マスター ノードをセットアップ](./creating-a-linux-master.md)して[、目的のネットワーク ソリューションを選択](./network-topologies.md)したらは、クラスターを形成する Windows Server ノードに参加する準備が整います。 参加する前に、いくつかの[Windows ノードの準備](#preparing-a-windows-node)が必要です。

## <a name="preparing-a-windows-node"></a>Windows のノードの準備 ##
> [!NOTE]  
> Windows セクションでのすべてのコード スニペットは、_管理者特権の_ PowerShell で実行します。

### <a name="install-docker-requires-reboot"></a>Docker (再起動が必要) をインストールします。 ###
Kubernetes は、インストールする必要がありますので、コンテナー エンジンとして[Docker](https://www.docker.com/)を使用します。 [Docs の公式手順](../manage-docker/configure-docker-daemon.md#install-docker)または [Docker の手順](https://store.docker.com/editions/enterprise/docker-ee-server-windows)に従うことも、以下の手順を試すこともできます。

```powershell
Install-Module -Name DockerMsftProvider -Repository PSGallery -Force
Install-Package -Name Docker -ProviderName DockerMsftProvider
Restart-Computer -Force
```

プロキシの内側にいる場合は、次の PowerShell 環境変数を定義する必要があります。
```powershell
[Environment]::SetEnvironmentVariable("HTTP_PROXY", "http://proxy.example.com:80/", [EnvironmentVariableTarget]::Machine)
[Environment]::SetEnvironmentVariable("HTTPS_PROXY", "http://proxy.example.com:443/", [EnvironmentVariableTarget]::Machine)
```

場合は、再起動後に、次のエラーを参照してください。

![テキスト](media/docker-svc-error.png)

次 docker サービスを手動で開始します。

```powershell
Start-Service docker
```

### <a name="create-the-pause-infrastructure-image"></a>「一時停止」(インフラストラクチャ) イメージを作成します。 ###
> [!Important]
> 競合しているコンテナーの画像はのように注意することが重要必要なタグがないの原因と、 `docker pull` 、コンテナーの互換性のないイメージの場合は、次のような[展開の問題](./common-problems.md#when-deploying-docker-containers-keep-restarting)を引き起こしている不定`ContainerCreating`状態。

`docker` のインストールが完了したため、Kubernetes インフラストラクチャ ポッドを準備するために Kubernetes で使用される "pause" イメージを準備する必要があります。 この 3 つの手順があります。 
  1. [イメージを取得します。](#pull-the-image)
  2. microsoft として[、タグ付け](#tag-the-image)を/nanoserver:latest
  3. [実行します。](#run-the-container)


#### <a name="pull-the-image"></a>画像を取り込む ####     
 特定の Windows のリリースの画像を取り込みます。 たとえば、Windows Server 2019 を実行している場合。

 ```powershell
docker pull microsoft/nanoserver:1803
 ```

#### <a name="tag-the-image"></a>画像をタグ付けします。 ####
このガイドの後半で使用する Dockerfiles を探して、`:latest`タグの画像します。 次のように取得するだけ nanoserver イメージをタグ付けには。

```powershell
docker tag microsoft/nanoserver:1803 microsoft/nanoserver:latest
```

#### <a name="run-the-container"></a>コンテナーを実行します。 ####
コンテナーが実際には、コンピューターで実行することを確認してください。

```powershell
docker run microsoft/nanoserver:latest
```

次のようなものを表示する必要があります。

![テキスト](./media/docker-run-sample.png)

> [!tip]
> 実行できない場合、コンテナーください」をご覧ください:[コンテナーの画像を含むコンテナー ホスト バージョンを一致します。](https://docs.microsoft.com/en-us/virtualization/windowscontainers/deploy-containers/version-compatibility#matching-container-host-version-with-container-image-versions)


#### <a name="prepare-kubernetes-for-windows-directory"></a>Windows 版の Kubernetes ディレクトリを準備します。 ####
だけでなく、配置スクリプトおよび構成ファイル Kubernetes バイナリを格納する"Kubernetes for Windows"ディレクトリを作成します。

```powershell
mkdir c:\k
```

#### <a name="copy-kubernetes-certificate"></a>Kubernetes 証明書をコピーします。 #### 
Kubernetes 証明書ファイルをコピーする (`$HOME/.kube/config`)[マスターから](./creating-a-linux-master.md#collect-cluster-information)この新規`C:\k`ディレクトリ。

#### <a name="download-kubernetes-binaries"></a>Kubernetes バイナリ ファイルをダウンロードします。 ####
Kubernetes を実行できるようにするには、最初にダウンロードする必要が、 `kubectl`、 `kubelet`、および`kube-proxy`バイナリします。 これらのリンクからダウンロードできます、`CHANGELOG.md`の[最新リリースで作成された](https://github.com/kubernetes/kubernetes/releases/)ファイル。
 - たとえば、 [v1.12 ノードのバイナリ](https://github.com/kubernetes/kubernetes/blob/master/CHANGELOG-1.12.md#node-binaries)を紹介します。
 - [7 Zip](http://www.7-zip.org/)などのツールを使用してアーカイブを展開しにバイナリを配置`C:\k\`します。

#### <a name="optional-setup-kubectl-on-windows"></a>(オプション)Windows kubectl をセットアップします。 ####
Windows からクラスターを制御する場合は、作業を使用して、`kubectl`コマンド。 最初に`kubectl`外の利用可能な`C:\k\`ディレクトリを変更する、`PATH`環境変数。

```powershell
$env:Path += ";C:\k"
```

この変更を永続化する場合は、コンピューター ターゲット内の変数を変更します。

```powershell
[Environment]::SetEnvironmentVariable("Path", $env:Path + ";C:\k", [EnvironmentVariableTarget]::Machine)
```

次に、[クラスター証明書](#copy-kubernetes-certificate)が有効であることを確認します。 場所を設定するために、`kubectl`構成ファイルの検索] に渡すことができます、`--kubeconfig`パラメーター、または変更する、`KUBECONFIG`環境変数します。 たとえば、`C:\k\config` に構成がある場合は、次のように設定します。

```powershell
$env:KUBECONFIG="C:\k\config"
```

現在のユーザーのスコープでこの設定を永続化するには、次のように設定します。

```powershell
[Environment]::SetEnvironmentVariable("KUBECONFIG", "C:\k\config", [EnvironmentVariableTarget]::User)
```

最後に、確認するには、構成が正しく検出されたかどうかは次のように使用します。

```powershell
kubectl config view
```

接続エラーが発生する場合は、

```
Unable to connect to the server: dial tcp [::1]:8080: connectex: No connection could be made because the target machine actively refused it.
```

Kubeconfig の場所を確認してくださいか、何度もコピーしようとしています。

エラーが表示されない場合、ノードをクラスターへの参加を準備することができました。

## <a name="joining-the-windows-node"></a>Windows ノードへの参加 ##
によっては、[選択したネットワーク ソリューション](./network-topologies.md)では、次の操作を実行できます。
1. [Windows Server ノード Flannel クラスターへの参加します。](#joining-a-flannel-cluster)
2. [Windows Server ノード ToR スイッチのクラスターへの参加します。](#joining-a-tor-cluster)

### <a name="joining-a-flannel-cluster"></a>Flannel クラスターへの参加 ###
[この Microsoft リポジトリ](https://github.com/Microsoft/SDN/tree/master/Kubernetes/flannel/l2bridge)クラスターにこのノードを結合するのに役立つ Flannel 配置スクリプトのコレクションがあります。

ZIP ファイルは、[こちら](https://github.com/Microsoft/SDN/archive/master.zip)から直接ダウンロードできます。 必要なですだけが、`Kubernetes/flannel/l2bridge`ディレクトリの内容を抽出する必要があります`C:\k\`:

```powershell
[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12
wget https://github.com/Microsoft/SDN/archive/master.zip -o master.zip
Expand-Archive master.zip -DestinationPath master
mv master/SDN-master/Kubernetes/flannel/l2bridge/* C:/k/
rm -recurse -force master,master.zip
```

これに加え、クラスター サブネット (例: チェック「10.244.0.0/16」) が正しいことを確認する必要があります。
- [ネット conf.json](https://github.com/Microsoft/SDN/blob/master/Kubernetes/flannel/l2bridge/net-conf.json)


[事前に準備して Windows ノード](#preparing-a-windows-node)を想定していますと`c:\k`ディレクトリは次のようには、ノードを結合する準備ができたらします。

![テキスト](./media/flannel-directory.png)

#### <a name="join-node"></a>ノードを結合します。 #### 
Windows ノードを結合するプロセスをシンプルにのみ実行に必要なを起動する 1 つの Windows スクリプト`kubelet`、 `kube-proxy`、 `flanneld`] ノードに参加します。

> [!Note]
> 更新された次のようなその他のファイルをダウンロードする[このスクリプト](https://github.com/Microsoft/SDN/blob/master/Kubernetes/flannel/l2bridge/start.ps1)`flanneld`実行可能ファイルと[インフラストラクチャ ポッドの Dockerfile](https://github.com/Microsoft/SDN/blob/master/Kubernetes/windows/Dockerfile) *とするを実行*します。 複数の powershell ウィンドウを 2 回目 l2bridge ポッド ネットワークの新しい外部としての作成中に、ネットワーク障害の数秒だけでなく開く/閉じるされている可能性があります。

```powershell
cd c:\k
.\start.ps1 -ManagementIP <Windows Node IP> -ClusterCIDR <Cluster CIDR> -ServiceCIDR <Service CIDR> -KubeDnsServiceIP <Kube-dns Service IP> 
```

> [!tip]
> 既に書き留めたクラスター サブネット、サービス サブネット、および Linux マスター kube DNS IP を[以前](./creating-a-linux-master.md#collect-cluster-information)

これを実行すると、できるようになります。
  * ビューを使用して Windows ノードを結合します。 `kubectl get nodes`
  * 3 つの powershell ウィンドウを開く] のいずれかを参照してください`kubelet`、1 つの`flanneld`、別の `kube-proxy`
  * ホスト エージェント プロセスを参照してください`flanneld`、 `kubelet`、および`kube-proxy`ノードで実行されています。


## <a name="joining-a-tor-cluster"></a>ToR クラスターへの参加 ##
> [!NOTE]
> として、ネットワーク ソリューション[以前](./network-topologies.md#flannel-in-host-gateway-mode)Flannel を選んだ場合は、このセクションを省略できます。

これを行うには、に対する[上位 L3 ルーティング トポロジの Kubernetes の Windows Server コンテナーのセットアップ](https://kubernetes.io/docs/getting-started-guides/windows/#for-1-upstream-l3-routing-topology-and-2-host-gateway-topology)手順を実行する必要があります。 これは、そのそれぞれノード IP に対応付けなどポッド CIDR プレフィックスをノードに割り当てられている上位ルーターを構成することを確認が含まれます。

新しいノードを想定しています「準備完了」がある`kubectl get nodes`、kubelet + kube プロキシが実行されている、上位 ToR ルーターを構成することでは、次の手順に進む準備ができたらします。

## <a name="next-steps"></a>次のステップ ##
このセクションは、Windows の利用者を Kubernetes クラスターへの参加方法を説明します。 手順 5 の準備が整いました。

> [!div class="nextstepaction"]
> [Linux 作業者への参加](./joining-linux-workers.md)

または、いない場合は Linux 作業者が自由に手順 6 にスキップします。

> [!div class="nextstepaction"]
> [Kubernetes リソースを展開します。](./deploying-resources.md)