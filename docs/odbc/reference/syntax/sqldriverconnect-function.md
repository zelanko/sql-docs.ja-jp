---
title: 機能を接続する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLDriverConnect
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLDriverConnect
helpviewer_keywords:
- SQLDriverConnect function [ODBC]
ms.assetid: e299be1d-5c74-4ede-b6a3-430eb189134f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 88ec70d68b46beca97fd6b0d758e21aab5d4f4b2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302773"
---
# <a name="sqldriverconnect-function"></a>SQLDriverConnect 関数
**適合 性**  
 バージョン導入: ODBC 1.0 標準準拠: ODBC  
  
 **まとめ**  
 **SQL 接続**の代替手段です **。** **SQLConnect**の 3 つの引数よりも多くの接続情報を必要とするデータ ソースをサポートし、すべての接続情報をユーザーに要求するダイアログ ボックス、およびシステム情報で定義されていないデータ ソースを指定します。  
  
 **次の**接続属性が用意されています。  
  
-   データ ソース名、1 つ以上のユーザー ID、1 つ以上のパスワード、およびデータ ソースに必要なその他の情報を含む接続文字列を使用して接続を確立します。  
  
-   部分的な接続文字列を使用するか、または追加情報を使用しない接続を確立します。この場合、ドライバ マネージャとドライバは、接続情報をユーザーに求めることができます。  
  
-   システム情報に定義されていないデータ・ソースへの接続を確立します。 アプリケーションが部分的な接続文字列を指定した場合、ドライバーは、接続情報のユーザーを求めることができます。  
  
-   dsn ファイル内の情報から構築された接続文字列を使用して、データ ソースへの接続を確立します。  
  
 接続が確立**されると、完了**した接続文字列が返されます。 アプリケーションは、後続の接続要求にこの文字列を使用できます。 詳細については、「[接続を使用して接続する](../../../odbc/reference/develop-app/connecting-with-sqldriverconnect.md)」を参照してください。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
SQLRETURN SQLDriverConnect(  
     SQLHDBC         ConnectionHandle,  
     SQLHWND         WindowHandle,  
     SQLCHAR *       InConnectionString,  
     SQLSMALLINT     StringLength1,  
     SQLCHAR *       OutConnectionString,  
     SQLSMALLINT     BufferLength,  
     SQLSMALLINT *   StringLength2Ptr,  
     SQLUSMALLINT    DriverCompletion);  
