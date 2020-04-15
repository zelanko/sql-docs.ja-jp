---
title: 統計 (dBASE ドライバー) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLStatistics function [ODBC], dBASE Driver
- DBase driver [ODBC], SQLStatistics
ms.assetid: 631cec1b-66b7-4103-b9a7-ffd81da3c442
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: deec1d7cff9ea1d0f8560b3c9b866cad79e69a25
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299352"
---
# <a name="sqlstatistics-dbase-driver"></a>SQLStatistics (dBASE ドライバー)
> [!NOTE]  
>  このトピックでは、dBASE ドライバー固有の情報を提供します。 この関数の一般的な情報については[、ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)の該当するトピックを参照してください。  
  
|列|説明|  
|------------|--------------|  
|TABLE_QUALIFIER|ディレクトリへのパス。<br /><br /> パターン マッチングは *、szTableQualifier*引数ではサポートされていません。|  
|TABLE_OWNER|所有者名がサポートされていないため、この列には NULL が戻されます。|  
|TABLE_NAME|区切り文字なしのテーブル名。<br /><br /> パターン マッチングは *、szTableName*引数ではサポートされていません。|  
|INDEX_QUALIFIER|NULL は常に返されます。|  
|INDEX_NAME|インデックスに依存します。|  
|TYPE|TYPE に対してSQL_TABLE_STATまたはSQL_INDEX_OTHERのみが返されます。|  
|SEQ_IN_INDEX|インデックスに依存します。|  
|COLUMN_NAME|インデックスに依存します。|  
|COLLATION|インデックスに依存します。|  
|PAGES|NULL は常に返されます。|  
  
 フィルタ処理は、一意性 *(fUnique*引数) に基づいています。 *fAccuracy*パラメーターは無視されます。
