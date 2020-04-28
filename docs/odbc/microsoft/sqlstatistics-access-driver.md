---
title: SQLStatistics (Access Driver) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Access driver [ODBC], SQLStatistics
- SQLStatistics function [ODBC], Access Driver
ms.assetid: 6117ac77-1020-4f0c-8eed-e671c34c1f21
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f75f41bf63cbf224772955effa0f120b5d384111
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299362"
---
# <a name="sqlstatistics-access-driver"></a>SQLStatistics (Access ドライバー)
> [!NOTE]  
>  このトピックでは、ドライバー固有の情報にアクセスします。 この関数の一般的な情報については、「 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)」の該当するトピックを参照してください。  
  
|列|説明|  
|------------|--------------|  
|TABLE_QUALIFIER|Microsoft Access では、データベースファイルへのパスが返されます。<br /><br /> パターンマッチングは、 *Sztablequalifier*引数ではサポートされていません。|  
|TABLE_OWNER|所有者名がサポートされていないため、この列には NULL が返されます。|  
|TABLE_NAME|区切られていないテーブル名です。<br /><br /> パターンマッチングは、 *Sztablename*引数ではサポートされていません。|  
|INDEX_QUALIFIER|常に NULL が返されます。|  
|INDEX_NAME|インデックスに依存します。|  
|TYPE|型に対しては、SQL_TABLE_STAT または SQL_INDEX_OTHER のみが返されます。|  
|SEQ_IN_INDEX|インデックスに依存します。|  
|COLUMN_NAME|インデックスに依存します。|  
|COLLATION|インデックスに依存します。|  
|CARDINALITY|Microsoft アクセスのみに対して返されます。|  
|PAGES|常に NULL が返されます。|  
  
 フィルター処理は、一意性 ( *Funique*引数) に基づいています。 *FAccuracy*パラメーターは無視されます。
