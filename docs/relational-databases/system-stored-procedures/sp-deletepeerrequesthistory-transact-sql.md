---
title: "sp_deletepeerrequesthistory (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
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
- sp_deletepeerrequesthistory
- sp_deletepeerrequesthistory_TSQL
helpviewer_keywords:
- sp_deletepeerrequesthistory
ms.assetid: 63a4ec6e-ce79-4bf1-9d37-5ac88f8d6beb
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9deb92cbdc9eff3e54efb1b37d18abc7bfc01252
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spdeletepeerrequesthistory-transact-sql"></a>sp_deletepeerrequesthistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  要求の履歴を含むパブリケーション状態要求に関連する履歴の削除 ([MSpeer_request &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/mspeer-request-transact-sql.md)) と応答履歴 ([MSpeer_response &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/mspeer-response-transact-sql.md)).このストアド プロシージャは、ピア ツー ピア レプリケーション トポロジに参加しているパブリッシャーでパブリケーション データベースで実行されます。 詳細については、「 [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)」を参照してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_deletepeerrequesthistory [ @publication = ] 'publication'  
    [ , [ @request_id = ] request_id ]  
    [ , [ @cutoff_date = ] cutoff_date ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@publication=** ] **'***パブリケーション***'**  
 状態要求が行われたパブリケーションの名前。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [  **@request_id=** ] *request_id*  
 状態要求に対するすべての応答を削除するため、状態要求を個別に指定します。 *request_id*は**int**既定値は NULL です。  
  
 [  **@cutoff_date=** ] *cutoff_date*  
 終了日を指定します。それ以前のすべての応答レコードが削除されます。 *cutoff_date*は**datetime**既定値は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_deletepeerrequesthistory**はピア ツー ピア トランザクション レプリケーション トポロジで使用します。 詳細については、「 [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)」を参照してください。  
  
 実行時に**sp_deletepeerrequesthistory**か、 *request_id*または*cutoff_date*指定する必要があります。  
  
## <a name="permissions"></a>Permissions  
 メンバーにのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_deletepeerrequesthistory**です。  
  
## <a name="see-also"></a>参照  
 [sp_helppeerrequests &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-helppeerrequests-transact-sql.md)   
 [sp_helppeerresponses &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql.md)   
 [sp_requestpeerresponse &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql.md)  
  
  
