---
title: Windows 10 上の Linux コンテナー
description: Hyper-V を使用することにより、Linux コンテナーを Windows 10 上でネイティブであるかのように実行するさまざまな方法について説明します。
keywords: Linux コンテナー, Docker, コンテナー, Windows 10
author: scooley
ms.author: scooley
ms.date: 09/17/2019
ms.topic: overview
ms.assetid: edfd11c8-ee99-42d8-9878-efc126fe1826
ms.openlocfilehash: ede0387707b8200ee02c4cf347e5b8710e52a1cf
ms.sourcegitcommit: 24a7d693da95512ac371bdbf6466f46e187c9c58
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/13/2021
ms.locfileid: "98181869"
---
# <a name="linux-containers-on-windows-10"></a>Windows 10 上の Linux コンテナー

Linux コンテナーは、コンテナー エコシステム全体の大部分を占めており、開発者エクスペリエンスと運用環境の両方の基盤となるものです。  しかし、コンテナーはコンテナー ホストとカーネルを共有するため、Windows で Linux コンテナーを直接実行することはできません。 ここで、仮想化が役立ちます。

## <a name="linux-containers-in-a-moby-vm"></a>Moby VM の Linux コンテナー

Linux VM で Linux コンテナーを実行するには、[Docker のスターティング ガイド](https://docs.docker.com/docker-for-windows/)の指示に従います。

Docker では、Hyper-V で動作する [LinuxKit](https://github.com/linuxkit/linuxkit) ベースの仮想マシンを使用することにより、2016 年の最初のリリースの時点 (Windows で Hyper-V による分離や Linux コンテナーが使用可能になる前) から、Windows デスクトップ上で Linux コンテナーを実行できました。

このモデルでは、Docker クライアントは Windows デスクトップ上で実行されますが、Linux VM 上の Docker デーモンを呼び出します。

![コンテナー ホストとしての Moby VM](media/MobyVM.png)

このモデルでは、すべての Linux コンテナーが 1 つの Linux ベース コンテナー ホストを共有しており、すべての Linux コンテナーに次の特徴があります。

* カーネルを相互に、また Moby VM とは共有するが、Windows ホストとは共有しない。
* Linux 上で実行されている Linux コンテナーと、ストレージおよびネットワークのプロパティが一貫している (Linux VM 上で実行されているため)。

これは、Linux コンテナー ホスト (Moby VM) が、Docker デーモンと Docker デーモンのすべての依存関係を実行している必要があることも意味しています。

Moby VM で実行しているかどうかを確認するには、Hyper-V マネージャー UI を使用するか、管理者特権での PowerShell ウィンドウで `Get-VM` を実行して、Moby VM の Hyper-V マネージャーを確認します。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [Linux コンテナーのセットアップ](../quick-start/quick-start-windows-10-linux.md)
