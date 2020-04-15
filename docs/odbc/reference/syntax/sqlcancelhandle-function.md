---
title: 関数を処理する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
f1_keywords:
- SQLCancelHandle
helpviewer_keywords:
- SQLCancelHandle function [ODBC]
ms.assetid: 16049b5b-22a7-4640-9897-c25dd0f19d21
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 059ed283032feb96ca5e6b12520682ccb034752a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299667"
---
# <a name="sqlcancelhandle-function"></a>SQLCancelHandle 関数
**適合 性**  
 バージョン導入: ODBC 3.8  
  
 標準規格のコンプライアンス: なし  
  
 ほとんどの ODBC 3.8 (以降) ドライバがこの関数を実装すると予想されます。 ドライバーが、*ハンドルパラメーターの*接続ハンドルを持つ**SQLCancelHandle**への呼び出しは、IM001 の SQLSTATE を持つSQL_ERRORを返し、メッセージ 'ドライバーはこの関数をサポートしていません'*ステートメント*ハンドルを使用して**SQLCancelHandle**への呼び出しは、ドライバー マネージャーによって**SQLCancel**への呼び出しにマップされ、ドライバーが**SQLCancel**を実装する場合に処理できます。 アプリケーションは、ドライバーが SQLCancelHandle をサポートするかどうかを判断するのに**は、SQLGetFunctions**を使用できます。 **SQLCancelHandle**  
  
 **まとめ**  
 **接続**またはステートメントの処理をキャンセルします。 ドライバー マネージャーは、**呼**び出しをマップしますハンドル*型*がSQL_HANDLE_STMT場合は **、SQLキャンセル**への呼び出しにします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
SQLRETURN SQLCancelHandle(  
      SQLSMALLINT  HandleType,  
      SQLHANDLE    Handle);  
