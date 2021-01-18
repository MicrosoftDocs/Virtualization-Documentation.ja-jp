---
title: Windows コンテナーの要件
description: Windows コンテナーの要件
keywords: メタデータ、コンテナー
author: taylorb-microsoft
ms.author: taylorb
ms.date: 10/22/2019
ms.topic: deployment
ms.assetid: 3c3d4c69-503d-40e8-973b-ecc4e1f523ed
ms.openlocfilehash: 6e6007d2b953f07d9b5b5d0cf1bec58dcbcd2fd7
ms.sourcegitcommit: 24a7d693da95512ac371bdbf6466f46e187c9c58
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/13/2021
ms.locfileid: "98182109"
---
# <a name="windows-container-requirements"></a>Windows コンテナーの要件

このガイドでは、Windows コンテナー ホストの要件を一覧で示します。

## <a name="operating-system-requirements"></a>オペレーティング システムの要件

- Windows コンテナーの機能は、Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows 10 Professional および Enterprise エディション (バージョン 1607 以降) で使用できます。
- Hyper-V による分離を実行する前に、Hyper-V ロールをインストールする必要があります。
- Windows Server コンテナー ホストでは、Windows を c:\ にインストールする必要があります。 Hyper-V で分離されたコンテナーのみを展開する場合、この制限は適用されません。

## <a name="virtualized-container-hosts"></a>仮想化されたコンテナー ホスト

Windows コンテナー ホストが Hyper-V 仮想マシンから実行され、Hyper-V による分離もホストする場合、入れ子になった仮想化を有効にする必要があります。 入れ子になった仮想化には次の要件があります。

- 仮想化された Hyper-V ホスト用に少なくとも 4 GB の RAM を利用できる。
- ホスト システム上に、Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、または Windows 10。仮想マシンに、Windows Server (Full または Server Core)。
- Intel VT-x に対応したプロセッサ (この機能は現在 Intel プロセッサのみで使用可能です)。
- コンテナー ホスト VM にも、少なくとも 2 つの仮想プロセッサが必要。

### <a name="memory-requirements"></a>メモリの要件

コンテナーに対して利用可能なメモリの制限は、[リソース コントロール](../manage-containers/resource-controls.md)を使用するか、コンテナー ホストをオーバーロードすることによって構成できます。  コンテナーの起動と基本的なコマンド (ipconfig、dir など) の実行に必要なメモリの最小量を以下に示します。

>[!NOTE]
>これらの値では、コンテナー間で共有しているリソースや、そのコンテナーで実行されるアプリケーションの要件が考慮されていません。  たとえば、512 MB の空きメモリを持つホストでは、Hyper-V による分離の下で複数の Server Core コンテナーを実行できます。これは、それらのコンテナーがリソースを共有するためです。

#### <a name="windows-server-2016"></a>Windows Server 2016

| TestVM  | Windows Server コンテナー | Hyper-V による分離    |
| ----------- | ------------------------ | -------------------- |
| Nano Server | 40 MB                     | 130 MB + 1 GB のページファイル |
| Server Core | 50 MB                     | 325 MB + 1 GB のページファイル |

#### <a name="windows-server-semi-annual-channel"></a>Windows Server (半期チャネル)

| TestVM  | Windows Server コンテナー | Hyper-V による分離    |
| ----------- | ------------------------ | -------------------- |
| Nano Server | 30 MB                     | 110 MB + 1 GB のページファイル |
| Server Core | 45 MB                     | 360 MB + 1 GB のページファイル |

## <a name="see-also"></a>関連項目

[オンプレミスのシナリオでの Windows コンテナーおよび Docker のサポート ポリシー](https://support.microsoft.com/help/4489234/support-policy-for-windows-containers-and-docker-on-premises)