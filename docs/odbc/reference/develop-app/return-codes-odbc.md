---
title: リターン コード ODBC |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- return codes [ODBC]
- diagnostic information [ODBC], return codes
ms.assetid: e893b719-4392-476f-911a-5ed6da6f7e94
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 15e434025ed1201ca61371c2fb88e70143e131a5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304313"
---
# <a name="return-codes-odbc"></a>リターン コード (ODBC)
ODBC の各関数は、関数の全体的な成功または失敗を示す*戻りコード*と呼ばれるコードを返します。 一般的に、プログラミング ロジックはリターン コードを基に組み立てます。  
  
 たとえば、次のコードは**SQLFetch**を呼び出して結果セット内の行を取得します。 この関数は、結果セットの終わりに達したかどうか (SQL_NO_DATA、警告情報が返された (SQL_SUCCESS_WITH_INFO) か、エラーが発生したかどうか (SQL_ERROR) を調べるため、関数の戻りコードをチェックします。  
  
```  
SQLRETURN   rc;  
SQLHSTMT    hstmt;  
  
while ((rc=SQLFetch(hstmt)) != SQL_NO_DATA) {  
   if (rc == SQL_SUCCESS_WITH_INFO) {  
      // Call function to display warning information.  
   } else if (rc == SQL_ERROR) {  
      // Call function to display error information.  
      break;  
   }  
   // Process row.  
}  
```  
  
 リターン コード SQL_INVALID_HANDLE は常にプログラミング エラーを示します。実行時にはこのコードが返されないようにしてください。 それ以外のリターン コードは実行時の情報を含んでいます。ただし、SQL_ERROR はプログラミング エラーを示す場合もあります。  
  
 次の表に、リターン コードを定義します。  
  
|リターン コード|説明|  
|-----------------|-----------------|  
|SQL_SUCCESS|関数は正常に完了しました。 アプリケーションは、ヘッダー レコードから追加情報を取得する**SQLGetDiagField**を呼び出します。|  
|SQL_SUCCESS_WITH_INFO|関数が正常に完了し、致命的でないエラー (警告) が発生した可能性があります。 アプリケーションは、追加情報を取得するために**SQLGetDiagRec**または**SQLGetDiagField**を呼び出します。|  
|SQL_ERROR|関数に失敗しました。 アプリケーションは、追加情報を取得するために**SQLGetDiagRec**または**SQLGetDiagField**を呼び出します。 関数に対する出力引数の内容は未定義です。|  
|SQL_INVALID_HANDLE|環境、接続、ステートメント、または記述子ハンドルが無効なため、関数が失敗しました。 これは、プログラミング エラーを示します。 追加情報は **、SQLDiagRec**または**SQLGetDiagField**から入手できません。 このコードは、接続ハンドルを必要とする引数にステートメント ハンドルが渡された場合など、ハンドルが null ポインターであるか、または型が間違っている場合にのみ返されます。|  
|SQL_NO_DATA|これ以上データが利用できませんでした。 アプリケーションは、追加情報を取得するために**SQLGetDiagRec**または**SQLGetDiagField**を呼び出します。 クラス 02xxx の 1 つ以上のドライバー定義の状態レコードが返される場合があります。 **注:** ODBC 2 で。*x*の場合、この戻りコードはSQL_NO_DATA_FOUND名前が付けられました。|  
|SQL_NEED_DATA|実行時にパラメーター・データが送信されたり、追加の接続情報が必要な場合など、さらにデータが必要になります。 アプリケーションは、追加情報を取得するために**SQLGetDiagRec**または**SQLGetDiagField**を呼び出します (存在する場合)。|  
|SQL_STILL_EXECUTING|非同期的に開始された関数は、まだ実行中です。 アプリケーションは、追加情報を取得するために**SQLGetDiagRec**または**SQLGetDiagField**を呼び出します (存在する場合)。|
