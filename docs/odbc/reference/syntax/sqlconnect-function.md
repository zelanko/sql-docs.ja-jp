---
title: "SQLConnect 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLConnect
apilocation: sqlsrv32.dll
apitype: dllExport
f1_keywords: SQLConnect
helpviewer_keywords: SQLConnect function [ODBC]
ms.assetid: 59075e46-a0ca-47bf-972a-367b08bb518d
caps.latest.revision: "37"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 7bda744eb99da9f199954c6ddeb94fc9b347265b
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="sqlconnect-function"></a>SQLConnect 関数
**準拠**  
 バージョンで導入されました ODBC 1.0 標準準拠: ISO 92。  
  
 **概要**  
 **SQLConnect**ドライバーおよびデータ ソースへの接続を確立します。 接続ハンドルでは、状態、トランザクションの状態、およびエラー情報を含む、データ ソースへの接続に関するすべての情報のストレージを参照します。  
  
## <a name="syntax"></a>構文  
  
```  
  
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
 *ConnectionHandle*  
 [入力]接続ハンドルです。  
  
 *ServerName*  
 [入力]データ ソースの名前。 データをプログラムと同じコンピューター上またはネットワーク上のどこか別のコンピューター上にあることがあります。 アプリケーションがデータ ソースを選択する方法については、次を参照してください。[データ ソースまたはドライバーを選択する](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md)です。  
  
 *NameLength1*  
 [入力]長さ **ServerName*文字です。  
  
 *UserName*  
 [入力]ユーザーの識別子です。  
  
 *NameLength2*  
 [入力]長さ **UserName*文字です。  
  
 *[認証]*  
 [入力]認証の文字列 (通常はパスワード)。  
  
 *NameLength3*  
 [入力]長さ **認証*文字です。  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、SQL_INVALID_HANDLE、または SQL_STILL_EXECUTING です。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLConnect** SQL_ERROR または SQL_SUCCESS_WITH_INFO、関連付けられた SQLSTATE 値を返しますを呼び出すことによって取得できます**SQLGetDiagRec**で、 *HandleType* sql _ のHANDLE_DBC と*処理*の*ConnectionHandle*です。 次の表に、によって通常返される SQLSTATE 値**SQLConnect**です。 この関数のコンテキストでは、各フォルダーについて説明しますと表記"(DM)"の前に、ドライバー マネージャーによって返される SQLSTATEs の説明。 SQLSTATE 値ごとに関連付けられている戻り値のコードは、特に明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|Description|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01S02|オプション値が変更されました|ドライバーが指定した値をサポートしていません、 *ValuePtr*引数**SQLSetConnectAttr**と同様の値を置換します。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|08001|クライアント接続を確立できません。|ドライバーは、データ ソースとの接続を確立できませんでした。|  
|08002|使用されている接続名|(DM)、指定した*ConnectionHandle*データ ソースとの接続と接続がまだ開かれていた、ユーザーがのや閲覧に接続を確立するために既に使用されていました。|  
|08004|サーバー接続を拒否しました|データ ソースには、実装定義上の理由から、接続の確立が拒否されました。|  
|08S01|通信リンクが失敗しました|関数は完了しました処理する前に、ドライバーとするドライバーが接続しようとするデータ ソース間の通信リンクが失敗しました。|  
|28000|無効な権限の指定|引数が指定された値*UserName*または引数が指定された値*認証*データ ソースで定義された制限に違反します。|  
|HY000|一般的なエラー|存在しなかった固有の SQLSTATE となる実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、  *\*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリ割り当てエラー|ドライバー マネージャーは、(DM) は、実行や、関数の終了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作が取り消されました|非同期処理が有効で、 *ConnectionHandle*です。 **SQLConnect**関数が呼び出され、実行を完了する前に[SQLCancelHandle 関数](../../../odbc/reference/syntax/sqlcancelhandle-function.md)で呼び出されましたが、 *ConnectionHandle*、およびし**SQLConnect**関数がもう一度、 *ConnectionHandle*です。<br /><br /> また、 **SQLConnect**関数が呼び出され、実行を完了する前に**SQLCancelHandle**で呼び出されましたが、 *ConnectionHandle*の別のスレッドから、マルチ スレッド アプリケーションです。|  
|HY010|関数のシーケンス エラー|(DM) の非同期的に実行中の関数 (いないこの 1 つ) が呼び出された、 *ConnectionHandle*この関数が呼び出されたときに実行されているとします。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、可能性のあるメモリ不足の状況が原因であるために、関数呼び出しを処理できませんでした。|  
|HY090|文字列またはバッファーの長さが無効です。|引数に指定された値 (DM) *NameLength1*、 *NameLength2*、または*NameLength3* SQL_NTS に等しくないが、0 より小さいをでした。<br /><br /> 引数の指定された値 (DM) *NameLength1*データ ソース名の最大長を超えています。|  
|HYT00|タイムアウトが発生しました|完了したデータ ソースに接続する前に、クエリのタイムアウト期間が期限切れです。 によって、タイムアウト期間が設定されている**SQLSetConnectAttr**、SQL_ATTR_LOGIN_TIMEOUT です。|  
|HY114|ドライバーは接続レベルの非同期関数の実行をサポートしていません|(DM) アプリケーションは、接続を確立する前に、接続ハンドルでの非同期操作を有効にします。 ただし、ドライバーは接続ハンドルで、非同期操作をサポートしていません。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続タイムアウト期間が期限切れです。 によって、接続タイムアウト期間が設定されている**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT です。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) データ ソース名で指定されたドライバーは、関数をサポートしていません。|  
|IM002|データ ソースが見つかりません、指定された既定のドライバー|(DM)、データ ソース名が、引数で指定された*ServerName*システム情報に見つからなかったも存在していた既定ドライバー仕様です。|  
|IM003|指定されたドライバーに接続できませんでした。|(DM) データに、ドライバーが表示されているシステム情報の送信元仕様が見つからなかったか、でしたに接続されていないその他の何らかの理由。|  
|IM004|ドライバーの SQLAllocHandle SQL_HANDLE_ENV に失敗しました|(DM) 中に**SQLConnect**、ドライバー マネージャーがドライバーのと呼ばれる**SQLAllocHandle**で機能、 *HandleType* SQL_HANDLE_ENV とドライバーのエラーが返されました。|  
|IM005|ドライバーの SQLAllocHandle sql_handle_dbc としてに失敗しました|(DM) 中に**SQLConnect**、ドライバー マネージャーがドライバーのと呼ばれる**SQLAllocHandle**で機能、 *HandleType* sql_handle_dbc としてとドライバーのエラーが返されました。|  
|IM006|ドライバーの SQLSetConnectAttr できませんでした。|中に**SQLConnect**、ドライバー マネージャーがドライバーのと呼ばれる**SQLSetConnectAttr**関数と、ドライバーにエラーが返されます。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|IM009|トランスレーター DLL に接続できません。|ドライバーは、変換、データ ソースの指定された DLL に接続できませんでした。|  
|IM010|データ ソース名が長すぎます|(DM)  *\*ServerName* SQL_MAX_DSN_LENGTH 文字より長くなっています。|  
|IM014|指定の DSN にはなアーキテクチャと一致しないドライバーとアプリケーションが含まれています|(DM) 32 ビット アプリケーションでは、64 ビット ドライバー; に接続する DSN を使用します。またはその逆です。|  
|IM015|ドライバーの SQLConnect SQL_HANDLE_DBC_INFO_HANDLE に失敗しました|ドライバーでは、SQL_ERROR が返された場合、ドライバー マネージャーは、アプリケーションに SQL_ERROR を返し、接続は失敗します。<br /><br /> SQL_HANDLE_DBC_INFO_TOKEN の詳細については、次を参照してください。 [ODBC ドライバーで接続プールの認識開発](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)です。|  
|IM017|非同期通知モードでのポーリングが無効になっています|通知のモデルを使用するとは、ポーリングは無効です。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するが呼び出されていません。|ハンドルに対する前の関数呼び出しに SQL_STILL_EXECUTING が返された場合、および通知モードが有効になっている**SQLCompleteAsync**ハンドルの後処理を行い、操作を完了するに呼び出せる必要があります。|  
|S1118|ドライバーは非同期通知をサポートしていません|ドライバーが非同期通知をサポートしていない場合は、SQL_ATTR_ASYNC_DBC_EVENT または SQL_ATTR_ASYNC_DBC_RETCODE_PTR を設定できません。|  
  
## <a name="comments"></a>コメント  
 理由については、アプリケーションを使用して**SQLConnect**を参照してください[SQLConnect による接続](../../../odbc/reference/develop-app/connecting-with-sqlconnect.md)です。  
  
 アプリケーションが、関数を呼び出すまで、ドライバー マネージャーがドライバーに接続できません (**SQLConnect**、 **SQLDriverConnect**、または**SQLBrowseConnect**) への接続にはドライバーです。 その時点まで、ドライバー マネージャーは、独自の処理と連携し、接続情報を管理します。 アプリケーションが接続関数を呼び出すと、ドライバー マネージャーは、ドライバーが、指定された現在に接続しているかどうかを確認*ConnectionHandle*:  
  
-   呼び出し、ドライバー、ドライバー マネージャーの接続には、ドライバーは接続されていない場合、 **SQLAllocHandle**で、 *HandleType* SQL_HANDLE_ENV の**SQLAllocHandle**で、*HandleType* sql_handle_dbc としての**SQLSetConnectAttr** (かどうかアプリケーション指定された任意の接続属性)、およびドライバーの接続関数。 ドライバー マネージャーは、SQLSTATE IM006 を返します (ドライバーの**SQLSetConnectOption**に失敗しました) と、ドライバーのエラーを返した場合、接続関数の SQL_SUCCESS_WITH_INFO **SQLSetConnectAttr**です。 詳細については、次を参照してください。[データ ソースまたはドライバーに接続する](../../../odbc/reference/develop-app/connecting-to-a-data-source-or-driver.md)です。  
  
-   指定されたドライバーが既にオンに接続されている場合、 *ConnectionHandle*、ドライバー マネージャーがドライバーの接続関数のみを呼び出します。 ここでは、ドライバーは必ず属性用のすべての接続、 *ConnectionHandle*その現在の設定を維持します。  
  
-   別のドライバーが接続されている場合、ドライバー マネージャーを呼び出す**SQLFreeHandle**で、 *HandleType*の sql_handle_dbc として、その他のドライバーが接続されていない場合にその環境で、これを呼び出して**SQLFreeHandle**で、 *HandleType* SQL_HANDLE_ENV に接続されているドライバーの後、そのドライバーを切断します。 ドライバーに接続されていない場合と同じ操作を実行します。  
  
 ドライバーは、ハンドルを割り当て、自体を初期化します。  
  
 アプリケーションを呼び出すと**SQLDisconnect**、ドライバー マネージャー呼び出し**SQLDisconnect**ドライバーにします。 ただし、ドライバーは切断されません。 繰り返しに接続し、データ ソースから切断するアプリケーションのメモリ内にあるドライバーが保持します。 アプリケーションを呼び出すと**SQLFreeHandle**で、 *HandleType*ドライバー マネージャーを呼び出し、sql_handle_dbc としての**SQLFreeHandle**で、 *HandleType* sql_handle_dbc としてのし**SQLFreeHandle**で、 *HandleType* driver では、SQL_HANDLE_ENV のと、ドライバーを切断します。  
  
 ODBC アプリケーションでは、複数の接続を確立できます。  
  
## <a name="driver-manager-guidelines"></a>ドライバー マネージャーのガイドライン  
 内容 **ServerName*ドライバー マネージャーとドライバーがどのように連携して、データ ソースへの接続を確立するには影響します。  
  
-   場合\* *ServerName*有効なデータ ソース名を含むドライバー マネージャーがシステム情報に対応するデータ ソースの指定を検索し、関連するドライバーに接続します。 ドライバー マネージャーに渡す各**SQLConnect**ドライバーに渡す引数。  
  
-   データ ソース名が見つからない場合、または*ServerName* null ポインターでは、ドライバー マネージャーは、既定のデータ ソースの指定を検索し、関連するドライバーに接続します。 ドライバー マネージャーがドライバーに渡します、 *UserName*と*認証*くだ、引数と"DEFAULT"を*ServerName*引数。  
  
-   場合、 *ServerName*引数が"DEFAULT"では、ドライバー マネージャーは、既定のデータ ソースの指定を検索し、関連するドライバーに接続します。 ドライバー マネージャーに渡す各**SQLConnect**ドライバーに渡す引数。  
  
-   データ ソース名が見つからない場合、または*ServerName*は null ポインターであり、既定のデータ ソースの指定が存在しない、ドライバー マネージャーは、SQLSTATE IM002 で SQL_ERROR が返されます (データ ソース名が見つかりません既定値はありません。指定されたドライバー)。  
  
 接続されているドライバー マネージャーによって後、ドライバーことができます、対応するデータ ソースの指定 システム情報を見つけて仕様からドライバー固有の情報を使用して、必要な接続情報のセットを完了します。  
  
 データ ソースのシステム情報 の既定の変換ライブラリを指定すると、ドライバーはそれに接続します。 呼び出して、別の翻訳ライブラリに接続できる**SQLSetConnectAttr** SQL_ATTR_TRANSLATE_LIB 属性を持つ。 呼び出して変換オプションを指定できます**SQLSetConnectAttr** SQL_ATTR_TRANSLATE_OPTION 属性を持つ。  
  
 ドライバーがサポートする場合は**SQLConnect**のシステム情報、ドライバーをドライバー キーワード セクションに含める必要があります、 **ConnectFunctions**キーワードの最初の文字"Y"に設定  
  
### <a name="connection-pooling"></a>接続のプール  
 接続プールと、アプリケーションを既に作成されている接続を再利用ができます。 接続プールが有効な場合と**SQLConnect**が呼び出されると、ドライバー マネージャーの接続プールに指定されている環境での接続のプールの一部である接続を使用して接続しよう。 この環境は、プールで接続を使用するすべてのアプリケーションによって使用される共有環境です。  
  
 接続プールが有効になっている環境が呼び出すことによって割り当てられる前に**SQLSetEnvAttr** (ドライバーごとに 1 つのプールの最大数を指定する) を SQL_CP_ONE_PER_DRIVER または SQL_CP_ONE_PER_HENV SQL_ATTR_CONNECTION_POOLING を設定するには(環境ごとに 1 つのプールの最大数を指定します。) **SQLSetEnvAttr**でこのケースで呼び出された*EnvironmentHandle*プロセス レベルの属性の属性を null に設定します。 SQL_ATTR_CONNECTION_POOLING を SQL_CP_OFF に設定すると、接続プールは無効になります。  
  
 接続プールは有効になっている、 **SQLAllocHandle**で、 *HandleType* sql_handle_env としては、環境を割り当てると呼ばれます。 この呼び出しによって割り当てられる環境は、接続プールを有効になっているために、共有環境です。 ただし、使用される環境をまで特定されないこと**SQLAllocHandle**で、 *HandleType* sql_handle_dbc としてのと呼びます。  
  
 **SQLAllocHandle**で、 *HandleType* sql_handle_dbc としては、接続の割り当てに呼び出されます。 ドライバー マネージャーは、アプリケーションによって設定される環境属性に一致する既存の共有環境を見つけようとします。 このような環境が存在しない場合、暗黙の型として作成されます*共有環境*です。 一致する共有環境が見つかった場合、環境ハンドルは、アプリケーションに返され、参照カウントがインクリメントされます。  
  
 ただし、使用される接続をまで特定されないこと**SQLConnect**と呼びます。 その時点では、ドライバー マネージャーは、アプリケーションによって要求された条件に一致する接続プール内の既存の接続を検索しようとします。 これらの条件がへの呼び出しで要求されている接続オプションを含める**SQLConnect** (の値、 *ServerName*、 *UserName*、および*認証*キーワード) から任意の接続属性を設定および**SQLAllocHandle**で、 *HandleType* sql_handle_dbc としてが呼び出されました。 ドライバー マネージャーでは、これらの条件に対して、対応する接続キーワードと、プール内の接続での属性を確認します。 一致が見つかった場合、プール内の接続は使用されます。 一致するものが見つからない場合は、新しい接続が作成されます。  
  
 SQL_ATTR_CP_MATCH 環境属性が SQL_CP_STRICT_MATCH に設定されている場合、一致は、プールで使用する接続のための正確なである必要があります。 SQL_ATTR_CP_MATCH 環境属性が SQL_CP_RELAXED_MATCH に設定されている場合、接続オプションへの呼び出し**SQLConnect**必要がありますが、一致する、すべての接続属性と一致しなければなりません。  
  
 次の規則は前に、アプリケーションによって設定されたときに、接続属性を適用は**SQLConnect**を呼び出すと、プール内の接続の接続属性と一致しません。  
  
-   場合は、接続が行われる前に、接続属性を設定する必要があります。  
  
     SQL_ATTR_CP_MATCH が SQL_CP_STRICT_MATCH の場合は、プールされた接続で SQL_ATTR_PACKET_SIZE がアプリケーションによって設定された属性と同じでなければなりません。 SQL_CP_RELAXED_MATCH、SQL_ATTR_PACKET_SIZE の値を別にすることができます。 場合、  
  
     SQL_ATTR_LOGIN_VALUE の値では、一致は影響しません。  
  
-   場合は、接続の確立後または前に、接続属性を設定できます。  
  
     接続属性が、アプリケーションが設定されていませんが、プール内に、接続が設定されて、既定値がある場合は、プールされた接続で接続の属性は、既定値に戻さし、一致するものが宣言されています。 既定値がない場合は、プールされた接続には一致するものはありません。  
  
     接続属性が、アプリケーションによって設定されているプールの接続に設定されていない場合は、プールの接続属性は、アプリケーションによってそのセットに変更し、一致するものが宣言されています。  
  
     接続属性が、アプリケーションで設定されているし、プール内の接続に設定されても、値が異なる場合は、アプリケーションの接続属性の値が使用され、一致するものが宣言されています。  
  
-   ドライバー固有の接続属性の値が同一でない SQL_ATTR_CP_MATCH が SQL_CP_STRICT_MATCH に設定されている場合は、プール内の接続は使用されません。  
  
 アプリケーションを呼び出すと**SQLDisconnect**切断するには、接続が接続プールに返されが再利用します。  
  
### <a name="optimizing-connection-pooling-performance"></a>接続プールのパフォーマンスを最適化します。  
 接続プールを使用してのパフォーマンスを最適化することは、分散トランザクションが関係しているときに**SQL_DTC_TRANSITION_COST**、SQLUINTEGER ビットマスクであります。 参照される遷移は、接続属性に 0 以外の値が 0 から移動 SQL_ATTR_ENLIST_IN_DTC の遷移と、その逆です。 これからの接続に参加しませんに分散トランザクションと分散トランザクションに参加しています。 どのドライバーが参加リスト (接続属性を設定 SQL_ATTR_ENLIST_IN_DTC) を実装によっては、それらの遷移は、高価な場合があり、したがって最適なパフォーマンスを避ける必要があります。  
  
 ドライバーによって返される値には、次のビットの任意の組み合わせが含まれています。  
  
-   **SQL_DTC_ENLIST_EXPENSIVE**ときに、設定、0 以外の遷移にゼロが 0 以外の値から別の 0 以外の値 (次のトランザクションで以前に参加している接続の参加) への移行よりも大幅に高くことを意味します。  
  
-   **SQL_DTC_UNENLIST_EXPENSIVE**ときに、設定、SQL_ATTR_ENLIST_IN_DTC 属性設定されているが既に 0 に接続を使用するよりも大幅に高く、0 以外の値をゼロ遷移は、ことを意味します。  
  
 これは、パフォーマンスと接続使用状況トレードオフを調整します。 ドライバーが 1 つ以上これらの遷移が高価なことを示している場合、ドライバー マネージャーの接続プーラーはプール内のより多くの接続を保持することでこれに応答します。 接続プール内の一部は、優先的に非トランザクションの使用、いくつかトランザクションでの使用をお勧めします。 ただし場合は、ドライバーは、それらの遷移が高コストでないことを示します、接続数を使用できます、非トランザクションとトランザクションの使用が交互など。  
  
 SQL_ATTR_ENLIST_IN_DTC をサポートしていないドライバーは、SQL_DTC_TRANSITION_COST をサポートする必要はありません。 SQL_ATTR_ENLIST_IN_DTC がない SQL_DTC_TRANSITION_COST をサポートするドライバーは、切り替え効果になっているドライバーにはこの値の 0 (ビットが設定されていない) が返される場合は、高価なものとします。  
  
 SQL_DTC_TRANSITION_COST は、ODBC 3.5 では、ODBC 2 で導入されました。*x*ドライバーもサポートできますが、ドライバー マネージャーがドライバーのバージョンに関係なく、この情報をクエリがあるためです。  
  
### <a name="code-example"></a>コード例  
 次の例では、アプリケーションが割り当てられます環境と接続ハンドルです。 ユーザー ID ジョンズを使用して SalesOrders データ ソースと黒のパスワードに接続し、データを処理します。 これには、データの処理が完了したら、そのデータ ソースから切断し、ハンドルを解放します。  
  
```  
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
  
|詳細|参照先|  
|---------------------------|---------|  
|ハンドルの割り当てください。|[SQLAllocHandle 関数](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|検出して、データ ソースへの接続に必要な値を列挙します。|[SQLBrowseConnect 関数](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|  
|データ ソースからの切断|[SQLDisconnect 関数](../../../odbc/reference/syntax/sqldisconnect-function.md)|  
|接続文字列やダイアログ ボックスを使用してデータ ソースに接続します。|[SQLDriverConnect 関数](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
|接続属性の設定値を返す|[SQLGetConnectAttr 関数](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|接続属性の設定|[SQLSetConnectAttr 関数](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
