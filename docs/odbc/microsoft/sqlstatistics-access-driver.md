---
title: SQL 統計 (アクセス ドライバー) |マイクロソフトドキュメント
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299362"
---
# <a name="sqlstatistics-access-driver"></a>SQLStatistics (Access ドライバー)
> [!NOTE]  
>  このトピックでは、アクセス ドライバー固有の情報を提供します。 この関数の一般的な情報については[、ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)の該当するトピックを参照してください。  
  
|列|説明|  
|------------|--------------|  
|TABLE_QUALIFIER|Access のデータベース ファイルへのパスが返されます。<br /><br /> パターン マッチングは *、szTableQualifier*引数ではサポートされていません。|  
|TABLE_OWNER|所有者名がサポートされていないため、この列には NULL が戻されます。|  
|TABLE_NAME|区切り文字なしのテーブル名。<br /><br /> パターン マッチングは *、szTableName*引数ではサポートされていません。|  
|INDEX_QUALIFIER|NULL は常に返されます。|  
|INDEX_NAME|インデックスに依存します。|  
|TYPE|TYPE に対してSQL_TABLE_STATまたはSQL_INDEX_OTHERのみが返されます。|  
|SEQ_IN_INDEX|インデックスに依存します。|  
|COLUMN_NAME|インデックスに依存します。|  
|COLLATION|インデックスに依存します。|  
|CARDINALITY|Access の場合にのみ返されます。|  
|PAGES|NULL は常に返されます。|  
  
 フィルタ処理は、一意性 *(fUnique*引数) に基づいています。 *fAccuracy*パラメーターは無視されます。
