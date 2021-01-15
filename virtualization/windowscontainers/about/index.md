---
title: Windows コンテナーについて
description: コンテナーは、オンプレミスおよびクラウドの多様な環境にわたって Windows アプリなどのアプリをパッケージ化して実行するためのテクノロジです。 このトピックでは、Docker や Azure Kubernetes Service の使用法を含め、Microsoft、Windows、および Azure がコンテナーでのアプリの開発とデプロイにどのように役立つかについて説明します。
keywords: Docker, コンテナー
author: taylorb-microsoft
ms.author: jgerend
ms.date: 10/22/2019
ms.topic: overview
ms.assetid: 8e273856-3620-4e58-9d1a-d1e06550448
ms.openlocfilehash: 3ace5ef044b18e8c479f01a30cac87ee11192fad
ms.sourcegitcommit: 24a7d693da95512ac371bdbf6466f46e187c9c58
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/13/2021
ms.locfileid: "98182059"
---
# <a name="windows-and-containers"></a>Windows とコンテナー

コンテナーは、オンプレミスおよびクラウドの多様な環境にわたって Windows と Linux のアプリケーションをパッケージ化して実行するためのテクノロジです。 コンテナーは、アプリの開発、デプロイ、管理を容易にする軽量で分離された環境を提供します。 コンテナーはすばやく開始および停止するので、需要の変化に迅速に対応する必要があるアプリに最適です。 また、軽量であるというコンテナーの性質により、インフラストラクチャの密度と使用率の向上に役立つツールでもあります。

![コンテナーがクラウドまたはオンプレミスでどのように実行されて、ほぼすべての言語で作成されたモノリシック アプリやマイクロサービスをサポートするかを示すグラフィック。](media/about-3-box.png)

