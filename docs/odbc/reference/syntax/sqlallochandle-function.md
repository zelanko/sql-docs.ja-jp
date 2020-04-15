---
title: 関数を処理する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLAllocHandle
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLAllocHandle
helpviewer_keywords:
- SQLAllocHandle function [ODBC]
ms.assetid: 6e7fe420-8cf4-4e72-8dad-212affaff317
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 178e3fad1ec062dd7f812125da66b7e21a7a4f4b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81290213"
---
# <a name="sqlallochandle-function"></a>SQLAllocHandle 関数
**適合 性**  
 バージョン導入: ODBC 3.0 規格準拠: ISO 92  
  
 **まとめ**  
 **SQLAllocHandle は**、環境、接続、ステートメント、または記述子ハンドルを割り当てます。  
  
> [!NOTE]  
>  この関数は、ODBC 2.0 関数**SQLAllocConnect 、SQLAllocEnv**、**SQLAllocEnv**および**SQLAllocStmt**を置き換えるハンドルを割り当てる汎用関数です。 **SQLAllocHandle**を呼び出すアプリケーションが ODBC 2 で動作することを許可します。*x*ドライバー、**ドライバー**への呼び出しは、ドライバー マネージャーで**SQLAllocConnect** **、SQLAllocEnv**、または**SQLAllocStmt**に適切にマップされます。 詳細については、「コメント」を参照してください。 ドライバー マネージャーは、ODBC 3 のときにこの関数をマップする方法の詳細について。*x*アプリケーションは ODBC 2 で動作しています。*x*ドライバについては、「[アプリケーションの下位互換性のための置換関数のマッピング](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md)」を参照してください。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
SQLRETURN SQLAllocHandle(  
      SQLSMALLINT   HandleType,  
      SQLHANDLE     InputHandle,  
      SQLHANDLE *   OutputHandlePtr);  
