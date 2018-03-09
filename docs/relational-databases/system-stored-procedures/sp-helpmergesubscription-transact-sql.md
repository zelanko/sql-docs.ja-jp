---
title: "sp_helpmergesubscription (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
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
- sp_helpmergesubscription
- sp_helpmergesubscription_TSQL
helpviewer_keywords:
- sp_helpmergesubscription
ms.assetid: da564112-f769-4e67-9251-5699823e8c86
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 85f9d4b9bba5d3dd6e56fcda1a81b6eafd49223d
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sphelpmergesubscription-transact-sql"></a>sp_helpmergesubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  マージ パブリケーションへのサブスクリプション (プッシュ サブスクリプションとプル サブスクリプション) に関する情報を返します。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されるか、再パブリッシュしているサブスクライバー側でサブスクリプション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helpmergesubscription [ [ @publication=] 'publication']  
    [ , [ @subscriber=] 'subscriber']  
    [ , [ @subscriber_db=] 'subscriber_db']  
    [ , [ @publisher=] 'publisher']  
    [ , [ @publisher_db=] 'publisher_db']  
    [ , [ @subscription_type=] 'subscription_type']  
    [ , [ @found=] 'found' OUTPUT]  
```  
  
## <a name="arguments"></a>引数  
 [  **@publication=**] **'***パブリケーション***'**  
 パブリケーションの名前です。 *パブリケーション*は**sysname**、既定値は **%**です。 パブリケーションが存在し、識別子の規則に従っている必要があります。 NULL の場合、または **%** 、すべてのマージ パブリケーションと、現在のデータベース内のサブスクリプションに関する情報が返されます。  
  
 [  **@subscriber=**] **'***サブスクライバー***'**  
 サブスクライバーの名前です。 *サブスクライバー*は**sysname**、既定値は **%**です。 NULL または % の場合は、指定したパブリケーションへのすべてのサブスクリプションに関する情報が返されます。  
  
 [  **@subscriber_db=**] **'***@subscriber_db***'**  
 サブスクリプション データベースの名前です。 *@subscriber_db*は**sysname**、既定値は **%** 、すべてのサブスクリプション データベースに関する情報が返されます。  
  
 [  **@publisher=**] **'***パブリッシャー***'**  
 パブリッシャーの名前です。 パブリッシャーは有効なサーバーであることが必要です。 *パブリッシャー*は**sysname**、既定値は **%** 、すべてのパブリッシャーに関する情報が返されます。  
  
 [  **@publisher_db=**] **'***publisher_db***'**  
 パブリッシャー データベースの名前です。 *publisher_db*は**sysname**、既定値は **%** 、すべてのパブリッシャー データベースに関する情報が返されます。  
  
 [  **@subscription_type=**] **'***subscription_type***'**  
 サブスクリプションの種類を指定します。 *subscription_type*は**nvarchar (15)**、これらの値のいずれかを指定できます。  
  
|値|Description|  
|-----------|-----------------|  
|**プッシュ**(既定値)|プッシュ サブスクリプション|  
|**プル**|プル サブスクリプション|  
|**両方**|プッシュおよびプル サブスクリプションの両方|  
  
 [  **@found=**] **'***見つかった***' 出力**  
 行を返すことを示すフラグです。 *見つかった*は**int**と出力パラメーター、既定値は NULL です。 **1**パブリケーションが見つかったことを示します。 **0**パブリケーションが見つからないことを示します。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**subscription_name**|**sysname**|サブスクリプションの名前。|  
|**パブリケーション**|**sysname**|パブリケーションの名前です。|  
|**パブリッシャー**|**sysname**|パブリッシャーの名前です。|  
|**publisher_db**|**sysname**|パブリッシャー データベースの名前です。|  
|**サブスクライバー**|**sysname**|サブスクライバーの名前です。|  
|**@subscriber_db**|**sysname**|サブスクリプション データベースの名前です。|  
|**ステータス**|**int**|サブスクリプションの状態。<br /><br /> **0** = すべてのジョブが開始を待機しています。<br /><br /> **1** = 1 つ以上のジョブが起動中<br /><br /> **2** = すべてのジョブが正常に実行されました<br /><br /> **3** = 少なくとも 1 つジョブが実行中<br /><br /> **4** = すべてのジョブがスケジュールされ、アイドル状態<br /><br /> **5** = 少なくとも 1 つジョブが前回のエラーの後に実行しようとしています<br /><br /> **6** = 少なくとも 1 つは正常に実行するジョブが失敗しました|  
|**subscriber_type**|**int**|サブスクライバーの種類です。|  
|**subscription_type**|**int**|サブスクリプションの種類。<br /><br /> **0**プッシュを =<br /><br /> **1**プルを =<br /><br /> **2** = 両方|  
|**優先順位**|**float(8)**|サブスクリプションの優先度を示す数値。|  
|**sync_type**|**tinyint**|サブスクリプションの同期の種類。|  
|**説明**|**nvarchar (255)**|マージ サブスクリプションの簡単な説明。|  
|**merge_jobid**|**binary (16)**|マージ エージェントのジョブ ID。|  
|**full_publication**|**tinyint**|完全なパブリケーションとフィルター選択されたパブリケーションのどちらに対するサブスクリプションであるかを示します。|  
|**offload_enabled**|**bit**|レプリケーション エージェントの負荷を軽減するためにサブスクライバーでの実行が設定されているかどうかを示します。 NULL の場合は、パブリッシャー側で実行されます。|  
|**offload_server**|**sysname**|エージェントが動作しているサーバーの名前。|  
|**use_interactive_resolver**|**int**|調整時に対話型の競合回避モジュールを使用するかどうかを示します。 場合**0**、インタラクティブ競合回避モジュールが使用されません。|  
|**ホスト名**|**sysname**|値によってサブスクリプションがフィルター処理されるときに指定された値、 [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md)関数。|  
|**subscriber_security_mode**|**smallint**|セキュリティ モードをサブスクライバーで、ここで**1** Windows 認証を意味と**0**意味[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。|  
|**subscriber_login**|**sysname**|サブスクライバーのログイン名です。|  
|**subscriber_password**|**sysname**|実際のサブスクライバー パスワードは返されません。 によって、結果がマスクされており、"**\*\*\*\*\*\***"文字列。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_helpmergesubscription**パブリッシャーまたは再パブリッシュ サブスクライバーで格納されているサブスクリプション情報を返すためにマージ レプリケーションで使用します。  
  
 匿名サブスクリプションの場合、 *subscription_type*値は常に**1** (プル) です。 ただし、実行する必要があります[sp_helpmergepullsubscription](../../relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql.md)匿名サブスクリプションに関する情報のサブスクライバーでします。  
  
## <a name="permissions"></a>Permissions  
 メンバーにのみ、 **sysadmin**固定サーバー ロール、 **db_owner**固定データベース ロールまたはサブスクリプションが属するパブリケーションのパブリケーション アクセス リストが実行できる**sp _helpmergesubscription**です。  
  
## <a name="see-also"></a>参照  
 [sp_addmergesubscription &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md)   
 [sp_changemergesubscription &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-changemergesubscription-transact-sql.md)   
 [sp_dropmergesubscription &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
