---
title: sp_changepublication (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 08/29/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_changepublication
- sp_changepublication_TSQL
helpviewer_keywords:
- sp_changepublication
ms.assetid: c36e5865-25d5-42b7-b045-dc5036225081
caps.latest.revision: 42
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 6b7f1c4b8c6075c322944a57f81a04a8a1763fa9
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="spchangepublication-transact-sql"></a>sp_changepublication (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  パブリケーションのプロパティを変更します。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
sp_changepublication [ [ @publication = ] 'publication' ]  
    [ , [ @property = ] 'property' ]  
    [ , [ @value = ] 'value' ]  
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@publication =** ] **'***publication***'**  
 パブリケーションの名前です。 *パブリケーション*は**sysname**、既定値は NULL です。  
  
 [  **@property =** ] **'***プロパティ***'**  
 変更するパブリケーションのプロパティを指定します。 *プロパティ*は**nvarchar (255)** です。  
  
 [  **@value =** ] **'***値***'**  
 新しいプロパティ値を指定します。 *値*は**nvarchar (255)**、既定値は NULL です。  
  
 次の表に、変更可能なパブリケーションのプロパティと、プロパティの値に関する制限を示します。  
  
|プロパティ|値|Description|  
|--------------|-----------|-----------------|  
|**allow_anonymous**|**true**|指定したパブリケーションに対して匿名サブスクリプションを作成できると*immediate_sync*必要もあります**true**です。 ピア ツー ピア パブリケーションの場合は変更できません。|  
||**false**|指定したパブリケーションに対して匿名サブスクリプションを作成できません。 ピア ツー ピア パブリケーションの場合は変更できません。|  
|**allow_initialize_from_backup**|**true**|サブスクライバーでは、初期スナップショットではなくバックアップから、このパブリケーションへのサブスクリプションを初期化できます。 このプロパティを変更することはできません以外[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリケーション。|  
||**false**|サブスクライバーでは初期スナップショットを使用する必要があります。 このプロパティを変更することはできません以外[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリケーション。|  
|**allow_partition_switch**|**true**|パブリッシュされたデータベースに対して ALTER TABLE ... SWITCH ステートメントを実行できます。 詳細については、「[パーティション テーブルとパーティション インデックスのレプリケート](../../relational-databases/replication/publish/replicate-partitioned-tables-and-indexes.md)」を参照してください。|  
||**false**|パブリッシュされたデータベースに対して ALTER TABLE ... SWITCH ステートメントを実行することはできません。|  
|**allow_pull**|**true**|指定したパブリケーションに対してプル サブスクリプションを許可します。 このプロパティを変更することはできません以外[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリケーション。|  
||**false**|指定したパブリケーションに対してプル サブスクリプションを許可しません。 このプロパティを変更することはできません以外[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリケーション。|  
|**allow_push**|**true**|指定したパブリケーションに対してプッシュ サブスクリプションを許可します。|  
||**false**|指定したパブリケーションに対してプッシュ サブスクリプションを許可しません。|  
|**allow_subscription_copy**|**true**|このパブリケーションにサブスクライブするデータベースをコピーできるようにします。 このプロパティを変更することはできません以外[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリケーション。|  
||**false**|このパブリケーションにサブスクライブするデータベースをコピーできないようにします。 このプロパティを変更することはできません以外[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリケーション。|  
|**alt_snapshot_folder**||スナップショットの代替フォルダーの場所。|  
|**centralized_conflicts**|**true**|競合レコードはパブリッシャーに保存されます。 アクティブなサブスクリプションがない場合にのみ変更できます。 このプロパティを変更することはできません以外[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリケーション。|  
||**false**|競合レコードは、競合の原因となったパブリッシャーとサブスクライバーの両方に保存されます。 アクティブなサブスクリプションがない場合にのみ変更できます。 このプロパティを変更することはできません以外[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリケーション。|  
|**compress_snapshot**|**true**|代替スナップショット フォルダーにあるスナップショットは .cab ファイル形式に圧縮されます。 既定のスナップショット フォルダー内のスナップショットは圧縮できません。|  
||**false**|スナップショットは圧縮されません。これはレプリケーションの既定の動作です。|  
|**conflict_policy**|**pub wins**|パブリッシャーが競合で優先される場合に、サブスクライバーの更新で競合を解決する方法です。 このプロパティを変更できるのは、アクティブなサブスクリプションがない場合に限られます。 Oracle パブリッシャーに対してはサポートされていません。|  
||**sub reinit**|サブスクライバーの更新で、競合が発生した場合はサブスクリプションを再初期化する必要があります。 このプロパティを変更できるのは、アクティブなサブスクリプションがない場合に限られます。 Oracle パブリッシャーに対してはサポートされていません。|  
||**sub wins**|サブスクライバーが競合で優先される場合に、サブスクライバーの更新で競合を解決する方法です。 このプロパティを変更できるのは、アクティブなサブスクリプションがない場合に限られます。 Oracle パブリッシャーに対してはサポートされていません。|  
|**conflict_retention**||**int**競合の保有期間を日数で指定します。 既定の保有期間は 14 日です。 **0**競合のクリーンアップが不要であることを意味します。 Oracle パブリッシャーに対してはサポートされていません。|  
|**説明**||パブリケーションを記述するエントリです。省略可能です。|  
|**enabled_for_het_sub**|**true**|パブリケーションをサポートしていないように[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サブスクライバーです。 **enabled_for_het_sub**パブリケーションに対するサブスクリプションがある場合は変更できません。 実行する必要があります[レプリケーションのストアド プロシージャ (TRANSACT-SQL)](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md)設定する前に、次の要件に準拠する**enabled_for_het_sub** true に設定します。<br /> - **allow_queued_tran**する必要があります**false**です。<br /> - **allow_sync_tran**する必要があります**false**です。<br /> 変更する**enabled_for_het_sub**に**true**既存のパブリケーション設定を変更することがあります。 詳細については、「 [Non-SQL Server Subscribers](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md)」を参照してください。 このプロパティを変更することはできません以外[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリケーション。|  
||**false**|パブリケーションでサポートされない非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サブスクライバーです。 このプロパティを変更することはできません以外[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリケーション。|  
|**enabled_for_internet**|**true**|パブリケーションはインターネットに対応しており、サブスクライバーへのスナップショット ファイルの転送にファイル転送プロトコル (FTP) を使用できます。 パブリケーションの同期ファイルはディレクトリ C:\Program Files\Microsoft SQL Server\MSSQL\Repldata\ftp に保存されます。 *ftp_address* NULL にすることはできません。 このプロパティを変更することはできません以外[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリケーション。|  
||**false**|パブリケーションはインターネットに対応していません。 このプロパティを変更することはできません以外[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリケーション。|  
|**enabled_for_p2p**|**true**|パブリケーションでピア ツー ピア レプリケーションがサポートされます。 このプロパティを変更することはできません以外[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリケーション。<br /> 設定する**enabled_for_p2p**に**true**、次の制限が適用されます。<br /> - **allow_anonymous**する必要があります**false**<br /> - **allow_dts を含む**する必要があります**false**です。<br /> - **allow_initialize_from_backup**する必要があります**は true。**<br /> - **allow_queued_tran**する必要があります**false**です。<br /> - **allow_sync_tran**する必要があります**false**です。<br /> - **enabled_for_het_sub**する必要があります**false**です。<br /> - **independent_agent**する必要があります**true**です。<br /> - **repl_freq**する必要があります**連続**です。<br /> - **replicate_ddl**する必要があります**1**です。|  
||**false**|パブリケーションでピア ツー ピア レプリケーションがサポートされません。 このプロパティを変更することはできません以外[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリケーション。|  
|**ftp_address**||パブリケーション スナップショット ファイルに FTP でアクセスできる場所です。 このプロパティを変更することはできません以外[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリケーション。|  
|**ftp_login**||FTP サービスへの接続に使用するユーザー名です。値 ANONYMOUS は許可されます。 このプロパティを変更することはできません以外[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリケーション。|  
|**ftp_password**||FTP サービスに接続するときに使用するユーザー名に対応するパスワード。 このプロパティを変更することはできません以外[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリケーション。|  
|**ftp_port**||ディストリビューター用 FTP サービスのポート番号。 このプロパティを変更することはできません以外[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリケーション。|  
|**ftp_subdirectory**||スナップショット ファイルが作成される場所を指定します、パブリケーションが FTP を使用してスナップショットの配布をサポートしている場合。 このプロパティを変更することはできません以外[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリケーション。|  
|**immediate_sync**|**true**|スナップショット エージェントを実行するたびに、パブリケーションの同期ファイルが作成または再作成されます。 サブスクリプションの前にスナップショット エージェントが完了していれば、サブスクライバーではサブスクリプションの直後に同期ファイルを取得できます。 新しいサブスクリプションは、最近実行されたスナップショット エージェントによって生成された最新の同期ファイルを取得します。 *independent_agent*必要もあります**true**です。 追加情報の下の「解説」を参照してください**immediate_sync**です。|  
||**false**|新しいサブスクリプションがある場合にのみ、同期ファイルが作成されます。 サブスクリプションの後、スナップショット エージェントが起動して完了するまで、サブスクライバーは同期ファイルを取得できません。|  
|**independent_agent**|**true**|パブリケーションに専用のディストリビューション エージェントがあります。|  
||**false**|パブリケーションでは共有ディストリビューション エージェントが使用されます。パブリケーションおよびサブスクリプション データベースの各ペアには 1 つの共有エージェントがあります。|  
|**@p2p_continue_onconflict**|**true**|ディストリビューション エージェントは、競合の検出時に変更の処理を続行します。<br /> **注意:** の既定値を使用することをお勧め`FALSE`です。 このオプションを設定すると`TRUE`、ディストリビューション エージェントが、最高の発信元 ID を持つノードから競合する行を適用してトポロジ内のデータを収束しようとしています。 この方法では収束が保証されません。 競合が検出された後に、トポロジに一貫性があることを確認する必要があります。 詳細については、「 [Conflict Detection in Peer-to-Peer Replication](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md)」の「競合の処理」を参照してください。|  
||**false**|ディストリビューション エージェントは、競合の検出時に変更の処理を停止します。|  
|**post_snapshot_script**||ディストリビューション エージェントで実行される [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプト ファイルの場所を指定します。このスクリプトの実行は、初期同期で、レプリケートされたすべてのオブジェクト スクリプトとデータが適用された後で行われます。|  
|**pre_snapshot_script**||ディストリビューション エージェントで実行される [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプト ファイルの場所を指定します。このスクリプトの実行は、初期同期で、レプリケートされたすべてのオブジェクト スクリプトとデータが適用される前に行われます。|  
|**publish_to_ActiveDirectory**|**true**|このパラメーターは、旧バージョンのスクリプトとの互換性を保つために用意されており、非推奨とされます。 パブリケーション情報を不要になった追加することができます、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Active Directory です。|  
||**false**|Active Directory からパブリケーション情報を削除します。|  
|**queue_type**|**sql**|使用して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]トランザクションを格納します。 このプロパティを変更できるのは、アクティブなサブスクリプションがない場合に限られます。<br /><br /> 注: サポートを使用して[!INCLUDE[msCoName](../../includes/msconame-md.md)]メッセージ キューは廃止されました。 値を指定する**msmq**の*値*でエラーが発生します。|  
|**repl_freq**|**継続的です**|ログ ベースのすべてのトランザクションの出力をパブリッシュします。|  
||**スナップショット**|スケジュールされた同期イベントのみをパブリッシュします。|  
|**replicate_ddl**|**1**|パブリッシャー側で実行されるデータ定義言語 (DDL) ステートメントがレプリケートされます。 このプロパティを変更することはできません以外[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリケーション。|  
||**0**|DDL ステートメントはレプリケートされません。 このプロパティを変更することはできません以外[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリケーション。 スキーマ変更のレプリケーションは、ピア ツー ピア レプリケーションを使用する場合は無効にできません。|  
|**replicate_partition_switch**|**true**|パブリッシュされたデータベースに対して実行される ALTER TABLE ... SWITCH ステートメントは、サブスクライバーにレプリケーションする必要があります。 このオプションは有効な場合にのみ、 *allow_partition_switch*が TRUE に設定します。 詳細については、「[パーティション テーブルとパーティション インデックスのレプリケート](../../relational-databases/replication/publish/replicate-partitioned-tables-and-indexes.md)」を参照してください。|  
||**false**|ALTER TABLE ... SWITCH ステートメントはサブスクライバーにレプリケートしないでください。|  
|**保有期間**||**int**保有期間を時間、サブスクリプションの利用状況を表すです。 保有期間内にサブスクリプションがアクティブ状態でなくなると削除されます。|  
|**snapshot_in_defaultfolder**|**true**|スナップショット ファイルは既定のスナップショット フォルダーに格納されます。 場合*alt_snapshot_folder*も指定スナップショット ファイルは、既定と代替位置に格納します。|  
||**false**|指定された別の場所にスナップショット ファイルが格納されている*alt_snapshot_folder*です。|  
|**ステータス**|**アクティブ**|パブリケーション データはパブリケーションが作成された直後にサブスクライバーで使用できます。 Oracle パブリッシャーに対してはサポートされていません。|  
||**非アクティブ**|パブリケーション データはパブリケーションが作成されてもサブスクライバーで使用できません。 Oracle パブリッシャーに対してはサポートされていません。|  
|**sync_method**|**native**|サブスクリプションの同期時に、すべてのテーブルのネイティブ モード一括コピー出力を使用します。|  
||**character**|サブスクリプションの同期時に、すべてのテーブルについてキャラクター モード一括コピー出力を使用します。|  
||**同時実行**|すべてのテーブルについてネイティブ モード BCP 出力を使用しますが、スナップショット生成処理中にテーブルをロックしません。 スナップショット レプリケーションには無効です。|  
||**concurrent_c**|すべてのテーブルについてキャラクター モード BCP 出力を使用しますが、スナップショット生成処理中にテーブルをロックしません。 スナップショット レプリケーションには無効です。|  
|**taskid**||このプロパティは現在サポートされておらず、非推奨とされます。|  
|**allow_drop**|**true**|により、`DROP TABLE`トランザクション レプリケーションの一部であるアーティクルの DLL をサポートします。 サポートされるバージョンの最小: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Service Pack 2 以降および[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]Service Pack 1 またはそれ以降。 その他の参照: [KB 3170123](https://support.microsoft.com/en-us/help/3170123/supports-drop-table-ddl-for-articles-that-are-included-in-transactional-replication-in-sql-server-2014-or-in-sql-server-2016-sp1)|
||**false**|無効に`DROP TABLE`トランザクション レプリケーションの一部であるアーティクルの DLL をサポートします。 これは、**既定**このプロパティの値。|
|**NULL** (既定値)||サポートされる値の一覧を返します*プロパティ*です。|  
  
[  **@force_invalidate_snapshot =** ]*更によって*  
 このストアド プロシージャが実行する操作によって既存のスナップショットが無効になることを許可します。 *更によって*は、**ビット**、既定値は**0**します。  
  - **0**スナップショットが無効であることをアーティクルへの変更が発生しないことを指定します。 ストアド プロシージャで、変更に新しいスナップショットが必要であることが検出されると、エラーが発生し、変更は加えられません。  
  - **1**アーティクルへの変更は、無効になるスナップショットで発生する可能性がありますを指定します。 新しいスナップショットが必要となる既存のサブスクリプションがある場合、この値は、既存のスナップショットに設定して、新しいスナップショットを生成のアクセス許可を示します。   
変更によって新しいスナップショットの生成が必要になるプロパティについては、「解説」を参照してください。  
  
[ **@force_reinit_subscription =** ]*更によって*  
 このストアド プロシージャが実行する操作によって、既存のサブスクリプションの再初期化が必要になることを許可します。 *更によって*は、**ビット**、既定値は**0**します。  
  - **0**アーティクルへの変更によってが再初期化するサブスクリプションを指定します。 変更に既存のサブスクリプションの再初期化が必要であることをストアド プロシージャが検出すると、エラーが発生し、変更は加えられません。  
  - **1**アーティクルへの変更が既存のサブスクリプションを初期化するには、サブスクリプションの再初期化を許可します。  
  
[ **@publisher** =] **'***パブリッシャー***'**  
 指定以外[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。 *パブリッシャー*は**sysname**、既定値は NULL です。  
  
  > [!NOTE]  
  >  *パブリッシャー*でアーティクルのプロパティを変更するときに使用しないで、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_changepublication**はスナップショット レプリケーションおよびトランザクション レプリケーションで使用します。  
  
 次のプロパティを変更した後、新しいスナップショットを生成する必要がありの値を指定する必要があります**1**の*更によって*パラメーター。  
-   **alt_snapshot_folder**  
-   **compress_snapshot**  
-   **enabled_for_het_sub**  
-   **ftp_address**  
-   **ftp_login**  
-   **ftp_password**  
-   **ftp_port**  
-   **ftp_subdirectory**  
-   **post_snapshot_script**  
-   **pre_snapshot_script**  
-   **snapshot_in_defaultfolder**  
-   **sync_mode**  
  
使用して、Active Directory パブリケーション オブジェクトの一覧に、 **publish_to_active_directory** 、パラメーター、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]オブジェクトは、Active Directory で既に作成する必要があります。  
  
## <a name="impact-of-immediate-sync"></a>即時同期の影響  
 即時同期がオンのとき、サブスクリプションが存在しない場合でも、初期スナップショットが生成された直後に、ログ内のすべての変更が追跡されます。 ログに記録された変更は、お客様が新しいピア ノードを追加するバックアップを使用する場合に使用されます。 バックアップを復元した後、ピアは、バックアップが作成された後に発生しているその他の変更と同期されます。 コマンドがディストリビューション データベースに追跡されるため、同期ロジックは最後の LSN のバックアップを確認し、このコマンドは、最大保有期間内で、バックアップを行った場合に使用できることを知ること、開始点として使用できます。 (既定値の最小保有期間は 0 時間、最大保有期間は 24 時間です)。  
  
 即時同期がオフの場合、変更は少なくとも最小保有期間に保持されのまだレプリケートされているすべてのトランザクションがすぐにクリーンアップします。 即時同期が無効で、既定の保有期間で構成される場合、バックアップの作成後に必要な変更がクリーンアップされたため、新しいピア ノードが正しく初期化されない可能性があります。 残された唯一のオプションがトポロジの停止です。 即時同期を有効に設定すると、柔軟性が向上するため、これは P2P アプリケーションにお勧めの設定です。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_changepublication](../../relational-databases/replication/codesnippet/tsql/sp-changepublication-tra_1.sql)]  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_changepublication**です。  
  
## <a name="see-also"></a>参照  
 [パブリケーション プロパティの表示および変更](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [パブリケーションとアーティクルのプロパティの変更](../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [sp_addpublication &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md)   
 [sp_droppublication &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droppublication-transact-sql.md)   
 [sp_helppublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md)   
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
