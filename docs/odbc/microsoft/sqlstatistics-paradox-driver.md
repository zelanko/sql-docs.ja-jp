---
title: SQLStatistics (Paradox ドライバー) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Paradox driver [ODBC], SQLStatistics
- SQLStatistics function [ODBC], Paradox Driver
ms.assetid: 886cab83-d599-4fbc-9c88-e8cb833aac4b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d60296a73367b4718c4da5df036befa0cd34b505
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68114374"
---
# <a name="sqlstatistics-paradox-driver"></a>SQLStatistics (Paradox ドライバー)
> [!NOTE]  
>  このトピックでは、Paradox ドライバー固有の情報について説明します。 この関数の一般的な情報については、「 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)」の該当するトピックを参照してください。  
  
|列|説明|  
|------------|--------------|  
|TABLE_QUALIFIER|ディレクトリへのパス。<br /><br /> パターンマッチングは、 *Sztablequalifier*引数ではサポートされていません。|  
|TABLE_OWNER|所有者名がサポートされていないため、この列には NULL が返されます。|  
|TABLE_NAME|区切られていないテーブル名です。<br /><br /> パターンマッチングは、 *Sztablename*引数ではサポートされていません。|  
|INDEX_QUALIFIER|常に NULL が返されます。|  
|INDEX_NAME|インデックスに依存します。|  
|TYPE|型に対しては、SQL_TABLE_STAT または SQL_INDEX_OTHER のみが返されます。|  
|SEQ_IN_INDEX|インデックスに依存します。|  
|COLUMN_NAME|インデックスに依存します。|  
|COLLATION|インデックスに依存します。|  
|PAGES|常に NULL が返されます。|  
  
 フィルター処理は、一意性 ( *Funique*引数) に基づいています。 *FAccuracy*パラメーターは無視されます。
