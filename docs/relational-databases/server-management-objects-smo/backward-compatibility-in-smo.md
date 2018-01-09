---
title: "SMO の旧バージョンとの互換性 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: smo
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 2f986436-aaf2-4eaf-9809-df849d97d4fb
caps.latest.revision: "12"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d82e62d1c4ed82a4339398f60a7e8a59ac9c2d59
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="backward-compatibility-in-smo"></a>SMO の旧バージョンとの互換性
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]以前のバージョンを使用して記述されている SMO アプリケーション[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で SMO を使用して再コンパイルできます[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]です。  
  
## <a name="migrating-smo-applications"></a>SMO アプリケーションの移行  
 古いバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の SMO dll への参照は削除し、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で提供される新しい SMO dll への参照を含める必要があります。  
  
 少なくとも、以下の参照を設定してください。  
  
-   Microsoft.SqlServer.ConnectionInfo  
  
-   Microsoft.SqlServer.Smo  
  
-   Microsoft.SqlServer.Management.Sdk.Sfc  
  
 これらのファイルは、接続クラス、SMO ユーティリティ クラス、および基盤クラスのために必要です。  
  
> [!NOTE]  
>  SmoEnum.dll は削除されたため、この dll への参照は SMO [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] プロジェクトから削除する必要があります。  
  
 名前空間も変更されたため、以下のものを使ってください。  
  
##### <a name="for-visual-c"></a>Visual C# 用  
  
```  
using Microsoft.SqlServer.Management.Smo;  
using Microsoft.SqlServer.Management.Common;  
```  
  
##### <a name="for-visual-basic"></a>Visual Basic 用  
  
```  
Imports Microsoft.SqlServer.Management.Smo  
Imports Microsoft.SqlServer.Management.Common  
```  
  
 コードがような Urn 機能を使用する場合**Server.GetSqlSmoObject(Urn)**、Microsoft.SqlServer.Management.Sdk.Sfc 名前空間にリンクする必要があります。  
  
 コードで Transfer オブジェクトを直接使用している場合は、Microsoft.SqlServer.Management.SmoExtended 名前空間へのリンクが必要になります。  
  
 コードを移行するときに、コードの修正が必要になる場合があります。 これは、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ではいくつかの [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 機能および [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 機能が非推奨になっているためです。 非推奨機能の詳細については、次を参照してください。 [SQL Server 2016 におけるデータベース エンジン機能を非推奨](../../database-engine/deprecated-database-engine-features-in-sql-server-2016.md)で[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]オンライン ブック。  
  
  
