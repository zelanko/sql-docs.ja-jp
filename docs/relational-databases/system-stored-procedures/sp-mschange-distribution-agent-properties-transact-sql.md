---
title: sp_MSchange_distribution_agent_properties (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
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
- sp_MSchange_distribution_agent_properties
- sp_MSchange_distribution_agent_properties_TSQL
helpviewer_keywords:
- sp_MSchange_distribution_agent_properties
ms.assetid: 7dac5e68-bf84-433a-a531-66921f35126f
caps.latest.revision: 17
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 4134d0fce27f28362cee87c8c039ddb8cdcfaebc
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="spmschangedistributionagentproperties-transact-sql"></a>sp_MSchange_distribution_agent_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  実行されるディストリビューション エージェント ジョブのプロパティを変更、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]またはそれ以降のバージョンのディストリビューター。 プロパティを変更するパブリッシャーのインスタンス上の実行時にこのストアド プロシージャを使用[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]です。 このストアド プロシージャは、ディストリビューター側でディストリビューション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_MSchange_distribution_agent_properties [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'   
        , [ @subscriber = ] 'subscriber'   
        , [ @subscriber_db = ] 'subscriber_db'   
        , [ @property = ] 'property'   
        , [ @value = ] 'value' ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@publisher** =] **'***パブリッシャー***'**  
 パブリッシャーの名前です。 *パブリッシャー*は**sysname**、既定値はありません。  
  
 [  **@publisher_db=** ] **'***publisher_db***'**  
 パブリケーション データベースの名前です。 *publisher_db*は**sysname**、既定値はありません。  
  
 [ **@publication =** ] **'***publication***'**  
 パブリケーションの名前です。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [  **@subscriber=** ] **'***サブスクライバー***'**  
 サブスクライバーの名前です。 *サブスクライバー*は**sysname**、既定値はありません。  
  
 [  **@subscriber_db=** ] **'***@subscriber_db***'**  
 サブスクリプション データベースの名前です。 *@subscriber_db*は**sysname**、既定値はありません。  
  
 [  **@property =** ] **'***プロパティ***'**  
 変更するパブリケーションのプロパティを指定します。 *プロパティ*は**sysname**、既定値はありません。  
  
 [  **@value =** ] **'***値***'**  
 新しいプロパティ値を指定します。 *値*は**nvarchar (524)**、既定値は NULL です。  
  
 次の表に、変更可能なディストリビューション エージェント ジョブのプロパティと、プロパティの値に関する制限を示します。  
  
|プロパティ|値|Description|  
|--------------|-----------|-----------------|  
|**distrib_job_login**||エージェントを実行する [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アカウントのログイン。|  
|**distrib_job_password**||エージェント ジョブを実行する Windows アカウントのパスワード。|  
|**対応する、**||OLE DB プロバイダーに接続するときに使用されるカタログ。 *このプロパティはに対してのみ有効以外*[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *サブスクライバーです。*|  
|**subscriber_datasource**||OLE DB プロバイダーで認識されるデータ ソースの名前。 *このプロパティはに対してのみ有効以外*[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *サブスクライバーです。*|  
|**subscriber_location**||OLE DB プロバイダーで認識されるデータベースの場所。 *このプロパティはに対してのみ有効以外*[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *サブスクライバーです。*|  
|**subscriber_login**||サブスクリプションの同期で、サブスクライバーに接続するときに使用するログイン。|  
|**subscriber_password**||サブスクライバーのパスワード。<br /><br /> [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)]|  
|**subscriber_provider**||一意なプログラム識別子 (PROGID) を OLE DB provider for 以外の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ ソースを登録します。 *このプロパティはに対してのみ有効以外*[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *サブスクライバーです。*|  
|**subscriber_providerstring**||データ ソースを識別する、OLE DB プロバイダー固有の接続文字列。 *このプロパティは有効の SQL Server 以外のサブスクライバーだけです。*|  
|**subscriber_security_mode**|**1**|Windows 認証。<br /><br /> [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]|  
||**0**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証。|  
|**subscriber_type**|**0**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サブスクライバー|  
||**1**|ODBC データ ソース サーバー|  
||**3**|OLE DB プロバイダー|  
|**subscriptionstreams**||変更のバッチをサブスクライバーに並列的に適用するために、ディストリビューション エージェントごとに許可される接続の数を表します。 *サポートされていません。 非*[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *サブスクライバー、Oracle パブリッシャーの場合、またはピア ツー ピア サブスクリプションです。*|  
  
> [!NOTE]  
>  エージェントのログインまたはパスワードを変更した後、変更を有効にするには、エージェントを停止して再起動する必要があります。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_MSchange_distribution_agent_properties**はスナップショット レプリケーションおよびトランザクション レプリケーションで使用します。  
  
 インスタンスで、パブリッシャーを実行するときに[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]以降のバージョンを使用する必要がある、または[sp_changesubscription](../../relational-databases/system-stored-procedures/sp-changesubscription-transact-sql.md)ディストリビューター側で実行されているプッシュ サブスクリプションを同期するマージ エージェント ジョブのプロパティを変更します。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin** 、ディストリビューター側の固定サーバー ロールが実行できる**sp_MSchange_distribution_agent_properties**です。  
  
## <a name="see-also"></a>参照  
 [sp_addpushsubscription_agent &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql.md)   
 [sp_addsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)  
  
  
