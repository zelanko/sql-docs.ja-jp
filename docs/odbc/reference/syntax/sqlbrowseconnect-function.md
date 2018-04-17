---
title: SQLBrowseConnect 関数 |Microsoft ドキュメント
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
- SQLBrowseConnect
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLBrowseConnect
helpviewer_keywords:
- SQLBrowseConnect function [ODBC]
ms.assetid: b7f1be66-e6c7-4790-88ec-62b7662103c0
caps.latest.revision: 36
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3bbe32ab3098b0e3e7b6ea5ec284a2a86d4f7752
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sqlbrowseconnect-function"></a>SQLBrowseConnect 関数
**準拠**  
 バージョンが導入されています ODBC 1.0 標準への準拠: ODBC。  
  
 **概要**  
 **SQLBrowseConnect**反復的なメソッドを検出して、属性とデータ ソースに接続するために必要な属性値を列挙するをサポートしています。 各呼び出し**SQLBrowseConnect**下位レベルの属性および属性値を返します。 すべてのレベルが列挙されて、データ ソースへの接続が完了し、によって完全な接続文字列が返される**SQLBrowseConnect**です。 SQL_SUCCESS または SQL_SUCCESS_WITH_INFO リターン コードは、すべての接続情報が指定されており、アプリケーションがデータ ソースに接続されているようになりましたことを示します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SQLRETURN SQLBrowseConnect(  
     SQLHDBC         ConnectionHandle,  
     SQLCHAR *       InConnectionString,  
     SQLSMALLINT     StringLength1,  
     SQLCHAR *       OutConnectionString,  
     SQLSMALLINT     BufferLength,  
     SQLSMALLINT *   StringLength2Ptr);  
