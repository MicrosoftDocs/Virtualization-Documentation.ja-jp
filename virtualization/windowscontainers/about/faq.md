---
title: Windows コンテナーに関する FAQ
description: Windows Server コンテナー FAQ
keywords: Docker, コンテナー
author: PatrickLang
ms.author: PatrickLang
ms.date: 10/25/2019
ms.topic: overview
ms.assetid: 25de368c-5a10-40a4-b4aa-ac8c9a9ca022
ms.openlocfilehash: 9489b785a097340de0d4acba7720ac7ae297739b
ms.sourcegitcommit: 24a7d693da95512ac371bdbf6466f46e187c9c58
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/13/2021
ms.locfileid: "98182039"
---
# <a name="frequently-asked-questions-about-containers"></a>コンテナーについてよく寄せられる質問

Windows Server コンテナーについて質問がある場合は、それが回答済みであるかどうかを以下の一覧から確認してください。

## <a name="whats-the-difference-between-linux-and-windows-server-containers"></a>Linux コンテナーと Windows Server コンテナーの違いは何ですか。

Linux コンテナーと Windows Server コンテナーはどちらも同様のテクノロジをカーネルとコア オペレーティング システム内に実装します。 違いは、プラットフォームと、コンテナー内で実行されるワークロードに由来します。

Windows Server コンテナーを使用しているお客様は、.NET、ASP.NET、PowerShell などの既存の Windows テクノロジと統合できます。

## <a name="what-are-the-prerequisites-for-running-containers-on-windows"></a>Windows でコンテナーを実行するための前提条件は何ですか。

コンテナーは、Windows Server 2016 でプラットフォームに導入されました。 コンテナーを使用するには、Windows Server 2016 または Windows 10 Anniversary アップデート (バージョン 1607) 以降のいずれかが必要です。 詳細については、[システム要件](../deploy-containers/system-requirements.md)を参照してください。

## <a name="what-windows-operating-systems-are-supported"></a>どの Windows オペレーティング システムがサポートされていますか?

AKS on Azure Stack HCI では、コンテナー ホストの OS バージョンとして Windows Server 2019 が使用され、プロセスの分離のみがサポートされます。 Windows コンテナーのバージョンの互換性については、「[Windows コンテナーのバージョンの互換性](../deploy-containers/version-compatibility.md)」を参照してください。

## <a name="how-do-i-patch-my-windows-nodes"></a>Windows ノードに修正プログラムを適用するにはどうすればいいですか?

最新の修正プログラムと更新プログラムを取得するには、AKS on Azure Stack HCI の Windows Server ノードをアップグレードする必要があります。 AKS on Azure Stack HCI の Windows ノードでは、Windows Update が有効になっていません。 ただし、AKS on Azure Stack HCI で Windows Server ノードのイメージを定期的に更新することで、Windows Update を利用できるようになります。

## <a name="can-my-windows-server-containers-use-gmsa"></a>Windows Server コンテナーで gMSA を使用できますか?

