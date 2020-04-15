---
title: 関数 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLBrowseConnect
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLBrowseConnect
helpviewer_keywords:
- SQLBrowseConnect function [ODBC]
ms.assetid: b7f1be66-e6c7-4790-88ec-62b7662103c0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 607b0d764a694098a23111e9d7f4ce9755ea982d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301342"
---
# <a name="sqlbrowseconnect-function"></a>SQLBrowseConnect 関数
**適合 性**  
 バージョン導入: ODBC 1.0 標準準拠: ODBC  
  
 **まとめ**  
 **SQLBrowseConnect**は、データ ソースへの接続に必要な属性と属性値を検出し、列挙する反復的な方法をサポートしています。 **SQLBrowseConnect**を呼び出すたびに、属性と属性値の連続したレベルが返されます。 すべてのレベルが列挙されると、データ ソースへの接続が完了し、完全な接続文字列が**SQLBrowseConnect**によって返されます。 SQL_SUCCESSまたはSQL_SUCCESS_WITH_INFOの戻りコードは、すべての接続情報が指定され、アプリケーションがデータ・ソースに接続されていることを示します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
SQLRETURN SQLBrowseConnect(  
     SQLHDBC         ConnectionHandle,  
     SQLCHAR *       InConnectionString,  
     SQLSMALLINT     StringLength1,  
     SQLCHAR *       OutConnectionString,  
     SQLSMALLINT     BufferLength,  
     SQLSMALLINT *   StringLength2Ptr);  
