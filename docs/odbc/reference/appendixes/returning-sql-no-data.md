---
title: 返却SQL_NO_DATA |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL_NO_DATA [ODBC]
- backward compatibility [ODBC], SQL_NO_DATA
- compatibility [ODBC], SQL_NO_DATA
ms.assetid: deed0163-9d1a-4e9b-9342-3f82e64477d2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3e2c806edd5d5647e09c00975ad7207ee5c2c876
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305113"
---
# <a name="returning-sql_no_data"></a>SQL_NO_DATA を返す
ODBC *3.x*ドライバーを使用して動作する ODBC *2.x*アプリケーションが**SQLExecDirect** **、SQLExecute**、または**SQLParamData**を呼び出し、検索された更新ステートメントまたは削除ステートメントが実行されたが、データ ソースの行に影響を与えなかった場合、ODBC *3.x*ドライバーはSQL_SUCCESSを返す必要があります。 ODBC *3.x*ドライバーを使用して動作する ODBC *3.x*アプリケーションが同じ結果を**SQLExecDirect、SQLExecute**、または**SQLParamData**を呼び出すと、ODBC *3.x*ドライバーはSQL_NO_DATA返す必要があります。 **SQLExecute**  
  
 ステートメントのバッチ内の検索された更新ステートメントまたは削除ステートメントがデータ ソースの行に影響を与えない場合 **、SQLMoreResults は**SQL_SUCCESSを返します。 SQL_NO_DATA返すことはできませんが、それ以上の結果が存在しないことを意味し、行に影響を与えない検索更新/削除の結果が存在するわけではないからです。
