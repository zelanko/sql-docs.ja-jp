---
title: SQLConnect 関数 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLConnect
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLConnect
helpviewer_keywords:
- SQLConnect function [ODBC]
ms.assetid: 59075e46-a0ca-47bf-972a-367b08bb518d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ab0a31845efeb484c554a9c9cf1afeaeab1a8bea
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301218"
---
# <a name="sqlconnect-function"></a>SQLConnect 関数
**適合 性**  
 バージョン導入: ODBC 1.0 規格準拠: ISO 92  
  
 **まとめ**  
 **SQLConnect**は、ドライバとデータ ソースへの接続を確立します。 接続ハンドルは、状態、トランザクション状態、エラー情報など、データ ソースへの接続に関するすべての情報のストレージを参照します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
SQLRETURN SQLConnect(  
     SQLHDBC        ConnectionHandle,  
     SQLCHAR *      ServerName,  
     SQLSMALLINT    NameLength1,  
     SQLCHAR *      UserName,  
     SQLSMALLINT    NameLength2,  
     SQLCHAR *      Authentication,  
     SQLSMALLINT    NameLength3);  
```  
  
## <a name="arguments"></a>引数  
 *接続ハンドル*  
 [入力] 接続ハンドル。  
  
 *ServerName*  
 [入力]データ ソース名。 データは、プログラムと同じコンピューター上に置くか、ネットワーク上の別のコンピューター上に配置されている可能性があります。 アプリケーションでデータ ソースを選択する方法については、「データ[ソースまたはドライバの選択](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md)」を参照してください。  
  
 *NameLength1*  
 [入力]**文字でのサーバー名*の長さ。  
  
 *名*  
 [入力]ユーザー識別子。  
  
 *名前の長さ 2*  
 [入力]**文字数でのユーザー名*の長さ。  
  
 *認証*  
 [入力]認証文字列 (通常はパスワード)。  
  
 *名前の長さ 3*  
 [入力]**文字での認証*の長さ。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、SQL_INVALID_HANDLE、またはSQL_STILL_EXECUTING。  
  
## <a name="diagnostics"></a>診断  
 **SQLConnect**がSQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返すときは、SQL_HANDLE_DBCの*ハンドル型*と*接続ハンドル*の*ハンドル*を指定して**SQLGetDiagRec**を呼び出すことによって、関連付けられた SQLSTATE 値を取得できます。 次の表は、SQLConnect によって返される**SQLSTATE**値の一覧と、この関数のコンテキストでの各値の説明です。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージ。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|01S02|オプション値が変更されました|ドライバーは、指定された値をサポートしていません、 *ValuePtr*引数**SQLSetConnectAttr**と同様の値を置き換えました。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|08001|クライアントが接続を確立できない|ドライバはデータ ソースとの接続を確立できませんでした。|  
|08002|使用中の接続名|(DM) 指定された*ConnectionHandle*は、データ ソースとの接続を確立するために既に使用されており、接続がまだ開かれていたか、ユーザーが接続を参照していました。|  
|08004|サーバーは接続を拒否しました|データ ソースは、実装で定義された理由により、接続の確立を拒否しました。|  
|08S01|通信リンクの障害|ドライバとドライバが接続を試みたデータ ソースとの間の通信リンクが、関数の処理が完了する前に失敗しました。|  
|28000|無効な承認仕様|*引数 UserName*に指定された値、または引数*Authentication*に指定された値が、データ ソースで定義された制限に違反しました。|  
|HY000|一般的なエラー|特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 メッセージ テキスト バッファー内の**SQLGetDiagRec**によって返されるエラー メッセージは、エラーとその原因を記述します。 * \**|  
|HY001|メモリ割り当てエラー|(DM) ドライバー マネージャーは、実行または関数の完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作がキャンセルされました|非同期処理が*有効*にされました。 **SQLConnect**関数が呼び出され、実行が完了する前に[、SQLCancelHandle 関数](../../../odbc/reference/syntax/sqlcancelhandle-function.md)が呼び出された、*接続ハンドル*で **、SQLConnect**関数が再度呼び出*されました。*<br /><br /> または **、SQLConnect**関数が呼び出され、実行が完了する前に、マルチスレッド アプリケーションの別のスレッドから*接続ハンドル*に対して**SQLCancelHandle**が呼び出されました。|  
|HY010|関数シーケンス エラー|(DM) 非同期実行関数 (この関数ではない) は *、ConnectionHandle*に対して呼び出され、この関数が呼び出されたときにまだ実行されていました。|  
|HY013|メモリ管理エラー|メモリ不足の状態が原因で、基になるメモリ オブジェクトにアクセスできなかったため、関数呼び出しを処理できませんでした。|  
|HY090|無効な文字列またはバッファ長|(DM) 引数*NameLength1、NameLength2、* または*NameLength3*に指定された値が 0 未満でしたが、SQL_NTSと等しくありません。 *NameLength2*<br /><br /> (DM) 引数*NameLength1*に指定された値が、データ ソース名の最大長を超えました。|  
|ヒュット00|タイムアウトに達しました|クエリのタイムアウト期間が経過した後、データ ソースへの接続が完了しました。 タイムアウト期間は **、SQL_ATTR_LOGIN_TIMEOUTを**使用して設定されます。|  
|HY114|ドライバは接続レベルの非同期関数の実行をサポートしていません|(DM) アプリケーションは、接続を確立する前に、接続ハンドルで非同期操作を有効にしました。 ただし、ドライバーは、接続ハンドルの非同期操作をサポートしていません。|  
|ヒュットー1|接続のタイムアウトが期限切れになりました|データ ソースが要求に応答する前に、接続タイムアウト期間が切れました。 接続タイムアウト期間は **、SQL_ATTR_CONNECTION_TIMEOUT SQLSetConnectAttr**を使用して設定されます。|  
|IM001|ドライバはこの機能をサポートしていません|(DM) データ ソース名で指定されたドライバは、この機能をサポートしていません。|  
|IM002|データ ソースが見つからず、既定のドライバが指定されていません|(DM) 引数*ServerName*で指定されたデータ ソース名がシステム情報に見つからなかったか、既定のドライバ仕様が存在しませんでした。|  
|IM003|指定されたドライバに接続できませんでした|(DM) システム情報のデータ ソース仕様に記載されているドライバが見つからないか、または他の何らかの理由で接続できませんでした。|  
|IM004|SQL_HANDLE_ENVでドライバーの SQLAllocHandle が失敗しました|(DM) **SQLConnect**の間に、ドライバー マネージャーは、ハンドル*の種類*のハンドルのSQL_HANDLE_ENVの**SQLAllocHandle**関数を呼び出し、ドライバーがエラーを返しました。|  
|IM005|SQL_HANDLE_DBCでドライバーの SQLAllocHandle が失敗しました|(DM) **SQLConnect**の間に、ドライバー マネージャーは、ハンドル*の種類*のSQL_HANDLE_DBCのハンドルを持つドライバーの**SQLAllocHandle**関数を呼び出し、ドライバーがエラーを返しました。|  
|IM006|ドライバーの SQL セットコネクトツールに失敗しました|**SQLConnect**の間に、ドライバー マネージャーは、ドライバーの**SQLSetConnectAttr**関数を呼び出し、ドライバーはエラーを返しました。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|IM009|翻訳 DLL に接続できません|ドライバは、データ ソースに指定された変換 DLL に接続できませんでした。|  
|IM010|データ ソース名が長すぎます|(DM)*\*サーバー名*がSQL_MAX_DSN_LENGTH文字より長かった。|  
|IM014|指定された DSN に、ドライバとアプリケーションのアーキテクチャの不一致が含まれています。|(DM) 32 ビット アプリケーションは、64 ビット ドライバーに接続する DSN を使用します。またはその逆も同様です。|  
|IM015|SQL_HANDLE_DBC_INFO_HANDLEでのドライバの SQLConnect の接続に失敗しました|ドライバーがSQL_ERRORを返す場合、ドライバー マネージャーは、アプリケーションにSQL_ERRORを返し、接続が失敗します。<br /><br /> SQL_HANDLE_DBC_INFO_TOKENの詳細については[、「ODBC ドライバーでの接続プール認識の開発](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)」を参照してください。|  
|IM017|非同期通知モードではポーリングが無効になっています|通知モデルを使用すると、ポーリングは無効になります。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するために呼び出されていません。|ハンドルの前の関数呼び出しがSQL_STILL_EXECUTINGを返し、通知モードが有効な場合、後処理を実行して操作を完了するために、ハンドルで**SQLCompleteAsync**を呼び出す必要があります。|  
|S1118|ドライバーは、非同期通知をサポートしていません。|ドライバーが非同期通知をサポートしていない場合は、SQL_ATTR_ASYNC_DBC_EVENTまたはSQL_ATTR_ASYNC_DBC_RETCODE_PTRを設定できません。|  
  
## <a name="comments"></a>説明  
 アプリケーションが**SQLConnect**を使用する理由については[、「SQLConnect を使用した接続](../../../odbc/reference/develop-app/connecting-with-sqlconnect.md)」を参照してください。  
  
 ドライバー マネージャーは、アプリケーションが関数 ( SQLConnect 、 **SQLDriverConnect**、または**SQLConnect****SQLBrowseConnect**) を呼び出してドライバーに接続するまで、ドライバーに接続しません。 それまでは、ドライバー マネージャーは、独自のハンドルを使用して、接続情報を管理します。 アプリケーションが接続関数を呼び出すと、ドライバー マネージャーは、指定された*ConnectionHandle*に対してドライバーが現在接続されているかどうかを確認します。  
  
-   ドライバーが接続されていない場合、ドライバー マネージャーはドライバーに接続し、SQL_HANDLE_ENVの SQL_HANDLE_DBC*ハンドル型*を使用して*HandleType***SQLAllocHandle**を呼び出します。 **SQLAllocHandle** **SQLSetConnectAttr** ドライバー マネージャーは、SQLSTATE IM006 (ドライバーの**SQLSetConnect オプション**に失敗しました) を返し、ドライバーが**SQLSetConnectAttr**のエラーを返した場合は、接続関数のSQL_SUCCESS_WITH_INFOします。 詳細については、「[データ ソースまたはドライバへの接続](../../../odbc/reference/develop-app/connecting-to-a-data-source-or-driver.md)」を参照してください。  
  
-   指定されたドライバーが接続先の*場合、既にに接続*されている場合、ドライバー マネージャーは、ドライバーの接続関数のみを呼び出します。 この場合、ドライバーは *、ConnectionHandle*のすべての接続属性が現在の設定を維持することを確認する必要があります。  
  
-   別のドライバーに接続されている場合、ドライバー マネージャーは、SQL_HANDLE_DBCの*HandleType*を使用して**SQLFreeHandle**を呼び出し、その環境で他のドライバーが接続されていない場合は、接続されているドライバーで SQL_HANDLE_ENV*ハンドルの種類*を持つ**SQLFreeHandle**を呼び出し、そのドライバーを切断します。 次に、ドライバーが接続されていないときと同じ操作を実行します。  
  
 ドライバーは、ハンドルを割り当て、それ自体を初期化します。  
  
 アプリケーションが**SQLDisconnect**を呼び出すと、ドライバー マネージャーは、ドライバーで**SQLDisconnect**を呼び出します。 ただし、ドライバは切断されません。 これにより、データ ソースに対して繰り返し接続およびデータ ソースから切断されるアプリケーションのメモリ内にドライバーが保持されます。 アプリケーションがハンドル*型*のSQL_HANDLE_DBCを使用して**SQLFreeHandle**を呼び出すと、ドライバー マネージャーはハンドル型の SQL_HANDLE_DBCハンドル*を*持つ**SQLFreeHandle**を呼び出し、ドライバーにハンドル*型*のハンドルを持つSQL_HANDLE_ENVを使用して、ドライバーを切断します。 **SQLFreeHandle**  
  
 ODBC アプリケーションは、複数の接続を確立できます。  
  
## <a name="driver-manager-guidelines"></a>ドライバー マネージャーのガイドライン  
 **ServerName*の内容は、ドライバー マネージャーとドライバーが連携してデータ ソースへの接続を確立する方法に影響します。  
  
-   \* *ServerName*に有効なデータ ソース名が含まれている場合、ドライバー マネージャーは、システム情報に対応するデータ ソースの仕様を検索し、関連付けられているドライバーに接続します。 ドライバー マネージャーは、各**SQLConnect**引数をドライバーに渡します。  
  
-   データ ソース名が見つからない場合、または*ServerName*が null ポインターの場合、ドライバー マネージャーは既定のデータ ソース仕様を検索し、関連付けられているドライバーに接続します。 ドライバー マネージャーは、*変更されていないユーザー名*と*認証*の引数、および "DEFAULT" 引数*の引数をドライバー*に渡します。  
  
-   引数*ServerName*が "DEFAULT" の場合、ドライバー マネージャーは既定のデータ ソース仕様を検索し、関連付けられているドライバーに接続します。 ドライバー マネージャーは、各**SQLConnect**引数をドライバーに渡します。  
  
-   データ ソース名が見つからないか、*または ServerName*が null ポインターであり、既定のデータ ソース仕様が存在しない場合、ドライバー マネージャーは SQLSTATE IM002 (データ ソース名が見つからず、既定のドライバーが指定されていない) とSQL_ERRORを返します。  
  
 ドライバー マネージャーによって接続された後、ドライバーは、システム情報に対応するデータ ソースの仕様を検索し、必要な接続情報のセットを完了する仕様からドライバー固有の情報を使用できます。  
  
 データ ソースのシステム情報に既定の変換ライブラリが指定されている場合、ドライバーは、その変換ライブラリに接続します。 SQL_ATTR_TRANSLATE_LIB属性を指定して**SQLSetConnectAttr**を呼び出すことで、別の変換ライブラリに接続できます。 変換オプションは、SQL_ATTR_TRANSLATE_OPTION属性を指定して**SQLSetConnectAttr**を呼び出すことによって指定できます。  
  
 ドライバーが**SQLConnect**をサポートしている場合、ドライバーのシステム情報のドライバー キーワード セクションには、最初の文字が "Y" に設定された**ConnectFunctions**キーワードが含まれている必要があります。  
  
### <a name="connection-pooling"></a>接続のプール  
 接続プールを使用すると、アプリケーションは既に作成されている接続を再利用できます。 接続プールが有効になっており **、SQLConnect**が呼び出されると、ドライバー マネージャーは、接続プール用に指定されている環境で接続のプールの一部である接続を使用して接続を作成しようとします。 この環境は、プール内の接続を使用するすべてのアプリケーションで使用される共有環境です。  
  
 接続プールは、環境が割り当てられる前に、環境が割り当てられる前に **、SQL_ATTR_CONNECTION_POOLING**をSQL_CP_ONE_PER_DRIVER (ドライバごとに最大 1 つのプールを指定) またはSQL_CP_ONE_PER_HENV (環境ごとに最大 1 つのプールを指定) に設定します。 この場合 **、SQLSetEnvAttr**は、この属性をプロセス レベルの属性に設定した*環境ハンドル*を null にして呼び出されます。 SQL_ATTR_CONNECTION_POOLINGがSQL_CP_OFFに設定されている場合、接続プールは無効になります。  
  
 接続プールが有効になると、SQL_HANDLE_ENVの*ハンドル型*を持つ**SQLAllocHandle**が呼び出され、環境が割り当てられます。 接続プールが有効になっているため、この呼び出しによって割り当てられる環境は共有環境です。 ただし、使用される環境は、*ハンドル型*のSQL_HANDLE_DBCを持つ**SQLAllocHandle**が呼び出されるまで決定されません。  
  
 SQL_HANDLE_DBCの*ハンドル型*を持つ**SQLAllocHandle**が呼び出され、接続が割り当てられます。 ドライバー マネージャーは、アプリケーションによって設定された環境属性に一致する既存の共有環境を検索しようとします。 そのような環境が存在しない場合は、 暗黙の*共有環境*として作成されます。 一致する共有環境が見つかった場合、環境ハンドルがアプリケーションに返され、その参照カウントがインクリメントされます。  
  
 ただし、使用される接続は **、SQLConnect**が呼び出されるまで決定されません。 その時点で、ドライバー マネージャーは、アプリケーションによって要求された条件に一致する接続プール内の既存の接続を検索しようとします。 これらの条件には **、SQLConnect**の呼び出しで要求された接続オプション (*サーバー名*、*ユーザー名*、および*認証*キーワードの値) と、*ハンドル型の*SQL_HANDLE_DBC を持つ**SQLAllocHandle**が呼び出された後に設定された接続属性が含まれます。 ドライバー マネージャーは、プール内の接続内の対応する接続キーワードと属性に対してこれらの条件をチェックします。 一致が見つかった場合は、プール内の接続が使用されます。 一致するものが見つからない場合は、新しい接続が作成されます。  
  
 SQL_ATTR_CP_MATCH環境属性がSQL_CP_STRICT_MATCHに設定されている場合、プール内の接続が使用される場合は、完全一致が必要です。 SQL_ATTR_CP_MATCH環境属性がSQL_CP_RELAXED_MATCHに設定されている場合 **、SQLConnect**の呼び出しで接続オプションが一致する必要がありますが、すべての接続属性が一致している必要はありません。  
  
 **SQLConnect**が呼び出される前にアプリケーションによって設定された接続属性が、プール内の接続の接続属性と一致しない場合、次の規則が適用されます。  
  
-   接続が確立される前に接続属性を設定する必要がある場合は、次の手順を実行します。  
  
     SQL_ATTR_CP_MATCHがSQL_CP_STRICT_MATCH場合、プールされた接続のSQL_ATTR_PACKET_SIZEは、アプリケーションによって設定された属性と同じでなければなりません。 SQL_CP_RELAXED_MATCH場合、SQL_ATTR_PACKET_SIZEの値は異なる場合があります。  
  
     SQL_ATTR_LOGIN_VALUEの値は、一致には影響しません。  
  
-   接続属性が接続の作成前または確立後に設定できる場合は、次の手順を実行します。  
  
     接続属性がアプリケーションによって設定されていないが、プール内の接続に設定されている場合、デフォルトがある場合、プールされた接続の接続属性はデフォルトに戻され、一致が宣言されます。 デフォルトがない場合、プールされた接続は一致と見なされません。  
  
     接続属性がアプリケーションによって設定されているが、プール内の接続に設定されていない場合、プールの接続属性は、アプリケーションによって設定された接続属性に変更され、一致が宣言されます。  
  
     接続属性がアプリケーションによって設定され、プール内の接続にも設定されているが、値が異なる場合は、アプリケーションの接続属性の値が使用され、一致が宣言されます。  
  
-   ドライバー固有の接続属性の値が同じではなく、SQL_ATTR_CP_MATCHがSQL_CP_STRICT_MATCHに設定されている場合、プール内の接続は使用されません。  
  
 アプリケーションが**SQLDisconnect**を呼び出して切断すると、接続が接続プールに戻され、再利用できるようになります。  
  
### <a name="optimizing-connection-pooling-performance"></a>接続プールのパフォーマンスの最適化  
 分散トランザクションが関係する場合は、SQLUINTEGER ビットマスクである**SQL_DTC_TRANSITION_COST**を使用して、接続プールのパフォーマンスを最適化できます。 参照される遷移は、接続属性の遷移SQL_ATTR_ENLIST_IN_DTC値 0 からゼロ以外への遷移、またはその逆の遷移です。 これは、分散トランザクションに参加していない接続から分散トランザクションに参加する接続、またはその逆の接続です。 ドライバーが参加を実装した方法 (接続属性SQL_ATTR_ENLIST_IN_DTC設定) によっては、これらの移行はコストがかかる可能性があるため、パフォーマンスを向上させるには避ける必要があります。  
  
 ドライバーによって返される値には、次のビットの任意の組み合わせが含まれています。  
  
-   **SQL_DTC_ENLIST_EXPENSIVE、** 設定すると、ゼロからゼロ以外への遷移は、ゼロ以外の値から別のゼロ以外の値への移行 (次のトランザクションに参加している接続) よりも大幅に高価であることを意味します。  
  
-   **SQL_DTC_UNENLIST_EXPENSIVE**、設定すると、ゼロ以外の遷移が、SQL_ATTR_ENLIST_IN_DTC属性が既にゼロに設定されている接続を使用するよりも、かなり高価であることを意味します。  
  
 パフォーマンスと接続の使用のトレードオフがあります。 ドライバーは、これらの移行の 1 つ以上が高価であることを示している場合、ドライバー マネージャーの接続プーラーは、プールでより多くの接続を保持することによって、これに応答します。 プール内の接続の一部は非トランザクションの使用に適しており、トランザクション用に推奨される接続もあります。 ただし、ドライバーがこれらの移行が高価ではないことを示している場合は、使用できる接続数が少なく、非トランザクションとトランザクションの使用が交互に行われる可能性があります。  
  
 SQL_ATTR_ENLIST_IN_DTCをサポートしていないドライバーは、SQL_DTC_TRANSITION_COSTをサポートする必要はありません。 SQL_ATTR_ENLIST_IN_DTCをサポートしているが、SQL_DTC_TRANSITION_COSTをサポートしていないドライバーの場合、この値に対して 0 (ビットが設定されていない) を返すかのように、移行は高価ではないと想定されます。  
  
 SQL_DTC_TRANSITION_COST ODBC 3.5 では導入されましたが、ODBC 2 は次の方法で導入されています。*x*ドライバーマネージャーは、ドライバーのバージョンに関係なく、この情報を照会するため、x ドライバーもサポートできます。  
  
### <a name="code-example"></a>コード例  
 次の例では、アプリケーションが環境ハンドルと接続ハンドルを割り当てます。 次に、ユーザー ID JohnS とパスワードの Sesame を使用して SalesOrders データ ソースに接続し、データを処理します。 データの処理が完了すると、データ ソースから切断され、ハンドルが解放されます。  
  
```cpp  
// SQLConnect_ref.cpp  
// compile with: odbc32.lib  
#include <windows.h>  
#include <sqlext.h>  
  
