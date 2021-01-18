---
title: Windows コンテナーの印刷スプーラー
description: Windows コンテナーでの印刷スプーラー サービスの現在の動作について説明します
keywords: Docker, コンテナー, プリンター, スプーラー
author: cwilhit
ms.author: cwilhit
ms.date: 10/22/2019
ms.topic: tutorial
ms.openlocfilehash: df51140f3e44bf24c5481d23a3437796fe4c3641
ms.sourcegitcommit: 24a7d693da95512ac371bdbf6466f46e187c9c58
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/13/2021
ms.locfileid: "98181839"
---
# <a name="print-spooler-in-windows-containers"></a>Windows コンテナーの印刷スプーラー

印刷サービスに依存するアプリケーションは、Windows コンテナーで正常にコンテナー化できます。 プリンター サービスの機能を正常に有効にするには、特別な要件を満たす必要があります。 このガイドでは、展開を適切に構成する方法について説明します。

> [!IMPORTANT]
> コンテナーで印刷サービスへのアクセスを正常に取得することはできるものの、形式上は機能の制限があり、印刷関連の一部の操作が機能しない可能性があります。 たとえば、ホストへのプリンター ドライバーのインストールに依存しているアプリは、**コンテナー内からドライバーをインストールすることはサポートされていない** ため、コンテナー化できません。 コンテナーでサポートされていない印刷機能のサポートをご希望の場合は、以下からフィードバックを開いてください。

## <a name="setup"></a>セットアップ

* ホストは、Windows Server 2019 または Windows 10 Pro または Enterprise の 2018 年 10 月の更新プログラム以降である必要があります。
* [mcr.microsoft.com/windows](https://hub.docker.com/_/microsoft-windowsfamily-windows) イメージが、対象の基本イメージである必要があります。 他の Windows コンテナーの基本イメージ (Nano Server や Windows Server Core など) は、プリント サーバーの役割を果たすことはできません。

### <a name="hyper-v-isolation"></a>Hyper-V による分離

Hyper-V による分離を使用してコンテナーを実行することをお勧めします。 このモードで実行すると、印刷サービスにアクセスしながら、希望する数のコンテナーを実行できます。 ホスト側のスプーラー サービスを変更する必要はありません。

次の PowerShell クエリを使用して、機能を確認できます。

```PowerShell
PS C:\Users\Administrator> docker run -it --isolation hyperv mcr.microsoft.com/windows:1809 powershell.exe
Windows PowerShell
Copyright (C) Microsoft Corporation. All rights reserved.

PS C:\> Get-Service spooler

Status   Name               DisplayName
------   ----               -----------
Running  spooler            Print Spooler


PS C:\> Get-Printer

Name                           ComputerName    Type         DriverName                PortName        Shared   Published
----                           ------------    ----         ----------                --------        ------   --------
Microsoft XPS Document Writer                  Local        Microsoft XPS Document... PORTPROMPT:     False    False
Microsoft Print to PDF                         Local        Microsoft Print To PDF    PORTPROMPT:     False    False
Fax                                            Local        Microsoft Shared Fax D... SHRFAX:         False    False


PS C:\>
```

### <a name="process-isolation"></a>プロセスの分離

プロセス分離コンテナーではカーネルが共有されるため、現在の動作では、ホストとそのコンテナーの子すべてで、ユーザーが実行できるプリンター スプーラー サービスの **インスタンスは 1 つ** のみに制限されています。 ホストでプリンター スプーラーが実行されている場合、ホストのそのサービスを停止してからでなければ、ゲストでプリンター サービスを起動できません。

> [!TIP]
> ユーザーがコンテナーを起動して、コンテナーとホストの両方で同時にスプーラー サービスに対するクエリを同時に実行すると、どちら側でも "実行中" として状態が報告されます。 しかし、紛らわしいことに、コンテナーは使用可能なプリンターの一覧についてクエリを実行できません。 ホストのスプーラー サービスは実行されていないはずです。

ホストでプリンター サービスが実行されているかどうかを確認するには、PowerShell で次のクエリを使用します。

```PowerShell
PS C:\Users\Administrator> Get-Service spooler

Status   Name               DisplayName
------   ----               -----------
Running  spooler            Print Spooler

PS C:\Users\Administrator>
```

ホストでスプーラー サービスを停止するには、PowerShell で次のコマンドを使用します。

```PowerShell
Stop-Service spooler
Set-Service spooler -StartupType Disabled
```

コンテナーを起動し、プリンターへのアクセスを確認します。

```PowerShell
PS C:\Users\Administrator> docker run -it --isolation process mcr.microsoft.com/windows:1809 powershell.exe
Windows PowerShell
Copyright (C) Microsoft Corporation. All rights reserved.


PS C:\> Get-Service spooler

Status   Name               DisplayName
------   ----               -----------
Running  spooler            Print Spooler


PS C:\> Get-Printer

Name                           ComputerName    Type         DriverName                PortName        Shared   Published
----                           ------------    ----         ----------                --------        ------   --------
Microsoft XPS Document Writer                  Local        Microsoft XPS Document... PORTPROMPT:     False    False
Microsoft Print to PDF                         Local        Microsoft Print To PDF    PORTPROMPT:     False    False
Fax                                            Local        Microsoft Shared Fax D... SHRFAX:         False    False


PS C:\>
```