```  
  
## <a name="arguments"></a>引数  
 *HandleType*  
 [入力]**によって**割り当てられるハンドルの型。 次のいずれかの値を指定する必要があります。  
  
-   SQL_HANDLE_DBC  
  
-   SQL_HANDLE_DBC_INFO_TOKEN  
  
-   SQL_HANDLE_DESC  
  
-   SQL_HANDLE_ENV  
  
-   SQL_HANDLE_STMT  
  
 SQL_HANDLE_DBC_INFO_TOKEN ハンドルは、ドライバー マネージャーとドライバーによってのみ使用されます。 アプリケーションでは、このハンドル型を使用しないでください。 SQL_HANDLE_DBC_INFO_TOKENの詳細については[、「ODBC ドライバーでの接続プール認識の開発](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)」を参照してください。  
  
 *入力ハンドル*  
 [入力]新しいハンドルを割り当てるコンテキストの入力ハンドル。 *ハンドル型*がSQL_HANDLE_ENV場合、これはSQL_NULL_HANDLE。 *HandleType*がSQL_HANDLE_DBC場合、これは環境ハンドルである必要があり、SQL_HANDLE_STMTまたはSQL_HANDLE_DESCの場合は、接続ハンドルである必要があります。  
  
 *を処理します。*  
 [出力]新しく割り当てられたデータ構造体へのハンドルを返すバッファーへのポインター。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_INVALID_HANDLE、またはSQL_ERROR。  
  
 環境ハンドル以外のハンドルを割り当てる場合 **、SQLAllocHandle**がSQL_ERRORを返す場合、出力引数が null ポインターでない限り *、HandleType*の値に応じて*OutputHandlePtr*をSQL_NULL_HDBC、SQL_NULL_HSTMT、またはSQL_NULL_HDESCに設定します。 アプリケーションは、*引数 InputHandle*のハンドルに関連付けられている診断データ構造体から追加情報を取得できます。  
  
## <a name="environment-handle-allocation-errors"></a>環境ハンドル割り当てエラー  
 環境の割り当ては、ドライバー マネージャー内と各ドライバー内の両方で発生します。 ハンドル*型*のSQL_HANDLE_ENVを持つ**SQLAllocHandle**によって返されるエラーは、エラーが発生したレベルによって異なります。  
  
 ハンドル型の SQL_HANDLE_ENVハンドルを持つ**SQLAllocHandle**が呼び出されたときにドライバー マネージャーが*\*OutputHandlePtr*の*メモリを割*り当てることができない場合、またはアプリケーションがを返す null ポインターを提供する*場合***SQL_ERROR返**します。 ドライバー マネージャーは、SQL_NULL_HENVに **OutputHandlePtr*を設定します (アプリケーションがSQL_ERRORを返す null ポインターを提供しない限り)。 追加の診断情報を関連付けるハンドルがありません。  
  
 ドライバー マネージャーは、アプリケーションが**SQLConnect、SQLBrowseConnect**、または**SQLDriverConnect**を呼び出すまで、ドライバー レベルの環境ハンドル割り当て関数を呼び出しません。 **SQLBrowseConnect** ドライバー レベルの**SQLAllocHandle**関数でエラーが発生した場合は、ドライバー マネージャー レベル**の SQLConnect** **、SQLBrowseConnect**、または**SQLDriverConnect**関数はSQL_ERROR返します。 診断データ構造体には、SQLSTATE IM004 が含まれています (ドライバーの**SQLAllocHandle**に失敗しました)。 接続ハンドルにエラーが返されます。  
  
 ドライバー マネージャーとドライバー間の関数呼び出しのフローの詳細については、 [SQLConnect 関数](../../../odbc/reference/syntax/sqlconnect-function.md)を参照してください。  
  
## <a name="diagnostics"></a>診断  
 **SQLAllocHandle**がSQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返すときは、関連付けられた SQLSTATE 値を取得するには、適切な*HandleType*と*ハンドル*を*InputHandle*の値に設定して**SQLGetDiagRec**を呼び出します。 SQL_SUCCESS_WITH_INFO (SQL_ERROR ではなく) を返すことができます、 *OutputHandle*引数です。 次の表は **、SQLAllocHandle**によって返される SQLSTATE 値を一覧表示し、この関数のコンテキストで各値を説明します。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージ。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|08003|接続が開かない|(DM)*引数*がSQL_HANDLE_STMTまたはSQL_HANDLE_DESCされましたが *、InputHandle*引数で指定された接続が開かれていない。 ドライバーがステートメントまたは記述子ハンドルを割り当てるには、接続プロセスが正常に完了している必要があります (接続が開いている必要があります)。|  
|HY000|一般的なエラー|特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 **メッセージ テキスト*バッファー内の**SQLGetDiagRec**によって返されるエラー メッセージは、エラーとその原因を記述します。|  
|HY001|メモリ割り当てエラー|(DM) ドライバー マネージャーは、指定されたハンドルのメモリを割り当てることができませんでした。<br /><br /> ドライバは、指定されたハンドルにメモリを割り当てることができませんでした。|  
|HY009|無効な null ポインターの使用|(DM)*引数は*null ポインターでした。|  
|HY010|関数シーケンス エラー|(DM)*引数*がSQL_HANDLE_DBCされ、SQL_ODBC_VERSION環境属性を設定するために**SQLSetEnvAttr**が呼び出されていません。<br /><br /> (DM) 非同期に実行される関数が呼び出されました、 **InputHandle、sqlAllocHandle**関数がSQL_HANDLE_STMTまたはSQL_HANDLE_DESCに設定された**ハンドルの**ハンドル関数が呼び出されたときは、まだ実行されていました。 **SQLAllocHandle**|  
|HY013|メモリ管理エラー|*引数は*SQL_HANDLE_DBC、SQL_HANDLE_STMT、またはSQL_HANDLE_DESC。メモリ状態が低いため、基になるメモリ オブジェクトにアクセスできなかったため、関数呼び出しを処理できませんでした。|  
|HY014|ハンドル数の制限を超えた|*HandleType*引数で示されるハンドルの種類に割り当てることができるハンドルの数のドライバー定義の制限に達しました。|  
|HY092|属性/オプション識別子が無効です|(DM)*引数*が、SQL_HANDLE_ENV、SQL_HANDLE_DBC、SQL_HANDLE_STMT、またはSQL_HANDLE_DESCではありませんでした。|  
|HY117|不明なトランザクション状態のため、接続が中断されました。 切断と読み取り専用の機能のみが許可されます。|(DM) 中断状態の詳細については[、SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)を参照してください。|  
|ハイク00|オプション機能が実装されていません|*引数 HandleType*がSQL_HANDLE_DESCされ、ドライバーが ODBC 2 です。*x*ドライバ。|  
|ヒュットー1|接続のタイムアウトが期限切れになりました|データ ソースが要求に応答する前に、接続タイムアウト期間が切れました。 接続タイムアウト期間は **、SQL_ATTR_CONNECTION_TIMEOUT SQLSetConnectAttr**を使用して設定されます。|  
|IM001|ドライバはこの機能をサポートしていません|(DM)*引数 HandleType*がSQL_HANDLE_STMTされ、ドライバが有効な ODBC ドライバではありませんでした。<br /><br /> (DM)*引数 HandleType*がSQL_HANDLE_DESCされ、ドライバーは記述子ハンドルの割り当てをサポートしていません。|  
  
## <a name="comments"></a>説明  
 **SQLAllocHandle**は、次のセクションで説明するように、環境、接続、ステートメント、および記述子のハンドルを割り当てるに使用されます。 ハンドルの一般情報については、「[ハンドル](../../../odbc/reference/develop-app/handles.md)」を参照してください。  
  
 複数の割り当てがドライバーによってサポートされている場合、アプリケーションは、一度に複数の環境、接続、またはステートメント ハンドルを割り当てることができます。 ODBC では、一度に割り振ることができる環境、接続、ステートメント、または記述子ハンドルの数に制限は定義されません。 ドライバーは、一度に割り当てることができるハンドルの特定の種類の数に制限を課す可能性があります。詳細については、ドライバのマニュアルを参照してください。  
  
 アプリケーションが、既存の環境、接続、ステートメント、または記述子ハンドルに設定された*\*OutputHandlePtr*を使用して**SQLAllocHandle**を呼び出す場合、アプリケーションが接続プーリングを使用していない限り、ドライバーは*ハンドル*に関連付けられた情報を上書きします (このセクションの後半の「接続プールのための環境属性の割り当て」を参照)。 ドライバー マネージャーは*\*、OutputHandlePtr*に入力された*ハンドル*が既に使用されているかどうかを確認したり、上書きする前に、ハンドルの以前の内容を確認しません。  
  
> [!NOTE]  
>  再割り当て前にハンドルを解放するために SQLFreeHandle を呼び出さずに*\*、OutputHandlePtr*に定義された同じアプリケーション変数を使用して**SQLAllocHandle**を 2 回呼び出すことは、ODBC アプリケーション プログラミングが正しくありません。 **SQLFreeHandle** このような方法で ODBC ハンドルを上書きすると、ODBC ドライバー側で一貫性のない動作やエラーが発生する可能性があります。  
  
 複数のスレッドをサポートするオペレーティング・システムでは、アプリケーションは異なるスレッド上で同じ環境、接続、ステートメント、または記述子ハンドルを使用できます。 したがって、ドライバーは、この情報への安全なマルチスレッド アクセスをサポートする必要があります。これを実現する 1 つの方法は、たとえば、クリティカル セクションまたはセマフォを使用することです。 スレッド処理の詳細については、「[マルチスレッド](../../../odbc/reference/develop-app/multithreading.md)」を参照してください。  
  
 **SQLAllocHandle**は、環境ハンドルを割り当てるために呼び出されるときに、SQL_ATTR_ODBC_VERSION環境属性を設定しません。環境属性は、アプリケーションによって設定する必要があります、または SQLSTATE HY010 (関数シーケンスエラー) 接続ハンドルを割り当てる**SQLAllocHandle**が呼び出されたときに返されます。  
  
 標準に準拠したアプリケーションの場合 **、SQLAllocHandle**はコンパイル時に**SQLAllocHandleStd**にマップされます。 これら 2 つの関数の違いは、引数*HandleType*を SQL_HANDLE_ENV に設定して呼び出すと **、sqlAllocHandleStd**がSQL_ATTR_ODBC_VERSION環境属性をSQL_OV_ODBC3に設定することです。 これは、標準に準拠したアプリケーションは常に ODBC 3 であるためです。*x*アプリケーション。 さらに、標準は、アプリケーションのバージョンを登録する必要はありません。 これは、これら 2 つの関数の唯一の違いです。それ以外の場合は同一です。 **ドライバー**マネージャー内の**SQLAllocHandle に**マップされます。 したがって、サード パーティ製のドライバーは**SQLAllocHandleStd**を実装する必要はありません。  
  
 ODBC 3.8 アプリケーションは、次の機能を使用する必要があります。  
  
-   環境ハンドルを割り当てる**には SQLAllocHandle ではなく SQLAllocHandle を**割り当てます。  
  
-   SQL_ATTR_ODBC_VERSION環境**属性をSQL_OV_ODBC3_80**に設定します。  
  
## <a name="allocating-an-environment-handle"></a>環境ハンドルの割り当て  
 環境ハンドルは、有効な接続ハンドルやアクティブな接続ハンドルなどのグローバル情報へのアクセスを提供します。 環境ハンドルの一般情報については、「[環境ハンドル](../../../odbc/reference/develop-app/environment-handles.md)」を参照してください。  
  
 環境ハンドルを要求するには、アプリケーションは、SQL_HANDLE_ENVの*ハンドル型*とSQL_NULL_HANDLEの*入力ハンドル*を使用して**SQLAllocHandle**を呼び出します。 ドライバーは、環境情報のメモリを割り当て、*\*関連*付けられているハンドルの値を渡す、 OutputHandlePtr 引数。 アプリケーションは、環境ハンドル*\** 引数を必要とする後続のすべての呼び出しで OutputHandle 値を渡します。 詳細については、「[環境ハンドルの割り当て](../../../odbc/reference/develop-app/allocating-the-environment-handle.md)」を参照してください。  
  
 ドライバー マネージャーの環境ハンドルの下で、ドライバーの環境ハンドルが既に存在する場合は、SQL_HANDLE_ENVの*HandleType*を持つ**SQLAllocHandle**は、接続が行われたときにそのドライバーで呼び出されません *、SQL_HANDLE_DBCのハンドルを*持つ**SQLAllocHandle**のみ。 ドライバー マネージャーの環境ハンドルの下にドライバーの環境ハンドルが存在しない場合は、SQL_HANDLE_ENVのハンドル型の SQLAllocHandle と、SQL_HANDLE_DBCの HandleType を持つ SQLAllocHandle の両方が、ドライバーで呼び出されます。  
  
 ドライバー マネージャーは、SQL_HANDLE_ENVの*ハンドル型*で**SQLAllocHandle**関数を処理するときに、システム情報の [ODBC] セクションで**トレース**キーワードをチェックします。 1 に設定されている場合、ドライバー マネージャーは、現在のアプリケーションのトレースを有効にします。 トレース フラグが設定されている場合、トレースは最初の環境ハンドルが割り当てられるときに開始され、最後の環境ハンドルが解放されると終了します。 詳細については、「データ[ソースの設定](../../../odbc/reference/install/configuring-data-sources.md)」を参照してください。  
  
 環境ハンドルを割り当てた後、アプリケーションは環境ハンドルで**SQLSetEnvAttr**を呼び出して、SQL_ATTR_ODBC_VERSION環境属性を設定する必要があります。 この属性が設定されていない場合は **、SQLAllocHandle**が呼び出され、環境に接続ハンドルを割り当てる場合、接続を割り当てる呼び出しは SQLSTATE HY010 (関数シーケンス エラー) を返します。 詳細については、「[アプリケーションの ODBC バージョンの宣言](../../../odbc/reference/develop-app/declaring-the-application-s-odbc-version.md)」を参照してください。  
  
## <a name="allocating-shared-environments-for-connection-pooling"></a>接続プール用の共有環境の割り当て  
 環境は、1 つのプロセスで複数のコンポーネント間で共有できます。 共有環境は、複数のコンポーネントで同時に使用できます。 コンポーネントが共有環境を使用する場合、プールされた接続を使用して、接続を再作成せずに既存の接続を割り当てて使用することができます。  
  
 接続プールに使用できる共有環境を割り当てる前に、アプリケーションは**SQLSetEnvAttr**を呼び出して、SQL_ATTR_CONNECTION_POOLING環境属性をSQL_CP_ONE_PER_DRIVERまたはSQL_CP_ONE_PER_HENVに設定する必要があります。 この場合 **、SQLSetEnvAttr**は、この属性をプロセス レベルの属性に設定した*環境ハンドル*を null にして呼び出されます。  
  
 接続プールが有効になると、アプリケーションは *、引数 HandleType*をSQL_HANDLE_ENVに設定して**SQLAllocHandle**を呼び出します。 接続プールが有効になっているため、この呼び出しによって割り当てられる環境は暗黙的な共有環境になります。  
  
 共有環境が割り当てられると、*ハンドル型*の SQL_HANDLE_DBC を持つ**SQLAllocHandle**が呼び出されるまで、使用される環境は決定されません。 その時点で、ドライバー マネージャーは、アプリケーションによって要求された環境属性に一致する既存の環境を検索しようとします。 そのような環境が存在しない場合は、共有環境として作成されます。 ドライバー マネージャーは、共有環境ごとに参照カウントを保持します。このカウントは、環境が最初に作成されるときに 1 に設定されます。 一致する環境が見つかった場合、その環境のハンドルがアプリケーションに返され、参照カウントがインクリメントされます。 この方法で割り当てられた環境ハンドルは、環境ハンドルを入力引数として受け入れる任意の ODBC 関数で使用できます。  
  
## <a name="allocating-a-connection-handle"></a>接続ハンドルの割り当て  
 接続ハンドルは、接続上の有効なステートメントおよび記述子ハンドル、およびトランザクションが現在オープンされているかどうかなどの情報へのアクセスを提供します。 接続ハンドルの一般情報については、「[接続ハンドル](../../../odbc/reference/develop-app/connection-handles.md)」を参照してください。  
  
 接続ハンドルを要求するには、アプリケーションはハンドル*型*のSQL_HANDLE_DBCを使用して**SQLAllocHandle**を呼び出します。 *引数*は、そのハンドルを割り当てた**SQLAllocHandle**の呼び出しによって返された環境ハンドルに設定されます。 ドライバーは、接続情報のメモリを割り当て、*\*関連*付けられているハンドルの値を返します。 アプリケーションは、接続ハンドル*\** を必要とする後続のすべての呼び出しで OutputHandlePtr 値を渡します。 詳細については、「[接続ハンドルの割り当て」を](../../../odbc/reference/develop-app/allocating-a-connection-handle-odbc.md)参照してください。  
  
 ドライバー マネージャーは **、SQLAllocHandle**関数を処理し、アプリケーションが**SQLConnect**、SQLBrowseConnect 、または**SQLDriverConnect**を呼び出すときにドライバーの**SQLAllocHandle**関数を呼び出します。 **SQLBrowseConnect** (詳細については[、SQLConnect 関数](../../../odbc/reference/syntax/sqlconnect-function.md)を参照してください。  
  
 **SQLAllocHandle**が呼び出される前に SQL_ATTR_ODBC_VERSION環境属性が設定されていない場合、接続を割り振るための呼び出しは SQLSTATE HY010 (関数シーケンス エラー) を返します。  
  
 アプリケーションが呼び出す場合、引数*InputHandle*がSQL_HANDLE_DBCに設定され、共有環境ハンドルにも設定されている**SQLAllocHandle**ドライバー マネージャーは、アプリケーションによって設定された環境属性に一致する既存の共有環境を検索しようとします。 そのような環境が存在しない場合は、1 が作成され、(ドライバー マネージャーによって管理される) 参照カウントが 1 になります。 一致する共有環境が見つかった場合、そのハンドルはアプリケーションに返され、その参照カウントはインクリメントされます。  
  
 使用される実際の接続は **、SQLConnect**または**SQL ドライバ接続**が呼び出されるまで、ドライバー マネージャーによって決定されません。 ドライバー マネージャーは **、SQLConnect**への呼び出しで接続オプション (または**SQLDriverConnect**の呼び出しで接続キーワード) と、プール内の接続を決定する接続の割り当て後に設定された接続属性を使用します。 詳細については、 [SQLConnect 関数](../../../odbc/reference/syntax/sqlconnect-function.md)を参照してください。  
  
## <a name="allocating-a-statement-handle"></a>ステートメント ハンドルの割り当て  
 ステートメント・ハンドルは、エラー・メッセージ、カーソル名、SQL ステートメント処理の状況情報などのステートメント情報へのアクセスを提供します。 ステートメント ハンドルの一般情報については、「[ステートメント ハンドル](../../../odbc/reference/develop-app/statement-handles.md)」を参照してください。  
  
 ステートメント ハンドルを要求するには、アプリケーションはデータ ソースに接続し、SQL ステートメントを送信する前に**SQLAllocHandle**を呼び出します。 この呼び出しでは *、HandleType*を SQL_HANDLE_STMT に設定し、*その*ハンドルを割り当てた**SQLAllocHandle**への呼び出しによって返された接続ハンドルに InputHandle を設定する必要があります。 ドライバーは、ステートメント情報のメモリを割り当てる指定された接続にステートメント ハンドルを関連付け、*\*関連*付けられているハンドルの値を返します。 アプリケーションは、ステートメント*\** ハンドルを必要とする後続のすべての呼び出しで OutputHandlePtr 値を渡します。 詳細については、「[ステートメント ハンドルの割り当て](../../../odbc/reference/develop-app/allocating-a-statement-handle-odbc.md)」を参照してください。  
  
 ステートメント ハンドルが割り当てられると、ドライバーは自動的に 4 つの記述子のセットを割り当て、これらの記述子のハンドルをSQL_ATTR_APP_ROW_DESC、SQL_ATTR_APP_PARAM_DESC、SQL_ATTR_IMP_ROW_DESC、およびSQL_ATTR_IMP_PARAM_DESCステートメントの属性に割り当てます。 これらは、*暗黙的*に割り当てられた記述子と呼ばれます。 アプリケーション記述子を明示的に割り当てるには、次の「記述子ハンドルの割り当て」を参照してください。  
  
## <a name="allocating-a-descriptor-handle"></a>記述子ハンドルの割り当て  
 アプリケーションがハンドル*型*のSQL_HANDLE_DESCを使用して**SQLAllocHandle**を呼び出すと、ドライバーはアプリケーション記述子を割り当てます。 これらは明示的*に割り*当てられた記述子と呼ばれます。 アプリケーションは、SQL_ATTR_APP_ROW_DESCまたはSQL_ATTR_APP_PARAM_DESC属性を指定して**SQLSetStmtAttr**関数を呼び出すことによって、指定されたステートメント ハンドルに対して自動的に割り当てられたアプリケーション記述子ではなく、明示的に割り当てられたアプリケーション記述子を使用するようにドライバーに指示します。 実装記述子は、明示的に割り当てることはできません。 **SQLSetStmtAttr**  
  
 明示的に割り当てられた記述子は、ステートメント ハンドルではなく接続ハンドルに関連付けられます (自動的に割り当てられた記述子が割り当てられます)。 記述子は、アプリケーションが実際にデータベースに接続されている場合にのみ割り当てられたままです。 明示的に割り当てられた記述子は接続ハンドルに関連付けられるので、アプリケーションは接続内の複数のステートメントに明示的に割り当てられた記述子を関連付けることができます。 一方、暗黙的に割り当てられたアプリケーション記述子は、複数のステートメント・ハンドルに関連付けることはできません。 (割り当て済み以外のステートメント・ハンドルには関連付けできません。明示的に割り当てられた記述子ハンドルは、アプリケーションによって、または SQL_HANDLE_DESCの*HandleType*を使用して**SQLFreeHandle**を呼び出すことによって明示的に解放できます。  
  
 明示的に割り当てられた記述子が解放されると、暗黙的に割り振られている記述子がステートメントに再び関連付けられます。 (そのステートメントのSQL_ATTR_APP_ROW_DESCまたはSQL_ATTR_APP_PARAM_DESC属性は、暗黙的に割り振られている記述子ハンドルに再び設定されます。これは、接続上で明示的に割り当てられた記述子に関連付けられたすべてのステートメントに当てはまります。  
  
 記述子の詳細については、[記述子](../../../odbc/reference/develop-app/descriptors.md)を参照してください。  
  
## <a name="code-example"></a>コード例  
 [サンプル ODBC プログラム](../../../odbc/reference/sample-odbc-program.md) [、SQL ブラウズ接続関数](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)、[関数](../../../odbc/reference/syntax/sqlconnect-function.md)、および[SQLSet カーソル名関数](../../../odbc/reference/syntax/sqlsetcursorname-function.md)を参照してください。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|SQL ステートメントの実行|[SQLExecDirect 関数](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|準備された SQL ステートメントの実行|[SQLExecute 関数](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|環境、接続、ステートメント、または記述子ハンドルの解放|[SQLFreeHandle 関数](../../../odbc/reference/syntax/sqlfreehandle-function.md)|  
|実行のためのステートメントの準備|[SQLPrepare 関数](../../../odbc/reference/syntax/sqlprepare-function.md)|  
|接続属性の設定|[SQLSetConnectAttr 関数](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
|記述子フィールドの設定|[SQLSetDescField 関数](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
|環境属性の設定|[SQLSetEnvAttr 関数](../../../odbc/reference/syntax/sqlsetenvattr-function.md)|  
|ステートメント属性の設定|[SQLSetStmtAttr 関数](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
