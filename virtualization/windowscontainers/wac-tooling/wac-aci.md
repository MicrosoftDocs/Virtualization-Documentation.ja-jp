---
title: Windows 管理センターでの Azure Container Instances の管理
description: Windows 管理センターでの Azure Container Instances
keywords: docker、コンテナー、Windows 管理センター
author: viniap
ms.author: viniap
ms.date: 12/24/2020
ms.topic: tutorial
ms.assetid: bb9bfbe0-5bdc-4984-912f-9c93ea67105f
ms.openlocfilehash: b4de665fdc9adb36281c17d0c0eb7e60e32e9459
ms.sourcegitcommit: 24a7d693da95512ac371bdbf6466f46e187c9c58
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/13/2021
ms.locfileid: "98186694"
---
# <a name="manage-azure-container-instances-using-windows-admin-center"></a>Windows 管理センターを使用して Azure Container Instances を管理する

このトピックでは、Windows 管理センターを使用して Azure Container Instances (ACI) を管理する方法について説明します。 Azure Container Instances は、オーケストレーションすることなく分離コンテナー内で運用できる、あらゆるシナリオ向けのソリューションです。

>[!Note]
>このチュートリアルの手順を実行するには、Azure サブスクリプションが必要です。 Windows 管理センターインスタンスを Azure に接続する方法の詳細については、「 [azure 統合の構成](https://docs.microsoft.com/windows-server/manage/windows-admin-center/azure/azure-integration)」を参照してください。

Windows 管理センターでは、既存のコンテナーインスタンスの一覧表示、インスタンスの起動と停止、インスタンスの削除、高度な管理のための Azure Portal のオープンなど、Azure Container Instances の基本的な管理を実行できます。

![Azure container instance](./media/WAC-ACI.png)

コンテナーインスタンスを使用すると、次の操作を実行できます。

- **Start**: 現在停止している既存のインスタンスを開始します。
- **終了**: 実行中のインスタンスを停止します。
- **削除**: インスタンスを削除します。 これは元に戻すことができず、インスタンスに対して行われたすべての構成を削除します。
- **Azure での管理**: **azure Portal** ウィンドウが開き、選択したコンテナーインスタンスが新しいブラウザータブで管理されます。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [Windows 管理センターでの Azure Container Registry の管理](./wac-acr.md)