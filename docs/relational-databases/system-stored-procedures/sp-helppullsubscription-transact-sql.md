---
title: sp_helppullsubscription (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helppullsubscription_TSQL
- sp_helppullsubscription
helpviewer_keywords:
- sp_helppullsubscription
ms.assetid: a0d9c3f1-1fe9-497c-8e2f-5b74f47a7346
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 10a8184fdad0c25c2377c5ed9df0a318aba736a2
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58527774"
---
# <a name="sphelppullsubscription-transact-sql"></a>sp_helppullsubscription (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  サブスクライバーでは、1 つまたは複数のサブスクリプションに関する情報を表示します。 このストアド プロシージャは、サブスクライバーのサブスクリプション データベースで実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helppullsubscription [ [ @publisher = ] 'publisher' ]  
    [ , [ @publisher_db = ] 'publisher_db' ]   
    [ , [ @publication = ] 'publication' ]  
    [ , [ @show_push = ] 'show_push' ]  
```  
  
## <a name="arguments"></a>引数  
`[ @publisher = ] 'publisher'` リモート サーバーの名前です。 *パブリッシャー*は**sysname**、既定値は**%**、すべてのパブリッシャーに対して情報が返されます。  
  
`[ @publisher_db = ] 'publisher_db'` パブリッシャー データベースの名前です。 *publisher_db*は**sysname**、既定値は**%**、すべてのパブリッシャー データベースが返されます。  
  
`[ @publication = ] 'publication'` パブリケーションの名前です。 *パブリケーション*は**sysname**、既定値は**%**、すべてのパブリケーションが返されます。 Independent_agent だけプル サブスクリプションをすべて、このパラメーターが等しい場合 = **0**が返されます。  
  
`[ @show_push = ] 'show_push'` すべてのプッシュ サブスクリプションは返されるかどうか、です。 *show_push*は**nvarchar (5)**、既定値は FALSE を返さないプッシュ サブスクリプションです。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**パブリッシャー**|**sysname**|パブリッシャーの名前。|  
|**パブリッシャー データベース**|**sysname**|パブリッシャー データベースの名前です。|  
|**パブリケーション**|**sysname**|パブリケーションの名前。|  
|**independent_agent**|**bit**|このパブリケーションに対して、スタンドアロンのディストリビューション エージェントがあるかどうかを示します。|  
|**サブスクリプションの種類**|**int**|パブリケーションに対するサブスクリプションの種類。|  
|**ディストリビューション エージェント**|**nvarchar(100)**|ディストリビューション エージェントがサブスクリプションを処理します。|  
|**パブリケーションの説明**|**nvarchar (255)**|パブリケーションの説明。|  
|**最終更新時刻**|**date**|サブスクリプション情報が更新された時刻。 これは、ISO 日付 (114) + ODBC 時刻 (121) の UNICODE 文字列です。 形式は yyyymmdd hh:mi:sss.mmm 'yyyy' は、年 'mm は月、dd は日、'hh' は、'mi は分、sss は秒、および mmm はミリ秒です。|  
|**サブスクリプション名**|**varchar(386)**|サブスクリプションの名前。|  
|**最後のトランザクションのタイムスタンプ**|**varbinary(16)**|最後にレプリケートされたトランザクションのタイムスタンプ。|  
|**更新モード**|**tinyint**|許可された更新の種類です。|  
|**ディストリビューション エージェント job_id**|**int**|ディストリビューション エージェントのジョブ ID。|  
|**enabled_for_synmgr**|**int**|サブスクリプションを介した同期が可能かどうか、[!INCLUDE[msCoName](../../includes/msconame-md.md)]同期マネージャーです。|  
|**サブスクリプション guid**|**binary(16)**|パブリケーションに対してサブスクリプションのバージョンのグローバル識別子です。|  
|**subid**|**binary(16)**|匿名サブスクリプションのグローバル識別子です。|  
|**immediate_sync**|**bit**|スナップショット エージェントを実行するたびに、同期ファイルを作成または再作成するかどうかを示します。|  
|**パブリッシャー ログイン**|**sysname**|パブリッシャーで使用されたログイン ID[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。|  
|**パブリッシャーのパスワード**|**nvarchar(524)**|パブリッシャーで使用するパスワード (暗号化)[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。|  
|**パブリッシャー security_mode**|**int**|パブリッシャーで実装されているセキュリティ モード。<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証<br /><br /> **1** = Windows 認証<br /><br /> **2**静的な同期のトリガーの使用を = **sysservers**リモート プロシージャ呼び出し (RPC) を実行するエントリと*パブリッシャー*で定義する必要があります、 **sysservers**リモート サーバーまたはリンク サーバーとしてのテーブル。|  
|**ディストリビューター**|**sysname**|ディストリビューターの名前。|  
|**distributor_login**|**sysname**|ディストリビューターで使用されたログイン ID[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。|  
|**distributor_password**|**nvarchar(524)**|ディストリビューターで使用するパスワード (暗号化)[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。|  
|**distributor_security_mode**|**int**|ディストリビューターで実装されているセキュリティ モード:<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証<br /><br /> **1** = Windows 認証|  
|**ftp_address**|**sysname**|これは旧バージョンとの互換性のためにだけ用意されています。|  
|**ftp_port**|**int**|これは旧バージョンとの互換性のためにだけ用意されています。|  
|**ftp_login**|**sysname**|これは旧バージョンとの互換性のためにだけ用意されています。|  
|**ftp_password**|**nvarchar(524)**|これは旧バージョンとの互換性のためにだけ用意されています。|  
|**alt_snapshot_folder**|**nvarchar (255)**|スナップショット フォルダーの場合は、場所は以外、またはさらに、既定の場所に格納される場所。|  
|**working_directory**|**nvarchar (255)**|該当するオプションが指定され、ファイル転送プロトコル (FTP) を使ってスナップショット ファイルを転送する場合の、転送先ディレクトリの完全修飾パス。|  
|**use_ftp**|**bit**|インターネット経由でサブスクリプションがパブリケーションにサブスクライブして、FTP アドレス プロパティが構成されます。 場合**0**サブスクリプションは FTP を使用していません。 場合**1**サブスクリプションは FTP を使用しています。|  
|**publication_type**|**int**|パブリケーションのレプリケーションの種類。<br /><br /> **0** = トランザクション レプリケーション<br /><br /> **1** = スナップショット レプリケーション<br /><br /> **2** = マージ レプリケーション|  
|**dts_package_name**|**sysname**|データ変換サービス (DTS) パッケージの名前を指定します。|  
|**dts_package_location**|**int**|DTS パッケージが格納される場所:<br /><br /> **0** = ディストリビューター<br /><br /> **1** = サブスクライバー|  
|**offload_agent**|**bit**|エージェントをリモートから起動できるかどうかを指定します。 場合**0**エージェントをリモートでアクティブにできません。|  
|**offload_server**|**sysname**|リモート アクティブ化に使用するサーバーのネットワーク名を指定します。|  
|**last_sync_status**|**int**|サブスクリプションの状態:<br /><br /> **0** = すべてのジョブが起動待ち<br /><br /> **1** = 1 つ以上のジョブが起動中<br /><br /> **2** = すべてのジョブが正常に実行されました<br /><br /> **3** = 少なくとも 1 つジョブが実行中<br /><br /> **4** = すべてのジョブがスケジュールされ、アイドル状態<br /><br /> **5** = 少なくとも 1 つジョブが前回のエラーの後に実行しようとしています<br /><br /> **6** = 少なくとも 1 つが正常に実行するジョブが失敗しました|  
|**last_sync_summary**|**sysname**|最後の同期の結果の説明です。|  
|**last_sync_time**|**datetime**|サブスクリプション情報が更新された時刻。 これは、ISO 日付 (114) + ODBC 時刻 (121) の UNICODE 文字列です。 形式は yyyymmdd hh:mi:sss.mmm 'yyyy' は、年 'mm は月、dd は日、'hh' は、'mi は分、sss は秒、および mmm はミリ秒です。|  
|**job_login**|**nvarchar(512)**|形式で返されるディストリビューション エージェントを実行する Windows アカウントは、*ドメイン*\\*username*します。|  
|**job_password**|**sysname**|セキュリティ上の理由の値"**\*\*\*\*\*\*\*\*\*\***"が常に返されます。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_helppullsubscription**スナップショットおよびトランザクション レプリケーションで使用されます。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_helppullsubscription**します。  
  
## <a name="see-also"></a>参照  
 [sp_addpullsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md)   
 [sp_droppullsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droppullsubscription-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
