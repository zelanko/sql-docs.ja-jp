---
title: sp_helppullsubscription (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
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
- sp_helppullsubscription_TSQL
- sp_helppullsubscription
helpviewer_keywords:
- sp_helppullsubscription
ms.assetid: a0d9c3f1-1fe9-497c-8e2f-5b74f47a7346
caps.latest.revision: 26
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: ada01ed2c7e447077026e65a9ca5776911b14dcd
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sphelppullsubscription-transact-sql"></a>sp_helppullsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  サブスクライバー側の 1 つ以上のサブスクリプションに関する情報を表示します。 このストアド プロシージャは、サブスクライバー側でサブスクリプション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helppullsubscription [ [ @publisher = ] 'publisher' ]  
    [ , [ @publisher_db = ] 'publisher_db' ]   
    [ , [ @publication = ] 'publication' ]  
    [ , [ @show_push = ] 'show_push' ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@publisher=**] **'***publisher***'**  
 リモート サーバーの名前を指定します。 *パブリッシャー*は**sysname**、既定値は**%**、すべてのパブリッシャーに対して情報が返されます。  
  
 [ **@publisher_db=**] **'***publisher_db***'**  
 パブリッシャー データベースの名前です。 *publisher_db*は**sysname**、既定値は**%**、すべてのパブリッシャー データベースが返されます。  
  
 [ **@publication=**] **'***publication***'**  
 パブリケーションの名前です。 *パブリケーション*は**sysname**、既定値は**%**、すべてのパブリケーションが返されます。 このパラメーターがすべて、プル サブスクリプションのみ independent_agent = **0**が返されます。  
  
 [  **@show_push=**] **'***show_push***'**  
 すべてのプッシュ サブスクリプションを返すかどうかを指定します。 *show_push*は**nvarchar (5)**、既定値は FALSE を返さないことプッシュ サブスクリプションです。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**パブリッシャー**|**sysname**|パブリッシャーの名前です。|  
|**パブリッシャー データベース**|**sysname**|パブリッシャー データベースの名前です。|  
|**パブリケーション**|**sysname**|パブリケーションの名前です。|  
|**independent_agent**|**bit**|このパブリケーションに対して、スタンドアロンのディストリビューション エージェントがあるかどうかを示します。|  
|**サブスクリプションの種類**|**int**|パブリケーションへのサブスクリプションの種類。|  
|**ディストリビューション エージェント**|**nvarchar(100)**|サブスクリプションを処理するディストリビューション エージェント。|  
|**パブリケーションの説明**|**nvarchar (255)**|パブリケーションの説明です。|  
|**最終更新時刻**|**date**|サブスクリプション情報を更新した時刻。 これは、ISO 日付 (114) + ODBC 時刻 (121) の UNICODE 文字列です。 形式は yyyymmdd hh:mi:sss.mmm で、yyyy は年、mm は月、dd は日、hh は時間、mi は分、sss は秒、mmm はミリ秒を表します。|  
|**サブスクリプション名**|**varchar(386)**|サブスクリプションの名前。|  
|**最後のトランザクションのタイムスタンプ**|**varbinary(16)**|最後にレプリケートしたトランザクションのタイムスタンプ。|  
|**更新モード**|**tinyint**|許可された更新の種類。|  
|**ディストリビューション エージェント job_id**|**int**|ディストリビューション エージェントのジョブ ID。|  
|**enabled_for_synmgr**|**int**|サブスクリプションを介した同期が可能かどうか、[!INCLUDE[msCoName](../../includes/msconame-md.md)]同期マネージャーです。|  
|**サブスクリプション guid**|**binary(16)**|パブリケーションに対してサブスクリプションのバージョンのグローバル識別子です。|  
|**subid**|**binary(16)**|匿名サブスクリプションを表すグローバル識別子。|  
|**immediate_sync**|**bit**|スナップショット エージェントを実行するたびに、同期ファイルを作成または再作成するかどうかを示します。|  
|**パブリッシャーのログイン**|**sysname**|パブリッシャーで使用されたログイン ID[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。|  
|**パブリッシャーのパスワード**|**nvarchar (524)**|パブリッシャーで使用する (暗号化) パスワード[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。|  
|**パブリッシャー security_mode**|**int**|パブリッシャーで実装されているセキュリティ モード。<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証<br /><br /> **1** = Windows 認証<br /><br /> **2**同期トリガーを使用する静的なを = **sysservers**をリモート プロシージャ コール (RPC) を行うにはエントリと*パブリッシャー*で定義する必要があります、 **sysservers**リモート サーバーまたはリンク サーバーとしてのテーブルです。|  
|**ディストリビューター**|**sysname**|ディストリビューターの名前です。|  
|**distributor_login**|**sysname**|場合はディストリビューターで使用されたログイン ID[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。|  
|**distributor_password**|**nvarchar (524)**|場合はディストリビューターで使用するパスワード (暗号化)[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。|  
|**distributor_security_mode**|**int**|ディストリビューターで実装されているセキュリティ モード:<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証<br /><br /> **1** = Windows 認証|  
|**ftp_address**|**sysname**|これは旧バージョンとの互換性のためにだけ用意されています。|  
|**ftp_port**|**int**|これは旧バージョンとの互換性のためにだけ用意されています。|  
|**ftp_login**|**sysname**|これは旧バージョンとの互換性のためにだけ用意されています。|  
|**ftp_password**|**nvarchar (524)**|これは旧バージョンとの互換性のためにだけ用意されています。|  
|**alt_snapshot_folder**|**nvarchar (255)**|スナップショット フォルダーが格納されている場所。スナップショット フォルダーが既定の場所以外、または既定の場所とさらに別の場所に保存されている場合が対象となります。|  
|**working_directory**|**nvarchar (255)**|該当するオプションが指定され、ファイル転送プロトコル (FTP) を使ってスナップショット ファイルを転送する場合の、転送先ディレクトリの完全修飾パス。|  
|**@use_ftp**|**bit**|インターネット経由でサブスクリプションがパブリケーションにサブスクライブして、FTP アドレス プロパティが構成されます。 場合**0**サブスクリプションは FTP を使用していません。 場合**1**サブスクリプションは FTP を使用しています。|  
|**publication_type**|**int**|パブリケーションのレプリケーションの種類。<br /><br /> **0** = トランザクション レプリケーション<br /><br /> **1** = スナップショット レプリケーション<br /><br /> **2** = マージ レプリケーション|  
|**dts_package_name**|**sysname**|データ変換サービス (DTS) パッケージの名前。|  
|**dts_package_location**|**int**|DTS パッケージの格納場所。<br /><br /> **0** = ディストリビューター<br /><br /> **1**サブスクライバーを =|  
|**offload_agent**|**bit**|エージェントをリモートから起動できるかどうかを指定します。 場合**0**エージェントをリモートでアクティブにできません。|  
|**offload_server**|**sysname**|リモートからのアクティブ化に使用するサーバーのネットワーク名。|  
|**last_sync_status**|**int**|サブスクリプションの状態:<br /><br /> **0** = すべてのジョブが開始を待機しています。<br /><br /> **1** = 1 つ以上のジョブが起動中<br /><br /> **2** = すべてのジョブが正常に実行されました<br /><br /> **3** = 少なくとも 1 つジョブが実行中<br /><br /> **4** = すべてのジョブがスケジュールされ、アイドル状態<br /><br /> **5** = 少なくとも 1 つジョブが前回のエラーの後に実行しようとしています<br /><br /> **6** = 少なくとも 1 つは正常に実行するジョブが失敗しました|  
|**last_sync_summary**|**sysname**|前回の同期化の結果に関する説明。|  
|**last_sync_time**|**datetime**|サブスクリプション情報を更新した時刻。 これは、ISO 日付 (114) + ODBC 時刻 (121) の UNICODE 文字列です。 形式は yyyymmdd hh:mi:sss.mmm で、yyyy は年、mm は月、dd は日、hh は時間、mi は分、sss は秒、mmm はミリ秒を表します。|  
|**job_login**|**nvarchar(512)**|形式で返される、ディストリビューション エージェントを実行する Windows アカウントは、*ドメイン*\\*username*です。|  
|**job_password**|**sysname**|セキュリティ上の理由の値"**\*\*\*\*\*\*\*\*\*\***"が常に返されます。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_helppullsubscription**は、スナップショットおよびトランザクション レプリケーションで使用します。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_helppullsubscription**です。  
  
## <a name="see-also"></a>参照  
 [sp_addpullsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md)   
 [sp_droppullsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droppullsubscription-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