```  
  
## <a name="arguments"></a>引数  
 *ConnectionHandle*  
 [入力]接続ハンドルです。  
  
 *InConnectionString*  
 [入力]要求の接続文字列を参照 (を参照してください"*InConnectionString*引数"で「コメント」) です。  
  
 *StringLength1*  
 [入力]長さ **InConnectionString*文字です。  
  
 *OutConnectionString*  
 [出力]参照の結果の接続文字列を返す文字バッファーへのポインター (を参照してください"*OutConnectionString*引数"「コメント」内)。  
  
 場合*OutConnectionString* null、 *StringLength2Ptr*は文字 (文字データの null 終端文字を除く) の合計数を返しますが、バッファーに返される使用可能なによって示される*OutConnectionString*です。  
  
 *BufferLength*  
 [入力]文字の長さの **OutConnectionString*バッファー。  
  
 *StringLength2Ptr*  
 [出力]合計文字数 (除外 null 終了あり) で返される使用可能な\* *OutConnectionString*です。 返される文字数がより大きいかに等しい場合*BufferLength*、内の接続文字列\* *OutConnectionString*に切り捨てられます*BufferLength* null 終端文字の長さマイナスです。  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_NEED_DATA、SQL_ERROR、SQL_INVALID_HANDLE、または SQL_STILL_EXECUTING です。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLBrowseConnect** SQL_ERROR、SQL_SUCCESS_WITH_INFO、または SQL_NEED_DATA、関連付けられた SQLSTATE 値を返しますを呼び出すことによって取得できます**SQLGetDiagRec**で、 *HandleType* sql_handle_stmt としての*ConnectionHandle のハンドル*です。 次の表に、一般的にによって返される SQLSTATE 値**SQLBrowseConnect**とコンテキストでこの関数のいずれかを説明します。 表記"(DM)"の前に、ドライバー マネージャーによって返される SQLSTATEs の説明。 SQLSTATE 値ごとに関連付けられている戻り値のコードは、特に明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|Description|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01004|文字列データで、右側が切り捨てられました|バッファー \* *OutConnectionString*全体参照結果の接続文字列を返す文字列は切り詰められましたため大きさがありません。 バッファー **StringLength2Ptr*切り詰められていない参照結果の接続文字列の長さが含まれています。 (関数は、SQL_NEED_DATA を返します)。|  
|01S00|無効な接続文字列の属性|参照要求の接続文字列に無効な属性キーワードが指定されました (*InConnectionString*)。 (関数は、SQL_NEED_DATA を返します)。<br /><br /> 属性キーワードが参照要求の接続文字列で指定された (*InConnectionString*) を現在の接続レベルには適用されません。 (関数は、SQL_NEED_DATA を返します)。|  
|01S02|値が変更されました|ドライバーが指定した値をサポートしていません、 *ValuePtr*引数**SQLSetConnectAttr**と同様の値を置換します。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|08001|クライアント接続を確立できません。|ドライバーは、データ ソースとの接続を確立できませんでした。|  
|08002|使用されている接続名|(DM) 指定された接続は、データ ソースとの接続を確立するために既に使用されていた、接続が開かれていたとします。|  
|08004|サーバー接続を拒否しました|データ ソースには、実装定義上の理由から、接続の確立が拒否されました。|  
|08S01|通信リンクが失敗しました|関数は完了しました処理する前に、ドライバーとする、ドライバーが接続を試みたデータ ソース間の通信リンクが失敗しました。|  
|28000|無効な権限の指定|ユーザー id、承認文字列またはその両方の参照で指定された要求の接続文字列 (*InConnectionString*)、データ ソースで定義された制限に違反します。|  
|HY000|一般的なエラー|存在しなかった固有の SQLSTATE となる実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、  *\*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリ割り当てエラー|ドライバー マネージャーは、(DM) は、実行や、関数の終了をサポートするために必要なメモリを割り当てることができませんでした。<br /><br /> ドライバーは、実行や、関数の終了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作が取り消されました|呼び出して非同期操作が取り消されました[SQLCancelHandle 関数](../../../odbc/reference/syntax/sqlcancelhandle-function.md)です。 その後、元の関数が再度呼び出さ上、 *ConnectionHandle*です。<br /><br /> 呼び出して、操作が取り消されました**SQLCancelHandle**上、 *ConnectionHandle*マルチ スレッド アプリケーションで別のスレッドからです。|  
|HY010|関数のシーケンス エラー|(DM) の非同期的に実行中の関数 (いないこの 1 つ) が呼び出された、 *ConnectionHandle*この関数が呼び出されたときに実行されているとします。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、可能性のあるメモリ不足の状況が原因であるために、関数呼び出しを処理できませんでした。|  
|HY090|文字列またはバッファーの長さが無効です。|引数の指定された値 (DM) *StringLength1* 0 より小さい、SQL_NTS に等しいされませんでした。<br /><br /> 引数の指定された値 (DM) *BufferLength*が 0 未満です。|  
|HY114|ドライバーは接続レベルの非同期関数の実行をサポートしていません|(DM) アプリケーションは、接続を確立する前に、接続ハンドルでの非同期操作を有効にします。 ただし、ドライバーは接続ハンドルでの非同期操作をサポートしていません。|  
|HYT00|タイムアウトが発生しました|完了したデータ ソースに接続する前に、ログイン タイムアウト期間が期限切れです。 によって、タイムアウト期間が設定されている**SQLSetConnectAttr**、SQL_ATTR_LOGIN_TIMEOUT です。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続タイムアウト期間が期限切れです。 によって、接続タイムアウト期間が設定されている**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT です。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) 指定したデータ ソース名に対応するドライバーは、関数をサポートしていません。|  
|IM002|データ ソースが見つかりません、指定された既定のドライバー|(DM) データ ソースの参照要求の接続文字列で指定された名前 (*InConnectionString*)、システムの情報に見つからなかったも存在していた既定ドライバーの指定。<br /><br /> (DM) システム情報 ODBC データ ソースと既定のドライバー情報が見つかりませんでした。|  
|IM003|指定されたドライバーを読み込むことができませんでした。|(DM)、ドライバーは、システム情報でデータ ソースの指定に一覧表示またはで指定された、**ドライバー**キーワードが見つからなかったか、またはその他の何らかの理由をロードできませんでした。|  
|IM004|ドライバーの**SQLAllocHandle**の SQL_HANDLE _ENV できませんでした|(DM) 中に**SQLBrowseConnect**、ドライバー マネージャーがドライバーのと呼ばれる**SQLAllocHandle**で機能、 *HandleType* SQL_HANDLE_ENV とドライバーの返される、エラーがあります。|  
|IM005|ドライバーの**SQLAllocHandle**を sql_handle_dbc としてできませんでした|(DM) 中に**SQLBrowseConnect**、ドライバー マネージャーがドライバーのと呼ばれる**SQLAllocHandle**で機能、 *HandleType* sql_handle_dbc としてとドライバーの返される、エラーがあります。|  
|IM006|ドライバーの**SQLSetConnectAttr**できませんでした|(DM) 中に**SQLBrowseConnect**、ドライバー マネージャーがドライバーのと呼ばれる**SQLSetConnectAttr**関数と、ドライバーにエラーが返されます。|  
|IM009|トランスレーター DLL を読み込めません。|ドライバーは、変換、データ ソースまたは接続の指定された DLL を読み込むことでした。|  
|IM010|データ ソース名が長すぎます|(DM) DSN キーワードの属性の値は、SQL_MAX_DSN_LENGTH 文字を超えていました。|  
|IM011|ドライバー名が長すぎます|(DM) DRIVER キーワードの属性の値は 255 文字を超えていました。|  
|IM012|DRIVER キーワードの構文エラー|(DM) DRIVER キーワードのキーワードと値のペアに構文エラーが含まれています。|  
|IM014|指定の DSN にはなアーキテクチャと一致しないドライバーとアプリケーションが含まれています|(DM) 32 ビット アプリケーションでは、64 ビット ドライバー; に接続する DSN を使用します。またはその逆です。|  
|IM017|非同期通知モードでのポーリングが無効になっています|通知のモデルを使用するとは、ポーリングは無効です。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するが呼び出されていません。|ハンドルに対する前の関数呼び出しに SQL_STILL_EXECUTING が返された場合、および通知モードが有効になっている**SQLCompleteAsync**ハンドルの後処理を行い、操作を完了するに呼び出せる必要があります。|  
|S1118|ドライバーは非同期通知をサポートしていません|ドライバーが非同期通知をサポートしていない場合は、SQL_ATTR_ASYNC_DBC_EVENT または SQL_ATTR_ASYNC_DBC_RETCODE_PTR を設定できません。|  
  
## <a name="inconnectionstring-argument"></a>InConnectionString 引数  
 参照の要求の接続文字列には、次の構文があります。  
  
 *接続文字列*:: =*属性*[`;`] &#124; *属性* `;` *接続文字列*です。<br>
 *属性*:: =*属性キーワード*`=`*属性と値* &#124; `DRIVER=`[`{`]*属性と値*[`}`]<br>
 *属性キーワード*:: = `DSN` &#124; `UID` &#124; `PWD` &#124; *ドライバーの定義の属性のキーワード*<br>
 *属性値*:: =*文字の文字列*<br>
 *ドライバーの定義の属性-キーワード*:: =*識別子*<br>
  
 ここで*文字列*0 個以上の文字です。*識別子*が 1 つ以上の文字です。*属性キーワード*; 大文字小文字を区別することはありません*属性と値*可能性があります。 大文字小文字を区別しの値、 **DSN**空白だけのキーワードはで構成されていません。 接続文字列および初期化ファイルの文法、キーワード、および属性値のため、文字を含む**{} ()、;?\*=! @**避ける必要があります。 システム情報の文法、ためキーワードおよびデータ ソース名が円記号を含めることはできません (\\) 文字です。 ODBC 2 の場合。*x*ドライバー、DRIVER キーワードの属性値を囲む中かっこが必要です。  
  
 での参照要求の接続文字列キーワードが繰り返される場合、ドライバーは、最初に見つかった、キーワードに関連付けられている値を使用します。 場合、 **DSN**と**ドライバー**キーワードは、同じ参照要求の接続文字列に含まれる、ドライバー マネージャーとドライバーを使用して最初にどちらのキーワードが表示されます。  
  
 アプリケーションがデータ ソースまたはドライバーを選択する方法については、次を参照してください。[データ ソースまたはドライバーを選択する](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md)です。  
  
## <a name="outconnectionstring-argument"></a>OutConnectionString 引数  
 参照の結果の接続文字列は、接続属性の一覧です。 接続属性は、属性キーワードと対応する属性値で構成されます。 参照の結果の接続文字列には、次の構文があります。  
  
 *接続文字列*:: =*属性*[`;`] &#124; *属性* `;` *接続文字列*<br>
 *属性*:: = [`*`]*属性キーワード*`=`*属性値*<br>
 *属性キーワード*:: = *ODBC 属性キーワード* &#124; *ドライバーの定義の属性のキーワード*<br>
 *ODBC 属性キーワード*= {`UID` &#124; `PWD`} [`:`*ローカライズ識別子*]*ドライバーの定義の属性-キーワード*:: = *識別子*[`:`*ローカライズ識別子*]*属性と値*:: = `{` *属性値リスト* `}` &#124; `?` (中かっこはリテラル以外の場合は、ドライバーによって返される)。<br>
 *属性値リスト*:: =*文字列*[`:`*ローカライズされた文字の文字列*] &#124; *文字列*[`:`*ローカライズされた文字の文字列*] `,` *属性値リスト*<br>
  
 ここで*文字列*と*ローカライズされた文字の文字列*0 個以上の文字です。*識別子*と*ローカライズ識別子*1 つまたは複数の文字です。*属性キーワード*小文字は区別; されず*属性と値*大文字小文字を区別することがあります。 接続のための文字列と初期化ファイル文法、キーワード、ローカライズされた識別子は、および属性値を文字を含む**{} ()、;?\*=! @**避ける必要があります。 システム情報の文法、ためキーワードおよびデータ ソース名が円記号を含めることはできません (\\) 文字です。  
  
 参照の結果の接続文字列の構文は次のセマンティックの規則に従って使用されます。  
  
-   場合に、アスタリスク (\*) の前に、*属性キーワード*、*属性*を省略して、次の呼び出しを省略できます**SQLBrowseConnect**です。  
  
-   属性のキーワード**UID**と**PWD**で定義されている、同じ意味を持つ**SQLDriverConnect**です。  
  
-   A*ドライバーの定義の属性-キーワード*属性値が指定する属性の種類の名前します。 たとえば、だと考えられます**サーバー**、**データベース**、**ホスト**、または**DBMS**です。  
  
-   *ODBC 属性キーワード*と*ドライバーの定義の属性-キーワード*キーワードのローカライズされたまたはユーザー フレンドリなバージョンが含まれています。 これは、ダイアログ ボックスのラベルとしてアプリケーションで使用可能性があります。 ただし、 **UID**、 **PWD**、または*識別子*単独で使用する必要があるドライバーを 参照要求の文字列を渡すときにします。  
  
-   {*属性値リスト*} 実際の値の列挙が有効では、対応するため*属性キーワード*です。 中かっこ ({}) には、オプションの一覧が示されていませんことに注意してください。ドライバーによって返されます。 たとえば、サーバー名の一覧またはデータベース名の一覧があることがあります。  
  
-   場合、*属性と値*単一の question mark (?) は、1 つの値に対応して、*属性キーワード*です。 たとえば、UID ジョンズ; を =PWD 白を = です。  
  
-   各呼び出し**SQLBrowseConnect**接続プロセスの次のレベルを満たすために必要な情報だけを返します。 ドライバーは、コンテキストは呼び出しごとに常に確認できるように、接続ハンドルを使用して状態情報を関連付けます。  
  
## <a name="using-sqlbrowseconnect"></a>SQLBrowseConnect を使用します。  
 **SQLBrowseConnect**割り当てられている接続が必要です。 ドライバー マネージャーに指定されているか、初期の参照要求の接続文字列で指定されたデータ ソース名に対応するドライバーを読み込みこの場合についてを参照してください「コメント」 [SQLConnect 関数](../../../odbc/reference/syntax/sqlconnect-function.md)です。 ドライバーは、参照の処理中に、データ ソースとの接続を確立可能性があります。 場合**SQLBrowseConnect** SQL_ERROR、未処理の接続が終了し、接続が接続されていない状態に返されるを返します。  
  
> [!NOTE]  
>  **SQLBrowseConnect**接続プールをサポートしていません。 場合**SQLBrowseConnect**接続プールを有効にすると、中に呼び出されます SQLSTATE HY000 (一般的なエラー) が返されます。  
  
 ときに**SQLBrowseConnect**が呼び出された接続で初めて参照要求の接続文字列を含める必要があります、 **DSN**キーワードまたは**ドライバー**キーワード。 参照の要求の接続文字列が含まれている場合、 **DSN**キーワード、ドライバー マネージャーは、システム情報に対応するデータ ソースの指定を検索します。  
  
-   ドライバー マネージャーには、対応するデータ ソースの指定が検出されると、読み込まれます関連付けられているドライバ DLL です。ドライバーは、システム情報のデータ ソースに関する情報を取得できます。  
  
-   既定のデータ ソースの指定を検索し、関連するドライバー DLL を読み込みますが、ドライバー マネージャーは、対応するデータ ソースの指定を見つけることができない場合、ドライバーは、システム情報の既定のデータ ソースに関する情報を取得できます。 "DEFAULT"は、DSN のドライバーに渡されます。  
  
-   SQLSTATE IM002 で SQL_ERROR が返されます、ドライバー マネージャーは、対応するデータ ソースの指定を見つけることができません、既定のデータ ソースの指定がない場合は、(データ ソースが見つかりません。 および指定された既定のドライバー)。  
  
 参照の要求の接続文字列が含まれている場合、**ドライバー**キーワード、ドライバー マネージャーは、指定されたドライバーの読み込み以外のシステム情報内でデータ ソースを検索しません。 **ドライバー**キーワードは、システム情報の情報を使用していない、ドライバーは、参照の要求の接続文字列の情報のみを使用してデータ ソースに接続できるように、ドライバーは十分なキーワードを定義する必要があります。  
  
 呼び出すたびに**SQLBrowseConnect**アプリケーションでは、参照要求の接続文字列で、接続属性の値を指定します。 ドライバーは、参照結果の接続文字列の下位レベルの属性および属性値を返します。参照要求の接続文字列に列挙されていない接続属性がある限り、SQL_NEED_DATA が返されます。 アプリケーションでは、参照の結果の接続文字列の内容を使用して、次の呼び出しの参照要求の接続文字列をビルド**SQLBrowseConnect**です。 すべての必須属性 (の前にアスタリスクにないもの、 *OutConnectionString*引数) の次の呼び出しを含める必要がある**SQLBrowseConnect**です。 アプリケーションも、現在の参照要求の接続文字列です。 をビルドする際に、以前の参照の結果の接続文字列の内容を使用できませんに注意してください。つまり、さまざまな属性の値を前のレベルで設定を指定できません。  
  
 接続と関連付けられている属性のすべてのレベルが列挙されたときに、ドライバーは SQL_SUCCESS を返します、データ ソースへの接続が完了したら、およびアプリケーションに完全な接続文字列が返されます。 接続文字列と組み合わせての使用に適した**SQLDriverConnect**、別の接続を確立するために SQL_DRIVER_NOPROMPT オプションを使用します。 別の呼び出しで、完全な接続文字列は使用できません**SQLBrowseConnect**、ただし; 場合**SQLBrowseConnect**が再び呼び出された、全体の一連の呼び出しが繰り返し表示する必要があります。  
  
 **SQLBrowseConnect**参照処理以外の場合は、無効なパスワードなど、アプリケーションで指定された属性のキーワードの中に回復可能な致命的でないエラーがある場合も SQL_NEED_DATA を返します。 SQL_NEED_DATA が返されると参照結果の接続文字列は、エラーが発生した変更されないと、アプリケーションを呼び出すことができます**SQLGetDiagRec**参照時のエラーの SQLSTATE を返すにします。 これにより、アプリケーションを属性を修正し、参照ボタンを続行できます。  
  
 アプリケーションは呼び出すことによっていつでも参照プロセスを終了することができます**SQLDisconnect**です。 ドライバーは、未処理の接続を終了し、接続されていない状態に戻されます。  
  
 接続ハンドルでの非同期操作が有効になっている場合**SQLBrowseConnect** SQL_STILL_EXECUTING を返すも可能性があります。 SQL_NEED_DATA が返されると、アプリケーションを使用する必要があります**SQLDisconnect**参照処理を取り消します。 場合**SQLBrowseConnect**返します SQL_STILL_EXECUTING、アプリケーションを使用する必要があります**SQLCancelHandle**進行中の操作をキャンセルします。 呼び出す**SQLCancelHandle**後、この関数は、SQL_NEED_DATA が影響を与えませんを返します。  
  
 詳細については、次を参照してください。 [SQLBrowseConnect による接続](../../../odbc/reference/develop-app/connecting-with-sqlbrowseconnect.md)です。  
  
 ドライバーがサポートする場合は**SQLBrowseConnect**、システム情報、ドライバーを ドライバー キーワード セクションに含める必要があります、 **ConnectFunctions**キーワード 3 番目の文字では、"Y"に設定  
  
## <a name="code-example"></a>コード例  
  
> [!NOTE]  
>  Windows 認証をサポートするデータ ソース プロバイダーに接続するかどうかは、する必要がありますを指定する`Trusted_Connection=yes`接続文字列でユーザー ID とパスワード情報の代わりにします。  
  
 次の例では、アプリケーションが呼び出す**SQLBrowseConnect**繰り返しです。 毎回**SQLBrowseConnect** 、SQL_NEED_DATA を返しますで必要なデータに関する情報を渡す\* *OutConnectionString*です。 アプリケーション パス*OutConnectionString*そのルーチンを**GetUserInput** (表示されません)。 **GetUserInput**情報を解析、ビルドおよびダイアログ ボックスを表示してでユーザーが入力した情報を返します\* *InConnectionString*です。 アプリケーションがドライバーに、次の呼び出しに、ユーザーの情報を渡す**SQLBrowseConnect**です。 アプリケーションがドライバーがデータ ソースに接続するためのすべての必要な情報を入力後**SQLBrowseConnect** SQL_SUCCESS とアプリケーションを返しますが続行されます。  
  
 呼び出すことによって、SQL Server ドライバーへの接続の詳細な例については**SQLBrowseConnect**を参照してください[SQL Server 参照例](../../../odbc/reference/develop-app/sql-server-browsing-example.md)です。  
  
 たとえば、ソースの売り上げ高をデータに接続するには次の操作があります。 アプリケーションが最初には、次の文字列を渡す**SQLBrowseConnect**:  
  
```  
"DSN=Sales"  
```  
  
 ドライバー マネージャーは、データ ソース Sales に関連付けられているドライバーを読み込みます。 ドライバーの順に呼び出して**SQLBrowseConnect**アプリケーションから受け取った同じ引数を伴う関数。 ドライバーでは、次の文字列を返します **OutConnectionString*:  
  
```  
"HOST:Server={red,blue,green};UID:ID=?;PWD:Password=?"  
```  
  
 アプリケーションがこの文字列に渡すその**GetUserInput**で日常的なダイアログ ボックスをビルドする赤、青、または緑のサーバーを選択して、ユーザー ID とパスワードを入力するユーザーに確認します。 日常的なパスで、次のユーザーが指定した情報がバックアップ\* *InConnectionString*、アプリケーションに渡します**SQLBrowseConnect**:  
  
```  
"HOST=red;UID=Smith;PWD=Sesame"  
```  
  
 **SQLBrowseConnect**黒、パスワードを持つ Smith として赤のサーバーに接続するこの情報を使用して、次の文字列を返します **OutConnectionString*:  
  
```  
"*DATABASE:Database={SalesEmployees,SalesGoals,SalesOrders}"  
```  
  
 アプリケーションがこの文字列に渡すその**GetUserInput**で日常的なダイアログ ボックスを作成するデータベースを選択するユーザーに確認します。 ユーザー選択 empdata とアプリケーションの呼び出しを**SQLBrowseConnect**この文字列で最後に。  
  
```  
"DATABASE=SalesOrders"  
```  
  
 これは、ドライバーがデータ ソースへの接続に必要な情報の最後の部分**SQLBrowseConnect**関係なく SQL_SUCCESS を返します、**OutConnectionString*完全な接続文字列が含まれています。  
  
```  
// SQLBrowseConnect_Function.cpp  
// compile with: odbc32.lib  
#include <windows.h>  
#include <sqltypes.h>  
#include <sqlext.h>  
  
