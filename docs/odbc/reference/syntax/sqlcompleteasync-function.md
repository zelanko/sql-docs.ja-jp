---
title: "SQLCompleteAsync 関数 |Microsoft ドキュメント"
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
f1_keywords: SQLCompleteAsync
helpviewer_keywords: SQLCompleteAsync function [ODBC]
ms.assetid: 1b97c46a-d2e5-4540-8239-9d975e5321c6
caps.latest.revision: "4"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 91a6449e07ff83fd6bb7478bfc52cb077a76c955
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="sqlcompleteasync-function"></a>SQLCompleteAsync 関数
**準拠**  
 バージョンが導入されています。 ODBC 3.8  
  
 標準への準拠: なし  
  
 **概要**  
 **SQLCompleteAsync**非同期関数が完了のいずれかの通知またはポーリングをベースの処理を使用する場合を判断するために使用できます。 非同期操作の詳細については、次を参照してください。[非同期実行](../../../odbc/reference/develop-app/asynchronous-execution.md)です。  
  
 **SQLCompleteAsync**は、ODBC ドライバー マネージャーでのみ実装されます。  
  
 通知ベースの非同期処理モードで**SQLCompleteAsync**ドライバー マネージャーは、通知に使用されるイベント オブジェクトの発生後に呼び出す必要があります。 **SQLCompleteAsync**完了、非同期処理と非同期関数、リターン コードが生成されます。  
  
 ポーリングをベースの非同期処理モードで**SQLCompleteAsync**の代わりに、元の非同期関数呼び出しで引数を指定しなくても、元の非同期関数を呼び出すことができます。 **SQLCompleteAsync** ODBC カーソル ライブラリが有効になっているかどうかに関係なく使用できます。  
  
## <a name="syntax"></a>構文  
  
```vb  
  
SQLRETURN SQLCompleteAsync(  
      SQLSMALLINT HandleType,  
      SQLHANDLE   Handle,  
      RETCODE *   AsyncRetCodePtr);  
```  
  
## <a name="arguments"></a>引数  
 *HandleType*  
 [入力]非同期を完了するためのハンドルの種類を処理します。 有効な値は sql_handle_dbc として SQL_HANDLE_STMT です。  
  
 *Handle*  
 [入力]非同期を完了するためのハンドルを処理します。 場合*処理*で指定された型の有効なハンドルではありません*HandleType*、 **SQLCompleteAsync** SQL_INVALID_HANDLE が返されます。  
  
 場合*処理*で指定された型の有効なハンドルではありません*HandleType*、 **SQLCompleteAsync** SQL_INVALID_HANDLE が返されます。  
  
 *AsyncRetCodePtr*  
 [出力]非同期 API のリターン コードを格納するバッファーへのポインター。 場合*AsyncRetCodePtr* null、 **SQLCompleteAsync** SQL_ERROR を返します。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_ERROR、SQL_NO_DATA、または SQL_INVALID_HANDLE です。  
  
## <a name="diagnostics"></a>診断  
 場合**SQLCompleteAsync**返します SQL_SUCCESS、アプリケーションが指すバッファーから非同期関数のリターン コードを取得する必要があります*AsyncRetCodePtr*です。 関連付けられている SQLSTATE、存在する場合、取得できますを呼び出して**SQLGetDiagRec**で、 *HandleType* SQL_HANDLE_STMT と、ステートメント ハンドルのまたは*HandleType* sql _ のHANDLE_DBC との接続を処理します。 これらの診断レコードがわけではありません、非同期関数に関連付けられた**SQLCompleteAsync**関数。  
  
 **SQLCompleteAsync**ことを示す SQL_SUCCESS 以外のコードを返します**SQLCompleteAsync**は正しく呼び出されません。 **SQLCompleteAsync**診断レコードをここでは送信しません。 リターン コードは次のとおりです。  
  
-   SQL_INVALID_HANDLE: によってハンドルが示される*HandleType*と*処理*ハンドルが有効ではありません。  
  
-   SQL_ERROR: *AsyncRetCodePtr*が NULL またはハンドルの非同期処理が有効になっていません。  
  
-   SQL_NO_DATA: 通知モードでの非同期操作が実行されていないか、ドライバー マネージャーが、アプリケーションが通知されません。 ポーリング モードでの非同期操作が実行されていません。  
  
## <a name="comments"></a>コメント  
 ポーリングをベースの非同期処理モードで*AsyncRetCodePtr* SQL_STILL_EXECUTING がありますと**SQLCompleteAsync** SQL_SUCCESS を返します。 アプリケーションはまでポーリングを保持する必要があります*AsyncRetCodePtr* SQL_STILL_EXECUTING ではありません。 通知ベースの非同期処理モードで*AsyncRetCodePtr* SQL_STILL_EXECUTING ができなくなります。  
  
## <a name="see-also"></a>参照  
 [非同期実行 (ポーリング メソッド)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)
