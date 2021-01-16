---
title: Windows 管理センターでの Azure Container Registry の管理
description: Windows 管理センターでの Azure Container Registry
keywords: docker、コンテナー、Windows 管理センター
author: vrapolinario
ms.author: viniap
ms.date: 12/24/2020
ms.topic: tutorial
ms.assetid: bb9bfbe0-5bdc-4984-912f-9c93ea67105f
ms.openlocfilehash: cba3af82164c157b416b8ed8c63998f90308187d
ms.sourcegitcommit: 0fed672793b8b0c07253c498ac6f7c98ca5fe2b2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/15/2021
ms.locfileid: "98241663"
---
# <a name="manage-azure-container-registry-using-windows-admin-center"></a>Windows 管理センターを使用して Azure Container Registry を管理する

このトピックでは、Windows 管理センターを使用して Azure Container Registry (ACR) を管理する方法について説明します。 Azure Container Registry では、あらゆる種類のコンテナー デプロイ用のプライベート レジストリにコンテナー イメージや成果物をビルド、保存、管理できます。 

>[!Note]
>このチュートリアルの手順を実行するには、Azure サブスクリプションが必要です。 Windows 管理センターインスタンスを Azure に接続する方法の詳細については、「 [azure 統合の構成](https://docs.microsoft.com/windows-server/manage/windows-admin-center/azure/azure-integration)」を参照してください。

Windows 管理センターでは、次のような Azure Container Registry の基本的な管理を実行できます。
  
- レジストリとイメージの一覧表示 
- 新しいレジストリの作成 
- イメージの削除 
- コンテナーホストにイメージをプルする
- Azure Container Registry に格納されているイメージから Azure Container Instances で新しいコンテナーを開始します

Windows 管理センターを使用して ACR を管理すると、**コンテナーホスト** の [**イメージ**] タブから直接イメージをプッシュできる Azure の場所を準備できます。 作業を開始するには、次の手順に従います。  

1. Windows 管理センターインスタンスを開き、コンテナーホストを選択します。 
2. 左側のウィンドウの [ **ツール** ] で、下にスクロールして、 **コンテナー** の拡張機能を選択します。
3. [ **Azure**] の下の [ **Azure Container Registry** ] タブを開きます。

    ![[Azure Container Registry] タブ](./media/WAC-ACR.png)

## <a name="manage-registries-and-images"></a>レジストリとイメージの管理

新しいレジストリを作成するには、[ **Azure Container Registry** で [ **新しいレジストリの作成**] を選択します。

![新しいレジストリの作成](./media/WAC-ACRNew.png)

[ **新しいレジストリの作成**] で、新しいレジストリの作成に使用するサブスクリプションと、レジストリを割り当てるリソースグループを選択します。 次に、レジストリ名、場所、および SKU を指定します。 各 SKU の価格と機能の詳細については、 [ACR のドキュメント](https://docs.microsoft.com/azure/container-registry/)を参照してください。 [ **作成** ] をクリックして、新しいレジストリを作成します。 完了すると、操作が正常に完了したことを知らせる通知が Windows 管理センターに表示され、新しいレジストリが一覧表示されます。

レジストリとイメージが一覧表示されたら、既存のイメージを削除するか、コンテナーホストにプルしてローカルで使用することができます。 イメージをプルするには、プルするイメージを選択し、[ **イメージのプル**] をクリックします。

![イメージのプル](./media/WAC-ACRPull.png)

プルプロセスが完了すると、Windows 管理センターから通知が表示され、[**コンテナーホスト**] の下にある [**イメージ**] タブでイメージを使用できるようになります。

最後に、ACR でホストされているイメージに基づいて新しいコンテナーを実行できます。 開始するには、実行するイメージを選択し、[ **インスタンスの実行**] をクリックします。

![インスタンスの実行](./media/WAC-ACRRun.png)

[ **実行インスタンス**] で、コンテナー名、使用するサブスクリプション、およびこのインスタンスを実行するリソースグループと場所を指定する必要があります。

次に、このインスタンスの CPU とメモリの割り当てと、必要に応じて開くポートを指定します。 [ **作成** ] をクリックすると、Windows 管理センターによって、インスタンスを実行するためのコマンドが Azure に送信されます。 コンテナーインスタンスの状態は、[ **Azure Container instance** ] タブで確認できます。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [Windows 管理センターで Azure Container Instance を管理する](./wac-aci.md)