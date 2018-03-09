---
title: "リターン コード ODBC |Microsoft ドキュメント"
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
- return codes [ODBC]
- diagnostic information [ODBC], return codes
ms.assetid: e893b719-4392-476f-911a-5ed6da6f7e94
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9e5daaf1389631ac392fd487e99b28864b71efb8
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="return-codes-odbc"></a>ODBC のリターン コード
ODBC の各関数と呼ばれる、コードが返されますその*リターン コード、*全体的な成功または関数の失敗を示します。 一般的に、プログラミング ロジックはリターン コードを基に組み立てます。  
  
 たとえば、次のコード呼び出し**SQLFetch**を結果セット内の行を取得します。 警告情報には、(SQL_SUCCESS_WITH_INFO) が返された場合、結果セットの末尾は (SQL_NO_DATA) に達した場合、またはエラーが発生しました (SQL_ERROR) を決定する関数のリターン コードを確認します。  
  
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
  
 次の表では、これらのリターン コードを定義します。  
  
|リターン コード|Description|  
|-----------------|-----------------|  
|SQL_SUCCESS|関数は正常に完了しました。 アプリケーションの呼び出し**SQLGetDiagField**ヘッダー レコードから追加情報を取得します。|  
|SQL_SUCCESS_WITH_INFO|関数が正常に完了して可能性のある重大なエラー (警告) をします。 アプリケーションの呼び出し**SQLGetDiagRec**または**SQLGetDiagField**追加情報を取得します。|  
|SQL_ERROR|関数が失敗しました。 アプリケーションの呼び出し**SQLGetDiagRec**または**SQLGetDiagField**追加情報を取得します。 関数に出力引数の内容は未定義です。|  
|SQL_INVALID_HANDLE|関数は、無効な環境、接続、ステートメント、または記述子ハンドルのため失敗しました。 これは、プログラミング エラーを示します。 追加情報が利用できない**SQLGetDiagRec**または**SQLGetDiagField**です。 ハンドルが null ポインターかなど、接続ハンドルを必要とする引数のステートメント ハンドルが渡されたときに、間違った種類場合にのみ、このコードが返されます。|  
|SQL_NO_DATA|以上のデータを使用でした。 アプリケーションの呼び出し**SQLGetDiagRec**または**SQLGetDiagField**追加情報を取得します。 クラス 02xxx 内の 1 つまたは複数のドライバーの定義済みの状態レコードが返される可能性があります。 **注:** Odbc 2 *。x*、これは、コードが SQL_NO_DATA_FOUND という名前が返されます。|  
|SQL_NEED_DATA|実行時にパラメーターのデータが送信されたときより多くのデータが必要なまたは、追加の接続情報が必要です。 アプリケーションの呼び出し**SQLGetDiagRec**または**SQLGetDiagField**に存在する場合、追加の情報を取得します。|  
|SQL_STILL_EXECUTING|非同期的に起動された関数が実行中です。 アプリケーションの呼び出し**SQLGetDiagRec**または**SQLGetDiagField**に存在する場合、追加の情報を取得します。|
