---
title: SQLAllocHandle 関数 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 43
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 9a864d1fd8255983ebd0a7d58661ca6afc1bf6b9
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sqlallochandle-function"></a>SQLAllocHandle 関数
**準拠**  
 バージョンで導入されました ODBC 3.0 Standards 準拠: ISO 92。  
  
 **概要**  
 **SQLAllocHandle**環境、接続、ステートメント、または記述子ハンドルを割り当てます。  
  
> [!NOTE]  
>  この関数は、ODBC 2.0 関数を置換するハンドルを割り当てるための汎用関数**SQLAllocConnect**、 **SQLAllocEnv**、および**SQLAllocStmt**です。 呼び出すアプリケーションを許可する**SQLAllocHandle** ODBC 2 を使用する*。x*ドライバーへの呼び出し**SQLAllocHandle**をドライバー マネージャーではマップ**SQLAllocConnect**、 **SQLAllocEnv**、または**SQLAllocStmt** をクリックします。 詳細については、「コメント」を参照してください。 どのようなドライバー マネージャーの詳細と ODBC 3 には、この関数にマップします。*x* ODBC 2 を利用するアプリケーション*。x*ドライバーを参照してください[アプリケーションの旧バージョンと互換性を保つのための置換関数のマッピング](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
SQLRETURN SQLAllocHandle(  
      SQLSMALLINT   HandleType,  
      SQLHANDLE     InputHandle,  
      SQLHANDLE *   OutputHandlePtr);  
```  
  
## <a name="arguments"></a>引数  
 *HandleType*  
 [入力]によって割り当てられるへのハンドルの種類**SQLAllocHandle**です。 次の値のいずれかを指定する必要があります。  
  
-   SQL_HANDLE_DBC として  
  
-   SQL_HANDLE_DBC_INFO_TOKEN  
  
-   SQL_HANDLE_DESC  
  
-   SQL_HANDLE_ENV  
  
-   SQL_HANDLE_STMT  
  
 SQL_HANDLE_DBC_INFO_TOKEN ハンドルは、ドライバー マネージャーとドライバーのによってのみ使用されます。 アプリケーションでは、この種類のハンドルは使用しないでください。 SQL_HANDLE_DBC_INFO_TOKEN の詳細については、次を参照してください。 [ODBC ドライバーで接続プールの認識開発](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)です。  
  
 *InputHandle*  
 [入力]コンテキストを持つ新しいハンドルは、割り当てられる入力のハンドルです。 場合*HandleType* sql_handle_env としてでは、これは、SQL_NULL_HANDLE です。 場合*HandleType* sql_handle_dbc として、環境ハンドルをあるこの必要があります、SQL_HANDLE_STMT または SQL_HANDLE_DESC の場合は、接続ハンドルがある必要があります。  
  
 *OutputHandlePtr*  
 [出力]新しく割り当てられたデータ構造体へのハンドルを返すバッファーへのポインター。  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_INVALID_HANDLE、または SQL_ERROR です。  
  
 場合に、環境ハンドル以外のハンドルを割り当てるときに**SQLAllocHandle** 、SQL_ERROR が返されます設定*OutputHandlePtr* SQL_NULL_HDBC、SQL_NULL_HSTMT、または SQL_NULL_HDESC、に応じて、値*HandleType*出力引数が null ポインターでない限り、します。 アプリケーション内のハンドルに関連付けられている診断データの構造から追加情報を取得できますし、 *InputHandle*引数。  
  
## <a name="environment-handle-allocation-errors"></a>環境ハンドルの割り当てエラー  
 環境の割り当てには、ドライバー マネージャー内でと各ドライバーの両方が行われます。 によって返されるエラー **SQLAllocHandle**で、 *HandleType* sql_handle_env としてのレベルによって異なりますエラーが発生しました。  
  
 場合は、ドライバー マネージャーがメモリを割り当てることはできません *\*OutputHandlePtr*とき**SQLAllocHandle**で、 *HandleType* SQL_HANDLE_ENV が呼び出されると、またはアプリケーションの null ポインターを提供する*OutputHandlePtr*、 **SQLAllocHandle** SQL_ERROR を返します。 ドライバー マネージャーの設定 **OutputHandlePtr* SQL_NULL_HENV を (場合を除く、アプリケーションには、SQL_ERROR が返されます、null ポインターが提供されます)。 追加の診断情報を関連付けられるハンドルはありません。  
  
 ドライバー マネージャーが、アプリケーションがドライバー レベルの環境ハンドルの割り当て関数を呼び出しません**SQLConnect**、 **SQLBrowseConnect**、または**SQLDriverConnect**. ドライバー レベルでエラーが発生した場合**SQLAllocHandle**関数、そのドライバー マネージャー – レベル**SQLConnect**、 **SQLBrowseConnect**、または**SQLDriverConnect** SQL_ERROR を返します。 診断データの構造を含む SQLSTATE IM004 (ドライバーの**SQLAllocHandle**に失敗しました)。 接続ハンドルでは、エラーが返されます。  
  
 ドライバー マネージャーとドライバーの間での関数呼び出しのフローの詳細については、次を参照してください。 [SQLConnect 関数](../../../odbc/reference/syntax/sqlconnect-function.md)です。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLAllocHandle** SQL_ERROR または SQL_SUCCESS_WITH_INFO、関連付けられた SQLSTATE 値を返しますを呼び出すことによって取得できます**SQLGetDiagRec**と適切な*HandleType*と*処理*の値に設定*InputHandle*です。 SQL_SUCCESS_WITH_INFO (ただし、SQL_ERROR されません) が返される、 *OutputHandle*引数。 次の表に、によって通常返される SQLSTATE 値**SQLAllocHandle**です。 この関数のコンテキストでは、各フォルダーについて説明しますと表記"(DM)"の前に、ドライバー マネージャーによって返される SQLSTATEs の説明。 SQLSTATE 値ごとに関連付けられている戻り値のコードは、特に明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|Description|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|08003|接続は開いていません|(DM)、 *HandleType*引数 SQL_HANDLE_STMT または SQL_HANDLE_DESC がで指定された接続、 *InputHandle*引数が開かれていたされません。 接続処理が正常に完了する必要があります (および、接続が開いている必要があります)、ドライバーを割り当てるステートメントまたは記述子ハンドルします。|  
|HY000|一般的なエラー|存在しなかった固有の SQLSTATE となる実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、**MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリ割り当てエラー|ドライバー マネージャーは、(DM) は、指定したハンドルのメモリを割り当てることができませんでした。<br /><br /> ドライバーは、指定したハンドルのメモリを割り当てることができませんでした。|  
|HY009|無効な null ポインターの使用|(DM)、 *OutputHandlePtr*引数が null ポインターでした。|  
|HY010|関数のシーケンス エラー|(DM)、 *HandleType*引数が sql_handle_dbc として、および**SQLSetEnvAttr** SQL_ODBC_VERSION 環境属性を設定するが呼び出されていません。<br /><br /> (DM) の非同期的に実行中の関数が呼び出された、 **InputHandle**ときに実行されていると、 **SQLAllocHandle**で関数が呼び出された**HandleType**設定sql_handle_stmt としてまたは SQL_HANDLE_DESC です。|  
|HY013|メモリ管理エラー|*HandleType*引数 sql_handle_dbc として、sql_handle_stmt として、または SQL_HANDLE_DESC; れ、基になるメモリ オブジェクトにアクセスできませんでした、可能性のあるメモリ不足が原因であるために、関数呼び出しを処理できませんでした条件。|  
|HY014|ハンドルを超えた数を制限します。|によって示されるハンドルの型を割り当てることができるハンドルの数のドライバーで定義された制限、 *HandleType*引数に達しています。|  
|HY092|無効な属性またはオプション識別子|(DM)、 *HandleType*引数がありませんでした: SQL_HANDLE_ENV、sql_handle_dbc として、sql_handle_stmt として、または SQL_HANDLE_DESC です。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)です。|  
|HYC00|省略可能な機能が実装されていません|*HandleType*引数 SQL_HANDLE_DESC、ドライバーは ODBC 2 をでした*。x*ドライバー。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続タイムアウト期間が期限切れです。 によって、接続タイムアウト期間が設定されている**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT です。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM)、 *HandleType*引数 SQL_HANDLE_STMT、れ、ドライバーは無効な ODBC ドライバー、でした。<br /><br /> (DM)、 *HandleType*引数 SQL_HANDLE_DESC、れ、ドライバーが記述子ハンドルの割り当てをサポートしていません。|  
  
## <a name="comments"></a>コメント  
 **SQLAllocHandle**次のセクションで説明するよう環境、接続、ステートメント、および記述子ハンドルの割り当てに使用されます。 ハンドルに関する概要については、次を参照してください。[ハンドル](../../../odbc/reference/develop-app/handles.md)です。  
  
 複数の割り当てがドライバーによってサポートされている場合、一度にアプリケーションによって 1 つ以上の環境、接続、またはステートメントのハンドルを割り当てることができます。 ODBC では、環境、接続、ステートメント、または任意の時点で割り当て可能な記述子ハンドルの数に制限は定義されません。 ドライバーは、特定の種類は一度に割り当てることができるハンドルの数に制限をかける場合があります。詳細については、ドライバーのマニュアルを参照してください。  
  
 アプリケーションを呼び出す場合**SQLAllocHandle**で *\*OutputHandlePtr*環境、接続、ステートメント、または既に存在する記述子ハンドルに設定すると、ドライバーを上書きします関連付けられている情報、*処理*アプリケーションが接続プール (を参照してください「の割り当て、環境属性を接続プール」このセクションで後述) を使用している場合を除き、します。 ドライバー マネージャーを表示するチェックしないかどうか、*処理*に入力された *\*OutputHandlePtr* 、既に使用されても、そのハンドルの以前の内容を上書きする前に確認.  
  
> [!NOTE]  
>  呼び出す ODBC アプリケーション プログラミングを不適切なである**SQLAllocHandle**に対して定義されている同じアプリケーション変数で 2 回 *\*OutputHandlePtr*呼び出さず**SQLFreeHandle**にそれを再割り当てする前に、ハンドルを解放します。 ODBC を上書きするようにハンドルを一貫性のない動作または ODBC ドライバーによるエラー可能性があります。  
  
 複数のスレッドをサポートするオペレーティング システムでアプリケーションは、異なるスレッドで同じ環境、接続、ステートメント、または記述子ハンドルを使用できます。 ドライバー必要があります。 この情報を安全なマルチ スレッドへのアクセスをサポートしてしたがってこれを実現する 1 つの方法は、クリティカル セクションまたはセマフォを使用しています。 スレッド処理の詳細については、次を参照してください。[マルチ スレッド](../../../odbc/reference/develop-app/multithreading.md)です。  
  
 **SQLAllocHandle**また環境属性が設定されていないアプリケーション、または含む SQLSTATE HY010 が環境属性を設定する必要があります、環境ハンドルを割り当てることで呼び出された場合 (関数のシーケンス エラー) になりますときに返される**SQLAllocHandle**接続ハンドルを割り当てるために呼び出されます。  
  
 標準に準拠したアプリケーションは、 **SQLAllocHandle**にマップされて**SQLAllocHandleStd**コンパイル時にします。 これら 2 つの関数の違いを**SQLAllocHandleStd**で呼び出されたときに、また環境属性を SQL_OV_ODBC3 に設定、 *HandleType*引数が SQL に設定_HANDLE_ENV です。 これは標準に準拠したアプリケーションは、ODBC 3 では常にあるためです。*x*アプリケーションです。 さらに、標準には、登録するアプリケーションのバージョンは不要です。 これは、これら 2 つの関数の唯一の違いそれ以外の場合、それらが同じです。 **SQLAllocHandleStd**にマップされて**SQLAllocHandle**ドライバー マネージャーの内部です。 そのため、サード パーティ製のドライバーは、実装する必要はありません**SQLAllocHandleStd**です。  
  
 ODBC 3.8 アプリケーションを使用する必要があります。  
  
-   **SQLAllocHandle といない SQLAllocHandleStd**環境ハンドルを割り当てられません。  
  
-   **SQLSetEnvAttr** SQL_OV_ODBC3_80 にまた環境属性を設定します。  
  
## <a name="allocating-an-environment-handle"></a>環境ハンドルの割り当て  
 環境ハンドルは、有効な接続ハンドルとアクティブな接続ハンドルなどのグローバル情報へのアクセスを提供します。 環境ハンドルに関する概要については、次を参照してください。[環境ハンドル](../../../odbc/reference/develop-app/environment-handles.md)です。  
  
 環境ハンドルを要求するアプリケーションを呼び出す**SQLAllocHandle**で、 *HandleType* sql_handle_env としての*InputHandle* SQL_NULL_HANDLE のです。 ドライバーは、環境情報と関連付けられたハンドルの値で渡すメモリを割り当て、  *\*OutputHandlePtr*引数。 アプリケーション パス、  *\*OutputHandle*環境ハンドル引数を必要とするすべての後続の呼び出しで値。 詳細については、次を参照してください。[環境ハンドルの割り当て](../../../odbc/reference/develop-app/allocating-the-environment-handle.md)です。  
  
 既に存在する場合、ドライバーの環境ハンドルし、ドライバー マネージャーの環境ハンドル  **SQLAllocHandle**で、 *HandleType* SQL_HANDLE_ENV は、ドライバーでは呼び出されませんがときに、接続が確立のみ**SQLAllocHandle**で、 *HandleType* sql_handle_dbc としてのです。 ドライバー マネージャーの環境ハンドル ドライバーの環境ハンドルが存在しない場合 HandleType の SQL_HANDLE_ENV に SQLAllocHandle と HandleType の sql_handle_dbc としてと SQLAllocHandle の両方が、ドライバーで呼び出されます場合、最初の接続環境のハンドルは、ドライバーに接続されます。  
  
 ドライバー マネージャーの処理時、 **SQLAllocHandle**で機能、 *HandleType* SQL_HANDLE_ENV のチェック、**トレース**システムの [ODBC] セクションでキーワード情報です。 1 に設定されている場合、ドライバー マネージャーの現在のアプリケーションのトレースを有効にします。 トレース フラグが設定されている場合、最初の環境ハンドルが割り当てられているし、最後の環境ハンドルが解放されると終了時にトレースを開始します。 詳細については、次を参照してください。[データ ソースを構成する](../../../odbc/reference/install/configuring-data-sources.md)です。  
  
 環境ハンドルの割り当て後でアプリケーションを呼び出す必要があります**SQLSetEnvAttr**また環境属性を設定する環境のハンドル。 この属性は、前に設定されていない場合**SQLAllocHandle**接続ハンドルを割り当てるために呼び出される環境で、接続の割り当てへの呼び出しは、SQLSTATE HY010 を返します (関数のシーケンス エラー)。 詳細については、次を参照してください。[アプリケーションの ODBC バージョンを宣言する](../../../odbc/reference/develop-app/declaring-the-application-s-odbc-version.md)です。  
  
## <a name="allocating-shared-environments-for-connection-pooling"></a>接続プールの共有環境の割り当て  
 環境は、1 つのプロセスで複数のコンポーネント間で共有することができます。 共有環境は、同時に複数のコンポーネントで使用できます。 コンポーネントは、共有環境を使用する場合、割り当てられ、その接続を再作成しなくても、既存の接続を使用することを許可されているプールされた接続を使用できます。  
  
 接続プールの共有環境の割り当てを使用することができます、前に、アプリケーションを呼び出す必要があります**SQLSetEnvAttr** SQL_CP_ONE_PER_DRIVER または SQL_CP_ONE_PER_ SQL_ATTR_CONNECTION_POOLING 環境属性を設定するにはHENV です。 **SQLSetEnvAttr**でこのケースで呼び出された*EnvironmentHandle*プロセス レベルの属性の属性を null に設定します。  
  
 接続プールが有効になって、アプリケーションは呼び出し**SQLAllocHandle**で、 *HandleType*引数 SQL_HANDLE_ENV に設定します。 この呼び出しによって割り当てられている環境には接続プールを有効になっているために、暗黙的な共有環境になります。  
  
 共有環境が割り当てられている場合、使用される環境は、までが決定されない**SQLAllocHandle**で、 *HandleType* sql_handle_dbc としてのと呼びます。 その時点では、ドライバー マネージャーは、アプリケーションによって要求された環境属性に一致する既存の環境を見つけようとします。 このような環境が存在しない場合は、共有環境として 1 つ作成されます。 ドライバー マネージャーは、参照カウントの各共有環境です。環境が最初に作成したときに、カウントが 1 に設定されます。 対応する環境が見つかった場合、その環境のハンドルは、アプリケーションに返され、参照カウントがインクリメントされます。 この方法で割り当てられている環境ハンドルは、入力引数として、環境ハンドルを受け入れるすべての ODBC 関数で使用できます。  
  
## <a name="allocating-a-connection-handle"></a>接続ハンドルの割り当て  
 接続ハンドルが有効なステートメントなどの情報へのアクセスを提供し、接続しているかどうか、トランザクションは、現在の記述子ハンドルを開きます。 接続ハンドルの詳細については、次を参照してください。[接続ハンドル](../../../odbc/reference/develop-app/connection-handles.md)です。  
  
 アプリケーションを呼び出すために、接続ハンドルを要求する**SQLAllocHandle**で、 *HandleType* sql_handle_dbc としてのです。 *InputHandle*引数への呼び出しによって返された環境ハンドルに設定されて**SQLAllocHandle**そのハンドルを割り当てられています。 ドライバーは、接続情報と関連付けられたハンドルの値で渡す用メモリを割り当てます *\*OutputHandlePtr*です。 アプリケーション パス、  *\*OutputHandlePtr*接続ハンドルを必要とするすべての後続の呼び出しで値。 詳細については、次を参照してください。[接続ハンドルの割り当て](../../../odbc/reference/develop-app/allocating-a-connection-handle-odbc.md)です。  
  
 ドライバー マネージャーの処理、 **SQLAllocHandle**関数を呼び出してドライバーの**SQLAllocHandle**アプリケーションを呼び出すときに機能**SQLConnect**、 **SQLBrowseConnect**、または**SQLDriverConnect**です。 (詳細については、次を参照してください[SQLConnect 関数](../../../odbc/reference/syntax/sqlconnect-function.md)。)。  
  
 前に、また環境属性が設定されていない場合**SQLAllocHandle**接続ハンドルを割り当てるために呼び出される環境で、接続の割り当てへの呼び出しは、SQLSTATE HY010 を返します (関数のシーケンスエラー)。  
  
 アプリケーションを呼び出すと**SQLAllocHandle**で、 *InputHandle*引数が sql_handle_dbc としてに設定され共有環境ハンドルを設定しても、ドライバー マネージャーが、既存の共有を検索しようとしています。アプリケーションによって設定される環境属性と一致する環境です。 このような環境が存在しない場合、いずれかが作成され、1 の参照カウント (ドライバー マネージャーによって維持されます)。 共有、一致する場合は、環境が検出され、そのハンドルは、アプリケーションに返される、参照カウントがインクリメントされます。  
  
 使用される実際の接続がまでドライバー マネージャーによって決定されない**SQLConnect**または**SQLDriverConnect**と呼びます。 ドライバー マネージャーへの呼び出しで、接続オプションを使用して**SQLConnect** (またはへの呼び出しで接続キーワード**SQLDriverConnect**)、接続属性を設定する接続の割り当て後に、プール内のどの接続を使用する必要がありますを決定します。 詳細については、次を参照してください。 [SQLConnect 関数](../../../odbc/reference/syntax/sqlconnect-function.md)です。  
  
## <a name="allocating-a-statement-handle"></a>ステートメント ハンドルの割り当てください。  
 ステートメント ハンドルでは、SQL ステートメントの処理のエラー メッセージ、カーソル名、およびステータス情報などのステートメントの情報へのアクセスを提供します。 ステートメント ハンドルの詳細については、次を参照してください。[ステートメント ハンドル](../../../odbc/reference/develop-app/statement-handles.md)です。  
  
 ステートメント ハンドルを要求するアプリケーションがデータ ソースに接続しを呼び出して**SQLAllocHandle** SQL ステートメントを送信する前にします。 この呼び出しで*HandleType* SQL_HANDLE_STMT を設定する必要がありますと*InputHandle*への呼び出しによって返された接続ハンドルに設定する必要があります**SQLAllocHandle**そのハンドルが割り当てられます。 ドライバーがステートメントについては、メモリを割り当て、指定された接続は、関連付けられたハンドルの値で渡すと、ステートメント ハンドルに関連付けます *\*OutputHandlePtr*です。 アプリケーション パス、  *\*OutputHandlePtr*ステートメント ハンドルを必要とするすべての後続の呼び出しで値。 詳細については、次を参照してください。[ステートメント ハンドルの割り当て](../../../odbc/reference/develop-app/allocating-a-statement-handle-odbc.md)です。  
  
 ドライバーは、ステートメント ハンドルを割り当てるときに、自動的に 4 つの記述子の設定を割り当て、SQL_ATTR_APP_ROW_DESC、SQL_ATTR_APP_PARAM_DESC、SQL_ATTR_IMP_ROW_DESC、および SQL_ATTR_IMP_PARAM_DESC にこれらの記述子のハンドルを割り当てますステートメント属性。 呼ばれる、*暗黙的に*記述子が割り当てられます。 アプリケーションの記述子を明示的に割り当てるには、「記述子ハンドルを割り当ててください。」次のセクションを参照してください。  
  
## <a name="allocating-a-descriptor-handle"></a>記述子ハンドルの割り当てください。  
 アプリケーションを呼び出すと**SQLAllocHandle**で、 *HandleType* SQL_HANDLE_DESC のドライバーが、アプリケーションの記述子を割り当てます。 呼ばれる、*明示的に*記述子が割り当てられます。 アプリケーションに指示を呼び出すことによってではなく、自動的に割り当てられた特定のステートメント ハンドルの明示的に割り当てられているアプリケーション記述子を使用するドライバー、 **SQLSetStmtAttr** SQL_ATTR_APP_ROW_DESC を持つ関数または SQL_ATTR_APP_PARAM_DESC 属性。 実装記述子を明示的に割り当てることができないも実装記述子で指定できる、 **SQLSetStmtAttr**関数呼び出しです。  
  
 ように自動的に割り当てられた記述子) は、明示的に割り当てられた記述子をステートメント ハンドルではなく、接続ハンドルに関連付けられます。 記述子は、アプリケーションが実際には、データベースに接続されている場合にのみに割り当てられたままです。 明示的に割り当てられた記述子が接続ハンドルに関連付けられているため、アプリケーションは、接続内で 1 つ以上のステートメントで明示的に割り当てられた記述子を関連付けることができます。 暗黙的に割り当てられているアプリケーション記述子では、その一方で、することはできません 1 つ以上のステートメント ハンドルに関連付けられました。 (できません以外が割り当てられたのいずれかのステートメント ハンドルに関連付けられたです。)明示的に割り当てられた記述子ハンドルを明示的に解放できるアプリケーションで、または呼び出すことによって**SQLFreeHandle**で、 *HandleType* SQL_HANDLE_DESC、または暗黙的に接続される場合閉じられます。  
  
 明示的に割り当てられた記述子が解放されると、暗黙的に割り当てられた記述子は、ステートメントに関連付けられてもう一度です。 (そのステートメントに対して SQL_ATTR_APP_ROW_DESC または SQL_ATTR_APP_PARAM_DESC 属性は、暗黙的に割り当てられた記述子ハンドルにもう一度設定)。これは、接続で明示的に割り当てられた記述子に関連付けられていたすべてのステートメントの場合は true です。  
  
 記述子の詳細については、次を参照してください。[記述子](../../../odbc/reference/develop-app/descriptors.md)です。  
  
## <a name="code-example"></a>コード例  
 参照してください[ODBC プログラムのサンプル](../../../odbc/reference/sample-odbc-program.md)、 [SQLBrowseConnect 関数](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)、 [SQLConnect 関数](../../../odbc/reference/syntax/sqlconnect-function.md)、および[SQLSetCursorName 関数](../../../odbc/reference/syntax/sqlsetcursorname-function.md)です。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|SQL ステートメントを実行します。|[SQLExecDirect 関数](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|準備された SQL ステートメントを実行します。|[SQLExecute 関数](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|環境、接続、ステートメント、または記述子ハンドルの解放|[SQLFreeHandle 関数](../../../odbc/reference/syntax/sqlfreehandle-function.md)|  
|実行のためのステートメントを準備します。|[SQLPrepare 関数](../../../odbc/reference/syntax/sqlprepare-function.md)|  
|接続属性の設定|[SQLSetConnectAttr 関数](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
|記述子フィールドの設定|[SQLSetDescField 関数](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
|環境属性を設定|[SQLSetEnvAttr 関数](../../../odbc/reference/syntax/sqlsetenvattr-function.md)|  
|ステートメント属性を設定|[SQLSetStmtAttr 関数](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