はい、gMSA はドメインに参加している Windows ワーカー ノードでサポートされています。 Windows コンテナーで gMSA を使用する方法の詳細については、「[gMSA を使用するための Windows ノードの準備](https://docs.microsoft.com/azure-stack/aks-hci/prepare-windows-nodes-gmsa)」を参照してください。

## <a name="what-are-wcow-and-lcow"></a>WCOW と LCOW とは何ですか。

WCOW とは、「Windows 上の Windows コンテナー」の略です。 LCOW とは、「Windows 上の Linux コンテナー」の略です。

## <a name="how-are-containers-licensed-is-there-a-limit-to-the-number-of-containers-i-can-run"></a>コンテナーはどのようにしてライセンス供与されますか。 実行できるコンテナーの数に制限はありますか。

Windows コンテナー イメージ [EULA](../images-eula.md) では、有効なライセンスを持つホスト OS を持つユーザーに依存する使用法について説明しています。 ユーザーが実行できるコンテナーの数は、ホスト OS のエディションと、コンテナーを実行されている[分離モード](../manage-containers/hyperv-container.md)によって異なります。また、これらのコンテナーが開発/テスト目的または運用環境のどちらで実行されているかによっても異なります。

|ホスト OS                                                         |プロセス分離コンテナーの制限                   |Hyper-v 分離コンテナーの制限                   |
|----------------------------------------------------------------|---------------------------------------------------|---------------------------------------------------|
|Windows Server Standard                                         |無制限                                          |2                                                  |
|Windows Server Datacenter                                       |無制限                                          |無制限                                          |
|Windows 10 Pro および Enterprise                                   |無制限 *(テストまたは開発目的のみ)*|無制限 *(テストまたは開発目的のみ)*|
|Windows 10 IoT Core および Enterprise                             |無制限*                                         |無制限*                                          |

Windows Server コンテナー イメージの使用法は、その[エディション](/windows-server/get-started-19/editions-comparison-19.md)でサポートされている仮想化ゲストの数を確認することによって決定されます。 <br/>

>[!NOTE]
>\*Windows の IoT エディション上のコンテナーの実稼働環境は、Windows 10 コアのランタイム イメージまたは Windows 10 IoT Enterprise デバイスライセンス (「Windows IoT コマーシャル契約」) の Microsoft 商用利用条件に同意したかどうかによって異なります。 Windows IoT の商用契約書に記載されている追加のご契約条件および制限は、運用環境でのコンテナー イメージの使用に適用されます。 許可されている内容とそうではないものを正確に解釈するために、[コンテナー イメージ EULA](../images-eula.md) をお読みください。

## <a name="as-a-developer-do-i-have-to-rewrite-my-app-for-each-type-of-container"></a>開発者として、コンテナーの種類ごとにアプリを再書き込みする必要がありますか。

いいえ。 Windows コンテナー イメージは Windows Server コンテナーと Hyper-V 分離で共通です。 コンテナーを開始すると、コンテナーの種類の選択が行われます。 開発者の観点では、Windows Server のコンテナーおよび HYPER-V の分離は、同じことを 2 種類に言い換えたものです。 オープンで拡張可能なこれらは、同じレベルの統合と Docker 経由でのサポートが含まれますが、同じ開発、プログラミング、および管理のエクスペリエンスを提供します。

開発者は、適切な実行時フラグを指定する以外には、何も変更せずに、Windows Server のコンテナーを使用して、コンテナーのイメージを作成し、HYPER-V 分離でそれを展開したり、またはその逆を行うことができます。

Windows Server コンテナーは、入れ子になった構成と比較して、スピンアップ時間の低減、ランタイム パフォーマンスの高速化など、速度が重要な場合に密度とパフォーマンスを格段に向上させています。 HYPER-V 分離では、その名の通り、1 つのコンテナーで実行されるコードが危険にさらすことはできないかどうか、または、ホスト オペレーティング システムまたは同じホストで実行されている他のコンテナーに影響を与えることを保証するよう幅広く分離しています。 これは、SaaS アプリケーションやコンピューティングのホストなど、信頼できないコードをホストするための要件を持つマルチテナント シナリオに便利です。

## <a name="can-i-run-windows-containers-in-process-isolated-mode-on-windows-10"></a>Windows 10 でプロセス分離モードで Windows コンテナーを実行できますか。

Windows 10 2018 年 10 月アップデート以降では、プロセス分離を使用して Windows コンテナーを実行できますが、まず、`docker run` でコンテナーを実行するときに `--isolation=process` フラグを使用してプロセス分離を直接要求する必要があります。 プロセス分離は、Windows 10 Pro、Windows 10 Enterprise、Windows 10 IoT Core、Windows 10 IoT Enterprise と互換性があります。

この方法で Windows コンテナーを実行する場合は、ホストで Windows 10 build 17763 以降が実行されていること、およびエンジン 18.09 以降の Docker バージョンがあることを確認する必要があります。

> [!WARNING]
> IoT Core および IoT Enterprise ホスト (追加の使用条件に同意した後) とは別に、この機能は開発とテストのみを目的としています。 運用環境のデプロイでは、引き続き Windows Server をホストとして使用する必要があります。 この機能を使用することにより、ホストとコンテナーのバージョン タグが一致するようにする必要があります。そうしないと、コンテナーの起動に失敗したり、未定義の動作が発生したりする可能性があります。

## <a name="how-do-i-make-my-container-images-available-on-air-gapped-machines"></a>物理的に隔離されたコンピューターでコンテナー イメージを使用できるようにする操作方法。

Windows コンテナーの基本イメージには、配布がライセンスによって制限されている成果物が含まれています。 これらのイメージをビルドしてプライベート レジストリまたはパブリック レジストリにプッシュすると、基本レイヤーがプッシュされることはありません。 代わりに、Azure クラウド ストレージに存在する実際の基本レイヤーを指す外部レイヤーの概念を使用します。

これにより、プライベート コンテナー レジストリのアドレスからイメージをプルすることしかできない物理的に隔離されたコンピューターがある場合に、処理が複雑になる可能性があります。 この場合、基本イメージを取得するために外部レイヤーに従う試行は機能しません。 外部レイヤーの動作をオーバーライドするには、Docker デーモンで `--allow-nondistributable-artifacts` フラグを使用することができます。

> [!IMPORTANT]
> このフラグを使用すると、Windows コンテナーの基本イメージ ライセンスのご契約条件に準拠する義務を排除することはできません。パブリックまたはサードパーティによる再配布のために Windows コンテンツを投稿することはできません。 お使いの環境内で使用できます。

## <a name="additional-feedback"></a>その他のフィードバック

FAQ に何かを追加しますか？ [コメント] セクションで新しいフィードバックの問題を開くか、GitHub を使用してこのページのプル要求を設定します。
