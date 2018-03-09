---
title: "sp_helpmergepullsubscription (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_helpmergepullsubscription
- sp_helpmergepullsubscription_TSQL
helpviewer_keywords:
- sp_helpmergepullsubscription
ms.assetid: 6f3125f3-0dfa-40bd-b725-8aa1591234f6
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4fdb0047d265b2f848b77a0b84445f8683132833
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sphelpmergepullsubscription-transact-sql"></a>sp_helpmergepullsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  サブスクライバーに存在するプル サブスクリプションに関する情報を返します。 このストアド プロシージャは、サブスクライバー側でサブスクリプション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helpmergepullsubscription [ [ @publication=] 'publication']  
    [ , [ @publisher=] 'publisher']  
    [ , [ @publisher_db=] 'publisher_db']  
    [ , [ @subscription_type=] 'subscription_type']  
```  
  
## <a name="argument"></a>引数  
 [  **@publication=**] **'***パブリケーション***'**  
 パブリケーションの名前です。 *パブリケーション*は**sysname**、既定値は **%**です。 場合*パブリケーション*は **%** 、すべてのマージ パブリケーションと、現在のデータベース内のサブスクリプションに関する情報が返されます。  
  
 [  **@publisher=**] **'***パブリッシャー***'**  
 パブリッシャーの名前です。 *パブリッシャー*は**sysname**、既定値は **%**です。  
  
 [  **@publisher_db=**] **'***publisher_db***'**  
 パブリッシャー データベースの名前です。 *publisher_db*は**sysname**、既定値は **%**です。  
  
 [  **@subscription_type=**] **'***subscription_type***'**  
 プル サブスクリプションを表示するかどうかを指定します。 *subscription_type*は**nvarchar (10)**、既定値は**'pull'**です。 有効な値は**'push'**、 **'pull'**、または**'both'**です。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**subscription_name**|**nvarchar (1000)**|サブスクリプションの名前。|  
|**パブリケーション**|**sysname**|パブリケーションの名前です。|  
|**パブリッシャー**|**sysname**|パブリッシャーの名前です。|  
|**publisher_db**|**sysname**|パブリッシャー データベースの名前です。|  
|**サブスクライバー**|**sysname**|サブスクライバーの名前です。|  
|**subscription_db**|**sysname**|サブスクリプション データベースの名前です。|  
|**ステータス**|**int**|サブスクリプションの状態:<br /><br /> **0** = 非アクティブなサブスクリプション<br /><br /> **1** = アクティブなサブスクリプション<br /><br /> **2** = 削除されたサブスクリプション<br /><br /> **3**デタッチされたサブスクリプションを =<br /><br /> **4**アタッチされたサブスクリプションを =<br /><br /> **5** = アップロードと共に再初期化するサブスクリプションにマークされています。<br /><br /> **6** = 失敗したサブスクリプションのアタッチ<br /><br /> **7** = バックアップから復元されたサブスクリプション|  
|**subscriber_type**|**int**|サブスクライバーの種類。<br /><br /> **1** = グローバル<br /><br /> **2** = ローカル<br /><br /> **3** = 匿名|  
|**subscription_type**|**int**|サブスクリプションの種類。<br /><br /> **0**プッシュを =<br /><br /> **1**プルを =<br /><br /> **2** = 匿名|  
|**優先順位**|**float(8)**|サブスクリプションの優先度です。 値がある必要がありますより小さい**100.00**です。|  
|**sync_type**|**tinyint**|サブスクリプションの同期の種類。<br /><br /> **1**自動を =<br /><br /> **2** = スナップショットは使用されません。|  
|**説明**|**nvarchar (255)**|プル サブスクリプションの簡単な説明です。|  
|**merge_jobid**|**binary (16)**|マージ エージェントのジョブ ID。|  
|**enabled_for_syncmgr**|**int**|サブスクリプションを介した同期が可能かどうか、[!INCLUDE[msCoName](../../includes/msconame-md.md)]同期マネージャーです。|  
|**last_updated**|**nvarchar(26)**|マージ エージェントがサブスクリプションの同期に最後に成功した時刻です。|  
|**publisher_login**|**sysname**|パブリッシャーのログイン名です。|  
|**publisher_password**|**sysname**|パブリッシャーのパスワード。|  
|**publisher_security_mode**|**int**|パブリッシャーのセキュリティ モードを指定します。<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証<br /><br /> **1** = Windows 認証|  
|**ディストリビューター**|**sysname**|ディストリビューターの名前です。|  
|**distributor_login**|**sysname**|ディストリビューターのログイン名。|  
|**distributor_password**|**sysname**|ディストリビューターのパスワード。|  
|**distributor_security_mode**|**int**|ディストリビューターのセキュリティ モードを指定します。<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証<br /><br /> **1** = Windows 認証|  
|**ftp_address**|**sysname**|旧バージョンとの互換性を保つのために利用できます。 ディストリビューター用のファイル転送プロトコル (FTP) サービスのネットワーク アドレスです。|  
|**ftp_port**|**int**|旧バージョンとの互換性を保つのために利用できます。 ディストリビューター用の FTP サービスのポート番号です。|  
|**ftp_login**|**sysname**|旧バージョンとの互換性を保つのために利用できます。 FTP サービスに接続するときに使用するユーザー名です。|  
|**ftp_password**|**sysname**|旧バージョンとの互換性を保つのために利用できます。 FTP サービスに接続するときに使用するユーザー パスワードです。|  
|**alt_snapshot_folder**|**nvarchar (255)**|スナップショット フォルダーが格納されている場所。スナップショット フォルダーが既定の場所以外、または既定の場所とさらに別の場所に保存されている場合が対象となります。|  
|**working_directory**|**nvarchar (255)**|該当するオプションが指定され、FTP を使ってスナップショット ファイルを転送する場合の、転送先のディレクトリの完全修飾パスです。|  
|**@use_ftp**|**bit**|サブスクリプションはインターネットを経由してパブリケーションにサブスクライブしており、FTP アドレス プロパティが構成されています。 場合**0**サブスクリプションは FTP を使用していません。 場合**1**サブスクリプションは FTP を使用しています。|  
|**offload_agent**|**bit**|エージェントをリモートから起動できるかどうかを指定します。 場合**0**エージェントをリモートでアクティブにできません。|  
|**offload_server**|**sysname**|リモートから起動するときに使用するサーバーの名前です。|  
|**use_interactive_resolver**|**int**|調整時に対話型の競合回避モジュールを使用するかどうかを示します。 場合**0**、インタラクティブ競合回避モジュールは使用されません。|  
|**subid**|**uniqueidentifier**|サブスクライバーの ID です。|  
|**dynamic_snapshot_location**|**nvarchar (255)**|スナップショット ファイルが保存されるフォルダーへのパス。|  
|**last_sync_status**|**int**|同期の状態です。<br /><br /> **1** = 起動中<br /><br /> **2** = に成功しました<br /><br /> **3** = 実行中<br /><br /> **4** = アイドル状態<br /><br /> **5**失敗後再試行中を =<br /><br /> **6** = に失敗しました<br /><br /> **7** = 検証失敗<br /><br /> **8** = 検証合格<br /><br /> **9**シャット ダウンの要求を =|  
|**last_sync_summary**|**sysname**|前回の同期化の結果に関する説明。|  
|**@use_web_sync**|**bit**|HTTPS 経由で、サブスクリプションを同期させることができるかどうかの値を指定します**1**この機能が有効になっていることを意味します。|  
|**internet_url**|**nvarchar (260)**|Web 同期中にレプリケーション リスナーの位置を表す URL です。|  
|**internet_login**|**nvarchar (128)**|基本認証を使用して Web 同期をホストしている Web サーバーに接続するときにマージ エージェントが使用するログインです。|  
|**internet_password**|**nvarchar (524)**|基本認証を使用して Web 同期をホストしている Web サーバーに接続するときにマージ エージェントが使用するログインのパスワードです。|  
|**internet_security_mode**|**int**|Web 同期をホストしている Web サーバーに接続するときに使用される認証モードです。 値**1** 、Windows 認証を示し、値は**0**意味[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。|  
|**internet_timeout**|**int**|Web 同期要求が期限切れとなるまでの時間 (秒単位)。|  
|**ホスト名**|**nvarchar (128)**|オーバー ロードされた値を指定[HOST_NAME](../../t-sql/functions/host-name-transact-sql.md)パラメーター化された行フィルターの WHERE 句でこの関数を使用する場合。|  
|**job_login**|**nvarchar(512)**|形式で返される、マージ エージェントを実行する Windows アカウントは、*ドメイン*\\*username*です。|  
|**job_password**|**sysname**|セキュリティ上の理由の値"**\*\*\*\*\*\*\*\*\*\***"が常に返されます。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_helpmergepullsubscription**はマージ レプリケーションで使用します。 結果セットで返される日付に**last_updated**としてフォーマットされている*YYYYMMDD hh:mm:ss.fff*です。  
  
## <a name="permissions"></a>Permissions  
 メンバーにのみ、 **sysadmin**固定サーバー ロールおよび**db_owner**固定データベース ロールが実行できる**sp_helpmergepullsubscription**です。  
  
## <a name="see-also"></a>参照  
 [sp_addmergepullsubscription &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md)   
 [sp_changemergepullsubscription &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-changemergepullsubscription-transact-sql.md)   
 [sp_dropmergepullsubscription &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-dropmergepullsubscription-transact-sql.md)   
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