```  
  
## <a name="arguments"></a>引数  
 *接続ハンドル*  
 [入力] 接続ハンドル。  
  
 *ウィンドウハンドル*  
 [入力]ウィンドウ ハンドル。 アプリケーションは、親ウィンドウのハンドルを渡すことができます (該当する場合)、またはウィンドウ ハンドルが適用できないか、**または SQLDriverConnect**がダイアログ ボックスを表示しない場合は null ポインター。  
  
 *インコネクションストリング*  
 [入力]完全な接続文字列 (「コメント」の構文を参照)、部分的な接続文字列、または空の文字列。  
  
 *文字列長1*  
 [入力]文字列が Unicode の場合は文字で表された **InConnectionString*の長さ、または文字列が ANSI または DBCS の場合はバイト数。  
  
 *アウトコネクションストリング*  
 [出力]完了した接続文字列のバッファーへのポインター。 ターゲット データ ソースへの接続が成功すると、このバッファーには、完了した接続文字列が格納されます。 アプリケーションでは、このバッファーに少なくとも 1,024 文字を割り当てる必要があります。  
  
 場合は*Null、* *StringLength2Ptr*は、引き続き返す文字の合計数 (文字データの null 終端文字を除く)*を*返します。  
  
 *BufferLength*  
 [入力]**アウトコネクション文字列*バッファーの長さ (文字数)。  
  
 *文字列長2Ptr*  
 [出力]\**返*される文字列の総数 (NULL 終端文字を除く) を返すバッファへのポインタ。 返される文字の数が*BufferLength*以上の場合\**、OutConnectionString*で完了した接続文字列は *、BufferLength*から null 終端文字の長さを引いた値に切り捨てられます。  
  
 *ドライバー完了*  
 [入力]ドライバー マネージャーまたはドライバーが詳細情報の接続情報を要求する必要があるかどうかを示すフラグ。  
  
 SQL_DRIVER_PROMPT、SQL_DRIVER_COMPLETE、SQL_DRIVER_COMPLETE_REQUIRED、またはSQL_DRIVER_NOPROMPT。  
  
 (詳細については、「コメント」を参照してください。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_NO_DATA、SQL_ERROR、SQL_INVALID_HANDLE、またはSQL_STILL_EXECUTING。  
  
## <a name="diagnostics"></a>診断  
 **SQL_ERROR**またはSQL_SUCCESS_WITH_INFOを返すときは、関連付けられた SQLSTATE 値を取得するには *、SQL_HANDLE_DBCの fHandleType*と*接続ハンドル*の*ハンドル*を指定して**SQLGetDiagRec**を呼び出します。 次の表は **、SQL ドライバ接続**によって一般的に返される SQLSTATE 値を示し、この関数のコンテキストで各値を説明しています。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージ。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|01004|文字列データ(右切り捨て)|バッファー\**の OutConnectionString*は接続文字列全体を返すのに十分な大きさではなかったので、接続文字列が切り捨てられました。 切り捨てられていない接続文字列の長さは、 **StringLength2Ptr*に返されます。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|01S00|無効な接続文字列属性|接続文字列 (*InConnectionString*) に無効な属性キーワードが指定されましたが、ドライバはデータ ソースに接続できかない。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|01S02|オプション値が変更されました|ドライバーは、指定された値をサポートしていません、 **SQLSetConnectAttr**の引数が指定し、同様の値を置き換えました。 *ValuePtr* (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|01S08|ファイル DSN の保存中にエラーが発生しました|文字列に**FILEDSN**キーワードが含まれていますが、.dsn ファイルは保存されませんでした。 * \** (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|01S09|無効なキーワード|(DM)*\*文字列*は **、SAVEFILE**キーワードが含まれていますが、**ドライバー**または**FILEDSN**キーワードは含まれていません。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|08001|クライアントが接続を確立できない|ドライバはデータ ソースとの接続を確立できませんでした。|  
|08002|使用中の接続名|(DM) 指定された*ConnectionHandle*は、データ ソースとの接続を確立するために既に使用されており、接続がまだ開かれていた。|  
|08004|サーバーは接続を拒否しました|データ ソースは、実装で定義された理由により、接続の確立を拒否しました。|  
|08S01|通信リンクの障害|ドライバーと、ドライバーが接続を試みていたデータ ソース間の通信リンクは **、SQLDriverConnect**関数の処理が完了する前に失敗しました。|  
|28000|無効な承認仕様|接続文字列 (*InConnectionString*) で指定されているユーザー ID または承認文字列、またはその両方が、データ ソースによって定義された制限に違反しています。|  
|HY000|一般的なエラー|特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 *\*バッファー内*の**SQLGetDiagRec**によって返されるエラー メッセージは、エラーとその原因を説明します。|  
|HY000|一般エラー: 無効なファイル dsn|(DM) **InConnectionString*内の文字列に FILEDSN キーワードが含まれていましたが、.dsn ファイルの名前が見つかりませんでした。|  
|HY000|一般エラー: ファイル バッファを作成できません|(DM) **InConnectionString*の文字列に FILEDSN キーワードが含まれていましたが、.dsn ファイルが読み取れません。|  
|HY001|メモリ割り当てエラー|ドライバー マネージャーは、実行または**SQLDriverConnect**関数の完了をサポートするために必要なメモリを割り当てることができませんでした。<br /><br /> ドライバは、関数の実行または完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作がキャンセルされました|非同期処理が*有効*にされました。 関数が呼び出され、実行が完了する前に[、SQLCancelHandle 関数](../../../odbc/reference/syntax/sqlcancelhandle-function.md)が呼び出された、*接続ハンドル*で **、SQLDriverConnect**関数が呼び出*されました。*<br /><br /> または **、SQLDriverConnect**関数が呼び出され、実行が完了する前に、マルチスレッド アプリケーションの別のスレッドから*接続ハンドル*で**SQLCancelHandle**が呼び出されました。|  
|HY010|関数シーケンス エラー|(DM) 別の非同期実行関数 **(SQLDriverConnect**ではない) が*接続ハンドル*に対して呼び出され **、SQLDriverConnect**関数が呼び出されたときにまだ実行されていました。|  
|HY013|メモリ管理エラー|メモリ不足の状態が原因で、基になるメモリ オブジェクトにアクセスできなかったため **、SQLDriverConnect**関数呼び出しを処理できませんでした。|  
|HY090|無効な文字列またはバッファ長|(DM) 引数*StringLength1*に指定された値が 0 未満であり、SQL_NTSと等しくありません。<br /><br /> (DM) 引数*BufferLength*に指定された値が 0 より小さかった。|  
|HY092|属性/オプション識別子が無効です|(DM) *DriverCompletion*引数がSQL_DRIVER_PROMPTされ、引数*は*Null ポインターでした。|  
|HY110|無効なドライバの完了|(DM)*引数 DriverCompletion*に指定された値が、SQL_DRIVER_PROMPT、SQL_DRIVER_COMPLETE、SQL_DRIVER_COMPLETE_REQUIRED、またはSQL_DRIVER_NOPROMPTに等しくありません。<br /><br /> (DM) 接続プールが有効になっており、引数*DriverCompletion*に指定された値がSQL_DRIVER_NOPROMPTに等しくありません。|  
|ハイク00|オプション機能が実装されていません|ドライバーは、アプリケーションが要求した ODBC 動作のバージョンをサポートしていません。|  
|ヒュット00|タイムアウトに達しました|データ ソースへの接続が完了する前に、ログイン タイムアウト期間が切れました。 タイムアウト期間は **、SQL_ATTR_LOGIN_TIMEOUTを**使用して設定されます。|  
|ヒュットー1|接続のタイムアウトが期限切れになりました|データ ソースが要求に応答する前に、接続タイムアウト期間が切れました。 接続タイムアウト期間は **、SQL_ATTR_CONNECTION_TIMEOUT SQLSetConnectAttr**を使用して設定されます。|  
|IM001|ドライバはこの機能をサポートしていません|(DM) 指定されたデータ ソース名に対応するドライバーは、この機能をサポートしていません。|  
|IM002|データ ソースが見つからず、既定のドライバが指定されていません|(DM) 接続文字列 (*InConnectionString*) で指定されたデータ ソース名がシステム情報に見つからず、既定のドライバ指定がありません。<br /><br /> (DM) ODBC データ ソースと既定のドライバ情報がシステム情報に見つかりませんでした。|  
|IM003|指定されたドライバを読み込めませんでした|(DM) システム情報にデータ ソース仕様にリストされているドライバ、または**DRIVER**キーワードで指定されたドライバが見つからないか、または他の理由で読み込めませんでした。|  
|IM004|SQL_HANDLE_ENVでドライバーの**SQLAllocHandle**が失敗しました|(DM)**実行中**にドライバー マネージャーは、ドライバーの**SQLAllocHandle**関数を呼び出すSQL_HANDLE_ENVの*fHandle型*とドライバーがエラーを返しました。|  
|IM005|SQL_HANDLE_DBCのドライバーの**SQLAllocHandle**に失敗しました。|(DM)**実行中**にドライバー マネージャーは、ドライバーの**SQLAllocHandle**関数を呼び出すSQL_HANDLE_DBCの*fHandle型*とドライバーがエラーを返しました。|  
|IM006|ドライバーの**SQL セットコネクトツールに**失敗しました|(DM)**実行中**にドライバー マネージャーは、ドライバーの**SQLSetConnectAttr**関数を呼び出し、ドライバーはエラーを返しました。|  
|IM007|データ ソースまたはドライバが指定されていません。ダイアログは禁止されています|接続文字列にデータ ソース名またはドライバが指定されていません*SQL_DRIVER_NOPROMPT。*|  
|IM008|ダイアログが失敗しました|ドライバーは、ログイン ダイアログ ボックスを表示しようとしましたが、失敗しました。<br /><br /> *ウィンドウハンドル*は null ポインターであり、*ドライバー補完*はSQL_DRIVER_NO_PROMPTされませんでした。|  
|IM009|変換 DLL を読み込めません|ドライバは、データ ソースまたは接続に指定された変換 DLL を読み込めませんでした。|  
|IM010|データ ソース名が長すぎます|(DM) DSN キーワードの属性値がSQL_MAX_DSN_LENGTH文字より長かった。|  
|IM011|ドライバ名が長すぎます|(DM) **DRIVER**キーワードの属性値が 255 文字を超えています。|  
|IM012|DRIVER キーワード構文エラー|(DM) **DRIVER**キーワードのキーワード値ペアに構文エラーが含まれていました。<br /><br /> (DM) * \*InConnectionString 内の*文字列に**FILEDSN**キーワードが含まれていますが、.dsn ファイルに**DRIVER**キーワードまたは**DSN**キーワードが含まれていません。|  
|IM014|指定された DSN に、ドライバとアプリケーションのアーキテクチャの不一致が含まれています。|(DM) 32 ビット アプリケーションは、64 ビット ドライバーに接続する DSN を使用します。またはその逆も同様です。|  
|IM015|SQL_HANDLE_DBC_INFO_HANDLEでドライバーの SQL ドライバ接続に失敗しました|ドライバーがSQL_ERRORを返す場合、ドライバー マネージャーは、アプリケーションにSQL_ERRORを返し、接続が失敗します。<br /><br /> SQL_HANDLE_DBC_INFO_TOKENの詳細については[、「ODBC ドライバーでの接続プール認識の開発](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)」を参照してください。|  
|IM017|非同期通知モードではポーリングが無効になっています|通知モデルを使用すると、ポーリングは無効になります。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するために呼び出されていません。|ハンドルの前の関数呼び出しがSQL_STILL_EXECUTINGを返し、通知モードが有効な場合、後処理を実行して操作を完了するために、ハンドルで**SQLCompleteAsync**を呼び出す必要があります。|  
|S1118|ドライバーは、非同期通知をサポートしていません。|ドライバーが非同期通知をサポートしていない場合は、SQL_ATTR_ASYNC_DBC_EVENTまたはSQL_ATTR_ASYNC_DBC_RETCODE_PTRを設定できません。|  
  
## <a name="comments"></a>説明  
 接続文字列には、次の構文があります。  
  
 *接続文字列*::=*空文字列*[;] *&#124;属性*[;] &#124;*属性*;*接続文字列*  
  
 *空文字列*::=*属性*::=*属性-キーワード*=*属性値*&#124; DRIVER=[{]*属性値*[}]  
  
 *属性キーワード*::= UID &#124;の DSN &#124; *PWD &#124;ドライバー定義属性キーワード*  
  
 *属性値*::=*文字ストリング*  
  
 *ドライバー定義属性-キーワード*::=*識別子*  
  
 *文字ストリング*はゼロ以上の文字を持っています。*識別子*には 1 つ以上の文字があります。*属性キーワード*は大文字と小文字を区別しません。*属性値*は大文字と小文字を区別する場合があります。**DSN**キーワードの値はブランクのみで構成されるわけではありません。  
  
 接続文字列と初期化ファイルの文法のために、キーワードと属性値は、文字を含む **[]{}()、;?\*=!@** は、中かっこで囲まないようにしてください。 **DSN**キーワードの値は、ブランクのみで構成することはできません。 システム情報の文法のため、キーワードとデータ ソース名には円記号 ()\\文字を含めることはできません。  
  
 アプリケーションは、属性にセミコロン (;)、 中括弧が必要な場合) を除き **、DRIVER**キーワードの後に属性値を囲む必要はありません。 ドライバーが受け取る属性値に中かっこが含まれている場合、ドライバーは、それらを削除する必要がありますが、返される接続文字列の一部である必要があります。  
  
 文字{}**[]{}()、;?\*=!@** はドライバにそのまま渡されます。 ただし、キーワードでこれらの文字を使用する場合、ドライバー マネージャーは、ファイル DSN を操作するときにエラーを返しますが、通常の接続文字列のドライバーに接続文字列を渡します。 キーワード値に埋め込み中かっこを使用しないでください。  
  
 接続文字列には、ドライバー定義のキーワードをいくつでも含めることができます。 **DRIVER**キーワードは、システム情報からの情報を使用しないため、ドライバーは、接続文字列の情報のみを使用してデータ ソースに接続できるように十分なキーワードを定義する必要があります。 (詳細については、このセクションの「ドライバのガイドライン」を参照してください)。ドライバーは、データ ソースに接続するために必要なキーワードを定義します。  
  
 次の表は **、DSN、****ファイル DSN、****ドライバ****、UID** **、PWD**、および**SAVEFILE**キーワードの属性値を示しています。  
  
|Keyword|属性値の説明|  
|-------------|---------------------------------|  
|**Dsn**|**SQL データソース**または**SQLDriverConnect**の [データ ソース] ダイアログ ボックスから返されるデータ ソースの名前。|  
|**ファイルDSN**|データ ソースの接続文字列の作成元となる .dsn ファイルの名前。 これらのデータ ソースは、ファイル データ ソースと呼ばれます。|  
|**ドライバー**|**SQLDrivers**関数によって返されるドライバーの説明。 たとえば、Rdb や SQL サーバーなどです。|  
|**UID**|ユーザー ID。|  
|**Pwd**|ユーザー ID に対応するパスワード、またはユーザー ID のパスワードがない場合は空のストリング (PWD=;)。|  
|**Savefile**|現在の接続の成功に使用されるキーワードの属性値を保存する .dsn ファイルのファイル名。|  
  
 アプリケーションでデータ ソースまたはドライバを選択する方法については、「データ[ソースまたはドライバの選択](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md)」を参照してください。  
  
 接続文字列でキーワードが繰り返し表示される場合、ドライバーは、キーワードの最初の出現に関連付けられた値を使用します。 **DSN**と**DRIVER**キーワードが同じ接続文字列に含まれている場合、ドライバー マネージャーとドライバーは、どちらのキーワードが最初に表示されます。  
  
 **FILEDSN**キーワードと**DSN**キーワードは相互に排他的であり、最初に出現するキーワードはどちらにしても使用され、2 番目に表示されるキーワードは無視されます。 一方 **、FILEDSN**キーワードと**DRIVER**キーワードは、相互に排他的ではありません。 **FILEDSN**を指定した接続文字列にキーワードが含まれている場合は、.dsn ファイル内の同じキーワードの属性値ではなく、接続文字列内のキーワードの属性値が使用されます。  
  
 **FILEDSN**キーワードを使用する場合は、.dsn ファイルで指定されたキーワードを使用して接続文字列を作成します。 (詳細については、このセクションの「ファイル データ ソース」を参照してください)。**UID**キーワードは省略可能です。.dsn ファイルは **、DRIVER**キーワードのみを使用して作成できます。 **PWD**キーワードは .dsn ファイルに格納されません。 dsn ファイルを保存および読み込む既定のディレクトリは、HKEY_LOCAL_MACHINE\SOFTWARE\Windows\現在のバージョンと "ODBC\データ ソース" で**CommonFileDir**によって指定されたパスの組み合わせになります。 (CommonFileDir が "C:\プログラム ファイル\共通ファイル" の場合、既定のディレクトリは "C:\プログラム ファイル\共通ファイル\ODBC\データ ソース" になります。  
  
> [!NOTE]  
>  dsn ファイルは、インストーラー DLL で[SQLReadFileDSN](../../../odbc/reference/syntax/sqlreadfiledsn-function.md)関数と[SQLWriteFileDSN](../../../odbc/reference/syntax/sqlwritefiledsn-function.md)関数を呼び出すことによって直接操作できます。  
  
 **SAVEFILE**キーワードを使用すると、現在の正常な接続を作成するときに使用されるキーワードの属性値は **、SAVEFILE**キーワードの属性値の名前を持つ .dsn ファイルとして保存されます。 **SAVEFILE**キーワードは **、ドライバー** ・キーワード **、FILEDSN**キーワード、またはその両方と組み合わせて使用するか、または SQLSTATE 01S09 (無効なキーワード) でSQL_SUCCESS_WITH_INFOを戻す必要があります。 **SAVEFILE**キーワードは、接続文字列内の**DRIVER**キーワードの前に指定する必要があります。  
  
## <a name="driver-manager-guidelines"></a>ドライバー マネージャーのガイドライン  
 ドライバー マネージャーは、ドライバーの**SQLDriverConnect**関数の*InConnectionString*引数でドライバーに渡す接続文字列を構築します。 ドライバー マネージャーは、アプリケーションによって渡される*InConnection 文字列*引数を変更しません。  
  
 ドライバー マネージャーのアクションは、*引数 DriverCompletion*の値に基づいています。  
  
-   SQL_DRIVER_PROMPT: 接続文字列に**DRIVER** **、DSN、** または**FILEDSN**キーワードが含まれていない場合、ドライバー マネージャーに [データ ソース] ダイアログ ボックスが表示されます。 このクラスは、ダイアログ ボックスから返されるデータ ソース名と、アプリケーションから渡されたその他のキーワードから接続文字列を構築します。 ダイアログ ボックスによって返されるデータ ソース名が空の場合、ドライバー マネージャーは、キーワードと値のペア DSN= 既定を指定します。 このダイアログ ボックスには、"Default" という名前のデータ ソースは表示されません。  
  
-   SQL_DRIVER_COMPLETEまたはSQL_DRIVER_COMPLETE_REQUIRED: アプリケーションで指定された接続文字列に**DSN**キーワードが含まれている場合、ドライバー マネージャーは、アプリケーションで指定された接続文字列をコピーします。 それ以外の場合は *、DriverCompletion*がSQL_DRIVER_PROMPT場合と同じアクションを実行します。  
  
-   SQL_DRIVER_NOPROMPT: ドライバー マネージャーは、アプリケーションで指定された接続文字列をコピーします。  
  
 アプリケーションで指定された接続文字列に**DRIVER**キーワードが含まれている場合、ドライバー マネージャーは、アプリケーションで指定された接続文字列をコピーします。  
  
 構築した接続文字列を使用して、ドライバー マネージャーは、使用するドライバーを決定し、そのドライバーに接続し、ドライバーに構築した接続文字列を渡します。ドライバ マネージャとドライバの操作の詳細については[、SQLConnect 関数](../../../odbc/reference/syntax/sqlconnect-function.md)の「コメント」セクションを参照してください。 接続文字列に**DRIVER**キーワードが含まれていない場合、ドライバー マネージャーは、次のように使用するドライバーを決定します。  
  
1.  接続文字列に**DSN**キーワードが含まれている場合、ドライバー マネージャーは、システム情報からデータ ソースに関連付けられているドライバーを取得します。  
  
2.  接続文字列に**DSN**キーワードが含まれていない場合、またはデータ ソースが見つからない場合、ドライバー マネージャーは、システム情報から既定のデータ ソースに関連付けられているドライバーを取得します。 (詳細については、「[既定のサブキー](../../../odbc/reference/install/default-subkey.md)」を参照してください)。ドライバー マネージャーは、接続文字列の**DSN**キーワードの値を "DEFAULT" に変更します。  
  
3.  接続文字列の**DSN**キーワードが "DEFAULT" に設定されている場合、ドライバー マネージャーは、システム情報から既定のデータ ソースに関連付けられているドライバーを取得します。  
  
4.  データ ソースが見つからず、既定のデータ ソースが見つからない場合、ドライバー マネージャーは SQLSTATE IM002 (データ ソースが見つからず、既定のドライバーが指定されていない) とSQL_ERRORを返します。  
  
## <a name="file-data-sources"></a>[ファイル データ ソース]  
 **SQLDriverConnect**の呼び出しでアプリケーションによって指定された接続文字列に**FILEDSN**キーワードが含まれ、このキーワードが**DSN**または**DRIVER**キーワードに置き換わられていない場合、ドライバー マネージャーは、.dsn ファイルと*InConnectionString*引数の情報を使用して接続文字列を作成します。 ドライバー マネージャーは、次のように処理されます。  
  
1.  dsn ファイルのファイル名が有効かどうかを確認します。 それでない場合は、SQLSTATE IM014 (ファイル DSN の無効な名前) でSQL_ERRORを返します。 ファイル名が空の文字列 ("") で、SQL_DRIVER_NOPROMPTが指定されていない場合は、[**ファイルを開く**] ダイアログ ボックスが表示されます。 ファイル名に有効なパスが含まれているが、ファイル名または無効なファイル名が含まれていない場合、SQL_DRIVER_NOPROMPTが指定されていない場合は、現在**の**ディレクトリがファイル名で指定されたディレクトリに設定された状態で表示されます。 ファイル名が空の文字列 ("") であるか、ファイル名に有効なパスが含まれているが、ファイル名または無効なファイル名が指定されている場合、SQL_DRIVER_NOPROMPTが指定されている場合、SQL_ERRORは SQLSTATE IM014 (ファイル DSN の無効な名前) で返されます。  
  
2.  dsn ファイルの [ODBC] セクション内のすべてのキーワードを読み取ります。 **DRIVER**キーワードが存在しない場合は、.dsn ファイルが共有不可能で**DSN**キーワードのみが含まれている場合を除き、SQLSTATE IM012 (ドライバー・キーワード構文エラー) を使用して SQL_ERRORを戻します。  
  
     ファイル データ ソースが共有できない場合、ドライバー マネージャーは**DSN**キーワードの値を読み取り、共有できないファイル データ ソースが指すユーザーまたはシステム データ ソースに必要に応じて接続します。 手順 3 ~ 5 は実行されません。  
  
3.  ドライバーの接続文字列を構築します。 ドライバー接続文字列は、.dsn ファイルで指定されたキーワードと、元のアプリケーション接続文字列で指定されたキーワードの和集合です。 キーワードが重複するドライバー接続文字列の構築規則は次のとおりです。  
  
    -   アプリケーション接続文字列に**DRIVER**キーワードが存在し **、DRIVER**キーワードで指定されたドライバーが .dsn ファイルとアプリケーション接続文字列で同じでない場合、.dsn ファイル内のドライバー情報は無視され、アプリケーション接続文字列のドライバー情報が使用されます。 **DRIVER**キーワードで指定されたドライバーが .dsn ファイルとアプリケーションの接続文字列で同じである場合、すべてのキーワードが重複する場合、アプリケーション接続文字列で指定されたドライバーは、.dsn ファイルで指定されたものよりも優先されます。  
  
    -   新しい接続文字列では **、FILEDSN**キーワードは削除されます。  
  
4.  レジストリ エントリを検索してドライバーを読み込む\ソフトウェア\ODBC\ODBCINSTHKEY_LOCAL_MACHINE。INI\\<ドライバ\>名 \\<ドライバで、ドライバ名>が**DRIVER**キーワードで指定されています。  
  
5.  ドライバーに新しい接続文字列を渡します。  
  
 dsn ファイルの例については、[ファイル データ ソースを使用した接続を](../../../odbc/reference/develop-app/connecting-using-file-data-sources.md)参照してください。  
  
## <a name="savefile-keyword"></a>セーブファイルキーワード  
 アプリケーションで指定された接続文字列に**SAVEFILE**キーワードが含まれている場合、ドライバー マネージャーは接続文字列を .dsn ファイルに保存します。 ドライバー マネージャーは、次のように処理されます。  
  
1.  **SAVEFILE**キーワードの属性値として指定された .dsn ファイルのファイル名が有効かどうかを検査します。 それでない場合は、SQLSTATE IM014 (ファイル DSN の無効な名前) でSQL_ERRORを返します。 ファイル名の妥当性は、標準のシステム命名規則によって決まります。 ファイル名が空の文字列 ("") で、*引数 DriverCompletion*がSQL_DRIVER_NOPROMPTされていない場合、ファイル名は有効です。 ファイル名が既に存在する場合 *、DriverCompletion*がSQL_DRIVER_NOPROMPT場合、ファイルは上書きされます。 *DriverCompletion*がSQL_DRIVER_PROMPT、SQL_DRIVER_COMPLETE、またはSQL_DRIVER_COMPLETE_REQUIREDの場合、ファイルを上書きするかどうかを指定するダイアログ ボックスが表示されます。 [いいえ] を入力すると、[**ファイルの保存**] ダイアログ ボックスが表示されます。  
  
2.  ドライバーがSQL_SUCCESSを返し、ファイル名が空の文字列ではなかった場合、ドライバー マネージャーは、指定したファイルに*OutConnectionString*引数で返された接続情報をこのセクションで前の「接続文字列」セクションで指定した形式で書き込みます。  
  
3.  ドライバーがSQL_SUCCESSを返し、ファイル名が空の文字列 ("") である場合、ドライバー マネージャーは、指定された*hwnd*で**ファイルの保存**の共通ダイアログ ボックスを呼び出し *、OutConnectionString*で返される接続情報を書き込む、ファイルの保存の共通ダイアログ ボックスで指定されたファイルに、このセクションで前の「接続文字列」セクションで指定した形式。  
  
4.  ドライバーがSQL_SUCCESS返す場合、アプリケーションに接続文字列を含む*OutConnectionString*引数を返します。  
  
5.  ドライバーがSQL_SUCCESS_WITH_INFOまたはSQL_ERRORを返す場合、ドライバー マネージャーは、アプリケーションに SQLSTATE を返します。  
  
## <a name="driver-guidelines"></a>ドライバのガイドライン  
 ドライバーは、ドライバー マネージャーによって渡された接続文字列には **、DSN**または**ドライバー**キーワードが含まれているかどうかを確認します。 接続文字列に**DRIVER**キーワードが含まれている場合、ドライバーは、システム情報からデータ ソースに関する情報を取得できません。 接続文字列に**DSN**キーワードが含まれている場合、または**DSN**キーワードまたは**DRIVER**キーワードが含まれていない場合、ドライバーは、次のようにシステム情報からデータ ソースに関する情報を取得できます。  
  
1.  接続文字列に**DSN**キーワードが含まれている場合、ドライバーは指定されたデータ ソースの情報を取得します。  
  
2.  接続文字列に**DSN**キーワードが含まれていない場合、指定されたデータ ソースが見つからない場合、または**DSN**キーワードが "DEFAULT" に設定されている場合、ドライバーは既定のデータ ソースの情報を取得します。  
  
 ドライバーは、システム情報から取得した情報を使用して、接続文字列で渡される情報を補強します。 システム情報の情報が接続文字列の情報と重複している場合、ドライバーは接続文字列の情報を使用します。  
  
 *DriverCompletion*の値に基づいて、ドライバーは、ユーザー ID やパスワードなどの接続情報をユーザーに求め、データ ソースに接続します。  
  
-   SQL_DRIVER_PROMPT: 接続文字列の値とシステム情報 (存在する場合) を初期値として使用して、ダイアログ ボックスが表示されます。 ユーザーがダイアログ ボックスを終了すると、ドライバーはデータ ソースに接続します。 また\**、InConnectionString*の**DSN**キーワードまたは**DRIVER**キーワードの値とダイアログ ボックスから返される情報から接続文字列を構築します。 この接続文字列を **OutConnectionString*バッファーに格納します。  
  
-   SQL_DRIVER_COMPLETEまたはSQL_DRIVER_COMPLETE_REQUIRED: 接続文字列に十分な情報が含まれ、その情報が正しい場合、ドライバーはデータ ソース\*に接続し *、InConnectionString*を\**OutConnectionString*にコピーします。 情報が見つからないか正しくない場合、ドライバは*DriverCompletion*がSQL_DRIVER_PROMPT時と同じアクションを実行しますが *、DriverCompletion*がSQL_DRIVER_COMPLETE_REQUIREDされた場合、データ ソースへの接続に必要な情報に対するコントロールが無効になります。  
  
-   SQL_DRIVER_NOPROMPT: 接続文字列に十分な情報が含まれている場合、ドライバーはデータ ソース\*に接続し *、InConnectionString*を\**OutConnectionString*にコピーします。 それ以外の場合、ドライバーは**SQL ドライバ接続**のSQL_ERRORを返します。  
  
 データ ソースへの接続が成功すると、ドライバーは\**StringLength2Ptr*を **OutConnectionString*で返す出力接続文字列の長さに設定します。  
  
 ユーザーがドライバー マネージャーまたはドライバーによって表示されるダイアログ ボックスをキャンセルした場合は **、sqlDriverConnect**はSQL_NO_DATAを返します。  
  
 接続プロセス中にドライバ マネージャとドライバがやり取りする方法については、 [SQLConnect 関数](../../../odbc/reference/syntax/sqlconnect-function.md)を参照してください。  
  
 ドライバーが**SQLDriverConnect**をサポートしている場合、ドライバーのシステム情報のドライバー キーワード セクションには、2 番目の文字が "Y" に設定された**ConnectFunctions**キーワードが含まれている必要があります。  
  
## <a name="connecting-when-connection-pooling-is-enabled"></a>接続プールが有効な場合の接続  
 接続プールを使用すると、アプリケーションは既に作成されている接続を再利用できます。 **SQLDriverConnect**が呼び出されると、ドライバー マネージャーは、接続プール用に指定されている環境で接続のプールの一部である接続を使用して接続を作成しようとします。 接続プールの詳細については[、SQLConnect 関数](../../../odbc/reference/syntax/sqlconnect-function.md)を参照してください。  
  
 アプリケーションは、プールが有効になっている接続で SQLDisconnect を呼び出す前に、SQL_ATTR_RESET_CONNECTIONを設定できます。 詳細については、「 [SQLSetConnectAttr 関数](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)」を参照してください。  
  
 アプリケーションが**SQLDriverConnect**を呼び出してプールされた接続に接続する場合は、次の制限が適用されます。  
  
-   接続ストリングに**SAVEFILE**キーワードが指定されている場合、接続プール処理は実行されません。  
  
-   接続プールが有効になっている場合 **、SQLDriverConnect**は、SQL_DRIVER_NOPROMPTの*DriverCompletion*引数を指定して呼び出すことができます。他の*ドライバ補完*で**SQLDriverConnect**が呼び出された場合は、SQLSTATE HY110 (無効なドライバ補完) が返されます。  
  
## <a name="connection-attributes"></a>接続属性  
 **SQLSetConnectAttr**を使用して設定されたSQL_ATTR_LOGIN_TIMEOUT接続属性は、ログイン要求が完了するまでの秒数を定義し、アプリケーションに戻る前にドライバーによる接続が成功するまでの間に定義します。 接続文字列を完了するように求められた場合、ドライバーが接続プロセスを開始すると、各ログイン要求の待機期間が開始されます。  
  
 ドライバーは、既定で、SQL_MODE_READ_WRITEアクセス モードで接続を開きます。 アクセス モードをSQL_MODE_READ_ONLYに設定するには、アプリケーションは**SQLDriverConnect**を呼び出す前に、SQL_ATTR_ACCESS_MODE属性を指定して**SQLSetConnectAttr**を呼び出す必要があります。  
  
 データ ソースのシステム情報に既定の変換ライブラリが指定されている場合、ドライバーは、そのデータ ソースを読み込みます。 SQL_ATTR_TRANSLATE_LIB属性を指定して**SQLSetConnectAttr を**呼び出すと、別の変換ライブラリをロードできます。 変換オプションは、SQL_ATTR_TRANSLATE_OPTIONオプションを指定して**SQLSetConnectAttr**を呼び出すことで指定できます。  
  
 詳細については、「[接続を使用して接続する](../../../odbc/reference/develop-app/connecting-with-sqldriverconnect.md)」を参照してください。  
  
```cpp  
// SQLDriverConnect_ref.cpp  
// compile with: odbc32.lib user32.lib  
#include <windows.h>  
#include <sqlext.h>  
  