#define BRWS_LEN 100  
SQLHENV henv;  
SQLHDBC hdbc;  
SQLHSTMT hstmt;  
SQLRETURN retcode;  
SQLCHAR szConnStrIn[BRWS_LEN], szConnStrOut[BRWS_LEN];  
SQLSMALLINT cbConnStrOut;  
  
void GetUserInput(SQLCHAR * szConnStrOut, SQLCHAR * szConnStrIn) {}  
  
int main() {  
   // Allocate the environment handle.  
   retcode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);        
   if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
  
      // Set the version environment attribute.  
      retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER*)SQL_OV_ODBC3, 0);  
      if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
  
         // Allocate the connection handle.  
         retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);  
         if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
            // Call SQLBrowseConnect until it returns a value other than SQL_NEED_DATA   
            // (pass data source name the first time).  If SQL_NEED_DATA is returned, call GetUserInput   
            // (not shown) to build a dialog from the values in szConnStrOut.  The user-supplied values   
            // are returned in szConnStrIn, which is passed in the next call to SQLBrowseConnect.  
  
            strcpy_s((char*)szConnStrIn, _countof(szConnStrIn), "DSN=Sales");  
            do {  
               retcode = SQLBrowseConnect(hdbc, szConnStrIn, SQL_NTS,  
                  szConnStrOut, BRWS_LEN, &cbConnStrOut);  
               if (retcode == SQL_NEED_DATA)  
                  GetUserInput(szConnStrOut, szConnStrIn);  
            } while (retcode == SQL_NEED_DATA);  
  
            if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO){  
  
               // Allocate the statement handle.  
               retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);  
  
               if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO)  
                  // Process data after successful connection  
                  SQLFreeHandle(SQL_HANDLE_STMT, hstmt);  
               SQLDisconnect(hdbc);  
            }  
         }  
         SQLFreeHandle(SQL_HANDLE_DBC, hdbc);  
      }  
   }  
   SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
```  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|接続ハンドルの割り当てください。|[SQLAllocHandle 関数](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|データ ソースへの接続|[SQLConnect 関数](../../../odbc/reference/syntax/sqlconnect-function.md)|  
|データ ソースからの切断|[SQLDisconnect 関数](../../../odbc/reference/syntax/sqldisconnect-function.md)|  
|接続文字列やダイアログ ボックスを使用してデータ ソースに接続します。|[SQLDriverConnect 関数](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
|ドライバーの説明と属性を返す|[SQLDrivers 関数](../../../odbc/reference/syntax/sqldrivers-function.md)|  
|接続ハンドルを解放します。|[SQLFreeHandle 関数](../../../odbc/reference/syntax/sqlfreehandle-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