```  
  
## <a name="arguments"></a>引数  
 *接続ハンドル*  
 [入力] 接続ハンドル。  
  
 *インコネクションストリング*  
 [入力]参照要求の接続文字列 (「コメント」の *「InConnectionString*引数」を参照してください)。  
  
 *文字列長1*  
 [入力]文字での **InConnection 文字列*の長さ。  
  
 *アウトコネクションストリング*  
 [出力]参照結果の接続文字列を返す文字バッファーへのポインター ("コメント" の *「OutConnectionString*引数」を参照)。  
  
 場合は*Null、* *StringLength2Ptr*は、引き続き返す文字の合計数 (文字データの null 終端文字を除く)*を*返します。  
  
 *BufferLength*  
 [入力]**アウトコネクション文字列*バッファーの長さ (文字数)。  
  
 *文字列長2Ptr*  
 [出力]返される\*文字の合計数 (Null 終端を除く) を*返す*。 返される文字の数が*BufferLength*以上の場合\**、OutConnectionString*の接続文字列は *、バッファー長*から null 終端文字の長さを引いた値に切り捨てられます。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_NEED_DATA、SQL_ERROR、SQL_INVALID_HANDLE、またはSQL_STILL_EXECUTING。  
  
## <a name="diagnostics"></a>診断  
 **SQLBrowseConnect**がSQL_ERROR、SQL_SUCCESS_WITH_INFO、またはSQL_NEED_DATAを返すときに、SQL_HANDLE_STMTの*ハンドル型*と*接続ハンドルのハンドル*を指定して**SQLGetDiagRec**を呼び出すことによって、関連付けられた SQLSTATE 値を取得できます。 次の表は **、SQLBrowseConnect**によって一般的に返される SQLSTATE 値を示し、この関数のコンテキストでそれぞれの値を説明しています。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージ。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|01004|文字列データ(右切り捨て)|バッファー \* *OutConnectionString*は、全体の参照結果の接続文字列を返すのに十分な大きさではなかったので、文字列が切り捨てられました。 バッファー **StringLength2Ptr*には、切り捨てられていない参照結果の接続文字列の長さが含まれています。 (関数はSQL_NEED_DATAを返します。|  
|01S00|無効な接続文字列属性|参照要求接続文字列 (*InConnectionString*) に無効な属性キーワードが指定されました。 (関数はSQL_NEED_DATAを返します。<br /><br /> 現在の接続レベルに適用されない参照要求接続文字列 (*InConnectionString*) で属性キーワードが指定されました。 (関数はSQL_NEED_DATAを返します。|  
|01S02|値が変更されました|ドライバーは、指定された値をサポートしていません、 *ValuePtr*引数**SQLSetConnectAttr**と同様の値を置き換えました。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|08001|クライアントが接続を確立できない|ドライバはデータ ソースとの接続を確立できませんでした。|  
|08002|使用中の接続名|(DM) 指定された接続は、既にデータ ソースとの接続を確立するために使用されており、接続が開かれていた。|  
|08004|サーバーは接続を拒否しました|データ ソースは、実装で定義された理由により、接続の確立を拒否しました。|  
|08S01|通信リンクの障害|ドライバとドライバが接続を試みていたデータ ソースとの間の通信リンクが、関数の処理を完了する前に失敗しました。|  
|28000|無効な承認仕様|参照要求の接続文字列 (*InConnectionString*) で指定されているユーザー識別子または承認文字列、またはその両方が、データ ソースによって定義された制限に違反しました。|  
|HY000|一般的なエラー|特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 メッセージ テキスト バッファー内の**SQLGetDiagRec**によって返されるエラー メッセージは、エラーとその原因を記述します。 * \**|  
|HY001|メモリ割り当てエラー|(DM) ドライバー マネージャーは、実行または関数の完了をサポートするために必要なメモリを割り当てることができませんでした。<br /><br /> ドライバは、関数の実行または完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作がキャンセルされました|非同期操作は[、呼](../../../odbc/reference/syntax/sqlcancelhandle-function.md)び出すことによってキャンセルされました。 その後、元の関数が再度呼び出された、 *ConnectionHandle*。<br /><br /> マルチスレッド アプリケーションの別のスレッドから**SQLCancelHandle**を呼び出すことによって操作がキャンセルされました。 *ConnectionHandle*|  
|HY010|関数シーケンス エラー|(DM) 非同期実行関数 (この関数ではない) は *、ConnectionHandle*に対して呼び出され、この関数が呼び出されたときにまだ実行されていました。|  
|HY013|メモリ管理エラー|メモリ不足の状態が原因で、基になるメモリ オブジェクトにアクセスできなかったため、関数呼び出しを処理できませんでした。|  
|HY090|無効な文字列またはバッファ長|(DM) 引数*StringLength1*に指定された値が 0 未満であり、SQL_NTSと等しくありません。<br /><br /> (DM) 引数*BufferLength*に指定された値が 0 より小さかった。|  
|HY114|ドライバは接続レベルの非同期関数の実行をサポートしていません|(DM) アプリケーションは、接続を確立する前に、接続ハンドルで非同期操作を有効にしました。 ただし、ドライバーは、接続ハンドルでの非同期操作をサポートしていません。|  
|ヒュット00|タイムアウトに達しました|データ ソースへの接続が完了する前に、ログイン タイムアウト期間が切れました。 タイムアウト期間は **、SQL_ATTR_LOGIN_TIMEOUTを**使用して設定されます。|  
|ヒュットー1|接続のタイムアウトが期限切れになりました|データ ソースが要求に応答する前に、接続タイムアウト期間が切れました。 接続タイムアウト期間は **、SQL_ATTR_CONNECTION_TIMEOUT SQLSetConnectAttr**を使用して設定されます。|  
|IM001|ドライバはこの機能をサポートしていません|(DM) 指定されたデータ ソース名に対応するドライバーは、この機能をサポートしていません。|  
|IM002|データ ソースが見つからず、既定のドライバが指定されていません|(DM) 参照要求接続文字列 (*InConnectionString*) で指定されたデータ ソース名がシステム情報に見つからなかったか、既定のドライバ仕様が存在しませんでした。<br /><br /> (DM) ODBC データ ソースと既定のドライバ情報がシステム情報に見つかりませんでした。|  
|IM003|指定されたドライバを読み込めませんでした|(DM) システム情報にデータ ソース仕様にリストされているドライバ、または**DRIVER**キーワードで指定されたドライバが見つからないか、または他の理由で読み込めませんでした。|  
|IM004|_ENVでドライバーの**SQLAllocHandle** SQL_HANDLE失敗しました|(DM) **SQLBrowseConnect**の間に、ドライバー マネージャーは、ハンドル*の種類*のSQL_HANDLE_ENVのハンドルを持つドライバーの**SQLAllocHandle**関数を呼び出し、ドライバーがエラーを返しました。|  
|IM005|SQL_HANDLE_DBCでドライバーの**SQLAllocHandle**が失敗しました|(DM) **SQLBrowseConnect**の間に、ドライバー マネージャーは、ハンドル*の種類*のSQL_HANDLE_DBCのドライバーの**SQLAllocHandle**関数を呼び出し、ドライバーがエラーを返しました。|  
|IM006|ドライバーの**SQL セットコネクトツールに**失敗しました|(DM) **SQLBrowseConnect**の間に、ドライバー マネージャーは、ドライバーの**SQLSetConnectAttr**関数を呼び出し、ドライバーがエラーを返しました。|  
|IM009|変換 DLL を読み込めません|ドライバは、データ ソースまたは接続に指定された変換 DLL を読み込めませんでした。|  
|IM010|データ ソース名が長すぎます|(DM) DSN キーワードの属性値がSQL_MAX_DSN_LENGTH文字より長かった。|  
|IM011|ドライバ名が長すぎます|(DM) DRIVER キーワードの属性値が 255 文字を超えています。|  
|IM012|DRIVER キーワード構文エラー|(DM) DRIVER キーワードのキーワード値ペアに構文エラーが含まれていました。|  
|IM014|指定された DSN に、ドライバとアプリケーションのアーキテクチャの不一致が含まれています。|(DM) 32 ビット アプリケーションは、64 ビット ドライバーに接続する DSN を使用します。またはその逆も同様です。|  
|IM017|非同期通知モードではポーリングが無効になっています|通知モデルを使用すると、ポーリングは無効になります。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するために呼び出されていません。|ハンドルの前の関数呼び出しがSQL_STILL_EXECUTINGを返し、通知モードが有効な場合、後処理を実行して操作を完了するために、ハンドルで**SQLCompleteAsync**を呼び出す必要があります。|  
|S1118|ドライバーは、非同期通知をサポートしていません。|ドライバーが非同期通知をサポートしていない場合は、SQL_ATTR_ASYNC_DBC_EVENTまたはSQL_ATTR_ASYNC_DBC_RETCODE_PTRを設定できません。|  
  
## <a name="inconnectionstring-argument"></a>文字列の引数  
 参照要求の接続文字列は、次の構文を使用します。  
  
 *接続文字列*::=*属性*`;`[ ]*属性*`;`*の接続文字列*&#124;;<br>
 *属性*: :=*属性キーワード*`=`*属性値*`DRIVER=``{`&#124; [ ]`}`*属性値*[ ]<br>
 *属性キーワード*::= `DSN` `UID` &#124;&#124;&#124;`PWD`*ドライバー定義属性キーワード*<br>
 *属性値*::=*文字ストリング*<br>
 *ドライバー定義属性-キーワード*::=*識別子*<br>
  
 *文字ストリング*はゼロ以上の文字を持っています。*識別子*には 1 つ以上の文字があります。*属性キーワード*は大文字と小文字を区別しません。*属性値*は大文字と小文字を区別する場合があります。**DSN**キーワードの値はブランクのみで構成されるわけではありません。 接続文字列と初期化ファイルの文法のために、キーワードと属性値は、文字を含む **[]{}()、;?\*=!@** は避けるべきです。 システム情報の文法のため、キーワードとデータ ソース名には円記号 ()\\文字を含めることはできません。 ODBC 2 の場合。*x*ドライバー、中かっこは、DRIVER キーワードの属性値の前後に必要です。  
  
 参照要求の接続文字列でキーワードが繰り返し表示される場合、ドライバーは、キーワードの最初の出現に関連付けられている値を使用します。 **DSN**と**DRIVER**キーワードが同じ参照要求の接続文字列に含まれている場合、ドライバー マネージャーとドライバーは、どちらのキーワードが最初に表示されます。  
  
 アプリケーションでデータ ソースまたはドライバを選択する方法については、「データ[ソースまたはドライバの選択](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md)」を参照してください。  
  
## <a name="outconnectionstring-argument"></a>アウトコネクション文字列の引数  
 参照結果の接続文字列は、接続属性の一覧です。 接続属性は、属性キーワードと対応する属性値で構成されます。 参照結果の接続文字列は、次の構文を使用します。  
  
 *接続文字列*::=*属性*`;`[ ]*属性*`;`*の接続文字列*&#124;<br>
 *属性*::=`*`[ ]*属性 - キーワード*`=`*属性値*<br>
 *属性キーワード*::= *ODBC 属性キーワード*&#124;*ドライバー定義属性キーワード*<br>
 *ODBC 属性キーワード*=`UID` { `PWD`&#124;`:`} [*ローカライズされた識別子*]*ドライバー定義属性キーワード*`:`::=*識別子*[*ローカライズ識別子*]*属性値*::= `{` *属性値リスト*`}`&#124; `?` (中かっこはリテラルであり、ドライバーによって返されます)。<br>
 *属性値リスト*::=*文字ストリング*[`:`*ローカライズ文字列*] &#124;*文字列*[`:`*ローカライズ文字列*] `,` *属性値リスト*<br>
  
 *ここで、文字ストリング*と*ローカライズされた文字ストリング*はゼロ以上の文字を持っています。*識別子*と*ローカライズされた識別子*には 1 つ以上の文字があります。*属性キーワード*は大文字と小文字を区別しません。属性*値は*大文字と小文字を区別する可能性があります。 接続文字列と初期化ファイルの文法、キーワード、ローカライズされた識別子、および文字を含む属性値 **[]{}()、;?\*=!@** は避けるべきです。 システム情報の文法のため、キーワードとデータ ソース名には円記号 ()\\文字を含めることはできません。  
  
 参照結果の接続文字列構文は、次のセマンティックルールに従って使用されます。  
  
-   *属性キーワード*の\*前にアスタリスク ( ) が付いている場合、*属性*は省略可能であり、 **SQLBrowseConnect**の次の呼び出しで省略できます。  
  
-   属性キーワード**UID**と**PWD**は **、SQLDriverConnect**で定義されているのと同じ意味を持ちます。  
  
-   *ドライバー定義属性キーワード*は、属性値を指定できる属性の種類を指定します。 たとえば、**サーバー**、**データベース**、**ホスト****、DBMS**などです。  
  
-   *ODBC 属性キーワード*と*ドライバー定義属性キーワードには、* ローカライズされたバージョンまたはユーザーフレンドリなバージョンのキーワードが含まれます。 これは、アプリケーションがダイアログ ボックスのラベルとして使用する場合があります。 ただし **、UID** **、PWD、** または*識別子*は、ドライバーに参照要求文字列を渡すときに単独で使用する必要があります。  
  
-   {*属性値リスト*} は、対応する属性キーワードに対して有効な実際*の値の列挙体です*。 中かっこ ({}) は選択肢のリストを示すものではありません。ドライバによって返されます。 たとえば、サーバー名のリストやデータベース名のリストなどです。  
  
-   *属性値*が単一の疑問符 (?) の場合、単一の値は*属性キーワード*に対応します。 たとえば、UID=ジョンPWD=ゴマ。  
  
-   **SQLBrowseConnect**を呼び出すたびに、接続プロセスの次のレベルを満たすために必要な情報だけが返されます。 ドライバーは、コンテキストが常に各呼び出しで決定できるように、接続ハンドルに状態情報を関連付けます。  
  
## <a name="using-sqlbrowseconnect"></a>を使用する  
 **割**り当てられた接続が必要です。 ドライバー マネージャーは、指定されたドライバー、または最初の参照要求の接続文字列で指定されたデータ ソース名に対応するドライバーを読み込みます。これが発生するタイミングについては[、SQLConnect 関数](../../../odbc/reference/syntax/sqlconnect-function.md)の「コメント」セクションを参照してください。 ドライバーは、参照プロセス中にデータ ソースとの接続を確立可能性があります。 **SQLBrowseConnect**がSQL_ERRORを戻した場合、未解決の接続は終了し、接続は未接続状態に戻されます。  
  
> [!NOTE]  
>  **接続**プールはサポートされていません。 接続プールが有効になっているときに**SQLBrowseConnect**が呼び出されると、SQLSTATE HY000 (一般エラー) が返されます。  
  
 接続時に**SQLBrowseConnect**が初めて呼び出される場合、ブラウズ要求接続文字列には**DSN**キーワードまたは**DRIVER**キーワードが含まれている必要があります。 参照要求の接続文字列に**DSN**キーワードが含まれている場合、ドライバー マネージャーは、システム情報に対応するデータ ソースの仕様を検索します。  
  
-   ドライバー マネージャーは、対応するデータ ソースの仕様を見つける場合は、関連付けられているドライバー DLL を読み込みます。ドライバーは、システム情報からデータ ソースに関する情報を取得できます。  
  
-   ドライバー マネージャーは、対応するデータ ソースの仕様を見つけることができない場合は、既定のデータ ソースの仕様を検索し、関連付けられているドライバー DLL を読み込みます。ドライバーは、システム情報から既定のデータ ソースに関する情報を取得できます。 DSN のドライバに"DEFAULT" が渡されます。  
  
-   ドライバー マネージャーは、対応するデータ ソースの仕様を見つけることができず、既定のデータ ソースの仕様がない場合は、SQLSTATE IM002 (データ ソースが見つからず、既定のドライバーが指定されていません) とSQL_ERRORを返します。  
  
 参照要求の接続文字列に**DRIVER**キーワードが含まれている場合、ドライバー マネージャーは指定されたドライバーを読み込みます。システム情報のデータ ソースの検索は試行されません。 **DRIVER**キーワードは、システム情報からの情報を使用しないため、ドライバーは、ドライバーが参照要求の接続文字列の情報のみを使用してデータ ソースに接続できるように十分なキーワードを定義する必要があります。  
  
 **SQLBrowseConnect**への呼び出しごとに、アプリケーションは参照要求接続文字列に接続属性値を指定します。 ドライバーは、参照結果の接続文字列で属性と属性値の連続したレベルを返します。参照要求の接続文字列に列挙されていない接続属性がある限り、SQL_NEED_DATA返します。 アプリケーションは、参照結果の接続文字列の内容を使用して **、次の SQLBrowseConnect**呼び出しの参照要求接続文字列を作成します。 すべての必須属性 (*引数 OutConnectionString*のアスタリスクが付いていない属性) は、次の**SQLBrowseConnect**呼び出しに含める必要があります。 アプリケーションは、現在の参照要求接続文字列を構築するときに、以前の参照結果の接続文字列の内容を使用できないことに注意してください。つまり、以前のレベルで設定された属性に異なる値を指定することはできません。  
  
 すべてのレベルの接続と関連付けられた属性が列挙されると、ドライバーはSQL_SUCCESSを返し、データ ソースへの接続が完了し、完全な接続文字列がアプリケーションに返されます。 接続文字列は、別の接続を確立するSQL_DRIVER_NOPROMPT オプションと共に**SQLDriverConnect**と組み合わせて使用するのに適しています。 ただし、完全な接続文字列は **、SQLBrowseConnect**の別の呼び出しでは使用できません。**SQLBrowseConnect**が再度呼び出された場合は、呼び出しのシーケンス全体を繰り返す必要があります。  
  
 **また**、ブラウズ処理中に回復可能で致命的でないエラーがあった場合は、SQL_NEED_DATAも返されます。たとえば、無効なパスワードや属性キーワードがアプリケーションによって提供されます。 SQL_NEED_DATAが返され、参照結果の接続文字列が変更されていない場合、エラーが発生し、アプリケーションは**SQLGetDiagRec**を呼び出してブラウズ時エラーの SQLSTATE を返すことができます。 これにより、アプリケーションは属性を修正し、参照を続行できます。  
  
 アプリケーションは**SQLDisconnect**を呼び出すことによって、いつでもブラウズ プロセスを終了できます。 ドライバは未解決の接続を終了し、接続されていない状態に戻ります。  
  
 接続ハンドルで非同期操作が有効になっている場合は **、SQLBrowseConnect**がSQL_STILL_EXECUTINGを返すこともあります。 アプリケーションは、SQL_NEED_DATAを返すときに **、SQLDisconnect**を使用して参照プロセスをキャンセルする必要があります。 **SQLBrowseConnect**がSQL_STILL_EXECUTINGを返す場合、アプリケーションは**SQLCancelHandle**を使用して、進行中の操作をキャンセルする必要があります。 関数が関数を返した後に**SQLCancelHandle**を呼び出すSQL_NEED_DATAは効果がありません。  
  
 詳細については、「 [SQLBrowseConnect を使用した接続](../../../odbc/reference/develop-app/connecting-with-sqlbrowseconnect.md)」を参照してください。  
  
 ドライバーが**SQLBrowseConnect**をサポートしている場合、ドライバーのシステム情報のドライバー キーワード セクションには、3 番目の文字が "Y" に設定された**ConnectFunctions**キーワードが含まれている必要があります。  
  
## <a name="code-example"></a>コード例  
  
> [!NOTE]  
>  Windows 認証をサポートするデータ ソース プロバイダに接続する場合は、接続文字列`Trusted_Connection=yes`でユーザー ID とパスワード情報の代わりに指定する必要があります。  
  
 次の例では、アプリケーションが**SQLBrowseConnect**を繰り返し呼び出します。 **SQLBrowseConnect**がSQL_NEED_DATAを返すたびに、必要なデータに関する情報を\* *OutConnectionString*に返します。 アプリケーションは、そのルーチン**GetUserInput** (示されていない) に*アウトコネクション文字列*を渡します。 **GetUserInput**は情報を解析し、ダイアログ ボックスを作成して表示し、ユーザーが\**InConnectionString*に入力した情報を返します。 アプリケーションは、次の呼び出しで、ユーザーの情報をドライバーに渡**します**。 アプリケーションがデータ ソースに接続するために必要なすべての情報を提供した後 **、SQLBrowseConnect**はSQL_SUCCESSを返し、アプリケーションが続行します。  
  
 **SQLBrowseConnect**を呼び出して SQL Server ドライバに接続する詳細な例については、「 [SQL Server の参照の例](../../../odbc/reference/develop-app/sql-server-browsing-example.md)」を参照してください。  
  
 たとえば、データ ソース Sales に接続するには、次のアクションが発生する可能性があります。 まず、アプリケーションは次の文字列を**SQLBrowseConnect**に渡します。  
  
```  
"DSN=Sales"  
```  
  
 ドライバー マネージャーは、データ ソースの販売に関連付けられているドライバーを読み込みます。 次に、アプリケーションから受け取った引数と同じ引数を使用して、ドライバーの**SQLBrowseConnect**関数を呼び出します。 ドライバーは、 **OutConnectionString*で次の文字列を返します。  
  
```  
"HOST:Server={red,blue,green};UID:ID=?;PWD:Password=?"  
```  
  
 アプリケーションは、この文字列を**GetUserInput**ルーチンに渡します。 このルーチンは、次のユーザー指定の情報\*を*InConnectionString*に戻し、アプリケーションは**SQLBrowseConnect**に渡します。  
  
```  
"HOST=red;UID=Smith;PWD=Sesame"  
```  
  
 **SQLBrowseConnect**は、この情報を使用してパスワードセサミを使用してスミスとして赤いサーバーに接続し、次の文字列を返します **OutConnectionString*。  
  
```  
"*DATABASE:Database={SalesEmployees,SalesGoals,SalesOrders}"  
```  
  
 アプリケーションは、ユーザーにデータベースの選択を求めるダイアログ ボックスを作成する**GetUserInput**ルーチンにこの文字列を渡します。 ユーザーが empdata を選択すると、アプリケーションは**SQLBrowseConnect**を呼び出して、この文字列を使用して最後の時刻を返します。  
  
```  
"DATABASE=SalesOrders"  
```  
  
 これは、ドライバがデータ ソースに接続するために必要な最後の情報です。**SQL_SUCCESS**返し、**OutConnectionString には*完了した接続文字列が含まれています。  
  
```cpp  
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
  
|対象|参照先|  
|---------------------------|---------|  
|接続ハンドルの割り当て|[SQLAllocHandle 関数](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|データ ソースへの接続|[SQLConnect 関数](../../../odbc/reference/syntax/sqlconnect-function.md)|  
|データ ソースからの切断|[SQLDisconnect 関数](../../../odbc/reference/syntax/sqldisconnect-function.md)|  
|接続文字列またはダイアログ ボックスを使用したデータ ソースへの接続|[SQLDriverConnect 関数](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
|ドライバーの説明と属性を返す|[SQLDrivers 関数](../../../odbc/reference/syntax/sqldrivers-function.md)|  
|接続ハンドルの解放|[SQLFreeHandle 関数](../../../odbc/reference/syntax/sqlfreehandle-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
