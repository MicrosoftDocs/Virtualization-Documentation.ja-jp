---
title: Windows Insider Program でコンテナーを使用する
description: Windows Insider Program で Windows コンテナーの使用を開始する方法について説明します
keywords: Docker, コンテナー, Insider, Windows
author: v-susbo
ms.author: v-susbo
ms.date: 12/29/2020
ms.topic: how-to
ms.openlocfilehash: f2eb6bce8ab482f8c1d34bdc9b7c5916ba0e708b
ms.sourcegitcommit: 24a7d693da95512ac371bdbf6466f46e187c9c58
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/13/2021
ms.locfileid: "98181989"
---
# <a name="use-containers-with-the-windows-insider-program"></a>Windows Insider Program でコンテナーを使用する

この演習では、Windows Insider Preview プログラムで提供されている最新の insider ビルドの Windows Server に、Windows コンテナー機能を展開して使用する手順を説明します。 この演習では、コンテナーの役割をインストールし、基本 OS イメージのプレビュー版を展開します。 コンテナーの概要については、[コンテナーについてのページ](../about/index.md)」をご覧ください。

## <a name="join-the-windows-insider-program"></a>Windows Insider Program に参加する

Insider バージョンの Windows コンテナーを実行するには、Windows Insider Program から提供された Windows Server の最新ビルドや、Windows Insider Program から提供された Windows 10 の最新ビルドがホストで実行されている必要があります。 [Windows Insider Program](https://insider.windows.com/GettingStarted) に参加して、使用条件をご確認ください。

> [!IMPORTANT]
> 以下で説明する基本イメージを使用するには、Windows Server Insider Preview プログラムから提供された Windows Server のビルド、または Windows Insider Preview プログラムから提供された Windows 10 のビルドを使用する必要があります。 これらのビルドを使用せずに、対象の基本イメージを使用した場合、コンテナーを開始できません。

## <a name="install-docker"></a>Docker のインストール

Docker がまだインストールされていない場合は、「[作業の開始](../quick-start/set-up-environment.md)」ガイドに従って Docker をインストールしてください。

## <a name="pull-an-insider-container-image"></a>Insider コンテナー イメージをプルする

Windows Insider Program に参加すると、基本イメージの最新ビルドを使用できます。

Nano Server Insider 基本イメージをプルするには、次のコマンドを実行します。

```console
docker pull mcr.microsoft.com/nanoserver/insider
```

Windows Server Core Insider 基本イメージをプルするには、次のコマンドを実行します。

```console
docker pull mcr.microsoft.com/windows/servercore/insider
```

Windows の基本イメージと IoTCore の基本イメージにも、プルに使用できる Insider バージョンがあります。 使用できる Insider 基本イメージの詳細については、「[コンテナーの基本イメージ](../manage-containers/container-base-images.md)」を参照してください。

> [!IMPORTANT]
> Windows コンテナーの OS イメージの[使用許諾契約](../images-eula.md )および Windows Insider Program の[使用条件](https://www.microsoft.com/software-download/windowsinsiderpreviewserver)をご確認ください。
