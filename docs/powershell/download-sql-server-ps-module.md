---
title: SQL Server PowerShell モジュールのダウンロード | Microsoft Docs
ms.custom: ''
ms.date: 10/08/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
keywords:
- sql server powershell のインストール, sql server powershell のダウンロード
ms.assetid: ''
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 40873fe63b897da52fc9a7d440a8568872431d72
ms.sourcegitcommit: b75fc8cfb9a8657f883df43a1f9ba1b70f1ac9fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/08/2018
ms.locfileid: "48851757"
---
# <a name="install-sql-server-powershell-module"></a>SQL Server PowerShell モジュールのインストール
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

この記事は、**SqlServer** PowerShell モジュールをインストールする手順を説明しています。
> [!NOTE]
> 2 つの SQL Server PowerShell モジュールがあります。 
> * **SQLPS**: このモジュールは (後方互換性のため) SQL Server のインストールに含まれていますが、今後更新されることはありません。 最新の PowerShell モジュールは **SqlServer** モジュールです。
> * **SqlServer**: このモジュールには、最新の SQL 機能をサポートする新しいコマンドレットが含まれています。 モジュールには、**SQLPS** 内のコマンドレットの更新バージョンも含まれています。 

SQL Server Management Studio (SSMS) には前のバージョンの **SqlServer** が含まれて*いました*が、SSMS の 16.x バージョンのみです。 PowerShell を SSMS 17.0 以降で使用するには、**SqlServer** モジュールを [PowerShell ギャラリー](https://www.powershellgallery.com/packages/Sqlserver)からインストールする必要があります。
**SqlServer** モジュールの現在のバージョンは 21.0.17279 です。 これは、Microsoft.SQLServer.SMO のバージョン v140 に基づいています。  
SQL Server の (Microsoft.SQLServer.SMO のバージョン v150 に基づく) 次のバージョンをサポートするバージョンのモジュールを探している場合は、このページの最後のセクション (モジュールのプレリリース バージョンを取得する方法) を参照してください。 モジュールの最新のプレリリース バージョンは 21.1.18040-preview です。

PowerShell ギャラリーから **SqlServer** モジュールをインストールするには、[PowerShell](https://docs.microsoft.com/powershell/scripting/powershell-scripting) セッションを開始し、次のコマンドを使用します。 インストールに問題が発生した場合は、[Install-module のドキュメント](https://docs.microsoft.com/powershell/gallery/psget/module/psget_install-module)と [Install-Module の参照](https://docs.microsoft.com/powershell/module/powershellget/Install-Module)をご覧ください。

**SqlServer** モジュールをインストールするには:

```Install-Module -Name SqlServer```

以前のバージョンの **SqlServer** モジュールがコンピューター上にある場合、`Update-Module` (この記事で後述) を使用できる、または `-AllowClobber` パラメーターを指定できる場合があります。  

```Install-Module -Name SqlServer -AllowClobber```

管理者として PowerShell セッションを実行できない場合は、次のようにして現在のユーザーにインストールできます。

```Install-Module -Name SqlServer -Scope CurrentUser```

**SqlServer** モジュールの更新バージョンがある場合、`Update-Module` を使用してバージョンを更新できます。

```Update-Module -Name SqlServer```

インストールされているモジュールのバージョンを表示する場合:

```Get-Module SqlServer -ListAvailable```

モジュールの特定のバージョンを使用するには、次のような特定のバージョン番号でインポートできます。

```Import-Module SqlServer -Version 21.0.17178```

> [!NOTE]
> モジュールのプレリリース ("プレビュー") バージョンは、PowerShell ギャラリーで入手できます。 [PowerShellGet](https://www.powershellgallery.com/packages/PowerShellGet) モジュール) の一部である、更新された *Find-Module* コマンドレットと *Install-Module* コマンドレットを使用して *-AllowPrerelease* スイッチを渡すことで、これらを検出してインストールできます。
>
> モジュールのプレリリース/プレビュー バージョンを検出するには、次のコマンドを実行できます。
>
> ```Find-Module SqlServer -AllowPrerelease```
>
> モジュールの特定のプレリリース/プレビュー バージョンをインストールするには、次のような特定のバージョン番号でインストールできます。
>
> ```Install-Module SqlServer -RequiredVersion 21.1.18040-preview -AllowPrerelease```
> 

PowerShell ギャラリーの **SqlServer** モジュールのバージョンは、バージョン管理をサポートし、PowerShell バージョン 5.0 以降が必要です。 

* [PowerShell ギャラリーの SqlServer モジュール](https://www.powershellgallery.com/packages/Sqlserver) 
* [SqlServer のコマンドレット](https://docs.microsoft.com/powershell/module/sqlserver)
* [SQLPS のコマンドレット](https://docs.microsoft.com/powershell/module/sqlps)
