---
title: SQLAllocHandle 関数 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLAllocHandle
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLAllocHandle
helpviewer_keywords:
- SQLAllocHandle function [ODBC]
ms.assetid: 6e7fe420-8cf4-4e72-8dad-212affaff317
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3f4f82a24e594a25b0b1ec9bbeab2256624ae6e9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68036250"
---
# <a name="sqlallochandle-function"></a>SQLAllocHandle 関数
**準拠**  
 バージョンが導入されました。ODBC 3.0 規格に準拠します。ISO 92  
  
 **まとめ**  
 **SQLAllocHandle**環境、接続、ステートメント、または記述子ハンドルを割り当てます。  
  
> [!NOTE]  
>  この関数は、ODBC 2.0 関数を置換するハンドルを割り当てるための汎用関数**SQLAllocConnect**、 **SQLAllocEnv**、および**SQLAllocStmt**します。 呼び出すアプリケーションを許可する**SQLAllocHandle** ODBC 2 を使用する *。x*ドライバーへの呼び出し**SQLAllocHandle**をドライバー マネージャーではマップ**SQLAllocConnect**、 **SQLAllocEnv**、または**SQLAllocStmt**必要に応じて、します。 詳細については、「コメントです。」を参照してください。 詳細についてはどのようなドライバー マネージャーのときに、ODBC 3 には、この関数にマップします。*x* ODBC 2 を利用するアプリケーション *。x*ドライバーを参照してください[アプリケーションの旧バージョンと互換性のマッピング置換関数](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md)します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
SQLRETURN SQLAllocHandle(  
      SQLSMALLINT   HandleType,  
      SQLHANDLE     InputHandle,  
      SQLHANDLE *   OutputHandlePtr);  
