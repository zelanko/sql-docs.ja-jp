---
title: sp_trace_setevent (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_trace_setevent_TSQL
- sp_trace_setevent
dev_langs:
- TSQL
helpviewer_keywords:
- sp_trace_setevent
ms.assetid: 7662d1d9-6d0f-443a-b011-c901a8b77a44
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 54f36b46f75bf943ecf08aafd93a6b861c2da90a
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58538584"
---
# <a name="sptracesetevent-transact-sql"></a>sp_trace_setevent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  トレースに対して、イベントまたはイベント列を追加または削除します。 **sp_trace_setevent**停止している既存のトレースに対してのみ実行できます (*状態*は**0**)。 エラーが返されます場合、このストアド プロシージャが存在しないトレースまたはで上で実行*状態*ない**0**します。  
  
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
`[ @traceid = ] trace_id` 変更するトレースの ID です。 *trace_id*は**int**、既定値はありません。 ユーザーがこれを採用して*trace_id*識別、変更、およびトレースを制御する値。  
  
`[ @eventid = ] event_id` 有効にするイベントの ID です。 *event_id*は**int**、既定値はありません。  
  
 次の表は、トレースに対して追加または削除できるイベントの一覧です。  
  
|イベントの数|イベント名|説明|  
|------------------|----------------|-----------------|  
|0-9|予約済み。|予約済み。|  
|10|RPC:Completed|リモート プロシージャ コール (RPC) が完了したときに発生します。|  
|11|RPC:Starting|RPC が開始したときに発生します。|  
|12|SQL:BatchCompleted|発生したときに、[!INCLUDE[tsql](../../includes/tsql-md.md)]のバッチが完了します。|  
|13|SQL:BatchStarting|[!INCLUDE[tsql](../../includes/tsql-md.md)] バッチが開始したときに発生します。|  
|14|Audit Login|ユーザーが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に正常にログオンしたときに発生します。|  
|15|Audit Logout|ユーザーが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からログアウトしたときに発生します。|  
|16|Attention|クライアントの割り込み要求やクライアント接続の切断などのアテンション イベントが発生したときに発生します。|  
|17|ExistingConnection|トレースの開始前から [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続しているユーザーのすべての利用状況を検出します。|  
|18|Audit Server Starts and Stops|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスの状態が変更されたときに発生します。|  
|19|DTCTransaction|複数のデータベース間で、[!INCLUDE[msCoName](../../includes/msconame-md.md)] 分散トランザクション コーディネーター (MS DTC) によってコーディネートされたトランザクションを追跡します。|  
|20|ログインの監査に失敗しました|クライアントから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] へのログイン試行が失敗したことを示します。|  
|21|EventLog|イベントが Windows アプリケーション ログに記録されたことを示します。|  
|22|ErrorLog|エラー イベントが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログに記録されたことを示します。|  
|23|Lock:Released|ページなどのリソースのロックが解除されたことを示します。|  
|24|Lock:Acquired|データ ページなどのリソースのロックが取得されたことを示します。|  
|25|Lock:Deadlock|2 つの同時実行トランザクションが他のトランザクションが所有するリソースに対して互換性のないロックを取得しようとして相互にデッドロックを示します。|  
|26|Lock:Cancel|(たとえば、デッドロック) のためのリソースのロックの取得が取り消されたことを示します。|  
|27|Lock:Timeout|ページなどのリソースのロックが要求されたが、他のトランザクションによってそのリソースのブロッキング ロックが保持されているため、要求がタイムアウトになったことを示します。 タイムアウトはによって決定されます、@@LOCK_TIMEOUT関数し、SET LOCK_TIMEOUT ステートメントで設定できます。|  
|28|Degree of Parallelism Event (7.0 Insert)|SELECT、INSERT、または UPDATE ステートメントが実行される前に発生します。|  
|29-31|予約済み。|代わりにイベント 28 を使用してください。|  
|32|予約済み。|予約済み。|  
|33|例外|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で例外が発生したことを示します。|  
|34|SP:CacheMiss|ストアド プロシージャがプロシージャ キャッシュに存在しないときを示します。|  
|35|SP:CacheInsert|プロシージャ キャッシュに項目を挿入する場合を示します。|  
|36|SP:CacheRemove|プロシージャ キャッシュからアイテムが削除されたことを示します。|  
|37|SP:Recompile|ストアド プロシージャが再コンパイルされたことを示します。|  
|38|SP:CacheHit|ストアド プロシージャがプロシージャ キャッシュ内にあることを示します。|  
|39|非推奨|非推奨|  
|40|SQL:StmtStarting|発生したときに、[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントが開始します。|  
|41|SQL:StmtCompleted|発生したときに、[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントが完了しました。|  
|42|SP:Starting|ストアド プロシージャが開始された時点を示します。|  
|43|SP:Completed|ストアド プロシージャが完了したことを示します。|  
|44|SP:StmtStarting|示します、[!INCLUDE[tsql](../../includes/tsql-md.md)]ストアド プロシージャ内のステートメントが実行を開始します。|  
|45|SP:StmtCompleted|ストアド プロシージャ内の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントの実行が完了したことを示します。|  
|46|オブジェクト: 作成|CREATE INDEX、CREATE TABLE、および CREATE DATABASE ステートメントなどの作成されたオブジェクトがされたことを示します。|  
|47|Object:Deleted|DROP INDEX や DROP TABLE などのステートメントで、オブジェクトが削除されたことを示します。|  
|48|予約済み。||  
|49|予約済み。||  
|50|SQL トランザクション|トラック[!INCLUDE[tsql](../../includes/tsql-md.md)]BEGIN、COMMIT、SAVE、および ROLLBACK TRANSACTION ステートメント。|  
|51|スキャン: 開始|テーブル スキャンまたはインデックス スキャンが開始されたことを示します。|  
|52|スキャン: 停止|テーブル スキャンまたはインデックス スキャンが停止したことを示します。|  
|53|CursorOpen|[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントで、ODBC、OLE DB、または DB-Library によりカーソルがオープンされたことを示します。|  
|54|TransactionLog|トランザクションがいつトランザクション ログに書き込まれるかを追跡します。|  
|55|ハッシュに関する警告|バッファー パーティション上で処理されていないハッシュ演算 (ハッシュ結合、ハッシュ集計、ハッシュ ユニオン、ハッシュ識別など) が代替プランに変更されたことを示します。 これは、再帰の深さのため発生、データ スキュー、トレース フラグ、またはビット カウンティングします。|  
|56-57|予約済み。||  
|58|Auto Stats|インデックス統計の自動更新が実行されたことを示します。|  
|59|Lock:Deadlock Chain|デッドロックにつながるイベントごとに生成します。|  
|60|Lock:Escalation|ページ ロックが TABLE ロックまたは HoBT ロックにエスカレートまたは変換された場合など、細かい単位のロックが大きな単位のロックに変換されたことを示します。|  
|61|OLE DB Errors|OLE DB エラーが発生したことを示します。|  
|62-66|予約済み。||  
|67|Execution Warnings|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ステートメントまたはストアド プロシージャの実行中に発生した警告を示します。|  
|68|Showplan Text (Unencoded)|実行された [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントのプラン ツリーを表示します。|  
|69|Sort Warnings|メモリに収まらない並べ替え操作を示します。 インデックスの作成に関連する並べ替え操作は対象になりません。SELECT ステートメントで使用される ORDER BY 句など、クエリ内の並べ替え操作のみが対象になります。|  
|70|CursorPrepare|カーソルを示す、 [!INCLUDE[tsql](../../includes/tsql-md.md)] ODBC、OLE DB、または Db-library によってステートメントが準備に使用します。|  
|71|Prepare SQL|ODBC、OLE DB、または Db-library が準備、[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントまたはステートメントを使用します。|  
|72|Exec Prepared SQL|ODBC、OLE DB、または DB-Library によって、準備された 1 つ以上の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントが実行されたことを示します。|  
|73|Unprepare SQL|ODBC、OLE DB、または Db-library が準備されていない (削除)、準備された[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントまたはステートメント。|  
|74|CursorExecute|[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントで ODBC、OLE DB、または DB-Library によって準備されたカーソルが実行されたことを示します。|  
|75|CursorRecompile|[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントで ODBC または DB-Library によってオープンされていたカーソルが、直接再コンパイルされたか、またはスキーマが変更されたために再コンパイルされたことを示します。<br /><br /> ANSI および非 ANSI のカーソルに対してトリガーされます。|  
|76|CursorImplicitConversion|カーソルを[!INCLUDE[tsql](../../includes/tsql-md.md)]でステートメントが変換されます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]別の 1 つの型から。<br /><br /> ANSI および非 ANSI のカーソルに対してトリガーされます。|  
|77|CursorUnprepare|[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントで準備されたカーソルが、ODBC、OLE DB、または DB-Library によって削除されたことを示します。|  
|78|CursorClose|以前にカーソルを開か、 [!INCLUDE[tsql](../../includes/tsql-md.md)] ODBC、OLE DB、または Db-library によってステートメントが終了します。|  
|79|不足している列の統計|オプティマイザーに有効な列の統計が利用できません。|  
|80|Missing Join Predicate|結合述語がクエリが実行されていません。 クエリの終了に時間がかかる可能性があります。|  
|81|Server Memory Change|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] メモリ使用量の増加または減少 1 メガバイト (MB) または最大サーバー メモリの 5% のいずれか、大きい方になります。|  
|82-91|ユーザー構成可能な (0 ~ 9)|ユーザーによって定義されたイベント データ。|  
|92|Data File Auto Grow します。|データ ファイルがサーバーによって自動的に拡張されたことを示します。|  
|93|Log File Auto Grow|ログ ファイルがサーバーによって自動的に拡張されたことを示します。|  
|94|Data File Auto Shrink|データ ファイルがサーバーによって自動的に圧縮されたことを示します。|  
|95|ログ ファイルの自動圧縮|ログ ファイルがサーバーによって自動的に圧縮されたことを示します。|  
|96|Showplan Text|クエリ オプティマイザーの SQL ステートメントのクエリ プラン ツリーを表示します。 なお、 **TextData**列にこのイベントの Showplan が含まれていません。|  
|97|Showplan All|実行された SQL ステートメントのコンパイル時の完全な詳細を含むクエリ プランが表示されます。 なお、 **TextData**列にこのイベントの Showplan が含まれていません。|  
|98|Showplan Statistics Profile|実行された SQL ステートメントの実行時の完全な詳細を含むクエリ プランが表示されます。 なお、 **TextData**列にこのイベントの Showplan が含まれていません。|  
|99|予約済み。||  
|100|RPC Output Parameter|各 RPC に対して、パラメーターの出力値を生成します。|  
|101|予約済み。||  
|102|データベース スコープの GDR が監査します。|データベースに対する権限の許可などのデータベース限定の操作時に、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の任意のユーザーがステートメント権限の GRANT、DENY、REVOKE を実行するたびに発生します。|  
|103|監査オブジェクトの GDR Event|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の任意のユーザーがオブジェクト権限の GRANT、DENY、REVOKE を実行するたびに発生します。|  
|104|Audit AddLogin イベント|発生したときに、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインが追加または削除の**sp_addlogin**と**sp_droplogin**します。|  
|105|Audit Login GDR Event|Windows ログインの権利が追加または削除されたときに発生します**sp_grantlogin**、 **sp_revokelogin**、および**sp_denylogin**します。|  
|106|Audit Login Change Property Event|パスワードを除く、ログインのプロパティが変更されたときに発生します**sp_defaultdb**と**sp_defaultlanguage**します。|  
|107|Audit Login Change パスワード Event|発生したときに、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログイン パスワードを変更します。<br /><br /> パスワードは記録されません。|  
|108|Audit Add Login to Server ロール イベント|ログインが追加または、固定サーバー ロールから削除されたときに発生します**sp_addsrvrolemember**、および**sp_dropsrvrolemember**します。|  
|109|Audit Add DB User Event|ログインが追加またはデータベース ユーザーとして削除するときに発生します (Windows または[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]) データベースには**sp_grantdbaccess**、 **sp_revokedbaccess**、 **sp_adduser**、**sp_dropuser**します。|  
|110|Audit Add Member to DB ロール Event|ログインが追加またはデータベースに (固定またはユーザー定義) は、データベース ユーザーとして削除するときに発生します**sp_addrolemember**、 **sp_droprolemember**、および**sp_changegroup**します。|  
|111|Audit Add ロール イベント|ログインが追加またはデータベースにデータベース ユーザーとして削除するときに発生します**sp_addrole**と**sp_droprole**します。|  
|112|Audit App Role Change Password Event|アプリケーション ロールのパスワードが変更されたときに発生します。|  
|113|Audit Statement Permission Event|CREATE TABLE などのステートメント権限が使用されたときに発生します。|  
|114|Audit Schema Object Access Event|SELECT などのオブジェクト権限が使用されたときに、それが成功したかどうかに関係なく発生します。|  
|115|Audit Backup/restore イベント|BACKUP または RESTORE コマンドが実行されたときに発生します。|  
|116|Audit DBCC Event|DBCC コマンドが実行されたときに発生します。|  
|117|Audit Change Audit Event|監査トレースが変更されたときに発生します。|  
|118|Audit Object Derived Permission Event|CREATE、ALTER、および DROP のオブジェクト コマンドが実行されたときに発生します。|  
|119|OLEDB Call イベント|分散クエリとリモート ストアド プロシージャに対して、OLE DB プロバイダー呼び出しが行われたときに発生します。|  
|120|OLEDB QueryInterface Event|Ole DB **QueryInterface**分散クエリやリモート ストアド プロシージャの呼び出しは行われます。|  
|121|OLEDB DataRead Event|OLE DB プロバイダーに対して、データ要求の呼び出しが行われたときに発生します。|  
|122|Showplan XML|SQL ステートメントを実行するときに発生します。 プラン表示操作を識別するには、このイベントが含まれます。 各イベントは、整形式の XML ドキュメントに格納されます。 なお、**バイナリ**列でこのイベントでエンコードされたプラン表示が含まれています。 トレースを開いてプラン表示を表示するには、SQL Server Profiler を使用します。|  
|123|SQL:FullTextQuery|フルテキスト クエリが実行されたときに発生します。|  
|124|Broker:Conversation|進行状況を報告する[!INCLUDE[ssSB](../../includes/sssb-md.md)]メッセージ交換します。|  
|125|Deprecation Announcement|将来のバージョンから削除される機能を使用するときに発生します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。|  
|126|Deprecation Final Support|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の次の主要なリリースで削除される予定の機能を使用したときに発生します。|  
|127|Exchange Spill イベント|並列クエリ プランの通信バッファーに一時的に書き込まれたときに発生します、 **tempdb**データベース。|  
|128|データベース管理の監査イベント|データベースが作成、変更、または削除されたときに発生します。|  
|129|監査データベース オブジェクトの管理イベント|スキーマなどのデータベース オブジェクトで CREATE、ALTER、または DROP ステートメントを実行するときに発生します。|  
|130|Audit Database Principal Management Event|ユーザーなどのプリンシパルが作成、変更、または、データベースから削除されるときに発生します。|  
|131|監査スキーマ オブジェクトの管理イベント|サーバー オブジェクトを作成、変更、または削除されると発生します。|  
|132|Audit Server Principal Impersonation Event|サーバー スコープ内で、EXECUTE AS LOGIN などの権限借用があるときに発生します。|  
|133|Audit Database Principal Impersonation Event|EXECUTE AS USER や SETUSER などのデータベース スコープ内で権限の借用が発生したときに発生します。|  
|134|監査サーバー オブジェクトの Take Ownership Event|サーバー スコープ内のオブジェクトの所有者が変更されたときに発生します。|  
|135|データベース オブジェクトの Take Ownership イベントを監査します。|データベースのスコープ内のオブジェクトの所有者の変更が発生したときに発生します。|  
|136|Broker:Conversation Group|[!INCLUDE[ssSB](../../includes/sssb-md.md)] によって、新しいメッセージ交換グループが作成されたか、既存のメッセージ交換グループが削除されたときに発生します。|  
|137|Blocked Process Report|指定された時間量より多くのプロセスがブロックされたときに発生します。 システム プロセスや、デッドロックを検出できないリソースで待機しているプロセスはこの対象外です。 使用**sp_configure**レポートが生成されるしきい値と頻度を構成します。|  
|138|Broker:Connection|[!INCLUDE[ssSB](../../includes/sssb-md.md)] によって管理される転送接続の状態をレポートします。|  
|139|Broker: 送信されたメッセージの転送|[!INCLUDE[ssSB](../../includes/sssb-md.md)] によってメッセージが転送されたときに発生します。|  
|140|Broker:Forwarded Message Dropped|[!INCLUDE[ssSB](../../includes/sssb-md.md)] によって転送予定のメッセージが削除されたときに発生します。|  
|141|Broker:Message Classify|[!INCLUDE[ssSB](../../includes/sssb-md.md)] でメッセージのルーティングが決定されたときに発生します。|  
|142|Broker:Transmission|エラーが発生したことを示します、[!INCLUDE[ssSB](../../includes/sssb-md.md)]トランスポート層です。 エラー番号と状態の値で、エラーの原因を確認できます。|  
|143|Broker: キューを無効になっています|5 つの連続するトランザクションのロールバックがあったため、有害なメッセージが検出されたを示します、[!INCLUDE[ssSB](../../includes/sssb-md.md)]キュー。 イベントには、データベース ID と有害メッセージを含むキューのキュー ID が含まれています。|  
|144-145|予約済み。||  
|146|Showplan XML Statistics Profile|SQL ステートメントを実行するときに発生します。 プラン表示操作を識別し、コンパイル時の完全なデータを表示します。 なお、**バイナリ**列でこのイベントでエンコードされたプラン表示が含まれています。 トレースを開いてプラン表示を表示するには、SQL Server Profiler を使用します。|  
|148|Deadlock Graph|試行がデッドロックの一部になり、デッドロックの対象として選択されたため、ロックの取得を試行が取り消されたときに発生します。 デッドロックについての XML の説明が提供されます。|  
|149|Broker:remote メッセージの受信確認|[!INCLUDE[ssSB](../../includes/sssb-md.md)] によってメッセージの受信確認が送信または受信されたときに発生します。|  
|150|トレース ファイルを閉じる|トレース ファイルのロール オーバー中にトレース ファイルを閉じるときに発生します。|  
|151|予約済み。||  
|152|Audit Change Database Owner|ALTER AUTHORIZATION を使用して、データベースの所有者を変更して、そのアクセス許可がオンになって発生します。|  
|153|スキーマ オブジェクトの Take Ownership イベントを監査します。|ALTER AUTHORIZATION を使用して、オブジェクトに所有者を割り当てるし、そのアクセス許可がオンになって発生します。|  
|154|予約済み。||  
|155|FT:Crawl 開始|フルテキストのクロール (カタログ作成) が開始したときに発生します。 確認して、クロール要求がワーカー タスクによってピックアップしているかどうかに使用します。|  
|156|FT:Crawl Stopped|フルテキストのクロール (カタログ作成) が停止したときに発生します。 停止は、クロールが正常に完了または致命的なエラーが発生した場合に発生します。|  
|157|FT:Crawl Aborted|フルテキスト クロール中に例外が発生したときに発生します。 通常、これによってフルテキストのクロールは停止します。|  
|158|Audit Broker Conversation|監査に関連するメッセージを報告[!INCLUDE[ssSB](../../includes/sssb-md.md)]ダイアログ セキュリティ。|  
|159|Audit Broker Login|監査に関連するメッセージを報告[!INCLUDE[ssSB](../../includes/sssb-md.md)]トランスポート セキュリティ。|  
|160|Broker:message Undeliverable|発生したときに[!INCLUDE[ssSB](../../includes/sssb-md.md)]をサービスに配信された受信メッセージを保持することはできません。|  
|161|Broker:Corrupted Message|発生したときに[!INCLUDE[ssSB](../../includes/sssb-md.md)]が破損したメッセージを受信します。|  
|162|User Error Message|エラーや例外が発生したときにユーザーに表示されるエラー メッセージを表示します。|  
|163|Broker のアクティブ化:|キュー モニターによって、アクティブ化ストアド プロシージャの開始や QUEUE_ACTIVATION 通知の送信が行われたときに発生します。またはキュー モニターが終了してアクティブ化ストアド プロシージャが開始したときに発生します。|  
|164|Object:Altered|データベース オブジェクトが変更されるときに発生します。|  
|165|Performance statistics|最初に、またはプラン キャッシュから削除された再コンパイルすると、コンパイルされたクエリ プランがキャッシュされているときに発生します。|  
|166|SQL:StmtRecompile|ステートメント レベルの再コンパイルが発生したときに発生します。|  
|167|データベース ミラーリングの状態の変更|ミラー化データベースの状態が変更されたときに発生します。|  
|168|Showplan XML For Query Compile|SQL ステートメントがコンパイルされたときに発生します。 コンパイル時の完全なデータが表示されます。 なお、**バイナリ**列でこのイベントでエンコードされたプラン表示が含まれています。 トレースを開いてプラン表示を表示するには、SQL Server Profiler を使用します。|  
|169|Showplan All For Query Compile|SQL ステートメントがコンパイルされたときに発生します。 コンパイル時の完全なデータを表示します。 プラン表示操作を識別するために使用します。|  
|170|監査サーバー スコープの GDR イベント|示す、付与、拒否、またはサーバー スコープの権限が発生しました、ログインの作成などのイベントを取り消すことです。|  
|171|監査サーバー オブジェクトの GDR イベント|示す、付与、拒否、またはテーブルや関数などのスキーマ オブジェクトのイベントを取り消すことが発生しました。|  
|172|Audit Database Object GDR Event|アセンブリやスキーマなどのデータベース オブジェクトに対して、付与、拒否、または取り消しのイベントが発生したことを示します。|  
|173|監査サーバー操作イベント|セキュリティ監査の設定、リソース、外部アクセス、または承認の変更などの操作を使用する場合に発生します。|  
|175|Audit Server Alter トレース イベント|ステートメントが ALTER TRACE 権限をチェックするときに発生します。|  
|176|監査サーバー オブジェクトの管理イベント|サーバー オブジェクトを作成、変更、または削除されると発生します。|  
|177|Audit Server Principal Management イベント|サーバー プリンシパルが作成、変更、または削除されたときに発生します。|  
|178|データベース操作の監査イベント|チェックポイントやクエリ通知のサブスクライブなど、データベース操作が行われたときに発生します。|  
|180|Audit Database Object Access Event|スキーマなどのデータベース オブジェクトがアクセスされたときに発生します。|  
|181|TM: Begin Tran starting|BEGIN TRANSACTION 要求が開始されたときに発生します。|  
|182|TM: Begin Tran が完了しました|BEGIN TRANSACTION 要求が完了したときに発生します。|  
|183|TM: Tran starting を昇格します。|PROMOTE TRANSACTION 要求が開始するときに発生します。|  
|184|TM: Tran completed の昇格します。|PROMOTE TRANSACTION 要求が完了したときに発生します。|  
|185|TM: Commit Tran starting|COMMIT TRANSACTION 要求が開始するときに発生します。|  
|186|TM: Commit Tran completed|COMMIT TRANSACTION 要求が完了したときに発生します。|  
|187|TM: Rollback Tran の開始|ROLLBACK TRANSACTION 要求が開始されたときに発生します。|  
|188|TM: Rollback Tran の完了|ROLLBACK TRANSACTION 要求が完了したときに発生します。|  
|189|Lock:Timeout (timeout > 0)|ページなどのリソース ロックの要求がタイムアウトしたときに発生します。|  
|190|Progress Report: オンライン インデックス操作|ビルド プロセスの実行中に、オンライン インデックス構築操作の進行状況を報告します。|  
|191|TM: Tran starting を保存します。|SAVE TRANSACTION 要求が開始されたときに発生します。|  
|192|TM: Tran completed の保存します。|SAVE TRANSACTION 要求が完了したときに発生します。|  
|193|バック グラウンド ジョブのエラー|バックグラウンド ジョブが異常終了したときに発生します。|  
|194|OLEDB Provider Information|分散クエリが実行され、プロバイダー接続に対応する情報を収集するときに発生します。|  
|195|Mount Tape|テープ マウント要求を受け取ったときに発生します。|  
|196|Assembly Load|CLR アセンブリの読み込み要求が発生したときに発生します。|  
|197|予約済み。||  
|198|XQuery Static Type|XQuery 式が実行されたときに発生します。 このイベント クラスでは静的な XQuery 式が提供されます。|  
|199|QN: サブスクリプション|クエリの登録がサブスクライブしているときに発生します。 **TextData**列には、イベントに関する情報が含まれています。|  
|200|QN: パラメーター テーブル|アクティブなサブスクリプションに関する情報は、内部パラメーター テーブルに格納されます。 このイベント クラスは、パラメーター テーブルが作成または削除されたときに発生します。 通常これらのテーブルは、データベースを再起動したときに作成または削除されます。 **TextData**列には、イベントに関する情報が含まれています。|  
|201|QN: template|クエリ テンプレートによって、サブスクリプション クエリのクラスが表されます。 通常、同じクラスにあるクエリは、パラメーター値を除いてすべて同じになります。 このイベント クラスは、新しいサブスクリプション要求が、既存のクラス (一致したクラス)、新しいクラス (作成)、または削除するクラスに分類されたときに発生します。これは、アクティブなサブスクリプションが含まれていないクエリ クラスのテンプレートをクリーンアップすることを示します。 **TextData**列には、イベントに関する情報が含まれています。|  
|202|QN: dynamics|クエリ通知の内部アクティビティを追跡します。 **TextData**列には、イベントに関する情報が含まれています。|  
|212|Bitmap Warning|クエリでビットマップ フィルターが無効にされた場合を示します。|  
|213|Database Suspect Data Page|ページが加わった時点を示します、 **suspect_pages**テーブルに**msdb**します。|  
|214|CPU Threshold Exceeded|リソース ガバナーのクエリが CPU しきい値 (REQUEST_MAX_CPU_TIME_SEC) を超えましたが検出した場合を示します。|  
|215|PreConnect:Starting|LOGON トリガーまたは Resource Governor 分類子関数の実行を開始する場合を示します。|  
|216|接続前手続き: 完了|LOGON トリガーまたは Resource Governor 分類子関数の実行を完了することを示します。|  
|217|Plan Guide Successful|SQL Server でプラン ガイドを含むクエリまたはバッチの実行プランが正常に生成されたことを示します。|  
|218|Plan Guide Unsuccessful|SQL Server でプラン ガイドを含むクエリまたはバッチの実行プランを生成できなかったことを示します。 SQL Server では、プラン ガイドを適用せずにこのクエリまたはバッチに対する実行プランを生成しようとしています。 無効なプラン ガイドは、この問題の原因があります。 Sys.fn_validate_plan_guide システム関数を使用してプラン ガイドを検証できます。|  
|235|Audit Fulltext||  
  
`[ @columnid = ] column_id` イベント用に追加する列の ID です。 *column_id*は**int**、既定値はありません。  
  
 次の表には、イベントを追加できる列が一覧表示します。  
  
|列番号|列名|説明|  
|-------------------|-----------------|-----------------|  
|1|**TextData**|トレースにキャプチャされるイベント クラスに依存するテキスト値。|  
|2|**BinaryData**|トレースでキャプチャされたイベント クラスに依存するバイナリ値。|  
|3|**DatabaseID**|使用することによって指定されたデータベースの ID*データベース*ステートメント、または使用しない場合の既定データベース*データベース*特定の接続に対してステートメントを実行します。<br /><br /> データベースの値は、DB_ID 関数を使用して決定できます。|  
|4|**TransactionID**|システムによって割り当てられたトランザクション ID。|  
|5|**LineNumber**|エラーを含む行の番号が格納されます。 [!INCLUDE[tsql](../../includes/tsql-md.md)] SP:StmtStarting **のような**ステートメントを含むイベントの場合、 **LineNumber** にはストアド プロシージャまたはバッチでのステートメントの行番号が格納されます。|  
|6|**NTUserName**|[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows のユーザー名。|  
|7|**NTDomainName**|ユーザーが所属する Windows ドメイン。|  
|8|**HostName**|要求を生成したクライアント コンピューターの名前。|  
|9|**ClientProcessID**|クライアント アプリケーションが実行されているプロセスにクライアント コンピューターによって割り当てられた ID。|  
|10|**ApplicationName**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスへの接続を作成したクライアント アプリケーションの名前。 この列には、プログラムの表示名ではなく、アプリケーションによって渡された値が格納されます。|  
|11|**LoginName**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クライアントのログイン名です。|  
|12|**SPID**|によって割り当てられたサーバー プロセス ID[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアントに関連付けられたプロセスにします。|  
|13|**Duration**|イベントの実行にかかった経過時間 (マイクロ秒単位)。 Hash Warning イベントこのデータ列は作成されません。|  
|14|**StartTime**|イベントの開始時刻 (取得できた場合)。|  
|15|**EndTime**|イベントの終了時刻。 **SQL:BatchStarting** や **SP:Starting**などの開始イベント クラスについては、この列に値が格納されません。 これはも作成されません、 **Hash Warning**イベント。|  
|16|**Reads**|イベントの代わりにサーバーによって実行される、論理ディスク読み取り回数。 この列は作成されません、**ロック: リリース**イベント。|  
|17|**Writes**|イベントの代わりにサーバーによって実行される、物理ディスクの書き込み回数。|  
|18|**CPU**|イベントに使用された CPU 時間 (ミリ秒単位)。|  
|19|**権限**|権限のビットマップを表します。セキュリティ監査で使用します。|  
|20|**Severity**|例外の重大度レベル。|  
|21|**EventSubClass**|イベント サブクラスの種類。 すべてのイベント クラスに対して、このデータ列が作成されるわけではありません。|  
|22|**Exchange Spill**|システムによって割り当てられたオブジェクト ID。|  
|23|**成功**|アクセス許可の使用状況の成功しようとします。監査に使用されます。<br /><br /> **1** = 成功**0** = 失敗|  
|24|**IndexID**|イベントの影響を受けるオブジェクトに付けられたインデックス用の ID。 オブジェクトのインデックス ID を調べるには、 **sysindexes** システム テーブルの **indid** 列を使用します。|  
|25|**IntegerData**|トレースでキャプチャされたイベント クラスに依存する整数値。|  
|26|**ServerName**|インスタンスの名前[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], か、 *servername*または*servername \instancename*、トレース中します。|  
|27|**EventClass**|記録されるイベント クラスの種類。|  
|28|**ObjectType**|などのオブジェクトの種類: テーブル、関数、またはストアド プロシージャ。|  
|29|**NestLevel**|入れ子のレベルでは、このストアド プロシージャを実行します。 参照してください[@@NESTLEVEL&#40;Transact-SQL&#41;](../../t-sql/functions/nestlevel-transact-sql.md).|  
|30|**State**|サーバーの状態、エラーが発生した場合。|  
|31|**Error**|エラー番号。|  
|32|**モード**|取得したロックのロック モード。 この列は作成されません、**ロック: リリース**イベント。|  
|33|**Handle**|イベントで参照されているオブジェクトのハンドル。|  
|34|**ObjectName**|アクセスされるオブジェクトの名前。|  
|35|**DatabaseName**|使用する指定されたデータベースの名前*データベース*ステートメント。|  
|36|**FileName**|変更されたファイル名の論理名。|  
|37|**OwnerName**|参照先オブジェクトの所有者の名前。|  
|38|**RoleName**|ステートメントの対象となっているデータベースまたはサーバー全体のロールの名前。|  
|39|**TargetUserName**|何らかのアクションの対象となるユーザー名。|  
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
|52|**BigintData1**|**bigint**値で、トレースにキャプチャするイベント クラスに依存します。|  
|53|**BigintData2**|**bigint**値で、トレースにキャプチャするイベント クラスに依存します。|  
|54|**GUID**|トレースでキャプチャされたイベント クラスに依存する GUID 値。|  
|55|**IntegerData2**|トレースにキャプチャされたイベント クラスに依存する整数値。|  
|56|**ObjectID2**|関連オブジェクトを使用可能な場合は、エンティティの ID。|  
|57|**型**|トレースにキャプチャされたイベント クラスに依存する整数値。|  
|58|**OwnerID**|ロックを所有するオブジェクトの型。 ロック イベントの場合にのみ該当します。|  
|59|**ParentName**|オブジェクトが存在するスキーマの名前。|  
|60|**IsSystem**|イベントがシステム プロセスとユーザー プロセスのどちらで発生したか。<br /><br /> **1** = システム<br /><br /> **0** = ユーザーです。|  
|61|**Offset**|ストアド プロシージャ内またはバッチ内のステートメントの開始オフセット。|  
|62|**SourceDatabaseID**|オブジェクトのソースが存在するデータベースの ID。|  
|63|**SqlHandle**|64 ビット ハッシュ。アドホック クエリやデータベースのテキスト、および SQL オブジェクトのオブジェクト ID に基づいています。 この値を **sys.dm_exec_sql_text()** に渡して、関連付けられている SQL テキストを取得できます。|  
|64|**SessionLoginName**|セッションを開始したユーザーのログイン名。 たとえば、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に **Login1** を使用して接続し、 **Login2**としてステートメントを実行した場合、 **SessionLoginName** には **Login1**が表示され、 **LoginName** には **Login2**が表示されます。 このデータ列には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインと Windows ログインの両方が表示されます。|  
  
 **[ @on=]** *on*  
 このイベントを ON (1) にするか OFF (0) にするかを指定します。 *で* は **ビット**, 、既定値はありません。  
  
 場合*で*に設定されている**1**、および*column_id*が NULL の場合、イベントが ON に設定し、すべての列を消去します。 場合*column_id*が null でない列がそのイベントを ON に設定します。  
  
 場合*で*に設定されている**0**と*column_id*が NULL の場合、イベントになって OFF されすべての列が消去されます。 場合*column_id*が null でない列が有効にし、オフします。  
  
 このテーブルの間のやり取りを示しています。 **@on**と **@columnid**します。  
  
|@on|@columnid|結果|  
|---------|---------------|------------|  
|ON (**1**)|NULL|イベントは ON になります。<br /><br /> すべての列が消去されます。|  
||NOT NULL|指定されたイベントに対して列はオンにします。|  
|OFF (**0**)|NULL|イベントになって OFF。<br /><br /> すべての列が消去されます。|  
||NOT NULL|指定されたイベントに対して列は OFF になります。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 次の表は、このストアド プロシージャの完了時に返されるコード値を示しています。  
  
|リターン コード|説明|  
|-----------------|-----------------|  
|0|エラーなし。|  
|1|不明なエラー。|  
|2|トレースは現在実行中です。 この時点でトレースを変更すると、エラーが発生します。|  
|3|指定したイベントが無効です。 イベントが存在しないか、ストアド プロシージャに対して適切なものではありません。|  
|4|指定した列は無効です。|  
|9|指定したトレース ハンドルが無効です。|  
|11|指定された列は、内部的に使用される、削除できません。|  
|13|メモリ不足。 指定したアクションを実行するための十分なメモリがない場合に返されます。|  
|16|関数は、このトレースは無効です。|  
  
## <a name="remarks"></a>コメント  
 **sp_trace_setevent**の以前のバージョンで使用可能な拡張のストアド プロシージャで実行される操作の多く[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 使用**sp_trace_setevent**以下ではなく。  
  
-   **xp_trace_addnewqueue**  
  
-   **xp_trace_eventclassrequired**  
  
-   **xp_trace_seteventclassrequired**  
  
 ユーザーが実行する必要があります**sp_trace_setevent**の各列の各イベントに追加します。 それぞれの実行中に場合**@on**に設定されている**1**、 **sp_trace_setevent**トレースのイベントの一覧を指定したイベントを追加します。 場合**@on**に設定されている**0**、 **sp_trace_setevent**リストから指定したイベントを削除します。  
  
 パラメーターのすべての SQL トレース ストアド プロシージャ (**sp_trace_xx**) は厳密に型指定されます。 これらのパラメーターを、引数の説明で指定されている正しいデータ型で指定しないと、このストアド プロシージャではエラーが返されます。  
  
 トレース ストアド プロシージャを使用した例については、「[トレースの作成 &#40;Transact-SQL&#41;](../../relational-databases/sql-trace/create-a-trace-transact-sql.md)」を参照してください。  
  
## <a name="permissions"></a>アクセス許可  
 ALTER TRACE 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [sys.fn_trace_geteventinfo &#40;TRANSACT-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-geteventinfo-transact-sql.md)   
 [sys.fn_trace_getinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql.md)   
 [sp_trace_generateevent &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql.md)   
 [SQL Server イベント クラスの参照](../../relational-databases/event-classes/sql-server-event-class-reference.md)   
 [SQL トレース (SQL Trace)](../../relational-databases/sql-trace/sql-trace.md)  
  
  
