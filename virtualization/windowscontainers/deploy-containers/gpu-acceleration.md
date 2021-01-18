---
title: Windows コンテナーでの GPU アクセラレーション
description: Windows コンテナーに存在する GPU アクセラレーションのレベル
keywords: Docker, コンテナー, デバイス, ハードウェア
author: v-susbo
ms.author: v-susbo
ms.date: 12/29/2020
ms.topic: how-to
ms.openlocfilehash: c6148f5703a3a50628ad81b506a7aac571781cd4
ms.sourcegitcommit: 24a7d693da95512ac371bdbf6466f46e187c9c58
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/13/2021
ms.locfileid: "98182029"
---
# <a name="gpu-acceleration-in-windows-containers"></a>Windows コンテナーでの GPU アクセラレーション

コンテナー化された多くのワークロードでは、CPU コンピューティング リソースが十分なパフォーマンスを提供します。 しかし、特定のクラスのワークロードでは、GPU (グラフィックス処理装置) によって提供される超並列コンピューティング能力により、処理速度が大幅に向上し、コストの削減とスループットの大幅な向上も実現できます。

GPU は、従来のレンダリングやシミュレーションから機械学習のトレーニングや推論まで、多くの一般的なワークロードで幅広く使用されるツールになっています。 Windows コンテナーでは、DirectX 用の GPU アクセラレーションと、その上に構築されたすべてのフレームワークがサポートされています。

> [!NOTE]
> この機能は、Docker Desktop バージョン 2.1、および Docker エンジン - Enterprise バージョン 19.03 以降で使用できます。

## <a name="requirements"></a>要件

この機能が動作するには、お使いの環境が次の要件を満たしている必要があります。

- コンテナー ホストでは、Windows Server 2019 または Windows 10 バージョン 1809 以降が実行されている必要があります。
- コンテナーの基本イメージは、[mcr.microsoft.com/windows:1809](https://hub.docker.com/_/microsoft-windows) 以降である必要があります。 Windows Server Core および Nano Server のコンテナー イメージは、現在サポートされていません。
- コンテナー ホストでは、Docker エンジン 19.03 以降が実行されている必要があります。
- コンテナー ホストには、ディスプレイ ドライバー バージョン WDDM 2.5 以降を実行している GPU が必要です。

ディスプレイ ドライバーの WDDM バージョンを確認するには、コンテナー ホストで DirectX 診断ツール (dxdiag.exe) を実行します。 ツールの [ディスプレイ] タブで、次に示すように [ドライバー] セクションを確認します。

![Dxdiag](media/dxdiag.png)

## <a name="run-a-container-with-gpu-acceleration"></a>GPU アクセラレーションを使用してコンテナーを実行する

GPU アクセラレーションを使用してコンテナーを起動するには、次のコマンドを実行します。

```shell
docker run --isolation process --device class/5B45201D-F2F2-4F3B-85BB-30FF1F953599 mcr.microsoft.com/windows:1809
```

> [!IMPORTANT]
> 現時点では、DirectX (およびその上に構築されたすべてのフレームワーク) が GPU で高速化できる唯一の API です。 サード パーティのフレームワークはサポートされていません。

## <a name="hyper-v-isolated-windows-container-support"></a>Hyper-V で分離された Windows コンテナーのサポート

Hyper-V で分離された Windows コンテナーのワークロードの GPU アクセラレーションは、現在サポートされていません。

## <a name="hyper-v-isolated-linux-container-support"></a>Hyper-V で分離された Linux コンテナーのサポート

Hyper-V で分離された Linux コンテナーのワークロードの GPU アクセラレーションは、現在サポートされていません。

## <a name="more-information"></a>説明を見る

GPU アクセラレーションを活用するコンテナー化された DirectX アプリの完全な例については、「[DirectX コンテナーのサンプル](https://github.com/MicrosoftDocs/Virtualization-Documentation/tree/master/windows-container-samples/directx)」を参照してください。
