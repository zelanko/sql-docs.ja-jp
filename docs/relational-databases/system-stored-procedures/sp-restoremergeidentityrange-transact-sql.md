---
title: sp_restoremergeidentityrange (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/03/2017
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
- sp_restoremergeidentityrange_TSQL
- sp_restoremergeidentityrange
helpviewer_keywords:
- sp_restoremergeidentityrange
ms.assetid: 7923e422-2748-40c0-b5a8-6410c48d5b70
caps.latest.revision: 12
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 27f59d25a0421338b4dde7c96e31b8c209a6d606
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
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
 パブリケーションの名前です。 *パブリケーション*は**sysname**、既定値は**すべて**です。 パブリケーションを指定した場合、そのパブリケーションの ID 範囲のみが復元されます。  
  
 [ **@article** =] **'***記事***'**  
 アーティクルの名前を指定します。 *記事*は**sysname**、既定値は**すべて**です。 アーティクルを指定した場合、そのアーティクルの ID 範囲のみが復元されます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_restoremergeidentityrange**はマージ レプリケーションで使用します。  
  
 **sp_restoremergeidentityrange**ディストリビューターから最大 id 範囲割り当て情報を取得し、内の値を更新、 **max_used**の列[MSmerge_identity_range_allocations &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-tables/msmerge-identity-range-allocations-transact-sql.md)自動 id 範囲管理を使用するアーティクルのです。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_restoremergeidentityrange**です。  
  
## <a name="see-also"></a>参照  
 [sp_addmergearticle &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)   
 [sp_changemergearticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md)   
 [ID 列のレプリケート](../../relational-databases/replication/publish/replicate-identity-columns.md)  
  
  
