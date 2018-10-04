---
title: sp_addpullsubscription (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_addpullsubscription
- sp_addpullsubscription_TSQL
helpviewer_keywords:
- sp_addpullsubscription
ms.assetid: 0f4bbedc-0c1c-414a-b82a-6fd47f0a6a7f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0d3c09a2d625f8b1a8c92d3fc55d8b571336a020
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47857030"
---
# <a name="spaddpullsubscription-transact-sql"></a>sp_addpullsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  スナップショット パブリケーションまたはトランザクション パブリケーションにプル サブスクリプションを追加します。 このストアド プロシージャは、プル サブスクリプションが作成されるデータベース上のサブスクライバー側で実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_addpullsubscription [ @publisher= ] 'publisher'  
    [ , [ @publisher_db= ] 'publisher_db' ]  
        , [ @publication= ] 'publication'  
    [ , [ @independent_agent= ] 'independent_agent' ]  
    [ , [ @subscription_type= ] 'subscription_type' ]  
    [ , [ @description= ] 'description' ]  
    [ , [ @update_mode= ] 'update_mode' ]  
    [ , [ @immediate_sync = ] immediate_sync ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@publisher=**] **'***publisher***'**  
 パブリッシャーの名前です。 *パブリッシャー*は**sysname**、既定値はありません。  
  
 [ **@publisher_db=**] **'***publisher_db***'**  
 パブリッシャー データベースの名前です。 *publisher_db*は**sysname**、既定値は NULL です。 *publisher_db* Oracle パブリッシャーでは無視されます。  
  
 [ **@publication=**] **'***publication***'**  
 パブリケーションの名前です。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [  **@independent_agent=**] **'***independent_agent***'**  
 このパブリケーションに対して、スタンドアロン ディストリビューション エージェントが存在するかどうかを指定します。 *independent_agent*は**nvarchar (5)**、既定値は TRUE。 場合**true**、このパブリケーション用のスタンドアロン ディストリビューション エージェントが存在します。 場合**false**、パブリッシャー データベース/サブスクライバー データベースの各ペアの 1 つのディストリビューション エージェントが存在します。 *independent_agent*パブリケーションのプロパティは、値が同じである必要がありますが、パブリッシャーであるためここでします。  
  
 [  **@subscription_type=**] **'***subscription_type***'**  
 サブスクリプションの種類を指定します。 *subscription_type*は**nvarchar (9)**、既定値は**匿名**します。 値を指定する必要があります**プル**の*subscription_type*パブリッシャー側でサブスクリプションを登録せずにサブスクリプションを作成する場合を除き、します。 ここでは、値を指定する必要があります**匿名**します。 これは確立できない場合に必要な[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サブスクリプションの構成時に、パブリッシャーに接続します。  
  
 [  **@description=**] **'***説明***'**  
 パブリケーションの説明です。 *説明*は**nvarchar (100)**、既定値は NULL です。  
  
 [  **@update_mode=**] **'***update_mode***'**  
 更新の種類を指定します。 *update_mode*は**nvarchar (30)** 値は次のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**読み取り専用**(既定値)|サブスクリプションは読み取り専用です。 サブスクライバーで加えられた変更はパブリッシャーには送り返されません。 サブスクライバーで更新を行わない場合に使用します。|  
|**synctran**|即時更新サブスクリプションのサポートを有効にします。|  
|**キューに置かれた tran**|サブスクリプションのキュー更新を有効にします。 サブスクライバーでデータを変更し、キューに格納し、それをパブリッシャーに配信することができます。|  
|**フェールオーバー**|キュー更新をフェールオーバーとするサブスクリプションの即時更新を有効にします。 サブスクライバーでデータを変更し、それを直ちにパブリッシャーに配信することができます。 パブリッシャーとサブスクライバーが接続されていない場合は、サブスクライバーとパブリッシャーが接続されるまで、サブスクライバーで加えられたデータの変更をキューに格納することができます。|  
|**キューに置かれたフェールオーバー**|即時更新モードへの変更が可能なキュー更新サブスクリプションとしてサブスクリプションを有効にします。 サブスクライバーでデータを変更し、サブスクライバーとパブリッシャーの間の接続が確立されるまで、その変更をキューに格納することができます。 継続的な接続が確立されると、更新モードを即時更新に変更できます。 *Oracle パブリッシャーに対してはサポートされていません*します。|  
  
 [  **@immediate_sync =**] *immediate_sync*  
 スナップショット エージェントを実行するたびに同期ファイルを作成または再作成するかどうかを指定します。 *immediate_sync*は**ビット**は 1 で、既定値と同じ値に設定する必要があります*immediate_sync*で**sp_addpublication**.*immediate_sync*パブリケーションのプロパティは、値が同じである必要がありますが、パブリッシャーであるためここでします。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_addpullsubscription**スナップショット レプリケーションおよびトランザクション レプリケーションで使用されます。  
  
> [!IMPORTANT]  
>  キュー更新サブスクリプションの場合、サブスクライバーへの接続には [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用し、各サブスクライバーへの接続にはそれぞれ異なるアカウントを指定してください。 キュー更新をサポートするプル サブスクリプションを作成する場合は、レプリケーションによって、常に Windows 認証を使用するように接続が設定されます (プル サブスクリプションでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用するために必要な、サブスクライバー側のメタデータにレプリケーションからアクセスすることはできません)。 この場合は、実行する必要があります[sp_changesubscription](../../relational-databases/system-stored-procedures/sp-changesubscription-transact-sql.md)を使用する接続を変更する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証の後、サブスクリプションを構成します。  
  
 場合、 [MSreplication_subscriptions &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-tables/msreplication-subscriptions-transact-sql.md)テーブルがサブスクライバーで、存在しない**sp_addpullsubscription**によって作成されます。 行が追加されます、 [MSreplication_subscriptions &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-tables/msreplication-subscriptions-transact-sql.md)テーブル。 プル サブスクリプションで[sp_addsubscription &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md) 、パブリッシャー側で最初に呼び出す必要があります。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_addtranpullsubscriptionagent](../../relational-databases/replication/codesnippet/tsql/sp-addpullsubscription-t_1.sql)]  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_addpullsubscription**します。  
  
## <a name="see-also"></a>参照  
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Create an Updatable Subscription to a Transactional Publication](../../relational-databases/replication/publish/create-updatable-subscription-to-transactional-publication.md) [パブリケーションのサブスクライブ](../../relational-databases/replication/subscribe-to-publications.md)   
 [sp_addpullsubscription_agent &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md)   
 [sp_change_subscription_properties &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-change-subscription-properties-transact-sql.md)   
 [sp_droppullsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droppullsubscription-transact-sql.md)   
 [sp_helppullsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql.md)   
 [sp_helpsubscription_properties &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
