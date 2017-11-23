---
title: "sp_dropsubscription (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sp_dropsubscription
- sp_dropsubscription_TSQL
helpviewer_keywords: sp_dropsubscription
ms.assetid: 7551f345-5510-4684-ab53-f9057249d13a
caps.latest.revision: "23"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 43185571b06705011346dc08ded48e587a624311
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spdropsubscription-transact-sql"></a>sp_dropsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  パブリッシャー上の特定のアーティクル、パブリケーション、またはサブスクリプションの集合へのサブスクリプションを削除します。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_dropsubscription [ [ @publication= ] 'publication' ]  
    [ , [ @article= ] 'article' ]  
        , [ @subscriber= ] 'subscriber'  
    [ , [ @destination_db= ] 'destination_db' ]  
    [ , [ @ignore_distributor = ] ignore_distributor ]  
    [ , [ @reserved= ] 'reserved' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@publication=** ] **'***パブリケーション***'**  
 関連付けられているパブリケーションの名前を指定します。 *パブリケーション*は**sysname**、既定値は NULL です。 場合**すべて**、指定したサブスクライバーのすべてのパブリケーションのすべてのサブスクリプションが取り消されました。 *パブリケーション*必須パラメーターです。  
  
 [  **@article=** ] **'***記事***'**  
 アーティクルの名前を指定します。 *記事*は**sysname**既定値は NULL です。 場合**すべて**、ごとにすべてのアーティクルに対してサブスクリプションがパブリケーションとサブスクライバーが削除を指定します。 使用して**すべて**即時を許可するパブリケーションを更新します。  
  
 [  **@subscriber=** ] **'***サブスクライブ*r**'**  
 削除するサブスクリプションがあるサブスクライバーの名前です。 *サブスクライバー*は**sysname**、既定値はありません。 場合**すべて**、すべてのサブスクライバーのすべてのサブスクリプションが削除されます。  
  
 [  **@destination_db=** ] **'***destination_db***'**  
 対象データベース名を指定します。 *destination_db*は**sysname**、既定値は NULL です。 NULL を指定する場合、そのサブスクライバーからすべてのサブスクリプションが削除されます。  
  
 [  **@ignore_distributor =** ] *ignore_distributor*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [  **@reserved=** ] **'***予約***'**  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_dropsubscription**は、スナップショットおよびトランザクション レプリケーションで使用します。  
  
 即時同期パブリケーションでアーティクルのサブスクリプションを削除した場合は、パブリケーション内のすべてのアーティクルのサブスクリプションを削除するのと同時に、これらすべてのサブスクリプションを追加し直さない限り、元に戻すことはできません。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_droptransubscription](../../relational-databases/replication/codesnippet/tsql/sp-dropsubscription-tran_1.sql)]  
  
## <a name="permissions"></a>Permissions  
 メンバーにのみ、 **sysadmin**固定サーバー ロール、 **db_owner**固定データベース ロール、またはサブスクリプションを作成したユーザーが実行できる**sp_dropsubscription**です。  
  
## <a name="see-also"></a>参照  
 [プッシュ サブスクリプションを削除します。](../../relational-databases/replication/delete-a-push-subscription.md)   
 [sp_addsubscription &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)   
 [sp_changesubstatus &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-changesubstatus-transact-sql.md)   
 [sp_helpsubscription &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)  
  
  
