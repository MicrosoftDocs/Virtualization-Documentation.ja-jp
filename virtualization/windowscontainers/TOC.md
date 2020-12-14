# [Windows 上のコンテナーに関するドキュメント](index.yml) 

# 概要
## [Windows コンテナーについて](about/index.md)
## [コンテナーとVM](about/containers-vs-vm.md)
## [システム要件](deploy-containers/system-requirements.md)
## [FAQ](about/faq.md)

# 開始
## [環境をセットアップする](quick-start/set-up-environment.md)
## [最初のコンテナーを実行する](quick-start/run-your-first-container.md)
## [サンプル アプリをコンテナー化する](quick-start/building-sample-app.md)

# チュートリアル
## Windows コンテナーを構築する
### [Dockerfile を作成する](manage-docker/manage-windows-dockerfile.md)
### [Dockerfile を最適化する](manage-docker/optimize-windows-dockerfile.md)
## Azure Kubernetes Service on Azure Stack HCI 上で実行する
### [Azure Stack HCI に Kubernetes クラスターを作成する](/azure-stack/aks-hci/create-kubernetes-cluster) 
## Azure Kubernetes Service で実行する
### [AKS で Windows コンテナー クラスターを作成する](/azure/aks/windows-container-cli)
### [現在の制限事項](/azure/aks/windows-node-limitations)
## Service Fabric で実行する
### [最初のコンテナーをデプロイする](/azure/service-fabric/service-fabric-quickstart-containers)
### [Windows コンテナー内の .NET アプリケーションをデプロイする](/azure/service-fabric/service-fabric-host-app-in-a-container)
## Azure App Service で実行する
### [Azure App Service のクイック スタート](/azure/app-service/app-service-web-get-started-windows-container)
### [Windows コンテナーと Azure App Service を使用して ASP.NET アプリを移行する](/azure/app-service/app-service-web-tutorial-windows-containers-custom-fonts)
## Windows 上の Linux コンテナー
### [概要](deploy-containers/linux-containers.md)
### [最初の Linux コンテナーを実行する](quick-start/quick-start-windows-10-linux.md)
## Windows Insider Program でコンテナーを使用する
### [概要](deploy-containers/insider-overview.md)

# 概念
## Windows コンテナーの基本事項
### [コンテナーの基本イメージ](manage-containers/container-base-images.md)
### [分離モード](manage-containers/hyperv-container.md)
### [バージョンの互換性](deploy-containers/version-compatibility.md)
### [コンテナーの更新](deploy-containers/update-containers.md)
### [リソース コントロール](manage-containers/resource-controls.md)
## Docker
### [Windows 上の Docker エンジン](manage-docker/configure-docker-daemon.md)
### [Windows Docker ホストのリモート管理](management/manage_remotehost.md)
## コンテナーのオーケストレーション
### [概要](about/overview-container-orchestrators.md)
### Windows で使用する Kubernetes
#### [Windows で使用する Kubernetes](kubernetes/getting-started-kubernetes-windows.md)
#### [トラブルシューティング](kubernetes/common-problems.md)
#### [Kubernetes バイナリをコンパイルする](kubernetes/compiling-kubernetes-binaries.md)
### Service Fabric
#### [Service Fabric とコンテナー](/azure/service-fabric/service-fabric-containers-overview)
#### [リソース ガバナンス](/azure/service-fabric/service-fabric-resource-governance)
### Docker Swarm
#### [Swarm モード](manage-containers/swarm-mode.md)
## ワークロード
### [プリンター サービス](deploy-containers/print-spooler.md)
## Security
### Group Managed Service Accounts
#### [gMSA を作成する](manage-containers/manage-serviceaccounts.md)
#### [gMSA を使用するようにアプリを構成する](manage-containers/gmsa-configure-app.md)
#### [gMSA を使用してコンテナーを実行する](manage-containers/gmsa-run-container.md)
#### [gMSA を使用してコンテナーを調整する](manage-containers/gmsa-orchestrate-containers.md)
#### [gMSA のトラブルシューティング](manage-containers/gmsa-troubleshooting.md)
## ネットワーク
### [概要](container-networking/architecture.md)
### [ネットワーク トポロジとドライバー](container-networking/network-drivers-topologies.md)
### [ネットワーク分離とセキュリティ](container-networking/network-isolation-security.md)
### [高度なネットワーク オプションを構成する](container-networking/advanced.md)
## 記憶域
### [概要](manage-containers/container-storage.md)
### [永続的ストレージ](manage-containers/persistent-storage.md)
## デバイス
### [ハードウェア デバイス](deploy-containers/hardware-devices-in-containers.md)
### [GPU アクセラレーション](deploy-containers/gpu-acceleration.md)

# 参照先
## [基本イメージのサービス ライフサイクル](deploy-containers/base-image-lifecycle.md)
## [ウイルス対策の最適化](/windows-hardware/drivers/ifs/anti-virus-optimization-for-windows-containers)
## [Container Platform のツール](deploy-containers/containerd.md)
## [コンテナー OS イメージの使用許諾契約書 (EULA)](./images-eula.md)

# 参照情報
## [既知の問題](manage-containers/known-issues.md)
## [コンテナーのサンプル](samples.md)
## [Windows Server コンテナーのロードマップ](https://github.com/microsoft/Windows-Containers/projects/1)
## [トラブルシューティング](troubleshooting.md)
## [コンテナーのフォーラム](https://social.msdn.microsoft.com/Forums/home?forum=windowscontainers)
## [コミュニティのビデオとブログ](communitylinks.md)