---
title: SQL 統計 (パラドックス ドライバ) |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5e9782eb22e4176a57aab7bdd3823982575a0d55
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299322"
---
# <a name="sqlstatistics-paradox-driver"></a>SQLStatistics (Paradox ドライバー)
> [!NOTE]  
>  このトピックでは、Paradox ドライバー固有の情報を提供します。 この関数の一般的な情報については[、ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)の該当するトピックを参照してください。  
  
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
