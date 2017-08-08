---
title: "SQL Server PowerShell モジュールのダウンロード | Microsoft Docs"
ms.custom: 
ms.date: 03/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
keywords:
- "sql server powershell のインストール, sql server powershell のダウンロード"
ms.assetid: 
caps.latest.revision: 113
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: b68d454230d414ff52d90b4f3f71dd68ee65c6bc
ms.openlocfilehash: f55266b6ec28e2552047cc36a5060945006b2caa
ms.contentlocale: ja-jp
ms.lasthandoff: 07/31/2017

---
# <a name="download-sql-server-powershell-module"></a>SQL Server PowerShell モジュールのダウンロード
SQL Server Management Studio の 17.0 リリースの一部として、SQL Server PowerShell モジュールが PowerShell ギャラリーを介して提供されます。  このモジュールは SSMS インストール パッケージには含まれなくなっています。 SSMS 17.0 以降で PowerShell を使うには、追加の手順として SQL Server モジュールをコンピューターにインストールする必要があります。

Windows Management Framework の最新バージョンのインストールおよび PowerShell モジュールの一般的なインストール方法に関する完全なドキュメントについては、[PowerShell ギャラリー](https://www.powershellgallery.com/)のサイトをご覧ください。

SQL Server をモジュールをインストールする PowerShell コマンドは次のとおりです。

> Install-module -Name SqlServer -Scope CurrentUser

コンピューターに SQL Server PowerShell モジュールの以前のバージョンがある場合は、"-AllowClobber" パラメーターの指定が必要になる場合があります。  

PowerShell ギャラリーにリリースされる SQL Server PowerShell モジュールのバージョンは、バージョン管理をサポートし、PowerShell バージョン 5.0 以降が必要です。

