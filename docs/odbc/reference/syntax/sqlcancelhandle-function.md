---
title: "SQLCancelHandle 関数 |Microsoft ドキュメント"
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
f1_keywords: SQLCancelHandle
helpviewer_keywords: SQLCancelHandle function [ODBC]
ms.assetid: 16049b5b-22a7-4640-9897-c25dd0f19d21
caps.latest.revision: "22"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3760400f23b558c27cd70a3ecd288171cbd56534
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="sqlcancelhandle-function"></a>SQLCancelHandle 関数
**準拠**  
 バージョンが導入されています。 ODBC 3.8  
  
 標準への準拠: なし  
  
 ほとんどの ODBC 3.8 (およびそれ以降) ドライバーがこの関数を実装することが必要です。 以外の場合、ドライバーへの呼び出し**SQLCancelHandle**接続での処理、*処理*パラメーターには、SQLSTATE の IM001、メッセージの SQL_ERROR が返される 'ドライバーでは、この関数はサポートされていません' の呼び出し**SQLCancelHandle**として処理するステートメントを使用して、*処理*パラメーターへの呼び出しにマップされます**SQLCancel**ドライバー マネージャーによって場合を処理できません。ドライバーを実装**SQLCancel**です。 アプリケーションで使用できます**SQLGetFunctions**ドライバーをサポートしているかどうかは**SQLCancelHandle**です。  
  
 **概要**  
 **SQLCancelHandle**接続やステートメントの処理をキャンセルします。 ドライバー マネージャーは、マップの呼び出し**SQLCancelHandle**への呼び出しに**SQLCancel**とき*HandleType* SQL_HANDLE_STMT がします。  
  
## <a name="syntax"></a>構文  
  
```  
  
SQLRETURN SQLCancelHandle(  
      SQLSMALLINT  HandleType,  
      SQLHANDLE    Handle);  
```  
  
## <a name="arguments"></a>引数  
 *HandleType*  
 [入力]Cacel 処理へのハンドルの型。 有効な値は sql_handle_dbc として SQL_HANDLE_STMT です。  
  
 *Handle*  
 [入力]処理をキャンセルするハンドル。  
  
 場合*処理*で指定された型の有効なハンドルではありません*HandleType*、 **SQLCancelHandle** SQL_INVALID_HANDLE が返されます。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、または SQL_INVALID_HANDLE です。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLCancelHandle** SQL_ERROR または SQL_SUCCESS_WITH_INFO、関連付けられた SQLSTATE 値を返しますを呼び出すことによって取得できます**SQLGetDiagRec**で、 *HandleType*のSQL_HANDLE_STMT と、ステートメントを処理する*処理*または*HandleType* sql_handle_dbc としてと接続ハンドルの*処理*です。  
  
 次の表に、一般的にによって返される SQLSTATE 値**SQLCancelHandle**とコンテキストでこの関数のいずれかを説明します。 表記"(DM)"の前に、ドライバー マネージャーによって返される SQLSTATEs の説明。 SQLSTATE 値ごとに関連付けられている戻り値のコードは、特に明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|Description|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|HY000|一般的なエラー|存在しなかった固有の SQLSTATE となる実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ[SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)引数で *\*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリ割り当てエラー|ドライバーは、実行や、関数の終了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY010|関数のシーケンス エラー|関連付けられているステートメント ハンドルのいずれかの非同期的に実行しているステートメント関連の関数が呼び出されました、*処理*、および*HandleType* sql_handle_dbc としてに設定されました。 非同期関数が実行時にまだ**SQLCancelHandle**が呼び出されました。<br /><br /> (DM)、 *HandleType*引数 SQL_HANDLE_STMT 以外の場合は、関連付けられている接続ハンドルで非同期的に実行中の関数が呼び出されましたれ、この関数が呼び出されたとき、関数が実行されています。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、または**SQLMoreResults**に関連付けられているステートメント ハンドルのいずれかで呼び出され、*処理*および*HandleType*が sql_handle_dbc としてに設定され、SQL_PARAM_DATA_AVAILABLE が返されます。 ストリーミングのすべてのパラメーターのデータが取得される前に、この関数が呼び出されました。<br /><br /> **SQLBrowseConnect**に対して呼び出されました*ConnectionHandle*SQL_NEED_DATA が返されます。 この関数は、参照の処理を完了する前に呼び出されました。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、可能性のあるメモリ不足の状況が原因であるために、関数呼び出しを処理できませんでした。|  
