---
title: コンテナー記憶域の概要
description: Windows Server コンテナーがホストとその他の種類の記憶域を使用する方法
keywords: コンテナー, ボリューム, 記憶域, マウント, bindmount
author: cwilhit
ms.author: jgerend
ms.date: 09/25/2019
ms.topic: overview
ms.openlocfilehash: 8bbb6a5116a8f6fcafcebbf8d96babc1f380b540
ms.sourcegitcommit: 24a7d693da95512ac371bdbf6466f46e187c9c58
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/13/2021
ms.locfileid: "98181859"
---
# <a name="container-storage-overview"></a>コンテナー記憶域の概要

<!-- Great diagram would be great! -->

このトピックでは、Windows 上のコンテナーによるさまざまな記憶域の使用方法の概要について説明します。 コンテナーの動作は、記憶域の点で仮想マシンとは異なります。 本質的には、コンテナー内で実行されているアプリによってホストのファイル システム全体に状態が書き込まれることを防ぐために、コンテナーが構築されます。 コンテナーには既定で "スクラッチ" 領域が使用されますが、Windows には記憶域を永続化する手段も用意されています。

## <a name="scratch-space"></a>スクラッチ領域

既定で、Windows コンテナーには一時記憶域が使用されます。 すべてのコンテナー I/O は "スクラッチ領域" で行われ、各コンテナーで独自のスクラッチが取得されます。 ファイルの作成とファイルの書き込みはスクラッチ領域にキャプチャされ、ホストにエスケープされません。 コンテナー インスタンスが停止すると、スクラッチ領域で発生したすべての変更は破棄されます。 新しいコンテナー インスタンスが開始されると、インスタンスに新しいスクラッチ領域が用意されます。

## <a name="layer-storage"></a>レイヤー記憶域

[コンテナーの概要](../about/index.md)に関するページで説明されているように、コンテナー イメージは一連のレイヤーとして表現されるファイルのバンドルです。 レイヤー記憶域は、コンテナーに組み込まれているすべてのファイルです。 コンテナーに対する `docker pull` および `docker run` を実行すると、結果は毎回同じになります。

### <a name="where-layers-are-stored-and-how-to-change-it"></a>レイヤーの保存場所と変更方法

既定のインストールでは、レイヤーが `C:\ProgramData\docker` に格納され、"image" ディレクトリおよび "windowsfilter" ディレクトリに分割されます。 レイヤーの保存場所は、「[Windows 上の Docker エンジン](../manage-docker/configure-docker-daemon.md)」の記載に従い、`docker-root` 構成を使用して変更できます。

> [!NOTE]
> レイヤー記憶域は、NTFS のみでサポートされます。 ReFS はサポートされません。

レイヤー ディレクトリ内のファイルは変更しないでください。これらは以下のようなコマンドを使用して慎重に管理します。

- [docker images](https://docs.docker.com/engine/reference/commandline/images/)
- [docker rmi](https://docs.docker.com/engine/reference/commandline/rmi/)
- [docker プル](https://docs.docker.com/engine/reference/commandline/pull/)
- [docker 負荷](https://docs.docker.com/engine/reference/commandline/load/)
- [docker save](https://docs.docker.com/engine/reference/commandline/save/)

### <a name="supported-operations-in-layer-storage"></a>レイヤー記憶域でサポートされる操作

コンテナーの実行では、ほとんどの NTFS 操作を使用できます (トランザクションを除く)。 これには ACL の設定が含まれており、すべての ACL はコンテナー内でチェックされます。 1 つのコンテナー内で複数のユーザーとしてプロセスを実行するには、`RUN net user /create ...` で `Dockerfile` 内にユーザーを作成し、ファイルの ACL を設定します。次に、[Dockerfile USER ディレクティブ](https://docs.docker.com/engine/reference/builder/#user)を使用して、そのユーザーで実行するプロセスを構成します。

## <a name="persistent-storage"></a>永続的な記憶域

Windows コンテナーは、バインド マウントとボリュームを介して永続的な記憶域を提供するメカニズムをサポートしています。 詳細については、「[コンテナー内の永続的な記憶域](./persistent-storage.md)」を参照してください。

## <a name="storage-limits"></a>ストレージの制限

Windows アプリケーションでは、新しいファイルをインストールまたは作成する前に、または一時ファイルのクリーンアップのトリガーとして、空きディスク領域の量を照会することが一般的なパターンとなっています。  アプリケーションの互換性を最大限に高める目的で、Windows コンテナーの C: ドライブは 20 GB の空き仮想サイズとなります。

ユーザーによっては、この既定値を上書きして、空き領域を小さい値または大きい値に構成することが必要になります。 そのためには、"storage-opt" 構成内で "size" オプションを使用します。

### <a name="examples"></a>例

コマンド ライン: `docker run --storage-opt "size=50GB" mcr.microsoft.com/windows/servercore:ltsc2019 cmd`

または、Docker 構成ファイルを直接変更できます。

```Docker Configuration File
"storage-opts": [
    "size=50GB"
  ]
```

> [!TIP]
> この方法は、Docker ビルドにも使用できます。 Docker 構成ファイルの変更について詳しくは、[Docker の構成](../manage-docker/configure-docker-daemon.md#configure-docker-with-a-configuration-file)ドキュメントをご覧ください。