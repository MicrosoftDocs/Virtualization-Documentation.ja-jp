---
title: Windows コンテナーのバージョンの互換性
description: さまざまなバージョンの Windows Server および Windows から構築されたコンテナーのバージョンの互換性。
keywords: メタデータ, コンテナー, バージョン
author: taylorb-microsoft
ms.author: jgerend
ms.topic: conceptual
ms.date: 10/22/2020
ms.openlocfilehash: a85bfc8a5f284d130cbf246b261d739d8c1a6d0b
ms.sourcegitcommit: 24a7d693da95512ac371bdbf6466f46e187c9c58
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/13/2021
ms.locfileid: "98182097"
---
# <a name="windows-container-version-compatibility"></a>Windows コンテナーのバージョンの互換性

Windows Server コンテナーのビルドと実行に対応した最初の Windows リリースは、Windows Server 2016 と Windows 10 Anniversary Update (いずれもバージョン 14393) でした。 これらのバージョンを使用してビルドされたコンテナーは新しいリリースで実行できますが、作業を開始する前にいくつかの注意点があります。

Windows コンテナーは、その機能を改善する過程で、互換性に影響を与える変更が行われています。 従来のバージョンで作成したコンテナーは、[Hyper-V による分離](../manage-containers/hyperv-container.md)を使って新しいホスト上でそのまま実行でき、同じ (従来の) カーネル バージョンが使用されます。 ただし、新しい Windows ビルドで作成されたコンテナーを実行する場合は、新しいホスト ビルドで実行する必要があります。

## <a name="windows-server-host-os-compatibility"></a>Windows Server ホスト OS の互換性

<!-- start tab view -->
# <a name="windows-server-version-20h2"></a>[Windows Server バージョン 20H2](#tab/windows-server-20H2)

|コンテナーの基本イメージの OS バージョン|Hyper-V による分離のサポート|プロセスの分離のサポート|
|---|:---:|:---:|
|Windows Server バージョン 20H2|&#10004;|&#10004;|
|Windows Server バージョン 2004|&#10004;|&#10060;|
|Windows Server バージョン 1909|&#10004;|&#10060;|
|Windows Server バージョン 1903|&#10004;|&#10060;|
|Windows Server 2019|&#10004;|&#10060;|
|Windows Server 2016|&#10004;|&#10060;|

# <a name="windows-server-version-2004"></a>[Windows Server バージョン 2004](#tab/windows-server-2004)

|コンテナーの基本イメージの OS バージョン|Hyper-V による分離のサポート|プロセスの分離のサポート|
|---|:---:|:---:|
|Windows Server バージョン 20H2|&#10060;|&#10060;|
|Windows Server バージョン 2004|&#10004;|&#10004;|
|Windows Server バージョン 1909|&#10004;|&#10060;|
|Windows Server バージョン 1903|&#10004;|&#10060;|
|Windows Server 2019|&#10004;|&#10060;|
|Windows Server 2016|&#10004;|&#10060;|

# <a name="windows-server-version-1909"></a>[Windows Server バージョン 1909](#tab/windows-server-1909)

|コンテナーの基本イメージの OS バージョン|Hyper-V による分離のサポート|プロセスの分離のサポート|
|---|:---:|:---:|
|Windows Server バージョン 20H2|&#10060;|&#10060;|
|Windows Server バージョン 2004|&#10060;|&#10060;|
|Windows Server バージョン 1909|&#10004;|&#10004;|
|Windows Server バージョン 1903|&#10004;|&#10060;|
|Windows Server 2019|&#10004;|&#10060;|
|Windows Server 2016|&#10004;|&#10060;|

# <a name="windows-server-version-1903"></a>[Windows Server バージョン 1903](#tab/windows-server-1903)

|コンテナーの基本イメージの OS バージョン|Hyper-V による分離のサポート|プロセスの分離のサポート|
|---|:---:|:---:|
|Windows Server バージョン 20H2|&#10060;|&#10060;|
|Windows Server バージョン 2004|&#10060;|&#10060;|
|Windows Server バージョン 1909|&#10060;|&#10060;|
|Windows Server バージョン 1903|&#10004;|&#10004;|
|Windows Server 2019|&#10004;|&#10060;|
|Windows Server 2016|&#10004;|&#10060;|

# <a name="windows-server-2019"></a>[Windows Server 2019](#tab/windows-server-2019)

|コンテナーの基本イメージの OS バージョン|Hyper-V による分離のサポート|プロセスの分離のサポート|
|---|:---:|:---:|
|Windows Server バージョン 20H2|&#10060;|&#10060;|
|Windows Server バージョン 2004|&#10060;|&#10060;|
|Windows Server バージョン 1909|&#10060;|&#10060;|
|Windows Server バージョン 1903|&#10060;|&#10060;|
|Windows Server 2019|&#10004;|&#10004;|
|Windows Server 2016|&#10004;|&#10060;|

# <a name="windows-server-2016"></a>[Windows Server 2016](#tab/windows-server-2016)

|コンテナーの基本イメージの OS バージョン|Hyper-V による分離のサポート|プロセスの分離のサポート|
|---|:---:|:---:|
|Windows Server バージョン 20H2|&#10060;|&#10060;|
|Windows Server バージョン 2004|&#10060;|&#10060;|
|Windows Server バージョン 1909|&#10060;|&#10060;|
|Windows Server バージョン 1903|&#10060;|&#10060;|
|Windows Server 2019|&#10060;|&#10060;|
|Windows Server 2016|&#10004;|&#10004;|

---
<!-- stop tab view -->

## <a name="windows-10-host-os-compatibility"></a>Windows 10 ホスト OS の互換性

<!-- start tab view -->

# <a name="windows-10-version-20h2"></a>[Windows 10、バージョン 20H2](#tab/windows-10-20H2)

|コンテナーの基本イメージの OS バージョン|Hyper-V による分離のサポート|プロセスの分離のサポート|
|---|:---:|:---:|
|Windows Server バージョン 20H2|&#10004;|&#10004;|
|Windows Server バージョン 2004|&#10004;|&#10060;|
|Windows Server バージョン 1909|&#10004;|&#10060;|
|Windows Server バージョン 1903|&#10004;|&#10060;|
|Windows Server 2019|&#10004;|&#10060;|
|Windows Server 2016|&#10004;|&#10060;|

# <a name="windows-10-version-2004"></a>[Windows 10 バージョン 2004](#tab/windows-10-2004)

|コンテナーの基本イメージの OS バージョン|Hyper-V による分離のサポート|プロセスの分離のサポート|
|---|:---:|:---:|
|Windows Server バージョン 20H2|&#10060;|&#10060;|
|Windows Server バージョン 2004|&#10004;|&#10004;|
|Windows Server バージョン 1909|&#10004;|&#10060;|
|Windows Server バージョン 1903|&#10004;|&#10060;|
|Windows Server 2019|&#10004;|&#10060;|
|Windows Server 2016|&#10004;|&#10060;|

