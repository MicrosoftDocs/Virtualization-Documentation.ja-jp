---
title: Windows コンテナーの基本イメージ
description: Windows コンテナーの基本イメージの概要と、その使用するタイミングについて説明します。
keywords: docker, コンテナー, ハッシュ
author: patricklang
ms.date: 09/25/2019
ms.topic: conceptual
ms.assetid: 88e6e080-cf8f-41d8-a301-035959dc5ce0
ms.openlocfilehash: 375dbecece5f5166ce0d44c7317739658d42983f
ms.sourcegitcommit: dc5d955689dfb51d43809b4dcf38468737d89c21
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97345715"
---
# <a name="container-base-images"></a>コンテナーの基本イメージ

Windows には、ユーザーが作成できるコンテナーの基本イメージが 4 つ用意されています。 基本イメージごとに、Windows オペレーティング システムの種類が異なり、ディスク上のフットプリントが異なり、Windows API セットのセットが異なります。

<ul class="columns is-multiline has-margin-left-none has-margin-bottom-none has-padding-top-medium">
    <li class="column is-one-quarter has-padding-top-small-mobile has-padding-bottom-small">
        <a class="is-undecorated is-full-height is-block"
            href="https://hub.docker.com/_/microsoft-windows-servercore" data-linktype="external">
            <article class="card has-outline-hover is-relative is-full-height has-padding-none">
                    <div class="cardImageOuter bgdAccent1 has-padding-top-large has-padding-bottom-large has-padding-left-large has-padding-right-large">
                        <div class="cardImage centered has-padding-top-large has-padding-bottom-large has-padding-left-large has-padding-right-large">
                            <img src="media/Microsoft_logo.svg" alt="Microsoft logo" data-linktype="relative-path">
                        </div>
                    </div>
                <div class="card-content has-text-overflow-ellipsis has-padding-top-small">
                    <div class="has-padding-bottom-none">
                        <h3 class="is-size-4 has-margin-top-none has-margin-bottom-none has-text-primary">Windows サーバー コア</h3>
                    </div>
                    <div class="is-size-7 has-margin-top-small has-line-height-reset">
                        <p>従来の .NET フレームワーク アプリケーションをサポートします。</p>
                    </div>
                </div>
            </article>
        </a>
    </li>
    <li class="column is-one-quarter has-padding-top-small-mobile has-padding-bottom-small">
        <a class="is-undecorated is-full-height is-block"
            href="https://hub.docker.com/_/microsoft-windows-nanoserver" data-linktype="external">
            <article class="card has-outline-hover is-relative is-full-height has-padding-none">
                    <div class="cardImageOuter bgdAccent1 has-padding-top-large has-padding-bottom-large has-padding-left-large has-padding-right-large">
                        <div class="cardImage centered has-padding-top-large has-padding-bottom-large has-padding-left-large has-padding-right-large">
                            <img src="media/Microsoft_logo.svg" alt="Microsoft logo." data-linktype="relative-path">
                        </div>
                    </div>
                <div class="card-content has-text-overflow-ellipsis has-padding-top-small">
                    <div class="has-padding-bottom-none">
                        <h3 class="is-size-4 has-margin-top-none has-margin-bottom-none has-text-primary">Nano Server</h3>
                    </div>
                    <div class="is-size-7 has-margin-top-small has-line-height-reset">
                        <p>.NET Core アプリケーション用に構築されています。</p>
                    </div>
                </div>
            </article>
        </a>
    </li>
    <li class="column is-one-quarter has-padding-top-small-mobile has-padding-bottom-small">
        <a class="is-undecorated is-full-height is-block"
            href="https://hub.docker.com/_/microsoft-windows" data-linktype="external">
            <article class="card has-outline-hover is-relative is-full-height has-padding-none">
                    <div class="cardImageOuter bgdAccent1 has-padding-top-large has-padding-bottom-large has-padding-left-large has-padding-right-large">
                        <div class="cardImage centered has-padding-top-large has-padding-bottom-large has-padding-left-large has-padding-right-large">
                            <img src="media/Microsoft_logo.svg" alt="Microsoft logo." data-linktype="relative-path">
                        </div>
                    </div>
                <div class="card-content has-text-overflow-ellipsis has-padding-top-small">
                    <div class="has-padding-bottom-none">
                        <h3 class="is-size-4 has-margin-top-none has-margin-bottom-none has-text-primary">Windows</h3>
                    </div>
                    <div class="is-size-7 has-margin-top-small has-line-height-reset">
                        <p>完全な Windows API セットを提供します。</p>
                    </div>
                </div>
            </article>
        </a>
    </li>
    <li class="column is-one-quarter has-padding-top-small-mobile has-padding-bottom-small">
        <a class="is-undecorated is-full-height is-block"
            href="https://hub.docker.com/_/microsoft-windows-iotcore" data-linktype="external">
            <article class="card has-outline-hover is-relative is-full-height has-padding-none">
                    <div class="cardImageOuter bgdAccent1 has-padding-top-large has-padding-bottom-large has-padding-left-large has-padding-right-large">
                        <div class="cardImage centered has-padding-top-large has-padding-bottom-large has-padding-left-large has-padding-right-large">
                            <img src="media/Microsoft_logo.svg" alt="Microsoft logo." data-linktype="relative-path">
                        </div>
                    </div>
                <div class="card-content has-text-overflow-ellipsis has-padding-top-small">
                    <div class="has-padding-bottom-none">
                        <h3 class="is-size-4 has-margin-top-none has-margin-bottom-none has-text-primary">Windows IoT Core</h3>
                    </div>
                    <div class="is-size-7 has-margin-top-small has-line-height-reset">
                        <p>IoT アプリケーション用に構築されています。</p>
                    </div>
                </div>
            </article>
        </a>
    </li>
