---
title: コンテナーにリフトアンドシフトする
description: 既存のアプリケーションをコンテナーに移行する方法について説明します
keywords: コンテナー、移行
author: v-susbo
ms.author: v-susbo
ms.date: 12/11/2020
ms.topic: quickstart
ms.openlocfilehash: 6185290fa34621c10305b3c5acff138a624c74b1
ms.sourcegitcommit: 24a7d693da95512ac371bdbf6466f46e187c9c58
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/13/2021
ms.locfileid: "98186838"
---
# <a name="lift-and-shift-to-containers"></a>コンテナーにリフトアンドシフトする
このトピックでは、従来のアプリやレガシ アプリをコンテナーにリフト アンド シフトすることで、それらを最新化する方法に関するガイダンスを提供します。 コンテナーに適したアプリの種類を特定し、コードの変更を最小限に抑えながらそれらをリフト アンド シフトする方法について説明します。 現在物理マシンまたは VM 上で実行されている従来の Windows Server アプリケーションの一部は、コンテナーに簡単に移動できます。 

計画済みおよび現在利用可能な機能のロードマップを表示するには、「[Windows Server コンテナーのロードマップ](https://github.com/microsoft/Windows-Containers/projects/1)」を参照してください。

## <a name="benefits-of-using-containers"></a>コンテナーを使用する利点
コンテナーは、そのコンテナーの外部に存在するアプリやプロセスの影響を受けない独自のパッケージにアプリケーションを分離する手段であるため、これによってコストが削減され、移植および管理しやすくなっているのがすぐにわかります。
コンテナーを使用してアプリを構築することで、インフラストラクチャを問わずあらゆるアプリケーションを構築して実行する機敏性が大幅に向上します。 コンテナーを使用すると、Microsoft の開発者ツールやオペレーティング システム全体にわたる Docker 統合により、コードをほとんどまたはまったく変更することなく、あらゆるアプリを開発環境から運用環境に移行できます。 コンテナーを使用する利点の全一覧については、「[Windows コンテナーとして既存の .NET アプリを展開する](https://docs.microsoft.com/dotnet/architecture/modernize-with-azure-containers/modernize-existing-apps-to-cloud-optimized/deploy-existing-net-apps-as-windows-containers)」を参照してください。

## <a name="supported-applications-for-containers"></a>コンテナーに対応しているアプリケーション

コンテナー化するアプリを選択する前に、次の表を確認してください。 

| Application | 考慮事項 |
|-------------|----------------|
| Web アプリ | Web ベースのアプリは、コンテナー化の候補として適しています。 ASP.NET でビルドされたレガシ アプリの場合、使用する最適なイメージは、.NET 3.5 用にプロビジョニングされた ASP.NET イメージです。これを使用すると、ASP.NET 2.0 と 1.X のアプリも実行できます。 |
| Windows Communication Foundation (WCF) サービス | WCF によりビルドされたこれらのサービス指向アプリの多くは IIS でホストされますが、別の Web アプリや Windows サービスなどの他のアプリやサービス内にホストすることもできます。 |
| Windows サービス | これらのアプリは Windows のバックグラウンド サービスとして実行され、コンテナー化できます。 ただし、サービスはバックグラウンドで実行されるため、コンテナーを実行し続けるには、フォアグラウンド プロセスを作成する必要があります。 |
|  コンソール アプリケーション | これらはコマンド ラインから実行されるアプリで、コンテナーの候補として適しています。 |

また、[コンテナーに対応していないアプリ](#applications-not-supported-by-containers)の一覧も確認してください。

## <a name="lift-and-shift-windows-applications"></a>Windows アプリケーションのリフト アンド シフト

### <a name="plan-how-to-lift-and-shift-legacy-applications"></a>レガシ アプリケーションをリフト アンド シフトする方法を計画する 

次の手順を使用して、従来のアプリとレガシ アプリをコンテナーに移動する方法を計画します。

1. 必要な Windows オペレーティング システムのベース イメージを決定します ([Windows Server Core](https://hub.docker.com/_/microsoft-windows-servercore) または [Nano Server](https://hub.docker.com/_/microsoft-windows-nanoserver) のいずれか)。
2. コンテナーの種類、たとえば、プロセス分離またはハイパーバイザー分離のどちらにする必要があるかを決定します。 詳細については、「[分離モード](../manage-containers/hyperv-container.md)」を参照してください。 現在、AKS と Azure Kubernetes Service on Azure Stack HCI では、プロセス分離コンテナーのみをサポートしており、サポートされている唯一のコンテナー ホストは、Windows Server 2019 Datacenter です。 今後のリリースでは、AKS と Azure Kubernetes Service on Azure Stack HCI の両方で、ハイパーバイザー分離コンテナーをサポートするようになります。
3. コンテナーのセキュリティを構成します。 グループの管理されたサービス アカウント (gMSA) を使用して実行するように Windows コンテナーを構成するには、「[Windows コンテナー用に gMSA を作成する](../manage-containers/manage-serviceaccounts.md)」を参照してください。
4. アプリをコンテナー化します。 これを行うには、Windows Admin Center に [**Containers** 拡張機能をインストール](../wac-tooling/wac-extension.md)する必要があります。 その後、Windows Admin Center を使用して[新しいコンテナー イメージを作成](../wac-tooling/wac-images.md)し、それらを[実行](../wac-tooling/wac-containers.md)できます。 
5. [コンテナー レジストリを作成](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-powershell)し、そのレジストリに[イメージをアップロード](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-powershell#push-image-to-registry)することで、レガシ アプリをプッシュします。
6. Windows がサポートされている Kubernetes 環境にデプロイします。 [Windows Admin Center](https://docs.microsoft.com/azure-stack/aks-hci/setup) または [PowerShell](https://docs.microsoft.com/azure-stack/aks-hci/setup-powershell) を使用して、[Azure Kubernetes Service](https://docs.microsoft.com/azure/aks/) または Azure Kubernetes Service on Azure Stack HCI のいずれかにデプロイできます。

次のフローチャートを参考に、リフト アンド シフトするアプリケーションを決定し、その方法について計画を立ててください。

![Windows アプリをリフト アンド シフトする方法に関するフローチャートを示すグラフィック。](./media/DecisionTreeflowchartv2.jpg#lightbox)    

## <a name="applications-not-supported-by-containers"></a>コンテナーでサポートされていないアプリケーション

2018 年 5 月の時点で、次のアプリケーションは Windows コンテナーでサポートされていません。
-  Microsoft Message Queuing (MSMQ) と Windows コンテナーを使用する場合にサポートされるシナリオの詳細については、Microsoft テクニカル コミュニティの記事「[MSMQ と Windows コンテナー](https://techcommunity.microsoft.com/t5/containers/msmq-and-windows-containers/ba-p/1981414)」を参照してください。 追加情報については、[Windows Server ディスカッション フォーラム](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)と [Microsoft Developer Network フォーラム](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)を参照してください。 
- 現在、Microsoft 分散トランザクション コーディネーター (MSDTC) は、Windows コンテナーではサポートされていません。 詳細については、[GitHub の問題](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)に関するページを参照してください。    
- Microsoft Office では現在、コンテナーがサポートされていません。 詳細については、[UserVoice 要求フォーラム](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)を参照してください。  
- ビジュアル ユーザー インターフェイスが使用されているクライアント アプリはサポートされていません。  
- Windows インフラストラクチャのロールはサポートされていません。 これには、DNS、DHCP、DC、NTP、プリント サービス、ファイル サーバー、および ID とアクセス管理 (IAM) が含まれます。  
  
Windows コンテナーの [GitHub リポジトリ](https://github.com/microsoft/Windows-Containers/issues)を使用して、コミュニティからのサポートされていないシナリオと要求に関する追加情報を確認してください。