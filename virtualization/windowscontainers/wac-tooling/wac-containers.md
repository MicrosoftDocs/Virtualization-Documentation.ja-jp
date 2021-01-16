---
title: Windows 管理センターでコンテナーを実行する
description: Windows 管理センターでコンテナーを実行する
keywords: docker、コンテナー、Windows 管理センター
author: vrapolinario
ms.author: viniap
ms.date: 12/23/2020
ms.topic: quickstart
ms.assetid: bb9bfbe0-5bdc-4984-912f-9c93ea67105f
ms.openlocfilehash: d7786caa70d51270e685bf4264e92a3b84df7f1f
ms.sourcegitcommit: 0fed672793b8b0c07253c498ac6f7c98ca5fe2b2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/15/2021
ms.locfileid: "98241613"
---
# <a name="run-new-containers-using-windows-admin-center"></a>Windows 管理センターを使用して新しいコンテナーを実行する

Windows 管理センターを使用すると、コンテナーホストでコンテナーをローカルに実行できます。 

1. コンテナー拡張機能がインストールされている Windows 管理センターを使用して、管理するコンテナーホストを開きます。
2. 左側の [ **ツール** ] で、 **コンテナー** の拡張機能を選択します。 
3. [コンテナーホスト] の下にある [ **イメージ** ] タブを選択します。

    ![[イメージ ] タブ](./media/WAC-Images.png)

4. 実行するイメージを選択し、[ **実行**] をクリックします。

    ![イメージの実行](./media/WAC-RunContainers.png)

5. [ **イメージの実行**] で、コンテナーに関連する構成を指定できます。

    - コンテナー名: これは省略可能な入力です。 作成したコンテナーを追跡するのに役立つコンテナー名を指定することができます。そうしないと、Docker によって汎用的な名前が提供されます。
    - 分離型: 既定のプロセス分離の代わりにハイパーバイザーを使用することを選択できます。 Windows コンテナーの分離モードの詳細については、「 [分離モード](../manage-containers/hyperv-container.md)」を参照してください。
    - 発行ポート: 既定では、Windows コンテナーはネットワークモードに NAT を使用します。 これは、コンテナーホストのポートがコンテナーにマップされることを意味します。 このオプションを使用すると、そのマッピングを指定できます。
    - メモリの割り当てと CPU の数: コンテナーが使用できるメモリの量と Cpu の数を指定できます。 このオプションでは、割り当てられたメモリまたは CPU はコンテナーに割り当てられません。 このオプションでは、コンテナーが割り当てることができる最大サイズを指定します。
    - 追加: 永続ボリュームの-v など、UI にない Docker の実行パラメーターを追加することもできます。 使用可能な Docker 実行パラメーターの詳細については、 [docker のドキュメント](https://docs.docker.com/engine/reference/commandline/run/)を参照してください。

6. コンテナーの構成が完了したら、[ **実行**] を選択します。 [ **コンテナー** ] タブで、実行中のコンテナーの状態を確認できます。

    ![[コンテナー] タブ](./media/WAC-Containers.png)

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [Windows 管理センターでの Azure Container Registry の管理](./wac-acr.md)