```  
  
## <a name="arguments"></a>引数  
 *HandleType*  
 [入力]処理を cacel するハンドルの型。 有効な値はSQL_HANDLE_DBCまたはSQL_HANDLE_STMTです。  
  
 *Handle*  
 [入力]処理をキャンセルするハンドル。  
  
 *ハンドル*が*ハンドル型*で指定された型の有効なハンドルでない場合は **、SQL_INVALID_HANDLE**を返します。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、またはSQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断  
 **SQLCancelHandle**がSQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返すときは、関連付けられた SQLSTATE 値を取得するには、SQL_HANDLE_STMTの*ハンドル型*とステートメント*ハンドル*ハンドル、またはSQL_HANDLE_DBC*ハンドルと**接続ハンドル*ハンドルを使用して**SQLGetDiagRec**を呼び出します。  
  
 次の表は **、SQLCancelHandle**によって一般的に返される SQLSTATE 値を示し、この関数のコンテキストで各値を説明します。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージ。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|HY000|一般的なエラー|特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 *引数\*MessageText*バッファー内の[SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)によって返されるエラー メッセージは、エラーとその原因を記述します。|  
|HY001|メモリ割り当てエラー|ドライバは、関数の実行または完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY010|関数シーケンス エラー|*Handle*に関連付けられたステートメント ハンドルの 1 つに対して、非同期に実行されるステートメント関連関数が呼び出され *、HandleType*がSQL_HANDLE_DBCに設定されました。 非同期関数は **、SQLCancelHandle**が呼び出されたときに実行されていました。<br /><br /> (DM)*引数*がSQL_HANDLE_STMT。非同期に実行される関数が、関連付けられた接続ハンドルで呼び出されました。この関数が呼び出されたとき、関数はまだ実行されていました。<br /><br /> (DM)*ハンドル*と*ハンドル型*に関連付けられたステートメント ハンドルの 1 つがSQL_HANDLE_DBCに設定され、SQL_PARAM_DATA_AVAILABLE返された場合に、SQL**実行** **、SQLExecDirect、** または**SQLMoreResults**が呼び出されました。 この関数は、ストリームされたすべてのパラメーターに対してデータが取得される前に呼び出されました。<br /><br /> **接続***ハンドル*に対して呼び出され、SQL_NEED_DATA返されました。 この関数は、参照処理が完了する前に呼び出されました。|  
|HY013|メモリ管理エラー|メモリ不足の状態が原因で、基になるメモリ オブジェクトにアクセスできなかったため、関数呼び出しを処理できませんでした。|  
|HY092|属性/オプション識別子が無効です|*ハンドルタイプ*はSQL_HANDLE_ENVまたはSQL_HANDLE_DESCに設定されました。|  
|HY117|不明なトランザクション状態のため、接続が中断されました。 切断と読み取り専用の機能のみが許可されます。|(DM) 中断状態の詳細については[、SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)を参照してください。|  
|ヒュットー1|接続のタイムアウトが期限切れになりました|データ ソースが要求に応答する前に、接続タイムアウト期間が切れました。 接続タイムアウト期間は **、SQL_ATTR_CONNECTION_TIMEOUT SQLSetConnectAttr**を使用して設定されます。|  
|IM001|ドライバはこの機能をサポートしていません|(DM)*ハンドル*に関連付けられているドライバーは、この機能をサポートしていません。|  
  
 *ハンドル型*をSQL_HANDLE_STMTに設定して**SQLCancelHandle**が呼び出された場合は、関数 SQLCancel によって返される可能性のある任意の**SQLSTATE を**返すことができます。  
  
## <a name="comments"></a>説明  
 この関数は**SQLCancel**に似ていますが、接続ハンドルまたはステートメント ハンドルを、ステートメント ハンドルだけでなくパラメータとして受け取る場合があります。 ドライバー マネージャーは、**呼**び出しをマップしますハンドル*型*がSQL_HANDLE_STMT場合は **、SQLキャンセル**への呼び出しにします。 これにより、アプリケーションは、ドライバーが**SQLCancelHandle**を実装していない場合でもステートメント操作をキャンセルする**SQLCancelHandle**を使用できます。  
  
 ステートメント操作の取り消しの詳細については[、SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)を参照してください。  
  
 処理中の操作がない場合は **、SQLCancelHandle**の呼び出しは無効です。 *Handle*  
  
 **接続ハンドルの SQLCancelHandle**は、次の種類の処理を取り消すことができます。  
  
-   接続で非同期に実行される関数。  
  
-   別のスレッドの接続ハンドルで実行されている関数。  
  
 接続で非同期に実行されている関数をキャンセルするために**SQLCancelHandle**が呼び出されると **、SQLCancelHandle**によってポストされた診断レコードは、取り消される操作によって返されるレコードに追加されます。ただし、別のスレッドで接続で実行されている関数をキャンセルする場合 **、SQLCancelHandle**は診断レコードを返しません。  
  
 **SQLEndTran**をキャンセルするために**SQL キャンセルハンドル**を使用すると、接続が中断状態になる可能性があります。 中断状態の詳細については[、SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)を参照してください。  
  
> [!NOTE]  
>  Windows 7 より古い Windows オペレーティング システムに展開されるアプリケーションで**SQLCancelHandle**を使用する方法については、「[互換性マトリックス](../../../odbc/reference/develop-app/compatibility-matrix.md)」を参照してください。  
  
#### <a name="canceling-connection-related-asynchronous-processing"></a>接続関連の非同期処理のキャンセル  
 関数がSQL_STILL_EXECUTINGを返す場合、アプリケーションは**SQLCancelHandle**を呼び出して操作をキャンセルできます。 キャンセル要求が成功した**場合は**、SQL_SUCCESSを返します。 これは、元の関数が取り消されたことを意味するものではありません。キャンセル要求が処理されたことを示します。 ドライバーとデータ ソースは、操作がキャンセルされたタイミングまたはかどうかを決定します。 戻りコードがSQL_STILL_EXECUTINGされないまで、アプリケーションは元の関数を呼び出し続ける必要があります。 元の関数が取り消された場合、戻りコードはSQL_ERRORされ、SQLSTATE HY008 (操作は取り消されました) になります。 元の関数が通常の処理を完了した場合 (取り消されなかった場合)、元の関数が失敗した場合、戻りコードはSQL_SUCCESSまたはSQL_SUCCESS_WITH_INFO、または SQL_ERROR HY008 以外の SQLSTATE (操作は取り消されました) です。  
  
#### <a name="canceling-functions-executing-on-another-thread"></a>別のスレッドで実行されている関数のキャンセル  
 マルチスレッド アプリケーションでは、アプリケーションは、別のスレッドで実行されている操作をキャンセルできます。 操作をキャンセルするには、アプリケーションは、関数によって使用されるハンドルを使用して**SQLCancelHandle**を呼び出しますが、別のスレッドで実行します。 ドライバーとオペレーティング システムは、操作をキャンセルする方法を決定します。 **SQLCancelHandle**戻りコードは、ドライバーが要求を処理したかどうかを示しますSQL_SUCCESSまたはSQL_ERROR (診断情報は返されません)。 元の関数の処理が取り消されると、元の関数はSQL_ERRORと SQLSTATE HY008 (操作が取り消されました) を返します。  
  
 関数を別のスレッドで**呼**び出して関数をキャンセルするときに関数が実行されている場合、その関数が成功し、キャンセルが有効になる前にSQL_SUCCESSを返すことができます。 **SQL キャンセルハンドル**の呼び出しは、操作が操作をキャンセル**する前に**完了した場合は無効です。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|ステートメント ハンドルで非同期に実行されている関数のキャンセル、データを必要とするステートメントの関数のキャンセル、または別のスレッド上のステートメントで実行されている関数のキャンセル。|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)   
 [非同期実行 (ポーリング メソッド)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)