# <a name="windows-10-version-1909"></a>[Windows 10 バージョン 1909](#tab/windows-10-1909)

|コンテナーの基本イメージの OS バージョン|Hyper-V による分離のサポート|プロセスの分離のサポート|
|---|:---:|:---:|
|Windows Server バージョン 20H2|&#10060;|&#10060;|
|Windows Server バージョン 2004|&#10060;|&#10060;|
|Windows Server バージョン 1909|&#10004;|&#10060;|
|Windows Server バージョン 1903|&#10004;|&#10060;|
|Windows Server 2019|&#10004;|&#10060;|
|Windows Server 2016|&#10004;|&#10060;|

# <a name="windows-10-version-1903"></a>[Windows 10 バージョン 1903](#tab/windows-10-1903)

|コンテナーの基本イメージの OS バージョン|Hyper-V による分離のサポート|プロセスの分離のサポート|
|---|:---:|:---:|
|Windows Server バージョン 20H2|&#10060;|&#10060;|
|Windows Server バージョン 2004|&#10060;|&#10060;|
|Windows Server バージョン 1909|&#10060;|&#10060;|
|Windows Server バージョン 1903|&#10004;|&#10060;|
|Windows Server 2019|&#10004;|&#10060;|
|Windows Server 2016|&#10004;|&#10060;|

# <a name="windows-10-version-1809"></a>[Windows 10 バージョン 1809](#tab/windows-10-1809)

|コンテナーの基本イメージの OS バージョン|Hyper-V による分離のサポート|プロセスの分離のサポート|
|---|:---:|:---:|
|Windows Server バージョン 20H2|&#10060;|&#10060;|
|Windows Server バージョン 2004|&#10060;|&#10060;|
|Windows Server バージョン 1909|&#10060;|&#10060;|
|Windows Server バージョン 1903|&#10060;|&#10060;|
|Windows Server 2019|&#10004;|&#10060;|
|Windows Server 2016|&#10004;|&#10060;|

---
<!-- stop tab view -->

## <a name="matching-container-host-version-with-container-image-versions"></a>コンテナー ホストのバージョンとコンテナー イメージのバージョンを一致させる

### <a name="windows-server-containers"></a>Windows Server コンテナー

Windows Server コンテナーとその基になっているホストは単一のカーネルを共有するため、コンテナーの基本イメージの OS バージョンは、ホストと一致している必要があります。 バージョンが異なる場合、コンテナーは起動するかもしれませんが、完全に機能することは保証されません。 Windows オペレーティング システムは、メジャー、マイナー、ビルド、リビジョンの 4 つのレベルでバージョン管理されています。 たとえば、バージョン 10.0.14393.103 の場合、メジャー バージョンが 10、マイナー バージョンが 0、ビルド番号が 14393、リビジョン番号が 103 になります。 ビルド番号は、バージョン 1709、1903 など、新しいバージョンの OS が公開された場合にのみ変更されます。 リビジョン番号は、Windows 更新プログラムが適用されると更新されます。

#### <a name="build-number-new-release-of-windows"></a>ビルド番号 (Windows の新しいリリース)

Windows Server コンテナーは、コンテナー ホストとコンテナー イメージの間でビルド番号が異なると起動がブロックされます。 たとえば、コンテナー ホストのバージョンが 10.0.14393.* (Windows Server 2016) でコンテナー イメージのバージョンが 10.0.16299.* (Windows Server バージョン 1709) の場合、コンテナーは起動しません。

#### <a name="revision-number-patching"></a>リビジョン番号 (修正プログラムの適用)

現在、Windows Server コンテナーでは、コンテナー ホストとコンテナー イメージのリビジョン番号が異なるシステムで Windows Server 2016 ベースのコンテナーを実行するシナリオはサポートされていません。 たとえば、コンテナー ホストのバージョンが 10.0.14393.**1914** (KB4051033 が適用された Windows Server 2016) で、コンテナー イメージのバージョンが 10.0.14393.**1944** (KB4053579 が適用された Windows Server 2016) の場合、イメージは起動しないことがあります。

ただし、ホストまたはイメージが Windows Server バージョン 1809 以降を使用している場合、このルールは適用されず、ホストとコンテナー イメージのリビジョンが一致している必要はありません。

システム (ホストおよびコンテナー) に最新の修正プログラムや更新プログラムを適用して最新の状態に保ち、セキュリティを維持することをお勧めします。

