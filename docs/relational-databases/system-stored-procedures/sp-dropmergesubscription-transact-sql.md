---
title: sp_dropmergesubscription (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_dropmergesubscription_TSQL
- sp_dropmergesubscription
helpviewer_keywords:
- sp_dropmergesubscription
ms.assetid: 34244ae6-bd98-4a6a-bbd3-85f50edfcdc0
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 2868afcf85895ce1e7456bc2eea3693d9b25e679
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82831164"
---
# <a name="sp_dropmergesubscription-transact-sql"></a>sp_dropmergesubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  マージ パブリケーションのサブスクリプションおよびこれと関連するマージ エージェントを削除します。 このストアドプロシージャは、パブリッシャー側でパブリケーションデータベースに対して実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_dropmergesubscription [ [ @publication= ] 'publication' ]   
    [ , [ @subscriber= ] 'subscriber'    
    [ , [ @subscriber_db= ] 'subscriber_db' ]   
    [ , [ @subscription_type= ] 'subscription_type' ]   
    [ , [ @ignore_distributor = ] ignore_distributor ]   
    [ , [ @reserved = ] reserved ]  
```  
  
## <a name="arguments"></a>引数  
`[ @publication = ] 'publication'`パブリケーション名を指定します。 *publication*は**sysname**,、既定値は NULL です。 パブリケーションは既に存在し、識別子のルールに準拠している必要があります。  
  
`[ @subscriber = ] 'subscriber'`サブスクライバーの名前を指定します。 *サブスクライバー*の**sysname**,、既定値は NULL です。  
  
`[ @subscriber_db = ] 'subscriber_db'`サブスクリプションデータベースの名前を指定します。 *subscription_database*は**sysname**,、既定値は NULL です。  
  
`[ @subscription_type = ] 'subscription_type'`サブスクリプションの種類を示します。 *subscription_type*は**nvarchar (15)** で、次のいずれかの値を指定できます。  
  
|[値]|説明|  
|-----------|-----------------|  
|**すべての**|プッシュサブスクリプション、プルサブスクリプション、および匿名サブスクリプション|  
|**非同期**|匿名サブスクリプションです。|  
|**押し付け**|プッシュサブスクリプション。|  
|**だとすると**|プル サブスクリプションです。|  
|**both** (既定値)|プッシュ サブスクリプションおよびプル サブスクリプションです。|  
  
`[ @ignore_distributor = ] ignore_distributor`ディストリビューターに接続せずにこのストアドプロシージャを実行するかどうかを示します。 *ignore_distributor*は**ビット**,、既定値は**0**です。 このパラメーターを使用すると、ディストリビューターでクリーンアップタスクを実行せずに、サブスクリプションを削除できます。 また、ディストリビューターを再インストールする必要がある場合にも役立ちます。  
  
`[ @reserved = ] reserved`将来使用するために予約されています。 *予約済み*は**ビット**,、既定値は**0**です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_dropmergesubscription**は、マージレプリケーションで使用します。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_dropmergesubscription](../../relational-databases/replication/codesnippet/tsql/sp-dropmergesubscription_1.sql)]  
  
## <a name="permissions"></a>アクセス許可  
 **Sp_dropmergesubscription**を実行できるのは、固定サーバーロール**sysadmin**または固定データベースロール**db_owner**のメンバーだけです。  
  
## <a name="see-also"></a>参照  
 [プッシュサブスクリプションを削除する](../../relational-databases/replication/delete-a-push-subscription.md)   
 [プルサブスクリプションの削除](../../relational-databases/replication/delete-a-pull-subscription.md)   
 [sp_addmergesubscription &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md)   
 [sp_changemergesubscription &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-changemergesubscription-transact-sql.md)   
 [sp_helpmergesubscription &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql.md)  
  
  