</ul>

## <a name="image-discovery"></a>イメージの検出

すべての Windows コンテナーの基本イメージは、[Docker Hub](https://hub.docker.com/_/microsoft-windows-base-os-images) を介して検出できます。 Windows コンテナーの基本イメージ自体は、Microsoft Container Registry (MCR) である [mcr.microsoft.com](https://azure.microsoft.com/services/container-registry/) から提供されます。 このため、Windows コンテナーの基本イメージのプルコマンドは次のようになります。

```code
docker pull mcr.microsoft.com/windows/servercore:ltsc2019
```

MCR には独自のカタログ エクスペリエンスはなく、Docker Hub などの既存のカタログをサポートすることを目的としています。 Azure のグローバル フットプリントと Azure CDN の組み合わせにより、MCR は一貫した高速なイメージ プル エクスペリエンスを実現しています。 Azure でワークロードを実行している Azure ユーザーのメリットとして、ネットワーク内のパフォーマンスの強化、MCR (Microsoft コンテナー イメージのソース) との緊密な統合、Azure Marketplace、デプロイ パッケージ形式としてコンテナーが提供される Azure のサービス数の増加があります。

## <a name="choosing-a-base-image"></a>基本イメージの選択

構築の基とする適切な基本イメージを選択するには、どうすればよいでしょうか。 ほとんどのユーザーにとって、`Windows Server Core` と `Nanoserver` は最も使用に適したイメージです。

### <a name="guidelines"></a>ガイドライン

 好みのイメージを自由にターゲットに設定できますが、ここでは選択する際のガイドラインをいくつか示します。

- **アプリケーションに完全な .NET フレームワークは必要ですか。** この質問への答えが「はい」の場合、`Windows Server Core` をターゲットにすることをお勧めします。
- **.NET Core に基づいて Windows アプリを構築していますか。** この質問への答えが「はい」の場合、`Nanoserver` をターゲットにすることをお勧めします。
- **IoT アプリケーションを構築していますか。** この質問への答えが「はい」の場合、`IoT Core` をターゲットにすることをお勧めします。
- **アプリに必要な依存関係が、Windows Server Core コンテナー イメージに不足していますか。** この質問への答えが「はい」の場合、`Windows` をターゲットにしてみることをお勧めします。 このイメージは、他の基本イメージよりもサイズがはるかに大きく、多数のコア Windows ライブラリ (GDI ライブラリなど) が含まれています。
- **Windows Insider ですか。** 「はい」の場合、Insider バージョンのイメージを使用することを検討してください。 後述する「Windows Insider の基本イメージ」を参照してください。

> [!TIP]
> .NET に依存しているアプリケーションをコンテナー化したいと考える Windows ユーザーは多数います。 Microsoft は、ここで説明する 4 つの基本イメージに加えて、[.NET framework](https://hub.docker.com/_/microsoft-dotnet-framework) イメージや [ASP .NET](https://hub.docker.com/_/microsoft-dotnet-framework-aspnet/) イメージなどの一般的な Microsoft フレームワークを使用して事前構成されたいくつかの Windows コンテナー イメージを公開しています。

### <a name="base-images-for-windows-insiders"></a>Windows Insider の基本イメージ

Microsoft は、各コンテナーの基本イメージの "Insider" バージョンを提供しています。 これらの Insider コンテナー イメージには、コンテナー イメージの最新かつ最高の機能開発が含まれています。 Windows の Insider バージョン (Windows Insider または Windows Server Insider) であるホストを実行している場合は、これらのイメージを使用することをお勧めします。 Insider イメージは Docker Hub で入手できます。

- [mcr.microsoft.com/windows/servercore/insider](https://hub.docker.com/_/microsoft-windows-servercore-insider)
- [mcr.microsoft.com/windows/nanoserver/insider](https://hub.docker.com/_/microsoft-windows-nanoserver-insider)
- [mcr.microsoft.com/windows/iotcore/insider](https://hub.docker.com/_/microsoft-windows-iotcore-insider)
- [mcr.microsoft.com/windows/insider](https://hub.docker.com/_/microsoft-windows-insider)

詳細については、「[Windows Insider Program でコンテナーを使用する](../deploy-containers/insider-overview.md)」を参照してください。

### <a name="windows-server-core-vs-nanoserver"></a>Windows Server Core と Nanoserver

`Windows Server Core` と `Nanoserver` は、ターゲットとして最も一般的な基本イメージです。 これらのイメージの主な違いは、Nanoserver の API サーフェスが大幅に小さいことです。 PowerShell、WMI、および Windows サービス スタックは、Nanoserver イメージにはありません。

Nanoserver は、.NET Core またはその他の最新のオープン ソース フレームワークに依存するアプリを実行するのに十分な API サーフェス を提供するために構築されました。 小さい API サーフェスとのトレードオフとして、Nanoserver イメージは、残りの Windows 基本イメージよりもディスク上のフットプリントが大幅に小さくなっています。 Nano Server 上には、いつでもレイヤーを追加できることに注意してください。 この例については、[.NET Core の Nano Server の Dockerfile](https://github.com/dotnet/dotnet-docker/blob/master/src/sdk/2.1/nanoserver-1909/amd64/Dockerfile) をご覧ください。
