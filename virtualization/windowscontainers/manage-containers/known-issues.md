---
title: の既知の問題
description: Windows Server コンテナーに関する既知の問題
keywords: メタデータ, コンテナー, バージョン
author: weijuans
ms. author: weijuans
manager: taylob
ms.date: 05/26/2020
ms.openlocfilehash: f53ff0c8c07e86b25358a3acba09622fdd3a6bbb
ms.sourcegitcommit: 82f45088d8b39e2c1f3f2a33bf359d18a88f975a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "84978334"
---
# <a name="known-issues"></a>の既知の問題

## <a name="know-issues-of-windows-server-version-2004"></a>Windows Server バージョン 2004 の既知の問題

### <a name="1-performance-issue-on-server-core-container"></a>1.Server Core コンテナーのパフォーマンスの問題
Windows Server バージョン 2004 リリースの一般提供の準備中に、Microsoft と .NET チームでは、2019 年 12 月に[こちら](https://techcommunity.microsoft.com/t5/containers/making-windows-server-core-containers-40-smaller/ba-p/1058874) と .NET チームのブログ ([こちら](https://devblogs.microsoft.com/dotnet/we-made-windows-server-core-container-images-40-smaller/)) に記載したパフォーマンスの向上と比較して、2020 年 5 月 27 日リリースの現行 Server Core コンテナー イメージには潜在的なパフォーマンスの問題があることを特定しました。 当時のパフォーマンス分析は、Windows Server バージョン 2004 Insider Preview リリースの Server Core コンテナー イメージで実行されました。 

次のような症状が観測されました。

Server Core コンテナー イメージを使用して独自のイメージを作成し、Azure Container Registry などのリモート コンテナー レジストリにアップロードした後、そのイメージをレジストリからプルして実行すると、コンテナーのパフォーマンスが低下します。 ただし、イメージをビルドしてローカルで実行した場合、パフォーマンスの違いは観測されません。

現在、この問題の根本原因は判明しており、修正中です。 次のリンクを使用して、問題を追跡できます。[microsoft/hcsshim# 830](https://github.com/microsoft/hcsshim/issues/830)

[moby/moby#41066](https://github.com/moby/moby/issues/41066)

[containerd/containerd#4301](https://github.com/containerd/containerd/issues/4301)

また、パートナーである Mirantis と連携して、Docker EE での修正に取り組んでいます。

## <a name="know-issues-of-windows-server-version-1909"></a>Windows Server バージョン 1909 の既知の問題

## <a name="know-issues-of-windows-server-version-1903"></a>Windows Server バージョン 1903 の既知の問題

## <a name="know-issues-of-windows-server-2019windows-server-version-1809"></a>Windows Server 2019/Windows Server バージョン 1809 の既知の問題

## <a name="know-issues-of-windows-server-2016"></a>Windows Server 2016 の既知の問題