|HY092|無効な属性またはオプション識別子|*HandleType* SQL_HANDLE_ENV または SQL_HANDLE_DESC に変更されました。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)です。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続タイムアウト期間が期限切れです。 によって、接続タイムアウト期間が設定されている**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT です。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に、ドライバーが関連付けられている、*処理*関数をサポートしていません。|  
  
 場合**SQLCancelHandle**で呼び出された*HandleType* SQL_HANDLE_STMT を設定、関数によって返される任意の SQLSTATE を返すこと**SQLCancel**です。  
  
## <a name="comments"></a>コメント  
 この関数がに似ていますが**SQLCancel**ステートメント ハンドルのみではなく、パラメーターとして接続またはステートメントのいずれかのハンドルがかかる場合があります。 ドライバー マネージャーは、マップの呼び出し**SQLCancelHandle**への呼び出しに**SQLCancel**とき*HandleType* SQL_HANDLE_STMT がします。 これにより、アプリケーションを使用する**SQLCancelHandle**ドライバーが実装していない場合でも、ステートメントの操作をキャンセルする**SQLCancelHandle**です。  
  
 詳細については、ステートメントの操作を取り消すと、次を参照してください。 [SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)です。  
  
 進行中の操作がない場合*処理*への呼び出し**SQLCancelHandle**も何も起こりません。  
  
 **SQLCancelHandle**接続では、ハンドルが次の種類の処理を取り消すことができます。  
  
-   接続で非同期的に実行されている関数です。  
  
-   別のスレッドで、接続ハンドルで実行されている関数です。  
  
 ときに**SQLCancelHandle**接続によって送信された診断レコードで非同期的に実行されている関数を取り消すために呼び出される**SQLCancelHandle**は操作の中で返されるものに追加されます取り消されました。**SQLCancelHandle**返さない診断レコードは、ただし、別のスレッド上の接続で実行されている関数を取り消すときです。  
  
 使用して**SQLCancelHandle**をキャンセルする**SQLEndTran**中断状態の接続を格納する可能性もあります。 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)です。  
  
> [!NOTE]  
>  使用する方法については**SQLCancelHandle** Windows 7 よりも古い Windows オペレーティング システム上に配置されるアプリケーションで、次を参照してください。[の互換性対応表](../../../odbc/reference/develop-app/compatibility-matrix.md)です。  
  
#### <a name="canceling-connection-related-asynchronous-processing"></a>接続に関連する非同期処理を取り消す  
 アプリケーションが呼び出すことができる場合は、関数が返す SQL_STILL_EXECUTING、 **SQLCancelHandle**操作をキャンセルします。 取り消し要求が成功すると場合、 **SQLCancelHandle** SQL_SUCCESS を返します。 元の関数がキャンセルされたことはありません。これは、キャンセル要求が処理されたことを示します。 ドライバーとデータ ソース、または操作が取り消された場合を決定します。 リターン コードが SQL_STILL_EXECUTING されるまで、元の関数を呼び出すアプリケーションを続行する必要があります。 元の関数が取り消された場合、リターン コード、SQL_ERROR SQLSTATE HY008 (操作が取り消されました)。 元の関数には、通常の処理が完了した場合 (キャンセルされていない)、リターン コードは SQL_SUCCESS や、SQL_SUCCESS_WITH_INFO または SQL_ERROR HY008 以外 SQLSTATE (操作がキャンセルされました)、元の関数が失敗した場合。  
  
#### <a name="canceling-functions-executing-on-another-thread"></a>別のスレッドで実行されている関数のキャンセル  
 マルチ スレッド アプリケーションで、アプリケーションは、別のスレッドで実行されている操作を取り消すことができます。 アプリケーションの呼び出し、操作をキャンセルする**SQLCancelHandle**関数では、別のスレッドで使用される、ハンドルを使用します。 ドライバーおよびオペレーティング システムは、操作が取り消される方法を決定します。 **SQLCancelHandle**返すコードでは、ドライバーが SQL_SUCCESS や SQL_ERROR (診断情報は返されません) のいずれかを返す要求を処理するかどうかを示します。 SQL_ERROR と SQLSTATE HY008 場合は、元の関数での処理が取り消されると、元の関数が返されます (操作は取り消されました)。  
  
 関数の中の場合実行すると実行**SQLCancelHandle**が呼び出された関数をキャンセルする別のスレッドで可能であれば、関数の場合に成功し、[キャンセル] を有効にするに関係なく SQL_SUCCESS を返します。 呼び出し**SQLCancelHandle**場合は、操作を完了する前に影響を与えません**SQLCancelHandle**操作を取り消すことができます。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|データを必要があるステートメントの関数を取り消すか、別のスレッドでステートメントで実行されている関数のキャンセル、ステートメント ハンドルで非同期的に実行されている関数は取り消されます。|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)   
 [非同期実行 (ポーリング メソッド)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)
