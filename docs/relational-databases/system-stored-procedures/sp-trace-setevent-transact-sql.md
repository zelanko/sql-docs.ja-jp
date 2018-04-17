---
title: sp_trace_setevent (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_trace_setevent_TSQL
- sp_trace_setevent
dev_langs:
- TSQL
helpviewer_keywords:
- sp_trace_setevent
ms.assetid: 7662d1d9-6d0f-443a-b011-c901a8b77a44
caps.latest.revision: 49
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: bf4e3f645a8480104fcb6f67790563fbb05d0480
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sptracesetevent-transact-sql"></a>sp_trace_setevent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  トレースに対して、イベントまたはイベント列を追加または削除します。 **sp_trace_setevent**停止している既存のトレースに対してのみ実行できます (*ステータス*は**0**)。 エラーが返されます場合、このストアド プロシージャが存在しないトレースまたはで実行される*ステータス*は**0**します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 代わりに拡張イベントを使用します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_trace_setevent [ @traceid = ] trace_id   
          , [ @eventid = ] event_id  
          , [ @columnid = ] column_id  
          , [ @on = ] on  
```  
  
## <a name="arguments"></a>引数  
 [ **@traceid=** ] *trace_id*  
 変更するトレースの ID を指定します。 *trace_id*は**int**、既定値はありません。 ユーザーが使用してこの*trace_id*識別、変更、およびトレースを制御する値。  
  
 [ **@eventid=** ] *event_id*  
 有効にするイベントの ID を指定します。 *event_id*は**int**、既定値はありません。  
  
 次の表は、トレースに対して追加または削除できるイベントの一覧です。  
  
|イベント番号|イベント名|Description|  
|------------------|----------------|-----------------|  
|0-9|予約済み。|予約済み。|  
|10|RPC:Completed|リモート プロシージャ呼び出し (RPC) が完了したときに発生します。|  
|11|RPC:Starting|RPC が開始したときに発生します。|  
|12|SQL:BatchCompleted|発生したときに、[!INCLUDE[tsql](../../includes/tsql-md.md)]のバッチが完了します。|  
|13|SQL:BatchStarting|[!INCLUDE[tsql](../../includes/tsql-md.md)] バッチが開始したときに発生します。|  
|14|Audit Login|ユーザーが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に正常にログオンしたときに発生します。|  
|15|Audit Logout|ユーザーが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からログアウトしたときに発生します。|  
|16|Attention|クライアントの割り込み要求や中断されたクライアント接続などのアテンション イベントが発生したときに発生します。|  
|17|ExistingConnection|トレースの開始前から [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続しているユーザーのすべての利用状況を検出します。|  
|18|Audit Server Starts and Stops|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスの状態が変更されたときに発生します。|  
|19|DTCTransaction|複数のデータベース間で、[!INCLUDE[msCoName](../../includes/msconame-md.md)] 分散トランザクション コーディネーター (MS DTC) によってコーディネートされたトランザクションを追跡します。|  
|20|Audit Login Failed|クライアントから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] へのログイン試行が失敗したことを示します。|  
|21|EventLog|イベントが Windows アプリケーション ログに記録されたことを示します。|  
|22|ErrorLog|エラー イベントが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログに記録されたことを示します。|  
|23|Lock:Released|ページなどのリソースのロックが解除されたことを示します。|  
|24|Lock:Acquired|データ ページなどのリソースのロックが取得されたことを示します。|  
|25|Lock:Deadlock|2 つの同時実行トランザクションが、互いに相手のトランザクションが所有するリソースをロックしようとして実現できず、デッドロックに陥ったことを示します。|  
|26|Lock:Cancel|デッドロックなどによって、リソースのロックの取得が取り消されたことを示します。|  
|27|Lock:Timeout|ページなどのリソースのロックが要求されたが、他のトランザクションによってそのリソースのブロッキング ロックが保持されているため、要求がタイムアウトになったことを示します。 タイムアウトはによって決定されます、@@LOCK_TIMEOUT関数、および SET LOCK_TIMEOUT ステートメントで設定することができます。|  
|28|Degree of Parallelism Event (7.0 Insert)|SELECT、INSERT、または UPDATE ステートメントが実行される前に発生します。|  
|29-31|予約済み。|代わりにイベント 28 を使用してください。|  
|32|予約済み。|予約済み。|  
|33|例外|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で例外が発生したことを示します。|  
|34|SP:CacheMiss|ストアド プロシージャがプロシージャ キャッシュ内にないことを示します。|  
|35|SP:CacheInsert|プロシージャ キャッシュにアイテムが挿入されたことを示します。|  
|36|SP:CacheRemove|プロシージャ キャッシュからアイテムが削除されたことを示します。|  
|37|SP:Recompile|ストアド プロシージャが再コンパイルされたことを示します。|  
|38|SP:CacheHit|ストアド プロシージャがプロシージャ キャッシュ内にあることを示します。|  
|39|廃止予定|廃止予定|  
|40|SQL:StmtStarting|発生したときに、[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントが開始します。|  
|41|SQL:StmtCompleted|発生したときに、[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントが完了しました。|  
|42|SP:Starting|ストアド プロシージャが開始されたことを示します。|  
|43|SP:Completed|ストアド プロシージャが完了したことを示します。|  
|44|SP:StmtStarting|示します、[!INCLUDE[tsql](../../includes/tsql-md.md)]ストアド プロシージャ内のステートメントが実行を開始します。|  
|45|SP:StmtCompleted|ストアド プロシージャ内の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントの実行が完了したことを示します。|  
|46|Object:Created|CREATE INDEX、CREATE TABLE、CREATE DATABASE などのステートメントで、オブジェクトが作成されたことを示します。|  
|47|Object:Deleted|DROP INDEX や DROP TABLE などのステートメントで、オブジェクトが削除されたことを示します。|  
|48|予約済み。||  
|49|予約済み。||  
|50|SQL Transaction|トラック[!INCLUDE[tsql](../../includes/tsql-md.md)]BEGIN、COMMIT、SAVE、および ROLLBACK TRANSACTION ステートメント。|  
|51|Scan:Started|テーブル スキャンまたはインデックス スキャンが開始されたことを示します。|  
|52|Scan:Stopped|テーブル スキャンまたはインデックス スキャンが停止したことを示します。|  
|53|CursorOpen|[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントで、ODBC、OLE DB、または DB-Library によりカーソルがオープンされたことを示します。|  
|54|TransactionLog|トランザクションがいつトランザクション ログに書き込まれるかを追跡します。|  
|55|Hash Warning|バッファー パーティション上で処理されていないハッシュ演算 (ハッシュ結合、ハッシュ集計、ハッシュ ユニオン、ハッシュ識別など) が代替プランに変更されたことを示します。 これは、再帰深度、データ スキュー、トレース フラグ、またはビット カウンティングが原因で発生します。|  
|56-57|予約済み。||  
|58|Auto Stats|インデックス統計の自動更新が実行されたことを示します。|  
|59|Lock:Deadlock Chain|デッドロックにつながる個々のイベントに対して生成されます。|  
|60|Lock:Escalation|ページ ロックが TABLE ロックまたは HoBT ロックにエスカレートまたは変換された場合など、細かい単位のロックが大きな単位のロックに変換されたことを示します。|  
|61|OLE DB Errors|OLE DB エラーが発生したことを示します。|  
|62-66|予約済み。||  
|67|Execution Warnings|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ステートメントまたはストアド プロシージャの実行中に発生した警告を示します。|  
|68|Showplan Text (Unencoded)|実行された [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントのプラン ツリーを表示します。|  
|69|Sort Warnings|メモリの中に収まらない並べ替え操作を示します。 インデックスの作成に関連する並べ替え操作は対象になりません。SELECT ステートメントで使用される ORDER BY 句など、クエリ内の並べ替え操作のみが対象になります。|  
|70|CursorPrepare|カーソルを示す、[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントは使用 ODBC、OLE DB、または Db-library によって準備します。|  
|71|Prepare SQL|ODBC、OLE DB、または Db-library では準備、[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントまたはステートメントを使用します。|  
|72|Exec Prepared SQL|ODBC、OLE DB、または DB-Library によって、準備された 1 つ以上の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントが実行されたことを示します。|  
|73|Unprepare SQL|ODBC、OLE DB、または Db-library が準備解除 (削除)、準備された[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントまたはステートメントです。|  
|74|CursorExecute|[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントで ODBC、OLE DB、または DB-Library によって準備されたカーソルが実行されたことを示します。|  
|75|CursorRecompile|[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントで ODBC または DB-Library によってオープンされていたカーソルが、直接再コンパイルされたか、またはスキーマが変更されたために再コンパイルされたことを示します。<br /><br /> これは ANSI および非 ANSI のカーソルの場合に発生します。|  
|76|CursorImplicitConversion|上でカーソル、[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントは、によって変換[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を別の 1 つの型からです。<br /><br /> これは ANSI および非 ANSI のカーソルの場合に発生します。|  
|77|CursorUnprepare|[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントで準備されたカーソルが、ODBC、OLE DB、または DB-Library によって削除されたことを示します。|  
|78|CursorClose|カーソルがオープンされていた、 [!INCLUDE[tsql](../../includes/tsql-md.md)] ODBC、OLE DB、または Db-library によってステートメントが終了します。|  
|79|Missing Column Statistics|オプティマイザーに有効な列の統計が利用できません。|  
|80|Missing Join Predicate|結合の述語がないクエリが実行されています。 クエリの終了に時間がかかる可能性があります。|  
|81|Server Memory Change|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] メモリ使用量が増加または減少 1 メガバイト (MB) または最大サーバー メモリの 5% のいずれか、大きい方です。|  
|82-91|User Configurable (0-9)|ユーザー定義のイベント データです。|  
|92|Data File Auto Grow|データ ファイルがサーバーによって自動的に拡張されたことを示します。|  
|93|Log File Auto Grow|ログ ファイルがサーバーによって自動的に拡張されたことを示します。|  
|94|Data File Auto Shrink|データ ファイルがサーバーによって自動的に圧縮されたことを示します。|  
|95|Log File Auto Shrink|ログ ファイルがサーバーによって自動的に圧縮されたことを示します。|  
|96|Showplan Text|クエリ オプティマイザーの SQL ステートメントのクエリ プラン ツリーを表示します。 なお、 **TextData**列にこのイベントの Showplan が含まれていません。|  
|97|Showplan All|クエリ プランを、実行された SQL ステートメントのコンパイル時の完全な詳細と共に表示します。 なお、 **TextData**列にこのイベントの Showplan が含まれていません。|  
|98|Showplan Statistics Profile|クエリ プランを、実行された SQL ステートメントの実行時の完全な詳細と共に表示します。 なお、 **TextData**列にこのイベントの Showplan が含まれていません。|  
|99|予約済み。||  
|100|RPC Output Parameter|各 RPC に対して、パラメーターの出力値を生成します。|  
|101|予約済み。||  
|102|Audit Database Scope GDR|データベースに対する権限の許可などのデータベース限定の操作時に、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の任意のユーザーがステートメント権限の GRANT、DENY、REVOKE を実行するたびに発生します。|  
|103|Audit Object GDR Event|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の任意のユーザーがオブジェクト権限の GRANT、DENY、REVOKE を実行するたびに発生します。|  
|104|Audit AddLogin Event|発生したときに、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインが追加または削除の**sp_addlogin**と**sp_droplogin**です。|  
|105|Audit Login GDR Event|Windows ログインの権利が追加または削除されたときに発生します。**sp_grantlogin**、 **sp_revokelogin**、および**sp_denylogin**です。|  
|106|Audit Login Change Property Event|パスワードを除く、ログインのプロパティが変更されたときに発生します。**sp_defaultdb**と**sp_defaultlanguage**です。|  
|107|Audit Login Change Password Event|発生したときに、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインのパスワードを変更します。<br /><br /> パスワードは記録されません。|  
|108|Audit Add Login to Server Role Event|ログインが追加または固定サーバー ロール; から削除されたときに発生します。**sp_addsrvrolemember**、および**sp_dropsrvrolemember**です。|  
|109|Audit Add DB User Event|ログインが追加またはデータベース ユーザーとして削除されたときに発生 (Windows または[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]); のデータベースに**sp_grantdbaccess**、 **sp_revokedbaccess**、 **sp_adduser**、および**sp_dropuser**です。|  
|110|Audit Add Member to DB Role Event|場合に、ログインが追加または削除 (固定またはユーザー定義) は、データベース ユーザーとしてデータベースです。**sp_addrolemember**、 **sp_droprolemember の各**、および**sp_changegroup**です。|  
|111|Audit Add Role Event|ログインが追加またはデータベースにデータベース ユーザーとして削除されたときに発生します。**sp_addrole**と**sp_droprole**です。|  
|112|Audit App Role Change Password Event|アプリケーション ロールのパスワードが変更されたときに発生します。|  
|113|Audit Statement Permission Event|CREATE TABLE などのステートメント権限が使用されたときに発生します。|  
|114|Audit Schema Object Access Event|SELECT などのオブジェクト権限が使用されたときに、それが成功したかどうかに関係なく発生します。|  
|115|Audit Backup/Restore Event|BACKUP または RESTORE コマンドが実行されたときに発生します。|  
|116|Audit DBCC Event|DBCC コマンドが実行されたときに発生します。|  
|117|Audit Change Audit Event|監査トレースが変更されたときに発生します。|  
|118|Audit Object Derived Permission Event|CREATE、ALTER、および DROP のオブジェクト コマンドが実行されたときに発生します。|  
|119|OLEDB Call Event|分散クエリとリモート ストアド プロシージャに対して、OLE DB プロバイダー呼び出しが行われたときに発生します。|  
|120|OLEDB QueryInterface Event|Ole DB **QueryInterface**分散クエリやリモート ストアド プロシージャの呼び出しは行われます。|  
|121|OLEDB DataRead Event|OLE DB プロバイダーに対して、データ要求の呼び出しが行われたときに発生します。|  
|122|Showplan XML|SQL ステートメントが実行されたときに発生します。 プラン表示演算子を識別するために、このイベントが含まれます。 各イベントは、整形式の XML ドキュメントに格納されます。 なお、**バイナリ**列でこのイベントにエンコードされたプラン表示が含まれています。 トレースを開いてプラン表示を確認するには、SQL Server Profiler を使用します。|  
|123|SQL:FullTextQuery|フルテキスト クエリが実行されたときに発生します。|  
|124|Broker:Conversation|進行状況を報告、[!INCLUDE[ssSB](../../includes/sssb-md.md)]メッセージ交換します。|  
|125|Deprecation Announcement|将来のバージョンから削除される機能を使用するときに発生[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。|  
|126|Deprecation Final Support|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の次の主要なリリースで削除される予定の機能を使用したときに発生します。|  
|127|Exchange Spill Event|並列クエリ プランの通信バッファーが一時的に書き込まれたときに発生、 **tempdb**データベース。|  
|128|Audit Database Management Event|データベースが作成、変更、または削除されたときに発生します。|  
|129|Audit Database Object Management Event|スキーマなどのデータベース オブジェクトで、CREATE、ALTER、または DROP ステートメントが実行されたときに発生します。|  
|130|Audit Database Principal Management Event|データベースに対して、ユーザーなどのプリンシパルが作成、変更、または削除されたときに発生します。|  
|131|Audit Schema Object Management Event|サーバー オブジェクトが作成、変更、または削除されたときに発生します。|  
|132|Audit Server Principal Impersonation Event|サーバー スコープ内で、EXECUTE AS LOGIN などの権限借用があるときに発生します。|  
|133|Audit Database Principal Impersonation Event|データベース スコープ内で、EXECUTE AS USER や SETUSER などの権限借用が発生したときに発生します。|  
|134|Audit Server Object Take Ownership Event|サーバー スコープ内のオブジェクトの所有者が変更されたときに発生します。|  
|135|Audit Database Object Take Ownership Event|データベース スコープ内のオブジェクトの所有者が変更されたときに発生します。|  
|136|Broker:Conversation Group|[!INCLUDE[ssSB](../../includes/sssb-md.md)] によって、新しいメッセージ交換グループが作成されたか、既存のメッセージ交換グループが削除されたときに発生します。|  
|137|Blocked Process Report|指定した時間以上プロセスがブロックされたときに発生します。 システム プロセスや、デッドロックを検出できないリソースで待機しているプロセスはこの対象外です。 使用して**sp_configure**レポートを生成するしきい値と頻度を構成します。|  
|138|Broker:Connection|[!INCLUDE[ssSB](../../includes/sssb-md.md)] によって管理される転送接続の状態をレポートします。|  
|139|Broker:Forwarded Message Sent|[!INCLUDE[ssSB](../../includes/sssb-md.md)] によってメッセージが転送されたときに発生します。|  
|140|Broker:Forwarded Message Dropped|[!INCLUDE[ssSB](../../includes/sssb-md.md)] によって転送予定のメッセージが削除されたときに発生します。|  
|141|Broker:Message Classify|[!INCLUDE[ssSB](../../includes/sssb-md.md)] でメッセージのルーティングが決定されたときに発生します。|  
|142|Broker:Transmission|エラーが発生したことを示します、[!INCLUDE[ssSB](../../includes/sssb-md.md)]トランスポート層です。 エラー番号と状態の値で、エラーの原因を確認できます。|  
|143|Broker:Queue Disabled|5 つの連続するトランザクションのロールバックがあったので、有害なメッセージが検出されましたかを示す、[!INCLUDE[ssSB](../../includes/sssb-md.md)]キュー。 このイベントには、データベース ID と、ポイズン メッセージが格納されているキューのキュー ID が含まれます。|  
|144-145|予約済み。||  
|146|Showplan XML Statistics Profile|SQL ステートメントが実行されたときに発生します。 プラン表示演算子が識別され、コンパイル時の完全なデータが表示されます。 なお、**バイナリ**列でこのイベントにエンコードされたプラン表示が含まれています。 トレースを開いてプラン表示を確認するには、SQL Server Profiler を使用します。|  
|148|Deadlock Graph|ロックを取得しようとしてデッドロックが発生したため、ロックの取得が取り消されたときに発生します。 デッドロックについての XML の説明が提供されます。|  
|149|Broker:Remote Message Acknowledgement|[!INCLUDE[ssSB](../../includes/sssb-md.md)] によってメッセージの受信確認が送信または受信されたときに発生します。|  
|150|Trace File Close|トレース ファイルのロールオーバー中にトレース ファイルが閉じられたときに発生します。|  
|151|予約済み。||  
|152|Audit Change Database Owner|ALTER AUTHORIZATION を使用して、データベースの所有者を変更するか、変更に必要な権限を確認したときに発生します。|  
|153|Audit Schema Object Take Ownership Event|ALTER AUTHORIZATION を使用して、オブジェクトに所有者を割り当てるか、割り当てに必要な権限を確認したときに発生します。|  
|154|予約済み。||  
|155|FT:Crawl Started|フルテキストのクロール (カタログ作成) が開始したときに発生します。 クロールの要求が作業タスクで受け取られたかどうかを確認する場合に使用します。|  
|156|FT:Crawl Stopped|フルテキストのクロール (カタログ作成) が停止したときに発生します。 クロールが停止するのは、正常に完了するか重大なエラーが発生したときです。|  
|157|FT:Crawl Aborted|フルテキストのクロール中に例外が検出されたときに発生します。 通常、これによってフルテキストのクロールは停止します。|  
|158|Audit Broker Conversation|監査に関連するメッセージを報告[!INCLUDE[ssSB](../../includes/sssb-md.md)]ダイアログ セキュリティ。|  
|159|Audit Broker Login|監査に関連するメッセージを報告[!INCLUDE[ssSB](../../includes/sssb-md.md)]トランスポート セキュリティ。|  
|160|Broker:Message Undeliverable|発生したときに[!INCLUDE[ssSB](../../includes/sssb-md.md)]をサービスに配信されていなければならない受信したメッセージを保持することはありません。|  
|161|Broker:Corrupted Message|発生したときに[!INCLUDE[ssSB](../../includes/sssb-md.md)]が破損したメッセージを受信します。|  
|162|User Error Message|エラーや例外が発生したときにユーザーに表示されるエラー メッセージを表示します。|  
|163|Broker:Activation|キュー モニターによって、アクティブ化ストアド プロシージャの開始や QUEUE_ACTIVATION 通知の送信が行われたときに発生します。またはキュー モニターが終了してアクティブ化ストアド プロシージャが開始したときに発生します。|  
|164|Object:Altered|データベース オブジェクトが変更されたときに発生します。|  
|165|Performance statistics|コンパイルされたクエリ プランが最初にキャッシュされたか、再コンパイルされたとき、またはプラン キャッシュから削除されたときに発生します。|  
|166|SQL:StmtRecompile|ステートメント レベルの再コンパイルが発生したときに発生します。|  
|167|Database Mirroring State Change|ミラー化データベースの状態が変更されたときに発生します。|  
|168|Showplan XML For Query Compile|SQL ステートメントがコンパイルされたときに発生します。 完了したら、コンパイル時のデータを表示します。 なお、**バイナリ**列でこのイベントにエンコードされたプラン表示が含まれています。 トレースを開いてプラン表示を確認するには、SQL Server Profiler を使用します。|  
|169|Showplan All For Query Compile|SQL ステートメントがコンパイルされたときに発生します。 コンパイル時の完全なデータが表示されます。 プラン表示演算子を識別する場合に使用します。|  
|170|Audit Server Scope GDR Event|サーバー スコープ内で権限の付与、拒否、および取り消しのイベントが発生したことを示します。このようなイベントは、ログインの作成などによって発生します。|  
|171|Audit Server Object GDR Event|テーブルや関数などのスキーマ オブジェクトに対して、付与、拒否、または取り消しのイベントが発生したことを示します。|  
|172|Audit Database Object GDR Event|アセンブリやスキーマなどのデータベース オブジェクトに対して、付与、拒否、または取り消しのイベントが発生したことを示します。|  
|173|Audit Server Operation Event|設定の変更、リソース、外部アクセス、承認などの、セキュリティ監査操作が使用されたときに発生します。|  
|175|Audit Server Alter Trace Event|ステートメントで ALTER TRACE 権限が確認されたときに発生します。|  
|176|Audit Server Object Management Event|サーバー オブジェクトが作成、変更、または削除されたときに発生します。|  
|177|Audit Server Principal Management Event|サーバー プリンシパルが作成、変更、または削除されたときに発生します。|  
|178|Audit Database Operation Event|チェックポイントやクエリ通知のサブスクライブなど、データベース操作が行われたときに発生します。|  
|180|Audit Database Object Access Event|スキーマなどのデータベース オブジェクトにアクセスがあったときに発生します。|  
|181|TM: Begin Tran starting|BEGIN TRANSACTION 要求が開始されたときに発生します。|  
|182|TM: Begin Tran completed|BEGIN TRANSACTION 要求が完了したときに発生します。|  
|183|TM: Promote Tran starting|PROMOTE TRANSACTION 要求が開始されたときに発生します。|  
|184|TM: Promote Tran completed|PROMOTE TRANSACTION 要求が完了したときに発生します。|  
|185|TM: Commit Tran starting|COMMIT TRANSACTION 要求が開始されたときに発生します。|  
|186|TM: Commit Tran completed|COMMIT TRANSACTION 要求が完了したときに発生します。|  
|187|TM: Rollback Tran starting|ROLLBACK TRANSACTION 要求が開始されたときに発生します。|  
|188|TM: Rollback Tran completed|ROLLBACK TRANSACTION 要求が完了したときに発生します。|  
|189|Lock:Timeout (timeout > 0)|ページなどのリソースへのロック要求がタイムアウトしたときに発生します。|  
|190|Progress Report: Online Index Operation|オンライン インデックスの構築中に、操作の進行状況をレポートします。|  
|191|TM: Save Tran starting|SAVE TRANSACTION 要求が開始されたときに発生します。|  
|192|TM: Save Tran completed|SAVE TRANSACTION 要求が完了したときに発生します。|  
|193|Background Job Error|バックグラウンド ジョブが異常終了したときに発生します。|  
|194|OLEDB Provider Information|分散クエリが実行され、プロバイダー接続に関する情報が収集されたときに発生します。|  
|195|Mount Tape|テープ マウント要求を受け取ったときに発生します。|  
|196|Assembly Load|CLR アセンブリの読み込み要求があったときに発生します。|  
|197|予約済み。||  
|198|XQuery Static Type|XQuery 式が実行されたときに発生します。 このイベント クラスでは静的な XQuery 式が提供されます。|  
|199|QN: subscription|クエリの登録がサブスクライブされなかったときに発生します。 **TextData**列には、イベントに関する情報が含まれています。|  
|200|QN: parameter table|アクティブなサブスクリプションに関する情報は、内部パラメーター テーブルに格納されます。 このイベント クラスは、パラメーター テーブルが作成または削除されたときに発生します。 通常これらのテーブルは、データベースを再起動したときに作成または削除されます。 **TextData**列には、イベントに関する情報が含まれています。|  
|201|QN: template|クエリ テンプレートによって、サブスクリプション クエリのクラスが表されます。 通常、同じクラスにあるクエリは、パラメーター値を除いてすべて同じになります。 このイベント クラスは、新しいサブスクリプション要求が、既存のクラス (一致したクラス)、新しいクラス (作成)、または削除するクラスに分類されたときに発生します。これは、アクティブなサブスクリプションが含まれていないクエリ クラスのテンプレートをクリーンアップすることを示します。 **TextData**列には、イベントに関する情報が含まれています。|  
|202|QN: dynamics|クエリ通知の内部アクティビティを追跡します。 **TextData**列には、イベントに関する情報が含まれています。|  
|212|Bitmap Warning|クエリでビットマップ フィルターが無効になっていることを示します。|  
|213|Database Suspect Data Page|ページが加わった時点を示します、 **suspect_pages**テーブルに**msdb**です。|  
|214|CPU Threshold Exceeded|CPU しきい値 (REQUEST_MAX_CPU_TIME_SEC) をクエリが超えたことをリソース ガバナーで検出したことを示します。|  
|215|LOGON トリガーまたはリソース ガバナー分類子関数の実行が開始されたことを示します。|LOGON トリガーまたはリソース ガバナー分類子関数の実行が開始されたことを示します。|  
|216|PreConnect:Completed|LOGON トリガーまたはリソース ガバナー分類子関数の実行が完了したことを示します。|  
|217|Plan Guide Successful|SQL Server でプラン ガイドを含むクエリまたはバッチの実行プランが正常に生成されたことを示します。|  
|218|Plan Guide Unsuccessful|SQL Server でプラン ガイドを含むクエリまたはバッチの実行プランを生成できなかったことを示します。 SQL Server はプラン ガイドを適用せずにこのクエリまたはバッチの実行プランを生成しようとしました。 無効なプラン ガイドが原因になった可能性があります。 sys.fn_validate_plan_guide システム関数を使用して、プラン ガイドを検証することができます。|  
|235|Audit Fulltext||  
  
 [ **@columnid=** ] *column_id*  
 イベントに対して追加する列の ID を指定します。 *column_id*は**int**、既定値はありません。  
  
 次の表は、イベントに対して追加できる列の一覧です。  
  
|列番号|列名|Description|  
|-------------------|-----------------|-----------------|  
|1|**TextData**|トレースにキャプチャされるイベント クラスに依存するテキスト値。|  
|2|**BinaryData**|トレースでキャプチャされたイベント クラスに依存するバイナリ値。|  
|3|**DatabaseID**|使用して指定されたデータベースの ID*データベース*ステートメント、または使用しない場合、既定のデータベース*データベース*特定の接続に対してステートメントを発行します。<br /><br /> データベースに対するデータベース ID の値は、DB_ID 関数を使用して指定できます。|  
|4|**TransactionID**|システムによって割り当てられたトランザクション ID。|  
|5|**LineNumber**|エラーを含む行の番号が格納されます。 [!INCLUDE[tsql](../../includes/tsql-md.md)] SP:StmtStarting **のような**ステートメントを含むイベントの場合、 **LineNumber** にはストアド プロシージャまたはバッチでのステートメントの行番号が格納されます。|  
|6|**NTUserName**|[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows のユーザー名。|  
|7|**NTDomainName**|ユーザーが所属する Windows ドメイン。|  
|8|**HostName**|要求を生成したクライアント コンピューターの名前。|  
|9|**ClientProcessID**|クライアント アプリケーションが実行されているプロセスに対し、クライアントのコンピューターが割り当てた ID。|  
|10|**ApplicationName**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスへの接続を作成したクライアント アプリケーションの名前。 この列には、プログラムの表示名ではなく、アプリケーションによって渡された値が格納されます。|  
|11|**LoginName**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クライアントのログイン名。|  
|12|**SPID**|によって割り当てられたサーバー プロセス ID[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアントに関連付けられたプロセスにします。|  
|13|**Duration**|イベントの実行に要した経過時間 (マイクロ秒単位)。 Hash Warning イベントに対しては、このデータ列は作成されません。|  
|14|**StartTime**|イベントの開始時刻 (取得できた場合)。|  
|15|**EndTime**|イベントの終了時刻。 **SQL:BatchStarting** や **SP:Starting**などの開始イベント クラスについては、この列に値が格納されません。 これも作成されませんが、 **Hash Warning**イベント。|  
|16|**Reads**|イベントの代わりにサーバーによって実行される、論理ディスク読み取り回数。 この列は作成されません、**ロック: リリース**イベント。|  
|17|**Writes**|イベントの代わりにサーバーによって実行される、物理ディスクの書き込み回数。|  
|18|**CPU**|イベントに使用された CPU 時間 (ミリ秒単位)。|  
|19|**権限**|セキュリティ監査によって使用される、権限のビットマップ。|  
|20|**Severity**|例外の重大度レベル。|  
|21|**EventSubClass**|イベント サブクラスの種類。 すべてのイベント クラスに対して、このデータ列が作成されるわけではありません。|  
|22|**Exchange Spill**|システムによって割り当てられたオブジェクト ID。|  
|23|**成功**|権限が正常に使用されたかどうか。監査で使用します。<br /><br /> **1** = 成功**0** = 失敗|  
|24|**IndexID**|イベントの影響を受けるオブジェクトに付けられたインデックス用の ID。 オブジェクトのインデックス ID を調べるには、 **sysindexes** システム テーブルの **indid** 列を使用します。|  
|25|**IntegerData**|トレースでキャプチャされたイベント クラスに依存する整数値。|  
|26|**ServerName**|インスタンスの名前[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]か、 *servername*または*servername \instancename*、トレース中します。|  
|27|**EventClass**|記録されるイベント クラスの種類。|  
|28|**ObjectType**|テーブル、関数、ストアド プロシージャなどのオブジェクトの種類。|  
|29|**NestLevel**|このストアド プロシージャが実行されている入れ子レベル。 参照してください[@@NESTLEVEL&#40;Transact-SQL&#41;](../../t-sql/functions/nestlevel-transact-sql.md).|  
|30|**状態**|エラーが発生した場合のサーバーの状態。|  
|31|**[エラー]**|エラー番号。|  
|32|**モード**|取得されたロックのロック モード。 この列は作成されません、**ロック: リリース**イベント。|  
|33|**Handle**|イベントで参照されているオブジェクトのハンドル。|  
|34|**ObjectName**|アクセスされるオブジェクトの名前。|  
|35|**DatabaseName**|使用する指定されたデータベースの名前*データベース*ステートメントです。|  
|36|**FileName**|変更されたファイル名の論理名。|  
|37|**OwnerName**|参照されたオブジェクトの所有者名。|  
|38|**RoleName**|ステートメントの対象となっているデータベースまたはサーバー全体のロールの名前。|  
|39|**TargetUserName**|アクションの対象となるユーザー名。|  
|40|**DBUserName**|クライアントの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース ユーザー名。|  
|41|**LoginSid**|ログインしたユーザーのセキュリティ識別子 (SID)。|  
|42|**TargetLoginName**|アクションの対象となるログイン名。|  
|43|**TargetLoginSid**|アクションの対象となるログインの SID。|  
|44|**ColumnPermissions**|列レベル権限の状態。セキュリティ監査で使用します。|  
|45|**LinkedServerName**|リンク サーバーの名前|  
|46|**ProviderName**|OLE DB プロバイダーの名前です。|  
|47|**MethodName**|OLE DB メソッドの名前。|  
|48|**RowCounts**|バッチに含まれる行数。|  
|49|**RequestID**|ステートメントが含まれている要求の ID。|  
|50|**XactSequence**|現在のトランザクションを記述するトークン。|  
|51|**EventSequence**|このイベントのシーケンス番号。|  
|52|**BigintData1**|**bigint**トレースにキャプチャされたイベント クラスに依存する値。|  
|53|**BigintData2**|**bigint**トレースにキャプチャされたイベント クラスに依存する値。|  
|54|**GUID**|トレースでキャプチャされたイベント クラスに依存する GUID 値。|  
|55|**IntegerData2**|トレースにキャプチャされたイベント クラスに依存する整数値。|  
|56|**ObjectID2**|関連するオブジェクトまたはエンティティの ID (使用可能な場合)。|  
|57|**型**|トレースにキャプチャされたイベント クラスに依存する整数値。|  
|58|**OwnerID**|ロックを所有するオブジェクトの型。 ロック イベントの場合にのみ該当します。|  
|59|**ParentName**|オブジェクトが存在するスキーマの名前。|  
|60|**IsSystem**|イベントがシステム プロセスとユーザー プロセスのどちらで発生したか。<br /><br /> **1** = システム<br /><br /> **0** = ユーザーです。|  
|61|**Offset**|ストアド プロシージャ内またはバッチ内のステートメントの開始オフセット。|  
|62|**SourceDatabaseID**|オブジェクトのソースが存在するデータベースの ID です。|  
|63|**SqlHandle**|64 ビット ハッシュ。アドホック クエリやデータベースのテキスト、および SQL オブジェクトのオブジェクト ID に基づいています。 この値を **sys.dm_exec_sql_text()** に渡して、関連付けられている SQL テキストを取得できます。|  
|64|**SessionLoginName**|セッションを開始したユーザーのログイン名。 たとえば、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に **Login1** を使用して接続し、 **Login2**としてステートメントを実行した場合、 **SessionLoginName** には **Login1**が表示され、 **LoginName** には **Login2**が表示されます。 このデータ列には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインと Windows ログインの両方が表示されます。|  
  
 **[ @on=]** *on*  
 このイベントを ON (1) にするか OFF (0) にするかを指定します。 *で* は **ビット**, 、既定値はありません。  
  
 場合*で*に設定されている**1**、および*column_id*を NULL にしてから、イベントが ON に設定されているすべての列を消去します。 場合*column_id*が null でない列はそのイベントを ON に設定されます。  
  
 場合*で*に設定されている**0**、および*column_id* NULL の場合は、イベントが有効になって OFF され、すべての列が消去されます。 場合*column_id*が null でない列が有効になって OFF です。  
  
 次の表は、間の相互作用を示しています。 **@on**と **@columnid**です。  
  
|@on|@columnid|結果|  
|---------|---------------|------------|  
|ON (**1**)|NULL|イベントは ON になります。<br /><br /> すべての列は消去されます。|  
||NOT NULL|指定されたイベントに対して列は ON になります。|  
|OFF (**0**)|NULL|イベントは OFF になります。<br /><br /> すべての列は消去されます。|  
||NOT NULL|指定されたイベントに対して列は OFF になります。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 次の表は、このストアド プロシージャの完了時に返されるコード値を示しています。  
  
|リターン コード|Description|  
|-----------------|-----------------|  
|0|エラーなし。|  
|1|不明なエラーです。|  
|2|トレースは現在実行中です。 この時点でトレースを変更すると、エラーが発生します。|  
|3|指定したイベントは無効です。 イベントが存在しないか、イベントがこのストアド プロシージャに対して適切ではありません。|  
|4|指定した列は無効です。|  
|9|指定したトレース ハンドルが正しくありません。|  
|11|指定した列は内部で使用されるので、削除できません。|  
|13|メモリ不足。 指定した操作を実行するための十分なメモリがない場合に返されます。|  
|16|関数がこのトレースに対して無効です。|  
  
## <a name="remarks"></a>解説  
 **sp_trace_setevent**の以前のバージョンで利用可能な拡張のストアド プロシージャで実行される操作の多く[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 使用して**sp_trace_setevent**次の代わりにします。  
  
-   **xp_trace_addnewqueue**  
  
-   **xp_trace_eventclassrequired**  
  
-   **xp_trace_seteventclassrequired**  
  
 ユーザーが実行する必要があります**sp_trace_setevent**イベントごとに追加された列ごとにします。 各実行中に場合**@on**に設定されている**1**、 **sp_trace_setevent**トレースのイベントの一覧に指定されたイベントを追加します。 場合**@on**に設定されている**0**、 **sp_trace_setevent**一覧から、指定されたイベントを削除します。  
  
 ストアド プロシージャのすべての SQL トレースのパラメーター (**sp_trace_xx**) は、厳密に型指定されています。 これらのパラメーターを、引数の説明で指定されている正しいデータ型で指定しないと、このストアド プロシージャではエラーが返されます。  
  
 トレース ストアド プロシージャを使用した例については、「[トレースの作成 &#40;Transact-SQL&#41;](../../relational-databases/sql-trace/create-a-trace-transact-sql.md)」を参照してください。  
  
## <a name="permissions"></a>権限  
 ユーザーに ALTER TRACE 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [sys.fn_trace_geteventinfo &#40;TRANSACT-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-geteventinfo-transact-sql.md)   
 [sys.fn_trace_getinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql.md)   
 [sp_trace_generateevent &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql.md)   
 [SQL Server イベント クラスのリファレンス](../../relational-databases/event-classes/sql-server-event-class-reference.md)   
 [SQL トレース (SQL Trace)](../../relational-databases/sql-trace/sql-trace.md)  
  
  
