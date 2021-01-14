---
title: Windows 管理センターでコンテナーイメージを管理する
description: WAC でコンテナーイメージを管理する
keywords: docker、コンテナー、Windows 管理センター
author: viniap
ms.author: viniap
ms.date: 12/23/2020
ms.topic: quickstart
ms.assetid: bb9bfbe0-5bdc-4984-912f-9c93ea67105f
ms.openlocfilehash: 9cdad44d0e588b64a6157a20a24ae6da84557f8f
ms.sourcegitcommit: 24a7d693da95512ac371bdbf6466f46e187c9c58
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/13/2021
ms.locfileid: "98186739"
---
# <a name="manage-container-images-on-windows-admin-center"></a>Windows 管理センターでコンテナーイメージを管理する

このトピックでは、Windows 管理センターでコンテナーイメージを管理する方法について説明します。 コンテナーイメージは、Windows マシンまたはその他のクラウドサービス (Azure Kubernetes Service など) で新しいコンテナーを作成するために使用されます。 Windows イメージの詳細については、「 [コンテナーイメージの概要](https://docs.microsoft.com/virtualization/windowscontainers/about/#container-images)」を参照してください。

## <a name="pull-container-images"></a>コンテナーイメージのプル

コンテナーホストをデプロイした後、次の手順では、イメージから新しいコンテナーを作成できるように、コンテナーイメージをプル (またはダウンロード) します。 Windows 管理センターを使用して、ターゲットのコンテナーホストでコンテナーの拡張機能を選択することで、新しいコンテナーイメージをプルできます。 次に、コンテナーの **ホスト****の下** にある [**イメージ**] タブを選択し、[**プル**] オプションを選択します。

![コンテナーイメージのプル](./media/WAC-Pull.png)

**プルコンテナーイメージ** の設定で、プルするイメージの URL とタグを指定します。 また、そのリポジトリのすべてのタグ付けされたイメージをプルするオプションを選択することもできます。

プルするイメージがプライベートリポジトリ上にある場合は、そのリポジトリに対して認証するためのユーザー名とパスワードを指定します。 リポジトリが Azure Container Registry でホストされている場合は、Windows 管理センターでネイティブ Azure 認証を使用してイメージにアクセスします。 これには、Windows 管理センターインスタンスが Azure に接続され、Azure アカウントで認証される必要があります。 Windows 管理センターインスタンスを Azure に接続する方法の詳細については、「 [azure 統合の構成](https://docs.microsoft.com/windows-server/manage/windows-admin-center/azure/azure-integration)」を参照してください。

どのイメージをプルするかわからない場合、Windows 管理センターには、Microsoft の共通イメージの一覧が表示されます。 **一般的な [Windows イメージ**] ドロップダウンを選択すると、一般的にプルされる基本イメージの一覧が表示されます。 プルするイメージを選択すると、Windows 管理センターによってリポジトリとタグのフィールドが入力されます。

## <a name="push-container-images"></a>コンテナーイメージのプッシュ

コンテナーイメージを作成したら、そのイメージを一元化されたリポジトリにプッシュして、他のコンテナーホストまたはクラウドサービスがイメージをプルできるようにすることをお勧めします。

Windows 管理センターの [**コンテナー** ] 拡張の [**イメージ**] タブで、プッシュする wan のイメージを選択し、[**プッシュ**] をクリックします。

![コンテナーイメージのプッシュ](./media/WAC-Push.png)

**プッシュコンテナーイメージ** の設定では、イメージの名前とタグをプッシュ (アップロード) する前に変更できます。 また、Azure Container Registry の汎用リポジトリまたはリポジトリのどちらにプッシュするかを選択することもできます。 汎用リポジトリの場合は、ユーザー名とパスワードを入力する必要があります。 Azure Container Registry には、Windows 管理センターで統合認証を使用できます。 Azure では、イメージをプッシュするサブスクリプションとレジストリを選択することもできます。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [Windows 管理センターで新しいコンテナーを作成する](./wac-images.md) 