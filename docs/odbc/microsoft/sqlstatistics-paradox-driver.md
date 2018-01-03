---
title: "SQLStatistics (Paradox ドライバー) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Paradox driver [ODBC], SQLStatistics
- SQLStatistics function [ODBC], Paradox Driver
ms.assetid: 886cab83-d599-4fbc-9c88-e8cb833aac4b
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c2f158fd9d3fc1a7695e49bfa634f8cd064aac13
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="sqlstatistics-paradox-driver"></a>SQLStatistics (Paradox ドライバー)
> [!NOTE]  
>  このトピックでは、Paradox ドライバー固有の情報を提供します。 この関数の概要については、下の該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)です。  
  
|[列]|コメント|  
|------------|--------------|  
|TABLE_QUALIFIER|ディレクトリへのパス。<br /><br /> パターン マッチはではサポートされていません、 *szTableQualifier*引数。|  
|TABLE_OWNER|所有者名がサポートされていないために、この列に NULL が返されます。|  
|TABLE_NAME|区切られていないテーブルの名前。<br /><br /> パターン マッチはではサポートされていません、 *szTableName*引数。|  
|INDEX_QUALIFIER|NULL は常に返されます。|  
|INDEX_NAME|インデックスに依存します。|  
|TYPE|型の SQL_TABLE_STAT または SQL_INDEX_OTHER のみが返されます。|  
|SEQ_IN_INDEX|インデックスに依存します。|  
|COLUMN_NAME|インデックスに依存します。|  
|COLLATION|インデックスに依存します。|  
|PAGES|NULL は常に返されます。|  
  
 一意性に基づくフィルター処理は、(、 *fUnique*引数)。 *FAccuracy*パラメーターは無視されます。