```  
  
## <a name="arguments"></a>引数  
 *HandleType*  
 [入力]によって割り当てられるへのハンドルの種類**SQLAllocHandle**します。 値は次のいずれかを指定する必要があります。  
  
-   SQL_HANDLE_DBC として  
  
-   SQL_HANDLE_DBC_INFO_TOKEN  
  
-   SQL_HANDLE_DESC  
  
-   SQL_HANDLE_ENV として  
  
-   SQL_HANDLE_STMT として  
  
 SQL_HANDLE_DBC_INFO_TOKEN ハンドルは、ドライバー マネージャーとドライバーでのみ使用されます。 アプリケーションでは、この種類のハンドルは使用しないでください。 SQL_HANDLE_DBC_INFO_TOKEN の詳細については、次を参照してください。 [ODBC ドライバーで接続プールの認識を開発](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)します。  
  
 *InputHandle*  
 [入力]コンテキストを持つ新しいハンドルが割り当てられる入力のハンドルです。 場合*HandleType* sql_handle_env としてでは、これは、SQL_NULL_HANDLE します。 場合*HandleType* sql_handle_dbc としてにも、環境ハンドルがあります、sql_handle_stmt としてまたは SQL_HANDLE_DESC の場合は、接続ハンドルであること必要があります。  
  
 *OutputHandlePtr*  
 [出力]新しく割り当てられたデータ構造体へのハンドルを返すバッファーへのポインター。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_INVALID_HANDLE、または SQL_ERROR します。  
  
 場合に、環境ハンドル以外のハンドルを割り当てるときに**SQLAllocHandle** 、SQL_ERROR を返します設定*OutputHandlePtr* SQL_NULL_HDBC、SQL_NULL_HSTMT、またはに応じて SQL_NULL_HDESC、値*HandleType*出力引数が null ポインターでない限り、します。 アプリケーションでハンドルに関連付けられている診断データの構造から追加情報を取得できますし、 *InputHandle*引数。  
  
## <a name="environment-handle-allocation-errors"></a>環境ハンドルの割り当てエラー  
 環境の割り当てには、ドライバー マネージャー内で、各ドライバー内で両方が発生します。 によって返されるエラー **SQLAllocHandle**で、 *HandleType* sql_handle_env としてのエラーが発生したレベルに依存します。  
  
 場合は、ドライバー マネージャーのメモリを割り当てることができません *\*OutputHandlePtr*とき**SQLAllocHandle**で、 *HandleType* sql_handle_env としてが呼び出されると、またはアプリケーションの null ポインターを提供する*OutputHandlePtr*、 **SQLAllocHandle** SQL_ERROR を返します。 ドライバー マネージャーの設定 **OutputHandlePtr* SQL_NULL_HENV に (ない場合、アプリケーションには、null ポインターの SQL_ERROR を返しますが提供されます)。 ハンドルに関連付ける追加の診断情報はありません。  
  
 ドライバー マネージャーは、アプリケーションがドライバー レベルの環境ハンドルの割り当て関数を呼び出しません**SQLConnect**、 **SQLBrowseConnect**、または**SQLDriverConnect**. ドライバー レベルでエラーが発生した場合**SQLAllocHandle**関数では、そのドライバー マネージャー レベル**SQLConnect**、 **SQLBrowseConnect**、または**SQLDriverConnect**関数は SQL_ERROR を返します。 診断データの構造には、SQLSTATE IM004 が含まれています (ドライバーの**SQLAllocHandle**できませんでした)。 接続ハンドルでは、エラーが返されます。  
  
 ドライバー マネージャーとドライバーの間の関数呼び出しのフローの詳細については、次を参照してください。 [SQLConnect 関数](../../../odbc/reference/syntax/sqlconnect-function.md)します。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLAllocHandle** SQL_ERROR または SQL_SUCCESS_WITH_INFO、関連付けられている SQLSTATE 値を返しますを呼び出すことによって取得できる**SQLGetDiagRec**と適切な*HandleType*と*処理*の値に設定*InputHandle*します。 SQL_SUCCESS_WITH_INFO (ただし、SQL_ERROR されません) が返される、 *OutputHandle*引数。 次の表に、によって返される通常の SQLSTATE 値**SQLAllocHandle** ; この関数のコンテキストでそれぞれについて説明しますと表記"(DM)"の前にドライバー マネージャーによって返されるについての説明。 SQLSTATE 値ごとに関連付けられているリターン コードは明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|08003|接続は開いていません|(DM)、 *HandleType*引数が sql_handle_stmt としてまたは SQL_HANDLE_DESC がで指定された接続、 *InputHandle*引数が開かれていませんでした。 接続プロセスを正常に完了する必要があります (との接続を開く必要があります)、ドライバーを割り当てるステートメントまたは記述子ハンドルします。|  
|HY000|一般的なエラー|これがなかった固有の SQLSTATE とする実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、**MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリの割り当てエラー|(DM)、ドライバー マネージャーは、指定したハンドルのメモリを割り当てられませんでした。<br /><br /> ドライバーは、指定したハンドルのメモリを割り当てられませんでした。|  
|HY009|無効な null ポインターの使用|(DM)、 *OutputHandlePtr*引数が null ポインター。|  
|HY010|関数のシーケンス エラー|(DM)、 *HandleType*引数が sql_handle_dbc として、および**SQLSetEnvAttr** SQL_ODBC_VERSION 環境属性を設定するが呼び出されていません。<br /><br /> (DM) を非同期的に実行中の関数が呼び出された、 **InputHandle**ときに実行されていると、 **SQLAllocHandle**で関数が呼び出された**HandleType**設定sql_handle_stmt としてまたは SQL_HANDLE_DESC します。|  
|HY013|メモリ管理エラー|*HandleType*引数が sql_handle_dbc として、sql_handle_stmt として、または SQL_HANDLE_DESC; と基になるメモリ オブジェクトにアクセスできませんでした、場合によってメモリ不足が原因であるために、関数呼び出しを処理できませんでした条件。|  
|HY014|超過ハンドルの数を制限します。|によって示されるハンドルの型を割り当てることができるハンドルの数のドライバーの定義済みの制限、 *HandleType*引数に達しています。|  
|HY092|無効な属性またはオプション識別子|(DM)、 *HandleType*引数がありませんでした。Sql_handle_env として、sql_handle_dbc として、sql_handle_stmt として、または SQL_HANDLE_DESC します。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)します。|  
|HYC00|省略可能な機能が実装されていません|*HandleType*引数 SQL_HANDLE_DESC、ドライバーは ODBC 2 をでした *。x*ドライバー。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続のタイムアウト期間が終了しました。 によって、接続タイムアウト期間が設定されます**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT します。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM)、 *HandleType*引数を sql_handle_stmt として、ドライバーは有効な ODBC ドライバーでした。<br /><br /> (DM)、 *HandleType*引数が SQL_HANDLE_DESC、およびドライバーは記述子ハンドルの割り当てをサポートしていません。|  
  
## <a name="comments"></a>コメント  
 **SQLAllocHandle**ように、次のセクションで説明されている環境、接続、ステートメント、および、記述子のハンドルの割り当てを使用します。 ハンドルの詳細については、次を参照してください。[ハンドル](../../../odbc/reference/develop-app/handles.md)します。  
  
 1 つ以上の環境、接続、またはステートメントのハンドルは、複数の割り当てがドライバーによってサポートされている場合、時に、アプリケーションによって割り当てられることができます。 ODBC では、環境、接続、ステートメント、または任意の時点で割り当て可能な記述子ハンドルの数で定義された制限はありません。 ドライバーは、特定の種類は一度に割り当てることができるハンドルの数に制限をかける場合があります。詳細については、ドライバーのドキュメントを参照してください。  
  
 アプリケーションを呼び出す場合**SQLAllocHandle**で *\*OutputHandlePtr*環境、接続、ステートメント、または既に存在する記述子ハンドルに設定すると、ドライバーを上書き、関連付けられている情報、*処理*アプリケーションで接続プール (を参照してください「の割り当て、環境属性の接続プール」このセクションで後述) を使用しない限り、します。 ドライバー マネージャーを表示するチェックしないかどうか、*処理*に入力された *\*OutputHandlePtr* 、既に使用されても、その上書き前に、ハンドルの以前の内容を確認.  
  
> [!NOTE]  
>  呼び出す ODBC アプリケーション プログラミングを正しくないが**SQLAllocHandle**で定義されている同じアプリケーション変数に 2 回 *\*OutputHandlePtr*呼び出さず**SQLFreeHandle**に再割り当てする前に、ハンドルを解放します。 ODBC を上書きするようにハンドル可能性が一貫性のない動作やエラーの ODBC ドライバーの方にあります。  
  
 複数のスレッドをサポートするオペレーティング システムでアプリケーションは、異なるスレッドで同じ環境、接続、ステートメント、または記述子ハンドルを使用できます。 ドライバーはこの情報を安全なマルチ スレッド アクセスをサポートする必要したがってこれを実現する方法の 1 つは、クリティカル セクションまたはセマフォを使用しています。 スレッド処理の詳細については、次を参照してください。[マルチ スレッド](../../../odbc/reference/develop-app/multithreading.md)します。  
  
 **SQLAllocHandle** SQL_ATTR_ODBC_VERSION 環境属性が設定されていないアプリケーション、または SQLSTATE HY010 環境属性を設定する必要があります環境ハンドルを割り当てることで呼び出された場合になります (関数のシーケンス エラー)。ときに返される**SQLAllocHandle**接続ハンドルを割り当てるために呼び出されます。  
  
 標準に準拠したアプリケーションでは、 **SQLAllocHandle**にマップされて**SQLAllocHandleStd**コンパイル時にします。 これら 2 つの関数の違いは**SQLAllocHandleStd**を使用して呼び出したときに、SQL_ATTR_ODBC_VERSION 環境属性を SQL_OV_ODBC3 に設定、 *HandleType*引数が SQL に設定_HANDLE_ENV します。 これは標準に準拠したアプリケーションは、ODBC 3 では常にためです。*x*アプリケーション。 さらに、標準では、アプリケーションのバージョンを登録するのには必要ありません。 これは、これら 2 つの関数の唯一の違いそれ以外の場合と同じです。 **SQLAllocHandleStd**にマップされて**SQLAllocHandle**ドライバー マネージャーの内部。 そのため、サードパーティ製のドライバーは、実装する必要はない**SQLAllocHandleStd**します。  
  
 ODBC 3.8 にアプリケーションを使用する必要があります。  
  
-   **SQLAllocHandle といない SQLAllocHandleStd**環境ハンドルを割り当てられません。  
  
-   **SQLSetEnvAttr** SQL_OV_ODBC3_80 を SQL_ATTR_ODBC_VERSION 環境属性を設定します。  
  
## <a name="allocating-an-environment-handle"></a>環境ハンドルの割り当て  
 環境ハンドルは、有効な接続ハンドルとアクティブな接続ハンドルなどのグローバル情報へのアクセスを提供します。 環境ハンドルの詳細については、次を参照してください。[環境ハンドル](../../../odbc/reference/develop-app/environment-handles.md)します。  
  
 環境ハンドルを要求するアプリケーションを呼び出す**SQLAllocHandle**で、 *HandleType* sql_handle_env としての*InputHandle* SQL_NULL_HANDLE の。 ドライバーは、環境情報と関連付けられているハンドルの値で渡すメモリを割り当て、  *\*OutputHandlePtr*引数。 アプリケーション パス、  *\*OutputHandle*環境ハンドル引数を必要とするすべての後続の呼び出しで値。 詳細については、次を参照してください。[環境ハンドルの割り当て](../../../odbc/reference/develop-app/allocating-the-environment-handle.md)します。  
  
 ドライバー マネージャーの環境のハンドルが既に存在する場合、ドライバーの環境ハンドルをし、 **SQLAllocHandle**で、 *HandleType* sql_handle_env としては、ドライバーでは呼び出されませんがときに、のみの接続が行われる**SQLAllocHandle**で、 *HandleType* sql_handle_dbc としての。 HandleType の sql_handle_env としてと SQLAllocHandle と HandleType の sql_handle_dbc としてと SQLAllocHandle の両方が、ドライバーでと呼ばれる環境ハンドルのドライバー マネージャーの ドライバーの環境ハンドルが存在しない場合と、最初の接続環境のハンドルは、ドライバーに接続されます。  
  
 ドライバー マネージャーが処理するときに、 **SQLAllocHandle**関数と、 *HandleType*がチェックを sql_handle_env としての**トレース**システムの [ODBC] セクションではキーワード情報。 1 に設定されている場合、ドライバー マネージャーの現在のアプリケーション トレースを有効にします。 トレース フラグが設定されている場合、最初の環境ハンドルが割り当てられ、最後の環境ハンドルが解放されるときに終了時にトレースを開始します。 詳細については、次を参照してください。[データ ソースを構成する](../../../odbc/reference/install/configuring-data-sources.md)します。  
  
 環境ハンドルの割り当て後でアプリケーションを呼び出す必要があります**SQLSetEnvAttr** SQL_ATTR_ODBC_VERSION 環境属性を設定する環境ハンドル。 この属性は、前に設定されていない場合**SQLAllocHandle**接続ハンドルを割り当てるために呼び出される、環境で、接続の割り当てに呼び出しが、SQLSTATE HY010 を返す (関数のシーケンス エラーです)。 詳細については、次を参照してください。[アプリケーションの ODBC バージョンを宣言する](../../../odbc/reference/develop-app/declaring-the-application-s-odbc-version.md)します。  
  
## <a name="allocating-shared-environments-for-connection-pooling"></a>接続プールの共有環境の割り当て  
 環境は、1 つのプロセスで複数のコンポーネント間で共有できます。 共有環境は、同時に 1 つ以上のコンポーネントで使用できます。 コンポーネントは、共有環境を使用する場合は、プールされた接続では、割り当て、その接続を再作成しなくても、既存の接続を使用して、許可するようを使用できます。  
  
 アプリケーションを呼び出す必要があります、共有環境の割り当てを使用すると、接続プーリング用に、 **SQLSetEnvAttr** SQL_CP_ONE_PER_DRIVER または SQL_CP_ONE_PER_ SQL_ATTR_CONNECTION_POOLING 環境属性を設定するにはHENV します。 **SQLSetEnvAttr**ここで使用して呼び出した*EnvironmentHandle*属性は、プロセス レベルの属性が null に設定します。  
  
 アプリケーションを呼び出す接続プールが有効になったら、 **SQLAllocHandle**で、 *HandleType*を SQL_HANDLE_ENV 引数を設定します。 接続プールが有効になっているために、この呼び出しによって割り当てられた環境は暗黙の共有環境になります。  
  
 共有環境が割り当てられるときに使用される環境をまで決まりません**SQLAllocHandle**で、 *HandleType* sql_handle_dbc としてが呼び出されます。 その時点では、ドライバー マネージャーは、アプリケーションによって要求された環境属性に一致する既存の環境を見つけようとします。 このような環境が存在しない場合は、共有環境として 1 つ作成されます。 ドライバー マネージャーは、共有環境ごとに; の参照カウントを維持します。環境が最初に作成されたときに、カウントは 1 に設定します。 対応する環境が見つかった場合、その環境のハンドルは、アプリケーションに返され、参照カウントがインクリメントされます。 この方法で割り当てられている環境ハンドルは、入力引数として、環境ハンドルが受け取るすべての ODBC 関数で使用できます。  
  
## <a name="allocating-a-connection-handle"></a>接続ハンドルの割り当て  
 接続ハンドルが有効なステートメントなどの情報へのアクセスを提供し、接続およびトランザクションが現在の記述子ハンドルを開きます。 接続ハンドルの詳細については、次を参照してください。[接続ハンドル](../../../odbc/reference/develop-app/connection-handles.md)します。  
  
 接続ハンドルを要求するアプリケーションを呼び出す**SQLAllocHandle**で、 *HandleType* sql_handle_dbc としての。 *InputHandle*引数への呼び出しによって返された環境ハンドルを設定する**SQLAllocHandle**そのハンドルを割り当てることです。 ドライバーは、接続情報と関連付けられているハンドルの値で渡すのためのメモリを割り当てます *\*OutputHandlePtr*します。 アプリケーション パス、  *\*OutputHandlePtr*接続ハンドルを必要とするすべての後続の呼び出しで値。 詳細については、次を参照してください。[接続ハンドルの割り当て](../../../odbc/reference/develop-app/allocating-a-connection-handle-odbc.md)します。  
  
 ドライバー マネージャーの処理、 **SQLAllocHandle**関数を呼び出してドライバーの**SQLAllocHandle**アプリケーションを呼び出すときに関数**SQLConnect**、 **SQLBrowseConnect**、または**SQLDriverConnect**します。 (詳細については、次を参照してください[SQLConnect 関数](../../../odbc/reference/syntax/sqlconnect-function.md)。)。  
  
 前に、SQL_ATTR_ODBC_VERSION 環境属性が設定されていない場合**SQLAllocHandle**接続ハンドルを割り当てるために呼び出される、環境で、接続の割り当てへの呼び出しは SQLSTATE HY010 を返します (シーケンスの関数エラー)。  
  
 アプリケーションを呼び出すと**SQLAllocHandle**で、 *InputHandle*引数が sql_handle_dbc としてに設定され、共有環境ハンドルを設定しても、ドライバー マネージャーが、既存の共有を検索しようとしています。アプリケーションによって設定された環境属性に一致する環境です。 このような環境が存在しない場合 1 つと、作成されます (ドライバー マネージャーによって保持される) 1 の参照カウントします。 共有、一致する場合は、環境が見つかったし、そのハンドルは、アプリケーションに返される、参照カウントがインクリメントされます。  
  
 使用される実際の接続をドライバー マネージャーによってまでを判断できない**SQLConnect**または**SQLDriverConnect**が呼び出されます。 ドライバー マネージャーへの呼び出しで、接続オプションを使用して**SQLConnect** (またはへの呼び出しで接続キーワード**SQLDriverConnect**) への接続の割り当て後に、接続属性の設定プールの接続を使用する必要がありますを決定します。 詳細については、次を参照してください。 [SQLConnect 関数](../../../odbc/reference/syntax/sqlconnect-function.md)します。  
  
## <a name="allocating-a-statement-handle"></a>ステートメント ハンドルの割り当て  
 ステートメント ハンドルでは、SQL ステートメントの処理のエラー メッセージ、カーソル名、およびステータス情報などのステートメントの情報へのアクセスを提供します。 ステートメント ハンドルの詳細については、次を参照してください。[ステートメント ハンドル](../../../odbc/reference/develop-app/statement-handles.md)します。  
  
 ステートメント ハンドルを要求するアプリケーションがデータ ソースに接続しを呼び出して**SQLAllocHandle** SQL ステートメントを送信する前にします。 この呼び出しで*HandleType*を sql_handle_stmt として設定する必要がありますと*InputHandle*への呼び出しによって返された接続ハンドルに設定する必要があります**SQLAllocHandle**そのハンドルを割り当てることもできます。 ドライバーがステートメントについては、メモリを割り当て、指定した接続は、関連付けられているハンドルの値で渡すと、ステートメント ハンドルに関連付けます *\*OutputHandlePtr*します。 アプリケーション パス、  *\*OutputHandlePtr*ステートメント ハンドルを必要とするすべての後続の呼び出しで値。 詳細については、次を参照してください。[ステートメント ハンドルの割り当て](../../../odbc/reference/develop-app/allocating-a-statement-handle-odbc.md)します。  
  
 ドライバーは、ステートメント ハンドルが割り当てられるときに、自動的に一連の 4 つの記述子を割り当て、SQL_ATTR_APP_ROW_DESC、SQL_ATTR_APP_PARAM_DESC、SQL_ATTR_IMP_ROW_DESC、および SQL_ATTR_IMP_PARAM_DESC にこれらの記述子のハンドルを割り当てますステートメント属性。 呼ばれる、*暗黙的に*記述子を割り当てられます。 アプリケーション記述子を明示的に割り当てるには、次のセクションでは、「記述子ハンドルの割り当て」を参照してください。  
  
## <a name="allocating-a-descriptor-handle"></a>記述子ハンドルの割り当てください。  
 アプリケーションを呼び出すと**SQLAllocHandle**で、 *HandleType* SQL_HANDLE_DESC のドライバーがアプリケーション記述子を割り当てます。 呼ばれる、*明示的に*記述子を割り当てられます。 アプリケーションに指示を呼び出して、指定されたステートメント ハンドルのため、自動的に割り当てられたものではなく、明示的に割り当てられたアプリケーション記述子を使用するためのドライバー、 **SQLSetStmtAttr** SQL_ATTR_APP_ROW_DESC 関数または、SQL_ATTR_APP_PARAM_DESC 属性。 実装記述子を明示的に割り当てることができないも実装記述子で指定できます、 **SQLSetStmtAttr**関数呼び出し。  
  
 明示的に割り当てられた記述子は、(自動的に割り当てられた記述子の) と同様に、ステートメント ハンドルではなく、接続ハンドルに関連付けられます。 記述子は、アプリケーションが実際には、データベースに接続されている場合にのみに割り当てられたままです。 明示的に割り当てられた記述子は、接続ハンドルに関連付けられたであるために、アプリケーションは接続内で 1 つ以上のステートメントを使用して、明示的に割り当てられた記述子を関連付けることができます。 暗黙的に割り当てられたアプリケーション記述子では、その一方で、することはできません 1 つ以上のステートメント ハンドルに関連付けられました。 (できません以外に割り当てられているいずれかのステートメント ハンドルに関連付けられています。)明示的に割り当てられた記述子ハンドルを明示的に解放できる、アプリケーションまたは呼び出すことによって**SQLFreeHandle**で、 *HandleType* SQL_HANDLE_DESC、または暗黙的に接続される場合閉じられます。  
  
 明示的に割り当てられた記述子が解放されると、暗黙的に割り当てられた記述子は、ステートメントに関連付けられてもう一度です。 (そのステートメントの SQL_ATTR_APP_ROW_DESC または SQL_ATTR_APP_PARAM_DESC 属性は、暗黙的に割り当てられた記述子ハンドルにもう一度設定)。これは、接続を明示的に割り当てられた記述子に関連付けられていたすべてのステートメントに当てはまります。  
  
 記述子の詳細については、次を参照してください。[記述子](../../../odbc/reference/develop-app/descriptors.md)します。  
  
## <a name="code-example"></a>コード例  
 参照してください[サンプル ODBC プログラム](../../../odbc/reference/sample-odbc-program.md)、 [SQLBrowseConnect 関数](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)、 [SQLConnect 関数](../../../odbc/reference/syntax/sqlconnect-function.md)、および[SQLSetCursorName 関数](../../../odbc/reference/syntax/sqlsetcursorname-function.md)します。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|SQL ステートメントを実行します。|[SQLExecDirect 関数](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|準備された SQL ステートメントを実行します。|[SQLExecute 関数](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|環境、接続、ステートメント、または記述子ハンドルを解放します。|[SQLFreeHandle 関数](../../../odbc/reference/syntax/sqlfreehandle-function.md)|  
|実行するステートメントを準備します。|[SQLPrepare 関数](../../../odbc/reference/syntax/sqlprepare-function.md)|  
|接続属性の設定|[SQLSetConnectAttr 関数](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
|記述子フィールドの設定|[SQLSetDescField 関数](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
|環境属性を設定|[SQLSetEnvAttr 関数](../../../odbc/reference/syntax/sqlsetenvattr-function.md)|  
|ステートメント属性を設定|[SQLSetStmtAttr 関数](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