計画済みおよび現在利用可能な機能のロードマップを表示するには、「[Windows Server コンテナーのロードマップ](https://github.com/microsoft/Windows-Containers/projects/1)」を参照してください。

## <a name="the-microsoft-container-ecosystem"></a>Microsoft コンテナーのエコシステム

Microsoft では、コンテナーでのアプリの開発とデプロイに役立つ多数のツールとプラットフォームを提供しています。

- [Docker Desktop](https://store.docker.com/editions/community/docker-ce-desktop-windows) を使用した開発およびテストのために、<strong>Windows ベースまたは Linux ベースのコンテナーを Windows 10 で実行します</strong>。これにより、Windows に組み込まれているコンテナー機能を利用することができます。 また、[Windows Server でネイティブにコンテナーを実行する](../quick-start/set-up-environment.md?tabs=Windows-Server)こともできます。
- Docker、Docker Compose、Kubernetes、Helm、およびその他の便利なテクノロジのサポートを含む、[Visual Studio での強力なコンテナー サポート](/visualstudio/containers/overview) および [Visual Studio Code](https://code.visualstudio.com/docs/azure/docker) を使用して、<strong>Windows ベースのコンテナーを開発、テスト、発行、デプロイ</strong>します。
- Visual Studio と Visual Studio Code 内から直接プッシュおよびプルして、他のユーザーが使用できるようにパブリック DockerHub に、または組織の独自の開発とデプロイのためにプライベート [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) に<strong>アプリをコンテナー イメージとして発行</strong>します。
- <strong>Azure (またはその他のクラウド) に大規模にコンテナーをデプロイします</strong>。

  - Azure Container Registry などのコンテナー レジストリからアプリ (コンテナー イメージ) をプルし、[Azure Kubernetes Service (AKS)](/azure/aks/intro-kubernetes) や [Azure Service Fabric](/azure/service-fabric/) などのオーケストレーターを使用して大規模にデプロイおよび管理します。
  - Azure Kubernetes Service は、コンテナーを Azure の仮想マシンにデプロイし、数十、数百、または数千個であってもそれらを大規模に管理します。 Azure の仮想マシンは、カスタマイズされた Windows Server イメージ (Windows ベースのアプリをデプロイしている場合)、またはカスタマイズされた Ubuntu Linux イメージ (Linux ベースのアプリをデプロイしている場合) のいずれかを実行します。
- [AKS エンジンを使用した Azure Stack](/azure-stack/user/azure-stack-kubernetes-aks-engine-overview) (Linux コンテナーでのプレビュー段階) または [OpenShift を使用した Azure Stack](/azure/virtual-machines/linux/openshift-azure-stack) を使って、<strong>コンテナーをオンプレミスにデプロイ</strong>します。 また、Windows Server に自分で Kubernetes をセットアップすることもできます (「[Windows で使用する Kubernetes](../kubernetes/getting-started-kubernetes-windows.md)」を参照)。さらに、Microsoft では、[RedHat OpenShift Container Platform で Windows コンテナー](https://techcommunity.microsoft.com/t5/Networking-Blog/Managing-Windows-containers-with-Red-Hat-OpenShift-Container/ba-p/339821)を実行するためのサポートについても取り組んでいます。

## <a name="how-containers-work"></a>コンテナーのしくみ

コンテナーは、ホスト オペレーティング システムでアプリケーションを実行するための、分離された軽量のサイロです。 コンテナーは、この図に示すように、ホスト オペレーティング システムのカーネル (オペレーティング システムの埋め込まれた配管のようなものと見なすことができる) の上に構築されます。

![コンテナーがカーネルの上でどのように実行されるかを示すアーキテクチャ図](media/container-diagram.svg)

コンテナーはホスト オペレーティング システムのカーネルを共有しますが、コンテナーがそれに自由にアクセスすることはできません。 代わりに、コンテナーは、分離された (場合によっては、仮想化された) システムのビューを取得します。 たとえば、コンテナーは、ファイル システムとレジストリの仮想化されたバージョンにアクセスできますが、変更はコンテナーにのみ影響し、停止すると破棄されます。 データを保存するために、コンテナーは [Azure Disk](https://azure.microsoft.com/services/storage/disks/) やファイル共有 ([Azure Files](https://azure.microsoft.com/services/storage/files/) など) の永続的ストレージをマウントできます。

コンテナーはカーネルの上に構築されますが、カーネルは、アプリが実行する必要のあるすべての API とサービスを提供するわけではありません。これらのほとんどは、ユーザー モードのカーネルの上で実行されるシステム ファイル (ライブラリ) によって提供されます。 コンテナーはホストのユーザー モード環境から分離されているため、コンテナーにはこれらのユーザー モード システム ファイルの独自のコピー (基本イメージと呼ばれるものにパッケージ化されている) が必要です。 基本イメージは、コンテナーが構築される基本層として機能し、カーネルによって提供されないオペレーティング システム サービスを提供します。 コンテナー イメージの詳細については後で説明します。

## <a name="containers-vs-virtual-machines"></a>コンテナーと仮想マシン

コンテナーとは対照的に、仮想マシン (VM) は、次の図に示すように、独自のカーネルを含む完全なオペレーティング システムを実行します。

![ホスト オペレーティング システムの横で、VM がどのようにオペレーティング システム全体を実行するかを示すアーキテクチャ図](media/virtual-machine-diagram.svg)

コンテナーと仮想マシンにはそれぞれの使用法があります。実際、コンテナーの多くのデプロイでは、仮想マシンをハードウェア上で直接実行するのではなく、ホスト オペレーティング システムとして使用します (特にクラウドでコンテナーを実行している場合)。

これらの補完的なテクノロジの類似点と相違点の詳細については、「[コンテナーと仮想マシン](containers-vs-vm.md)」を参照してください。

## <a name="container-images"></a>コンテナー イメージ

すべてのコンテナーは、コンテナー イメージから作成されます。 コンテナー イメージは、ローカル コンピューターまたはリモート コンテナー レジストリに存在する多数の層に編成されたファイルのバンドルです。 コンテナー イメージは、アプリをサポートするために必要なユーザー モードのオペレーティング システム ファイル、アプリ、アプリのランタイムまたは依存関係、アプリを正常に実行するために必要なその他の構成ファイルで構成されています。

Microsoft では、独自のコンテナー イメージを構築するための出発点として使用できるいくつかのイメージ (基本イメージと呼ばれる) を提供しています。

* <strong>Windows</strong> - Windows API とシステム サービス (サーバー ロールは除く) の完全セットが含まれています。
* <strong>Windows Server Core</strong> - Windows Server API (つまり、完全な .NET framework) のサブセットを含む小さいイメージ。 これには、ほとんどのサーバー ロールも含まれています。ただし、Fax サーバーは含まれていません。
* <strong>Nano Server</strong> - .NET Core API と一部のサーバー ロールのサポートが含まれた最小の Windows Server イメージ。
* <strong>Windows 10 IoT Core</strong> - ARM または x86/x64 のプロセッサを実行する小型の IoT デバイスのハードウェア製造元によって使用される Windows のバージョン。

既に説明したように、コンテナー イメージは一連の層で構成されています。 各層には一連のファイルが含まれており、それが重なり合って、コンテナー イメージを表します。 コンテナーには複数層の性質があるため、Windows コンテナーを構築するために、常に基本イメージをターゲットにする必要はありません。 代わりに、必要なフレームワークを既に保持している別のイメージをターゲットにすることができます。 たとえば、.NET チームは、.NET Core ランタイムを保持する [.NET Core イメージ](https://hub.docker.com/_/microsoft-dotnet-core)を発行します。 これにより、ユーザーは、.NET Core をインストールするプロセスを繰り返す必要がなくなり、代わりにこのコンテナー イメージの層を再利用することができます。 .NET Core イメージ自体は、Nano Server に基づいて構築されています。

詳細については、「[コンテナーの基本イメージ](../manage-containers/container-base-images.md)」を参照してください。

## <a name="container-users"></a>コンテナーのユーザー

### <a name="containers-for-developers"></a>開発者向けのコンテナー

コンテナーを使用すると、開発者は、より品質の高いアプリをより短時間で作成して出荷することができます。 コンテナーにより、開発者は、数秒で複数の環境に同様にデプロイできるコンテナー イメージを作成できます。 コンテナーは、ホスト ファイル システムに影響を与えることなくチーム間でコードを共有し、開発環境をブートストラップするための簡単なメカニズムとして機能します。

コンテナーは、移植性と汎用性を備えており、あらゆる言語で作成されたアプリを実行できます。また、Windows 10 バージョン 1607 以降、または Windows Server 2016 以降を実行しているすべてのコンピューターと互換性があります。 開発者は、コンテナーをノート PC やデスクトップでローカルに作成してテストし、その同じコンテナー イメージを会社のプライベート クラウド、パブリック クラウド、またはサービス プロバイダーにデプロイできます。 コンテナーに備わっている機敏性が、大規模で仮想化されたクラウド環境における最新のアプリ開発パターンをサポートします。

### <a name="containers-for-it-professionals"></a>IT プロフェッショナル向けのコンテナー

管理者は、コンテナーを使用することにより、更新と保守が容易で、ハードウェア リソースをより完全に活用するインフラストラクチャを作成することができます。 IT プロフェッショナルは、コンテナーを使用して、開発、品質保証、運用の各チームに標準化された環境を提供することができます。 システム管理者は、コンテナーを使用することにより、オペレーティング システムのインストールと基礎となるインフラストラクチャの違いを取り除きます。

## <a name="container-orchestration"></a>コンテナーのオーケストレーション

オーケストレーターは、コンテナー ベースの環境をセットアップする際のインフラストラクチャの重要な部分です。 Docker と Windows を使用していくつかのコンテナーを手動で管理することもできますが、多くの場合、アプリでは 5 個、10 個、または数百個ものコンテナーが使用されるため、オーケストレーターが必要となります。

コンテナーのオーケストレーターは、コンテナーの管理を大規模に運用環境で行うために構築されました。 オーケストレーターは、次の機能を提供します。

- 大規模なデプロイ
- ワークロードのスケジュール設定
- ヘルスの監視
- ノードで障害が発生したときのフェールオーバー
- スケールアップまたはスケールダウン
- ネットワーク
- サービス検出
- アプリのアップグレードの調整
- クラスタ ノードのアフィニティ

Windows コンテナーでは、さまざまな種類のオーケストレーターを使用できます。Microsoft では次のオプションを提供しています。
- [Azure Kubernetes Service (AKS)](/azure/aks/intro-kubernetes) - マネージド Azure Kubernetes Service を使用します
- [Azure Service Fabric](/azure/service-fabric/) - マネージド サービスを使用します
- [AKS エンジンを使用した Azure Stack](/azure-stack/user/azure-stack-kubernetes-aks-engine-overview) - オンプレミスの Azure Kubernetes Service を使用します
- [Windows 上の Kubernetes](../kubernetes/getting-started-kubernetes-windows.md) - ユーザー自身が Windows 上に Kubernetes を設定します

## <a name="try-containers-on-windows"></a>Windows でコンテナーを試す

Windows Server または Windows 10 でコンテナーの使用を開始するには、次を参照してください。
> [!div class="nextstepaction"]
> [はじめに: コンテナー用の環境を構成する](../quick-start/set-up-environment.md)

自分のシナリオに適した Azure サービスを決定するには、[Azure コンテナー サービス](https://azure.microsoft.com/product-categories/containers/)と[アプリケーションをホストするために使用する Azure サービスの選択](/azure/architecture/guide/technology-choices/compute-decision-tree)に関する記事を参照してください。