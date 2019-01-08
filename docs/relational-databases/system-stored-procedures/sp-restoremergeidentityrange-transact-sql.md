---
title: sp_restoremergeidentityrange (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_restoremergeidentityrange_TSQL
- sp_restoremergeidentityrange
helpviewer_keywords:
- sp_restoremergeidentityrange
ms.assetid: 7923e422-2748-40c0-b5a8-6410c48d5b70
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 88cf393ac488f6e6f4c078b9bd346a3e6cb53204
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52823056"
---
# <a name="sprestoremergeidentityrange-transact-sql"></a>sp_restoremergeidentityrange (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  このストアド プロシージャは、ID 範囲の割り当てを更新するために使用します。 このストアド プロシージャを使用すると、パブリッシャーがバックアップから復元された後に自動 ID 範囲の管理が正しく機能します。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_restoremergeidentityrange [ [ @publication = ] 'publication' ]  
    [ , [ @article = ] 'article' ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@publication** =] **'***パブリケーション***'**  
 パブリケーションの名前です。 *パブリケーション*は**sysname**で既定値は**すべて**します。 パブリケーションを指定した場合、そのパブリケーションの ID 範囲のみが復元されます。  
  
 [ **@article** =] **'***記事***'**  
 アーティクルの名前を指定します。 *記事*は**sysname**の既定値を持つ**すべて**します。 アーティクルを指定した場合、そのアーティクルの ID 範囲のみが復元されます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_restoremergeidentityrange**はマージ レプリケーションで使用します。  
  
 **sp_restoremergeidentityrange**ディストリビューターから最大 id 範囲割り当て情報を取得し、内の値を更新、 **max_used**の列[MSmerge_identity_range_allocations &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-tables/msmerge-identity-range-allocations-transact-sql.md)自動 id 範囲管理を使用するアーティクルのです。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_restoremergeidentityrange**します。  
  
## <a name="see-also"></a>参照  
 [sp_addmergearticle &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)   
 [sp_changemergearticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md)   
 [ID 列のレプリケート](../../relational-databases/replication/publish/replicate-identity-columns.md)  
  
  
