---
title: "SQL Server PowerShell モジュールのダウンロード | Microsoft Docs"
ms.custom: 
ms.date: 03/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
keywords: "sql server powershell のインストール, sql server powershell のダウンロード"
ms.assetid: 
caps.latest.revision: "113"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 7f6ab758ecd32d4d9bdb39d9157cbba9b38e73ba
ms.sourcegitcommit: b0c223ba0f78af5eb76948e68e2d1aab2e7b80c1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2017
---
# <a name="download-sql-server-powershell-module"></a>SQL Server PowerShell モジュールのダウンロード
SQL Server Management Studio の 17.0 リリースの一部として、SQL Server PowerShell モジュールが PowerShell ギャラリーを介して提供されます。  このモジュールは SSMS インストール パッケージには含まれなくなっています。 SSMS 17.0 以降で PowerShell を使うには、追加の手順として SQL Server モジュールをコンピューターにインストールする必要があります。

Windows Management Framework の最新バージョンのインストールおよび PowerShell モジュールの一般的なインストール方法に関する完全なドキュメントについては、[PowerShell ギャラリー](https://www.powershellgallery.com/)のサイトをご覧ください。

SQL Server モジュールをインストールする PowerShell コマンドは次のとおりです。

> Install-Module -Name SqlServer

このコマンドは、コンピューターのすべてのユーザーに対するモジュールをインストールします。 管理者として PowerShell プロセスを実行している必要があります。

> Install-Module -Name SqlServer -Scope CurrentUser

このコマンドは、PowerShell の現在のプロセスを実行しているユーザーに対するモジュールをインストールします。 管理者権限で PowerShell プロセスを実行している必要はありません。

コンピューターに SQL Server PowerShell モジュールの以前のバージョンがある場合は、"-AllowClobber" パラメーターの指定が必要になる場合があります。  

管理者として実行していて、コンピューターのすべてのユーザーに対するモジュールをインストールする場合

> Install-Module -Name SqlServer -AllowClobber

管理者として実行できない、または現在のユーザーに対してのみインストールする場合

> Install-Module -Name SqlServer -Scope CurrentUser -AllowClobber

SqlServer モジュールの更新バージョンがある場合、Update-Module コマンドを使用してバージョンを更新できます

> Update-Module -Name SqlServer

使用可能なマシンにインストールされているモジュールのバージョンを表示する場合

> Get-Module SqlServer -ListAvailable

インポートに使用できるスクリプトで特定のバージョンのモジュールを使用する場合

> Import-Module SqlServer -Version 21.0.17178

PowerShell ギャラリーにリリースされる SQL Server PowerShell モジュールのバージョンは、バージョン管理をサポートし、PowerShell バージョン 5.0 以降が必要です。 SqlServer モジュールは [PowerShell ギャラリー](https://www.powershellgallery.com/packages/Sqlserver/)にあります 
