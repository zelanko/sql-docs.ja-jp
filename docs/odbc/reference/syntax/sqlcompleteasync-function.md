---
title: コンプリート非同期関数 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
f1_keywords:
- SQLCompleteAsync
helpviewer_keywords:
- SQLCompleteAsync function [ODBC]
ms.assetid: 1b97c46a-d2e5-4540-8239-9d975e5321c6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4e09d61ef516e846798dd3af2d07dafa78af4605
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299657"
---
# <a name="sqlcompleteasync-function"></a>SQLCompleteAsync 関数
**適合 性**  
 バージョン導入: ODBC 3.8  
  
 標準規格のコンプライアンス: なし  
  
 **まとめ**  
 **SQLCompleteAsync**を使用して、通知ベースまたはポーリングベースの処理を使用して、非同期関数が完了したタイミングを判断できます。 非同期操作の詳細については、「[非同期実行](../../../odbc/reference/develop-app/asynchronous-execution.md)」を参照してください。  
  
 **SQLCompleteAsync**は ODBC ドライバー マネージャーでのみ実装されます。  
  
 通知ベースの非同期処理モードでは、ドライバー マネージャーが通知に使用されるイベント オブジェクトを発生させた後に**SQLCompleteAsync**を呼び出す必要があります。 **SQLCompleteAsync は**非同期処理を完了し、非同期関数は戻りコードを生成します。  
  
 ポーリングベースの非同期処理モードでは **、SQLCompleteAsync**は元の非同期関数呼び出しで引数を指定する必要なく、元の非同期関数を呼び出す代わりに使用できます。 ODBC カーソル ライブラリが有効になっているかどうかに関係なく **、SQLCompleteAsync**を使用できます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
SQLRETURN SQLCompleteAsync(  
      SQLSMALLINT HandleType,  
      SQLHANDLE   Handle,  
      RETCODE *   AsyncRetCodePtr);  
```  
  
## <a name="arguments"></a>引数  
 *HandleType*  
 [入力]非同期処理を完了するハンドルの型。 有効な値はSQL_HANDLE_DBCまたはSQL_HANDLE_STMTです。  
  
 *Handle*  
 [入力]非同期処理を完了するハンドル。 *ハンドル*が*ハンドル型*で指定された型の有効なハンドルでない場合 **、SQLCompleteAsync**はSQL_INVALID_HANDLEを返します。  
  
 *ハンドル*が*ハンドル型*で指定された型の有効なハンドルでない場合 **、SQLCompleteAsync**はSQL_INVALID_HANDLEを返します。  
  
 *非同期レットコードプター*  
 [出力]非同期 API の戻りコードを格納するバッファーへのポインター。 *非同期レットコードプター*が NULL の場合 **、SQL_ERROR返**します。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_ERROR、SQL_NO_DATA、またはSQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断  
 **SQLCompleteAsync**がSQL_SUCCESSを返す場合、アプリケーションは非同期関数の戻りコードを*AsyncRetCodePtr*が指すバッファから取得する必要があります。 関連する SQLSTATE がある場合は *、SQL_HANDLE_STMTの HandleType*とステートメント ハンドル、または SQL_HANDLE_DBC の*HandleType*と接続ハンドルを使用して**SQLGetDiagRec**を呼び出すことによって取得できます。 これらの診断レコードは、この**SQLCompleteAsync**関数ではなく、非同期関数に関連付けられます。  
  
 **SQLCompleteAsync は**、SQL_SUCCESS以外のコードを返して **、SQLCompleteAsync**が正しく呼び出されないことを示します。 この場合 **、SQLCompleteAsync**は診断レコードを送信しません。 可能な戻りコードは次のとおりです。  
  
-   SQL_INVALID_HANDLE:*ハンドル型*とハンドルで示された*ハンドル*は有効なハンドルではありません。  
  
-   SQL_ERROR: *AsyncRetCodePtr*が NULL であるか、非同期処理がハンドルで有効になっていません。  
  
-   SQL_NO_DATA: 通知モードで、非同期操作が進行中ではないか、ドライバー マネージャーがアプリケーションに通知していません。 ポーリング モードでは、非同期操作は進行中ではありません。  
  
## <a name="comments"></a>説明  
 ポーリングベースの非同期処理モードでは **、SQLCompleteAsync**がSQL_SUCCESSを返すとき*に、AsyncRetCodePtr*がSQL_STILL_EXECUTINGされる場合があります。 アプリケーションは *、AsyncRetCodePtr*がSQL_STILL_EXECUTINGされないまでポーリングを維持する必要があります。 通知ベースの非同期処理モードでは *、AsyncRetCodePtr*はSQL_STILL_EXECUTINGされません。  
  
## <a name="see-also"></a>参照  
 [非同期実行 (ポーリング メソッド)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)