int main() {  
   SQLHENV henv;  
   SQLHDBC hdbc;  
   SQLHSTMT hstmt;  
   SQLRETURN retcode;  
  
   SQLCHAR OutConnStr[255];  
   SQLSMALLINT OutConnStrLen;  
  
   HWND desktopHandle = GetDesktopWindow();   // desktop's window handle  
  
   // Allocate environment handle  
   retcode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
  
   // Set the ODBC version environment attribute  
   if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
      retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER*)SQL_OV_ODBC3, 0);   
  
      // Allocate connection handle  
      if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
         retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);   
  
         // Set login timeout to 5 seconds  
         if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
            SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)5, 0);  
  
            retcode = SQLDriverConnect( // SQL_NULL_HDBC  
               hdbc,   
               desktopHandle,   
               (SQLCHAR*)"driver=SQL Server",   
               _countof("driver=SQL Server"),  
               OutConnStr,  
               255,   
               &OutConnStrLen,  
               SQL_DRIVER_PROMPT );  
  
            // Allocate statement handle  
            if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {                 
               retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);   
  
               // Process data  
               if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
                  SQLFreeHandle(SQL_HANDLE_STMT, hstmt);  
               }  
  
               SQLDisconnect(hdbc);  
            }  
  
            SQLFreeHandle(SQL_HANDLE_DBC, hdbc);  
         }  
      }  
      SQLFreeHandle(SQL_HANDLE_ENV, henv);  
   }  
}  
```  
  
 サンプル[ODBC プログラム](../../../odbc/reference/sample-odbc-program.md)も参照してください。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|ハンドルの割り当て|[SQLAllocHandle 関数](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|データ ソースへの接続に必要な値の検出と列挙|[SQLBrowseConnect 関数](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|  
|データ ソースへの接続|[SQLConnect 関数](../../../odbc/reference/syntax/sqlconnect-function.md)|  
|データ ソースからの切断|[SQLDisconnect 関数](../../../odbc/reference/syntax/sqldisconnect-function.md)|  
|ドライバーの説明と属性を返す|[SQLDrivers 関数](../../../odbc/reference/syntax/sqldrivers-function.md)|  
|ハンドルを解放する|[SQLFreeHandle 関数](../../../odbc/reference/syntax/sqlfreehandle-function.md)|  
|接続属性の設定|[SQLSetConnectAttr 関数](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