>[!NOTE]
>Windows Server コンテナーを、2020 年 2 月 11 日にリリースされたセキュリティ更新プログラム ("2B" とも呼ばれる) か、それ以降の月次セキュリティ更新プログラム リリースとともに使用する場合、問題が発生する可能性があります。 詳細については、[この記事](https://support.microsoft.com/help/4542617/you-might-encounter-issues-when-using-windows-server-containers-with-t)をご覧ください。
>
>ホストとコンテナーの両方を、最新の修正プログラムと更新プログラムで更新して、セキュリティと互換性を維持することを強くお勧めします。 Windows コンテナーの更新方法についての重要なガイダンスは、「[Windows Server のコンテナーの更新](update-containers.md)」を参照してください。

#### <a name="practical-application"></a>実際の適用例

例 1:KB4041691 が適用された Windows Server 2016 をコンテナー ホストが実行している場合。 このホストに展開されている Windows Server コンテナーはすべて、バージョン 10.0.14393.1770 のコンテナー基本イメージに基づいている必要があります。 KB4053579 をホスト コンテナーに適用する場合、ホスト コンテナーでサポートされるように、イメージも更新する必要があります。

例 2: KB4534273 が適用された Windows Server バージョン 1809 をコンテナー ホストが実行している場合。 このホストに展開されている Windows Server コンテナーはすべて、Windows Server バージョン 1809 (10.0.17763) コンテナー基本イメージに基づいている必要がありますが、ホストの KB と一致する必要はありません。 KB4534273 がホストに適用されている場合でも、これらのコンテナー イメージは引き続きサポートされますが、潜在的なセキュリティの問題に対処するためにそれらを更新することをお勧めします。

#### <a name="querying-version"></a>バージョンの照会

方法 1:バージョン 1709 以降、cmd プロンプトと **ver** コマンドでリビジョン詳細が返されるようになりました。

```batch
Microsoft Windows [Version 10.0.16299.125]
(c) 2017 Microsoft Corporation. All rights reserved.

C:\>ver

Microsoft Windows [Version 10.0.16299.125]
```

方法 2:次のレジストリ キーのクエリを実行します。HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion

たとえば、次のように入力します。

```batch
C:\>reg query "HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion" /v BuildLabEx
```

```powershell
Windows PowerShell
Copyright (C) 2016 Microsoft Corporation. All rights reserved.

PS C:\Users\Administrator> (Get-ItemProperty 'HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion\').BuildLabEx
14393.321.amd64fre.rs1_release_inmarket.161004-2338
```

基本イメージが使用しているバージョンは、Docker Hub のタグまたはイメージの説明で提供されるイメージのハッシュ テーブルで確認できます。 「[Windows 10 の更新履歴](https://support.microsoft.com/help/12387/windows-10-update-history)」のページでは、各ビルドとリビジョンがリリースされた日付がわかります。

### <a name="hyper-v-isolation-for-containers"></a>Hyper-V によるコンテナーの分離

Windows コンテナーは、Hyper-V の分離を使用して、または使用せずに実行できます。 Hyper-V による分離を使用すると、最適化された VM によって、コンテナーの周囲にセキュリティ保護された境界が形成されます。 標準の Windows コンテナーではコンテナーとホストの間でカーネルが共有されるのに対し、Hyper-V によって分離されたコンテナーでは専用の Windows カーネル インスタンスを利用します。 つまり、コンテナー ホストとコンテナー イメージで異なるバージョンの OS を使用できます (詳細については、下の互換性マトリクスを参照)。

Hyper-V による分離を使ってコンテナーを実行するには、docker run コマンドに `--isolation=hyperv` というタグを追加します。

## <a name="errors-from-mismatched-versions"></a>一致しないバージョンを使用した場合に発生するエラー

サポートされていない組み合わせを実行しようとすると、次のエラーが発生します。

```dockerfile
docker: Error response from daemon: container b81ed896222eb87906ccab1c3dd2fc49324eafa798438f7979b87b210906f839 encountered an error during CreateContainer: failure in a Windows system call: The operating system of the container does not match the operating system of the host. (0xc0370101) extra info: {"SystemType":"Container","Name":"b81ed896222eb87906ccab1c3dd2fc49324eafa798438f7979b87b210906f839","Owner":"docker","IsDummy":false,"VolumePath":"\\\\?\\Volume{2443d38a-1379-4bcf-a4b7-fc6ad4cd7b65}","IgnoreFlushesDuringBoot":true,"LayerFolderPath":"C:\\ProgramData\\docker\\windowsfilter\\b81ed896222eb87906ccab1c3dd2fc49324eafa798438f7979b87b210906f839","Layers":[{"ID":"1532b584-8431-5b5a-8735-5e1b4fe9c2a9","Path":"C:\\ProgramData\\docker\\windowsfilter\\b2b88bc2a47abcc682e422507abbba9c9b6d826d34e67b9e4e3144cc125a1f80"},{"ID":"a64b8da5-cd6e-5540-bc73-d81acae6da54","Path":"C:\\ProgramData\\docker\\windowsfilter\\5caaedbced1f546bccd01c9d31ea6eea4d30701ebba7b95ee8faa8c098a6845a"}],"HostName":"b81ed896222e","MappedDirectories":[],"HvPartition":false,"EndpointList":["002a0d9e-13b7-42c0-89b2-c1e80d9af243"],"Servicing":false,"AllowUnqualifiedDNSQuery":true}.
```

このエラーは次の 3 つの方法で解決できます。

- `mcr.microsoft.com/microsoft-windows-nanoserver` または `mcr.microsoft.com/windows/servercore` の正しいバージョンに基づいて、コンテナーをリビルドする
- ホストのほうが新しい場合、**docker run --isolation=hyperv ...** を実行する
- 同じ Windows バージョンがインストールされた別のホスト上でコンテナーを実行してみる

## <a name="choose-which-container-os-version-to-use"></a>使用するコンテナー OS バージョンを選択する

>[!NOTE]
>2019 年 4 月 16 日以降、[Windows ベース OS コンテナー イメージ](https://hub.docker.com/_/microsoft-windows-base-os-images) の "latest" タグは公開も維持もされなくなりました。 これらのリポジトリからイメージをプルまたは参照する際には、特定のタグを宣言してください。

コンテナーにどのバージョンを使用すべきか、理解しておく必要があります。 たとえばコンテナー OS として Windows Server バージョン 1809 を使用し、それに対応する最新の修正プログラムを適用したい場合、必要なベース OS コンテナー イメージのバージョンを指定するときに、次のように `1809` タグを使用します。

```dockerfile
FROM mcr.microsoft.com/windows/nanoserver:1809
...
```

ただし、Windows Server バージョン 1809 の特定の修正プログラムが必要な場合は、タグで KB 番号を指定できます。 たとえば、Windows Server バージョン 1809 の Nano Server ベース OS コンテナー イメージに KB4493509 を適用する必要がある場合は、次のように指定します。

```dockerfile
FROM mcr.microsoft.com/windows/nanoserver:1809-KB4493509
...
```

また上記のスキーマを使い、タグで OS バージョンを指定して、必要な修正プログラムを厳密に指定することもできます。

```dockerfile
FROM mcr.microsoft.com/windows/nanoserver:10.0.17763.437
...
```

Windows Server 2019 と Windows Server 2016 に基づく Server Core 基本イメージは、[長期サービス チャネル (LTSC)](/windows-server/get-started-19/servicing-channels-19#long-term-servicing-channel-ltsc) リリースです。 Server Core イメージのコンテナー OS として、たとえば Windows Server 2019 を使用し、それに対応する最新の修正プログラムを適用したい場合、次のように LTSC リリースを指定することができます。

```dockerfile
FROM mcr.microsoft.com/windows/servercore:ltsc2019
...
```

## <a name="matching-versions-using-docker-swarm"></a>Docker Swarm を使ってバージョンを一致させる方法

現在、Docker Swarm には、コンテナーが使用する Windows のバージョンを、同じバージョンのホストに一致させる方法は組み込まれていません。 サービスを更新して新しいコンテナーを使用するようにすると、正常に実行されます。

長期間にわたって複数のバージョンの Windows を実行させる必要がある場合、2 つの方法を取ることができます。常に Hyper-V による分離を使用するように Windows ホストを構成するか、ラベルの制約を使用することです。

### <a name="finding-a-service-that-wont-start"></a>起動しないサービスの検出方法

サービスが起動しない場合、`MODE` には `replicated` と表示されますが、`REPLICAS` が 0 のままになります。 問題が OS のバージョンにあるかどうかを確認するには、次のコマンドを使用します。

**docker service ls** を実行して、サービス名を検索します。

```dockerfile
ID                  NAME                MODE                REPLICAS            IMAGE                                             PORTS
xh6mwbdq2uil        angry_liskov        replicated          0/1                 windows/servercore/iis
```

**docker service ps (サービス名)** を実行して、状態と直近の試行を取得します。

```dockerfile
C:\Program Files\Docker>docker service ps angry_liskov
ID                  NAME                 IMAGE                                             NODE                DESIRED STATE       CURRENT STATE               ERROR                              PORTS
klkbhn742lv0        angry_liskov.1       windows/servercore/iis   WIN-BSTMQDRQC2E     Ready               Ready 3 seconds ago
y5blbdum70zo         \_ angry_liskov.1   windows/servercore/iis   WIN-BSTMQDRQC2E     Shutdown            Failed 24 seconds ago       "starting container failed: co…"
yjq6zwzqj8kt         \_ angry_liskov.1   windows/servercore/iis   WIN-BSTMQDRQC2E     Shutdown            Failed 31 seconds ago       "starting container failed: co…"

ytnnv80p03xx         \_ angry_liskov.1   windows/servercore/iis   WIN-BSTMQDRQC2E     Shutdown            Failed about a minute ago   "starting container failed: co…"
xeqkxbsao57w         \_ angry_liskov.1   windows/servercore/iis   WIN-BSTMQDRQC2E     Shutdown            Failed about a minute ago   "starting container failed: co…"
```

`starting container failed: ...` がある場合、**docker service ps --no-trunc (コンテナー名)** を実行することにより、エラー全体を確認できます。

```dockerfile
C:\Program Files\Docker>docker service ps --no-trunc angry_liskov
ID                          NAME                 IMAGE                                                                                                                     NODE                DESIRED STATE       CURRENT STATE                     ERROR                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          PORTS
dwsd6sjlwsgic5vrglhtxu178   angry_liskov.1       windows/servercore/iis@sha256:868bca7e89e1743792e15f78edb5a73070ef44eae6807dc3f05f9b94c23943d5   WIN-BSTMQDRQC2E     Running             Starting less than a second ago
y5blbdum70zoh1f6uhx5nxsfv    \_ angry_liskov.1   windows/servercore/iis@sha256:868bca7e89e1743792e15f78edb5a73070ef44eae6807dc3f05f9b94c23943d5   WIN-BSTMQDRQC2E     Shutdown            Failed 39 seconds ago             "starting container failed: container e7b5d3adba7e510569c18d8e55f7c689d7cb92be40a516c91b363e27f84604d0 encountered an error during CreateContainer: failure in a Windows system call: The operating system of the container does not match the operating system of the host. (0xc0370101) extra info: {"SystemType":"Container","Name":"e7b5d3adba7e510569c18d8e55f7c689d7cb92be40a516c91b363e27f84604d0","Owner":"docker","VolumePath":"\\\\?\\Volume{2443d38a-1379-4bcf-a4b7-fc6ad4cd7b65}","IgnoreFlushesDuringBoot":true,"LayerFolderPath":"C:\\ProgramData\\docker\\windowsfilter\\e7b5d3adba7e510569c18d8e55f7c689d7cb92be40a516c91b363e27f84604d0","Layers":[{"ID":"bcf2630f-ea95-529b-b33c-e5cdab0afdb4","Path":"C:\\ProgramData\\docker\\windowsfilter\\200235127f92416724ae1d53ed3fdc86d78767132d019bdda1e1192ee4cf3ae4"},{"ID":"e3ea10a8-4c2f-5b93-b2aa-720982f116f6","Path":"C:\\ProgramData\\docker\\windowsfilter\\0ccc9fa71a9f4c5f6f3bc8134fe3533e454e09f453de662cf99ab5d2106abbdc"},{"ID":"cff5391f-e481-593c-aff7-12e080c653ab","Path":"C:\\ProgramData\\docker\\windowsfilter\\a49576b24cd6ec4a26202871c36c0a2083d507394a3072186133131a72601a31"},{"ID":"499cb51e-b891-549a-b1f4-8a25a4665fbd","Path":"C:\\ProgramData\\docker\\windowsfilter\\fdf2f52c4323c62f7ff9b031c0bc3af42cf5fba91098d51089d039fb3e834c08"},{"ID":"1532b584-8431-5b5a-8735-5e1b4fe9c2a9","Path":"C:\\ProgramData\\docker\\windowsfilter\\b2b88bc2a47abcc682e422507abbba9c9b6d826d34e67b9e4e3144cc125a1f80"},{"ID":"a64b8da5-cd6e-5540-bc73-d81acae6da54","Path":"C:\\ProgramData\\docker\\windowsfilter\\5caaedbced1f546bccd01c9d31ea6eea4d30701ebba7b95ee8faa8c098a6845a"}],"HostName":"e7b5d3adba7e","HvPartition":false,"EndpointList":["298bb656-8800-4948-a41c-1b0500f3d94c"],"AllowUnqualifiedDNSQuery":true}"
```

これは、`CreateContainer: failure in a Windows system call: The operating system of the container does not match the operating system of the host. (0xc0370101)` のエラーと同じです。

### <a name="fix---update-the-service-to-use-a-matching-version"></a>修正方法: 一致するバージョンが使用されるようにサービスを更新する

Docker Swarm を使う場合、2 つの考慮事項があります。 自分が作成したのではないイメージを使用するサービスを含む Compose ファイルがある場合、それに応じて参照を更新します。 たとえば、次のように入力します。

``` yaml
version: '3'

services:
  YourServiceName:
    image: windows/servercore:1709
...
```

もう 1 つの考慮事項として、ポイント先のイメージが自分で作成したイメージである場合 (たとえば、contoso/myimage) は、次のように指定します。

```yaml
version: '3'

services:
  YourServiceName:
    image: contoso/myimage
...
```

この場合、docker-compose 行ではなく、「[一致しないバージョンを使用した場合に発生するエラー](#errors-from-mismatched-versions)」で説明されている方法を使用してその Dockerfile を変更する必要があります。

### <a name="mitigation---use-hyper-v-isolation-with-docker-swarm"></a>軽減策: Docker Swarm で Hyper-V による分離を使用する

コンテナーごとに Hyper-V による分離をサポートするように提案が行われていますが、コードはまだ完成していません。 この提案の進行状況については、[GitHub](https://github.com/moby/moby/issues/31616) でご確認ください。 それが完成するまでの間、ホストは Hyper-V による分離を常時実行するように構成する必要があります。

これには、Docker サービスの構成を変更した後、Docker エンジンを再起動します。

1. `C:\ProgramData\docker\config\daemon.json` を編集します
2. `"exec-opts":["isolation=hyperv"]` の行を追加します

    >[!NOTE]
    >daemon.json ファイルは、既定では存在しません。 ディレクトリを調査して、このファイルが存在していない場合は、ファイルを作成する必要があります。 その後、次のようにコピーします。

    ```JSON
    {
        "exec-opts":["isolation=hyperv"]
    }
    ```

3. ファイルを閉じて保存し、PowerShell で次のコマンドレットを実行して、Docker エンジンを再起動します。

    ```powershell
    Stop-Service docker
    Start-Service docker
    ```

4. サービスを再起動した後、コンテナーを起動します。 コンテナーを実行したら、次のコマンドレットでコンテナーを調べて、コンテナーの分離レベルを確認できます。

    ```powershell
    docker inspect --format='{{json .HostConfig.Isolation}}' $instanceNameOrId
    ```

このコマンドから、"Process" または "hyperv" が返されます。 上記のように変更し、daemon.json を設定した場合は、"hyperv" が表示されます。

### <a name="mitigation---use-labels-and-constraints"></a>軽減策: ラベルと制約を使用する

ラベルと制約を使用してバージョンを一致させるには、次のようにします。

1. ラベルを各ノードに追加します。

    各ノードで、`OS` と `OsVersion` の 2 つのラベルを追加します。 ここではローカルでの実行を想定していますが、リモート ホスト上で変更を行ってこれらのラベルを設定することもできます。

    ```powershell
    docker node update --label-add OS="windows" $ENV:COMPUTERNAME
    docker node update --label-add OsVersion="$((Get-ComputerInfo).OsVersion)" $ENV:COMPUTERNAME
    ```

    その後、**docker node inspect** コマンドを実行すると新しく追加されたラベルが表示されるので、それを確認します。

    ```yaml
           "Spec": {
                "Labels": {
                   "OS": "windows",
                   "OsVersion": "10.0.16296"
               },
                "Role": "manager",
                "Availability": "active"
            }
    ```

2. サービスの制約を追加します。

    各ノードにラベルを付けたので、サービスの配置を決定する制約を更新することができます。 次の例で、"contoso_service" を実際のサービス名で置き換えてください。

    ```powershell
    docker service update \
        --constraint-add "node.labels.OS == windows" \
        --constraint-add "node.labels.OsVersion == $((Get-ComputerInfo).OsVersion)" \
        contoso_service
    ```

    これにより、コードが実行できる場所が指定され、制限が課されます。

サービスの制約の使用方法について詳しくは、[サービスの作成に関するリファレンス](https://docs.docker.com/engine/reference/commandline/service_create/#specify-service-constraints-constraint)を参照してください。

## <a name="matching-versions-using-kubernetes"></a>Kubernetes を使用したバージョンの一致

Kubernetes でポッドをスケジュールすると、「[Docker Swarm を使ってバージョンを一致させる方法](#matching-versions-using-docker-swarm)」で説明されているのと同じ問題が生じることがあります。 この問題も、同様の方法で回避できます。

- 開発環境と運用環境で同じ OS バージョンに基づいてコンテナーをリビルドする。 詳しくは、「[使用するコンテナー OS バージョンを選択する](#choose-which-container-os-version-to-use)」をご覧ください。
- Windows Server 2016 と Windows Server バージョン 1709 の両方のノードが同じクラスター上にある場合は、ノード ラベルとノード セレクターを使って、互換性のあるノードにポッドがスケジュールされていることを確認する。
- OS のバージョンに基づいて別のクラスターを使用する。

### <a name="finding-pods-failed-on-os-mismatch"></a>OS の不一致が原因で失敗したポッドの検索

次の例の展開では、OS バージョンが一致していないノード上でポッドがスケジュールされ、しかも Hyper-V による分離が無効です。

同じエラーは、`kubectl describe pod <podname>` によって表示されたイベントにも存在します。 複数回の試行後、多くの場合、ポッドの状態が `CrashLoopBackOff` になります。

```
$ kubectl -n plang describe pod fabrikamfiber.web-789699744-rqv6p

Name:           fabrikamfiber.web-789699744-rqv6p
Namespace:      plang
Node:           38519acs9011/10.240.0.6
Start Time:     Mon, 09 Oct 2017 19:40:30 +0000
Labels:         io.kompose.service=fabrikamfiber.web
                pod-template-hash=789699744
Annotations:    kubernetes.io/created-by={"kind":"SerializedReference","apiVersion":"v1","reference":{"kind":"ReplicaSet","namespace":"plang","name":"fabrikamfiber.web-789699744","uid":"b5062a08-ad29-11e7-b16e-000d3a...
Status:         Running
IP:             10.244.3.169
Created By:     ReplicaSet/fabrikamfiber.web-789699744
Controlled By:  ReplicaSet/fabrikamfiber.web-789699744
Containers:
  fabrikamfiberweb:
    Container ID:       docker://eab0151378308315ed6c31adf4ad9e31e6d65fd300e56e742757004a969a803a
    Image:              patricklang/fabrikamfiber.web:latest
    Image ID:           docker-pullable://patricklang/fabrikamfiber.web@sha256:562741016ce7d9a232a389449a4fd0a0a55aab178cf324144404812887250ead
    Port:               80/TCP
    State:              Waiting
      Reason:           CrashLoopBackOff
    Last State:         Terminated
      Reason:           ContainerCannotRun
      Message:          container eab0151378308315ed6c31adf4ad9e31e6d65fd300e56e742757004a969a803a encountered an error during CreateContainer: failure in a Windows system call: The operating system of the container does not match the operating system of the host. (0xc0370101) extra info: {"SystemType":"Container","Name":"eab0151378308315ed6c31adf4ad9e31e6d65fd300e56e742757004a969a803a","Owner":"docker","IsDummy":false,"VolumePath":"\\\\?\\Volume{037b6606-bc9c-461f-ae02-829c28410798}","IgnoreFlushesDuringBoot":true,"LayerFolderPath":"C:\\ProgramData\\docker\\windowsfilter\\eab0151378308315ed6c31adf4ad9e31e6d65fd300e56e742757004a969a803a","Layers":[{"ID":"f8bc427f-7aa3-59c6-b271-7331713e9451","Path":"C:\\ProgramData\\docker\\windowsfilter\\e206d2514a6265a76645b9d6b3dc6a78777c34dbf5da9fa2d564651645685881"},{"ID":"a6f35e41-a86c-5e4d-a19a-a6c2464bfb47","Path":"C:\\ProgramData\\docker\\windowsfilter\\0f21f1e28ef13030bbf0d87cbc97d1bc75f82ea53c842e9a3250a2156ced12d5"},{"ID":"4f624ca7-2c6d-5c42-b73f-be6e6baf2530","Path":"C:\\ProgramData\\docker\\windowsfilter\\4d9e2ad969fbd74fd58c98b5ab61e55a523087910da5200920e2b6f641d00c67"},{"ID":"88e360ff-32af-521d-9a3f-3760c12b35e2","Path":"C:\\ProgramData\\docker\\windowsfilter\\9e16a3d53d3e9b33344a6f0d4ed34c8a46448ee7636b672b61718225b8165e6e"},{"ID":"20f1a4e0-a6f3-5db3-9bf2-01fd3e9e855a","Path":"C:\\ProgramData\\docker\\windowsfilter\\7eec7f59f9adce38cc0a6755da58a3589287d920d37414b5b21b5b543d910461"},{"ID":"c2b3d728-4879-5343-a92a-b735752a4724","Path":"C:\\ProgramData\\docker\\windowsfilter\\8ed04b60acc0f65f541292a9e598d5f73019c8db425f8d49ea5819eab16a42f3"},{"ID":"2973e760-dc59-5800-a3de-ab9d93be81e5","Path":"C:\\ProgramData\\docker\\windowsfilter\\cc71305d45f09ce377ef497f28c3a74ee027c27f20657d2c4a5f157d2457cc75"},{"ID":"454a7d36-038c-5364-8a25-fa84091869d6","Path":"C:\\ProgramData\\docker\\windowsfilter\\9e8cde1ce8f5de861a5f22841f1ab9bc53d5f606d06efeacf5177f340e8d54d0"},{"ID":"9b748c8c-69eb-55fb-a1c1-5688cac4efd8","Path":"C:\\ProgramData\\docker\\windowsfilter\\8e02bf5404057055a71d542780a2bb2731be4b3707c01918ba969fb4d83b98ec"},{"ID":"bfde5c26-b33f-5424-9405-9d69c2fea4d0","Path":"C:\\ProgramData\\docker\\windowsfilter\\77483cedfb0964008c33d92d306734e1fab3b5e1ebb27e898f58ccfd108108f2"},{"ID":"bdabfbf5-80d1-57f1-86f3-448ce97e2d05","Path":"C:\\ProgramData\\docker\\windowsfilter\\aed2ebbb31ad24b38ee8521dd17744319f83d267bf7f360bc177e27ae9a006cf"},{"ID":"ad9b34f2-dcee-59ea-8962-b30704ae6331","Path":"C:\\ProgramData\\docker\\windowsfilter\\d44d3a675fec1070b61d6ea9bacef4ac12513caf16bd6453f043eed2792f75d8"}],"HostName":"fabrikamfiber.web-789699744-rqv6p","MappedDirectories":[{"HostPath":"c:\\var\\lib\\kubelet\\pods\\b50f0027-ad29-11e7-b16e-000d3afd2878\\volumes\\kubernetes.io~secret\\default-token-rw9dn","ContainerPath":"c:\\var\\run\\secrets\\kubernetes.io\\serviceaccount","ReadOnly":true,"BandwidthMaximum":0,"IOPSMaximum":0}],"HvPartition":false,"EndpointList":null,"NetworkSharedContainerName":"586870f5833279678773cb700db3c175afc81d557a75867bf39b43f985133d13","Servicing":false,"AllowUnqualifiedDNSQuery":false}
      Exit Code:        128
      Started:          Mon, 09 Oct 2017 20:27:08 +0000
      Finished:         Mon, 09 Oct 2017 20:27:08 +0000
    Ready:              False
    Restart Count:      10
    Environment:        <none>
    Mounts:
      /var/run/secrets/kubernetes.io/serviceaccount from default-token-rw9dn (ro)
Conditions:
  Type          Status
  Initialized   True
  Ready         False
  PodScheduled  True
Volumes:
  default-token-rw9dn:
    Type:       Secret (a volume populated by a Secret)
    SecretName: default-token-rw9dn
    Optional:   false
QoS Class:      BestEffort
Node-Selectors: beta.kubernetes.io/os=windows
Tolerations:    <none>
Events:
  FirstSeen     LastSeen        Count   From                    SubObjectPath                           Type            Reason                  Message
  ---------     --------        -----   ----                    -------------                           --------        ------                  -------
  49m           49m             1       default-scheduler                                               Normal          Scheduled               Successfully assigned fabrikamfiber.web-789699744-rqv6p to 38519acs9011
  49m           49m             1       kubelet, 38519acs9011                                           Normal          SuccessfulMountVolume   MountVolume.SetUp succeeded for volume "default-token-rw9dn"
  29m           29m             1       kubelet, 38519acs9011   spec.containers{fabrikamfiberweb}       Warning         Failed                  Failed to pull image "patricklang/fabrikamfiber.web:latest": rpc error: code = 2 desc = Error response from daemon: {"message":"Get https://registry-1.docker.io/v2/: dial tcp: lookup registry-1.docker.io: no such host"}
  49m           3m              12      kubelet, 38519acs9011   spec.containers{fabrikamfiberweb}       Normal          Pulling                 pulling image "patricklang/fabrikamfiber.web:latest"
  33m           3m              11      kubelet, 38519acs9011   spec.containers{fabrikamfiberweb}       Normal          Pulled                  Successfully pulled image "patricklang/fabrikamfiber.web:latest"
  33m           3m              11      kubelet, 38519acs9011   spec.containers{fabrikamfiberweb}       Normal          Created                 Created container
  33m           2m              11      kubelet, 38519acs9011   spec.containers{fabrikamfiberweb}       Warning         Failed                  Error: failed to start container "fabrikamfiberweb": Error response from daemon: {"message":"container fabrikamfiberweb encountered an error during CreateContainer: failure in a Windows system call: The operating system of the container does not match the operating system of the host. (0xc0370101) extra info: {\"SystemType\":\"Container\",\"Name\":\"fabrikamfiberweb\",\"Owner\":\"docker\",\"IsDummy\":false,\"VolumePath\":\"\\\\\\\\?\\\\Volume{037b6606-bc9c-461f-ae02-829c28410798}\",\"IgnoreFlushesDuringBoot\":true,\"LayerFolderPath\":\"C:\\\\ProgramData\\\\docker\\\\windowsfilter\\\\fabrikamfiberweb\",\"Layers\":[{\"ID\":\"f8bc427f-7aa3-59c6-b271-7331713e9451\",\"Path\":\"C:\\\\ProgramData\\\\docker\\\\windowsfilter\\\\e206d2514a6265a76645b9d6b3dc6a78777c34dbf5da9fa2d564651645685881\"},{\"ID\":\"a6f35e41-a86c-5e4d-a19a-a6c2464bfb47\",\"Path\":\"C:\\\\ProgramData\\\\docker\\\\windowsfilter\\\\0f21f1e28ef13030bbf0d87cbc97d1bc75f82ea53c842e9a3250a2156ced12d5\"},{\"ID\":\"4f624ca7-2c6d-5c42-b73f-be6e6baf2530\",\"Path\":\"C:\\\\ProgramData\\\\docker\\\\windowsfilter\\\\4d9e2ad969fbd74fd58c98b5ab61e55a523087910da5200920e2b6f641d00c67\"},{\"ID\":\"88e360ff-32af-521d-9a3f-3760c12b35e2\",\"Path\":\"C:\\\\ProgramData\\\\docker\\\\windowsfilter\\\\9e16a3d53d3e9b33344a6f0d4ed34c8a46448ee7636b672b61718225b8165e6e\"},{\"ID\":\"20f1a4e0-a6f3-5db3-9bf2-01fd3e9e855a\",\"Path\":\"C:\\\\ProgramData\\\\docker\\\\windowsfilter\\\\7eec7f59f9adce38cc0a6755da58a3589287d920d37414b5b21b5b543d910461\"},{\"ID\":\"c2b3d728-4879-5343-a92a-b735752a4724\",\"Path\":\"C:\\\\ProgramData\\\\docker\\\\windowsfilter\\\\8ed04b60acc0f65f541292a9e598d5f73019c8db425f8d49ea5819eab16a42f3\"},{\"ID\":\"2973e760-dc59-5800-a3de-ab9d93be81e5\",\"Path\":\"C:\\\\ProgramData\\\\docker\\\\windowsfilter\\\\cc71305d45f09ce377ef497f28c3a74ee027c27f20657d2c4a5f157d2457cc75\"},{\"ID\":\"454a7d36-038c-5364-8a25-fa84091869d6\",\"Path\":\"C:\\\\ProgramData\\\\docker\\\\windowsfilter\\\\9e8cde1ce8f5de861a5f22841f1ab9bc53d5f606d06efeacf5177f340e8d54d0\"},{\"ID\":\"9b748c8c-69eb-55fb-a1c1-5688cac4efd8\",\"Path\":\"C:\\\\ProgramData\\\\docker\\\\windowsfilter\\\\8e02bf5404057055a71d542780a2bb2731be4b3707c01918ba969fb4d83b98ec\"},{\"ID\":\"bfde5c26-b33f-5424-9405-9d69c2fea4d0\",\"Path\":\"C:\\\\ProgramData\\\\docker\\\\windowsfilter\\\\77483cedfb0964008c33d92d306734e1fab3b5e1ebb27e898f58ccfd108108f2\"},{\"ID\":\"bdabfbf5-80d1-57f1-86f3-448ce97e2d05\",\"Path\":\"C:\\\\ProgramData\\\\docker\\\\windowsfilter\\\\aed2ebbb31ad24b38ee8521dd17744319f83d267bf7f360bc177e27ae9a006cf\"},{\"ID\":\"ad9b34f2-dcee-59ea-8962-b30704ae6331\",\"Path\":\"C:\\\\ProgramData\\\\docker\\\\windowsfilter\\\\d44d3a675fec1070b61d6ea9bacef4ac12513caf16bd6453f043eed2792f75d8\"}],\"HostName\":\"fabrikamfiber.web-789699744-rqv6p\",\"MappedDirectories\":[{\"HostPath\":\"c:\\\\var\\\\lib\\\\kubelet\\\\pods\\\\b50f0027-ad29-11e7-b16e-000d3afd2878\\\\volumes\\\\kubernetes.io~secret\\\\default-token-rw9dn\",\"ContainerPath\":\"c:\\\\var\\\\run\\\\secrets\\\\kubernetes.io\\\\serviceaccount\",\"ReadOnly\":true,\"BandwidthMaximum\":0,\"IOPSMaximum\":0}],\"HvPartition\":false,\"EndpointList\":null,\"NetworkSharedContainerName\":\"586870f5833279678773cb700db3c175afc81d557a75867bf39b43f985133d13\",\"Servicing\":false,\"AllowUnqualifiedDNSQuery\":false}"}
  33m           11s             151     kubelet, 38519acs9011                                           Warning         FailedSync              Error syncing pod
  32m           11s             139     kubelet, 38519acs9011   spec.containers{fabrikamfiberweb}       Warning         BackOff                 Back-off restarting failed container
```

### <a name="mitigation---using-node-labels-and-nodeselector"></a>軽減策: ノード ラベルとノード セレクターを使用する

**kubectl get node** を実行して、すべてのノードの一覧を取得します。 その後、**kubectl describe node (ノード名)** を実行して詳細情報を取得します。

次の例では、2 つの Windows ノードで異なるバージョンが実行されています。

```
$ kubectl get node

NAME                        STATUS    AGE       VERSION
38519acs9010                Ready     21h       v1.7.7-7+e79c96c8ff2d8e
38519acs9011                Ready     4h        v1.7.7-25+bc3094f1d650a2
k8s-linuxpool1-38519084-0   Ready     21h       v1.7.7
k8s-master-38519084-0       Ready     21h       v1.7.7

$ kubectl describe node 38519acs9010

Name:                   38519acs9010
Role:
Labels:                 beta.kubernetes.io/arch=amd64
                        beta.kubernetes.io/instance-type=Standard_D2_v2
                        beta.kubernetes.io/os=windows
                        failure-domain.beta.kubernetes.io/region=westus2
                        failure-domain.beta.kubernetes.io/zone=0
                        kubernetes.io/hostname=38519acs9010
Annotations:            node.alpha.kubernetes.io/ttl=0
                        volumes.kubernetes.io/controller-managed-attach-detach=true
Taints:                 <none>
CreationTimestamp:      Fri, 06 Oct 2017 01:41:02 +0000

...

System Info:
 Machine ID:                    38519acs9010
 System UUID:
 Boot ID:
 Kernel Version:                10.0 14393 (14393.1715.amd64fre.rs1_release_inmarket.170906-1810)
 OS Image:
 Operating System:              windows
 Architecture:                  amd64
 ...

$ kubectl describe node 38519acs9011
Name:                   38519acs9011
Role:
Labels:                 beta.kubernetes.io/arch=amd64
                        beta.kubernetes.io/instance-type=Standard_DS1_v2
                        beta.kubernetes.io/os=windows
                        failure-domain.beta.kubernetes.io/region=westus2
                        failure-domain.beta.kubernetes.io/zone=0
                        kubernetes.io/hostname=38519acs9011
Annotations:            node.alpha.kubernetes.io/ttl=0
                        volumes.kubernetes.io/controller-managed-attach-detach=true
Taints:                 <none>
CreationTimestamp:      Fri, 06 Oct 2017 18:13:25 +0000
Conditions:
...

System Info:
 Machine ID:                    38519acs9011
 System UUID:
 Boot ID:
 Kernel Version:                10.0 16299 (16299.0.amd64fre.rs3_release.170922-1354)
 OS Image:
 Operating System:              windows
 Architecture:                  amd64
...

```

この例を使用して、バージョンを一致させる方法を説明します。

1. システム情報から各ノード名と `Kernel Version` (カーネル バージョン) をメモします。

    この例では、情報は次のようになります。

    名前         | バージョン
    -------------|--------------------------------------------------------
    38519acs9010 | 14393.1715.amd64fre.rs1_release_inmarket.170906-1810
    38519acs9011 | 16299.0.amd64fre.rs3_release.170922-1354

2. 各ノードに、`beta.kubernetes.io/osbuild` というラベルを追加します。 Hyper-V による分離を指定しない場合、Windows Server 2016 では、メジャーおよびマイナー バージョンの両方 (この例では 14393.1715) がサポートされている必要があります。 Windows Server バージョン 1709 では、一致する必要があるのはメジャー バージョン (この例では 16299) だけです。

    この例では、ラベルを追加するコマンドは次のようになります。

    ```
    $ kubectl label node 38519acs9010 beta.kubernetes.io/osbuild=14393.1715


    node "38519acs9010" labeled
    $ kubectl label node 38519acs9011 beta.kubernetes.io/osbuild=16299

    node "38519acs9011" labeled

    ```

3. **kubectl get nodes --show-labels** を実行して、ラベルが存在することを確認します。

    この例では、出力は次のようになります。

    ```
    $ kubectl get nodes --show-labels

    NAME                        STATUS                     AGE       VERSION                    LABELS
    38519acs9010                Ready,SchedulingDisabled   3d        v1.7.7-7+e79c96c8ff2d8e    beta.kubernetes.io/arch=amd64,beta.kubernetes.io/instance-type=Standard_D2_v2,beta.kubernetes.io/os=windows,beta.kubernetes.io/osbuild=14393.1715,failure-domain.beta.kubernetes.io/region=westus2,failure-domain.beta.kubernetes.io/zone=0,kubernetes.io/hostname=38519acs9010
    38519acs9011                Ready                      3d        v1.7.7-25+bc3094f1d650a2   beta.kubernetes.io/arch=amd64,beta.kubernetes.io/instance-type=Standard_DS1_v2,beta.kubernetes.io/os=windows,beta.kubernetes.io/osbuild=16299,failure-domain.beta.kubernetes.io/region=westus2,failure-domain.beta.kubernetes.io/zone=0,kubernetes.io/hostname=38519acs9011
    k8s-linuxpool1-38519084-0   Ready                      3d        v1.7.7                     agentpool=linuxpool1,beta.kubernetes.io/arch=amd64,beta.kubernetes.io/instance-type=Standard_D2_v2,beta.kubernetes.io/os=linux,failure-domain.beta.kubernetes.io/region=westus2,failure-domain.beta.kubernetes.io/zone=0,kubernetes.io/hostname=k8s-linuxpool1-38519084-0,kubernetes.io/role=agent
    k8s-master-38519084-0       Ready                      3d        v1.7.7                     beta.kubernetes.io/arch=amd64,beta.kubernetes.io/instance-type=Standard_D2_v2,beta.kubernetes.io/os=linux,failure-domain.beta.kubernetes.io/region=westus2,failure-domain.beta.kubernetes.io/zone=0,kubernetes.io/hostname=k8s-master-38519084-0,kubernetes.io/role=master
    ```

4. ノード セレクターを展開に追加します。 この例では、`beta.kubernetes.io/os`= windows と `beta.kubernetes.io/osbuild`= 14393.* または 16299 を使って、`nodeSelector` をコンテナー仕様に追加し、コンテナーで使用されているベース OS に一致させます。

    Windows Server 2016 向けにビルドされたコンテナーを実行するためのサンプル コード全体を次に示します。

    ```yaml
    apiVersion: extensions/v1beta1
    kind: Deployment
    metadata:
      annotations:
        kompose.cmd: kompose convert -f docker-compose-combined.yml
        kompose.version: 1.2.0 (99f88ef)
      creationTimestamp: null
      labels:
        io.kompose.service: fabrikamfiber.web
      name: fabrikamfiber.web
    spec:
      replicas: 1
      strategy: {}
      template:
        metadata:
          creationTimestamp: null
          labels:
            io.kompose.service: fabrikamfiber.web
        spec:
          containers:
          - image: patricklang/fabrikamfiber.web:latest
            name: fabrikamfiberweb
            ports:
            - containerPort: 80
            resources: {}
          restartPolicy: Always
          nodeSelector:
            "beta.kubernetes.io/os": windows
            "beta.kubernetes.io/osbuild": "14393.1715"
    status: {}
    ```

    これで、更新された展開を使ってポッドを起動できるようになりました。 ノード セレクターも `kubectl describe pod <podname>` で表示されるので、そのコマンドを実行して追加されていることを確認できます。

    この例の出力は次のようになります。

    ```
    $ kubectl -n plang describe po fa

    Name:           fabrikamfiber.web-1780117715-5c8vw
    Namespace:      plang
    Node:           38519acs9010/10.240.0.4
    Start Time:     Tue, 10 Oct 2017 01:43:28 +0000
    Labels:         io.kompose.service=fabrikamfiber.web
                    pod-template-hash=1780117715
    Annotations:    kubernetes.io/created-by={"kind":"SerializedReference","apiVersion":"v1","reference":{"kind":"ReplicaSet","namespace":"plang","name":"fabrikamfiber.web-1780117715","uid":"6a07aaf3-ad5c-11e7-b16e-000d3...
    Status:         Running
    IP:             10.244.1.84
    Created By:     ReplicaSet/fabrikamfiber.web-1780117715
    Controlled By:  ReplicaSet/fabrikamfiber.web-1780117715
    Containers:
      fabrikamfiberweb:
        Container ID:       docker://c94594fb53161f3821cf050d9af7546991aaafbeab41d333d9f64291327fae13
        Image:              patricklang/fabrikamfiber.web:latest
        Image ID:           docker-pullable://patricklang/fabrikamfiber.web@sha256:562741016ce7d9a232a389449a4fd0a0a55aab178cf324144404812887250ead
        Port:               80/TCP
        State:              Running
          Started:          Tue, 10 Oct 2017 01:43:42 +0000
        Ready:              True
        Restart Count:      0
        Environment:        <none>
        Mounts:
          /var/run/secrets/kubernetes.io/serviceaccount from default-token-rw9dn (ro)
    Conditions:
      Type          Status
      Initialized   True
      Ready         True
      PodScheduled  True
    Volumes:
      default-token-rw9dn:
        Type:       Secret (a volume populated by a Secret)
        SecretName: default-token-rw9dn
        Optional:   false
    QoS Class:      BestEffort
    Node-Selectors: beta.kubernetes.io/os=windows
                    beta.kubernetes.io/osbuild=14393.1715
    Tolerations:    <none>
    Events:
      FirstSeen     LastSeen        Count   From                    SubObjectPath                           Type            Reason                  Message
      ---------     --------        -----   ----                    -------------                           --------        ------                  -------
      5m            5m              1       default-scheduler                                               Normal          Scheduled               Successfully assigned fabrikamfiber.web-1780117715-5c8vw to 38519acs9010
      5m            5m              1       kubelet, 38519acs9010                                           Normal          SuccessfulMountVolume   MountVolume.SetUp succeeded for volume "default-token-rw9dn"
      5m            5m              1       kubelet, 38519acs9010   spec.containers{fabrikamfiberweb}       Normal          Pulling                 pulling image "patricklang/fabrikamfiber.web:latest"
      5m            5m              1       kubelet, 38519acs9010   spec.containers{fabrikamfiberweb}       Normal          Pulled                  Successfully pulled image "patricklang/fabrikamfiber.web:latest"
      5m            5m              1       kubelet, 38519acs9010   spec.containers{fabrikamfiberweb}       Normal          Created                 Created container
      5m            5m              1       kubelet, 38519acs9010   spec.containers{fabrikamfiberweb}       Normal          Started                 Started container
    ```