int main() {  
   SQLHENV henv;  
   SQLHDBC hdbc;  
   SQLHSTMT hstmt;  
   SQLRETURN retcode;  
  
   SQLCHAR * OutConnStr = (SQLCHAR * )malloc(255);  
   SQLSMALLINT * OutConnStrLen = (SQLSMALLINT *)malloc(255);  
  
   // Allocate environment handle  
   retcode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
  
   // Set the ODBC version environment attribute  
   if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
      retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (void*)SQL_OV_ODBC3, 0);   
  
      // Allocate connection handle  
      if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
         retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);   
  
         // Set login timeout to 5 seconds  
         if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
            SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)5, 0);  
  
            // Connect to data source  
            retcode = SQLConnect(hdbc, (SQLCHAR*) "NorthWind", SQL_NTS, (SQLCHAR*) NULL, 0, NULL, 0);  
  
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
  
### <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|ハンドルの割り当て|[SQLAllocHandle 関数](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|データ ソースへの接続に必要な値の検出と列挙|[SQLBrowseConnect 関数](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|  
|データ ソースからの切断|[SQLDisconnect 関数](../../../odbc/reference/syntax/sqldisconnect-function.md)|  
|接続文字列またはダイアログ ボックスを使用したデータ ソースへの接続|[SQLDriverConnect 関数](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
|接続属性の設定を返す|[SQLGetConnectAttr 関数](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|接続属性の設定|[SQLSetConnectAttr 関数](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
