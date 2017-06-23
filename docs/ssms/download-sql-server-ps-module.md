---
title: "SQL Server PowerShell モジュールのダウンロード |Microsoft ドキュメント"
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
- "sql server powershell のインストール、sql server powershell のダウンロード"
ms.assetid: 
caps.latest.revision: 113
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: b68d454230d414ff52d90b4f3f71dd68ee65c6bc
ms.openlocfilehash: f55266b6ec28e2552047cc36a5060945006b2caa
ms.contentlocale: ja-jp
ms.lasthandoff: 06/23/2017

---
# <a name="download-sql-server-powershell-module"></a>SQL Server PowerShell モジュールをダウンロードします。
SQL Server Management Studio の 17.0 リリースの一環として、SQL Server PowerShell モジュールは、PowerShell ギャラリーを介して今すぐ同梱されています。  モジュールは、SSMS のインストール パッケージに含まれなくです。 SSMS 17.0 以降は、PowerShell を使用してするには、SQL Server のモジュールを追加の手順としてのコンピューターにインストールする必要があります。

Windows Management Framework の最新バージョンのインストールに関するドキュメントを完全し、PowerShell モジュールをインストールする方法で一般にあります、 [PowerShell ギャラリー](https://www.powershellgallery.com/)サイトです。

SQL Server のモジュールをインストールする PowerShell コマンドです。

> Install-module の名前を SqlServer-CurrentUser のスコープ

コンピューター上の SQL Server PowerShell モジュールの以前のバージョンがある場合は、必要がありますを提供する、"-AllowClobber"パラメーター。  

PowerShell ギャラリーに出荷された、SQL Server PowerShell モジュールのバージョンでは、バージョン管理をサポートし、PowerShell バージョン 5.0 以降が必要です。

