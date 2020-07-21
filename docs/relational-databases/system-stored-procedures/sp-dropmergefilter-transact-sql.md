---
title: sp_dropmergefilter (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_dropmergefilter_TSQL
- sp_dropmergefilter
helpviewer_keywords:
- sp_dropmergefilter
ms.assetid: 798586d7-05f3-4a5e-bea8-a34b7b52d0fd
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 2de7b17ff172c5945c7bfb83cae6a8a11325e6d0
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85881822"
---
# <a name="sp_dropmergefilter-transact-sql"></a>sp_dropmergefilter (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  マージフィルターを削除します。 **sp_dropmergefilter** 、削除するマージフィルターに定義されているすべてのマージフィルター列を削除します。 このストアドプロシージャは、パブリッシャー側でパブリケーションデータベースに対して実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_dropmergefilter [ @publication= ] 'publication', [ @article= ] 'article'     , [ @filtername= ] 'filtername'  
    [ , [ @force_invalidate_snapshot= ] force_invalidate_snapshot ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
```  
  
## <a name="arguments"></a>引数  
`[ @publication = ] 'publication'`パブリケーションの名前を指定します。 *publication*は**sysname**,、既定値はありません。  
  
`[ @article = ] 'article'`アーティクルの名前を指定します。 *アーティクル*は**sysname**で、既定値はありません。  
  
`[ @filtername = ] 'filtername'`削除するフィルターの名前を指定します。 *filtername*は**sysname**,、既定値はありません。  
  
`[ @force_invalidate_snapshot = ] force_invalidate_snapshot`スナップショットを無効にする機能を有効または無効にします。 *force_invalidate_snapshot*は**ビット**であり、既定値は**0**です。  
  
 **0**を指定すると、マージアーティクルへの変更によってスナップショットが無効になることはありません。  
  
 **1**は、マージアーティクルへの変更によってスナップショットが無効になる可能性があることを意味します。 この場合、値が**1**の場合は、新しいスナップショットを作成する権限が与えられます。  
  
`[ @force_reinit_subscription = ] force_reinit_subscription`サブスクリプションを無効としてマークする機能を有効または無効にします。 *force_reinit_subscription*は**ビット**であり、既定値は**0**です。  
  
 **0**を指定すると、マージアーティクルフィルターへの変更によってサブスクリプションが無効になることはありません。  
  
 **1**は、マージアーティクルフィルターへの変更によってサブスクリプションが無効になることを意味します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>Remarks  
 **sp_dropmergefilter**は、マージレプリケーションで使用します。  
  
## <a name="permissions"></a>アクセス許可  
 **Sp_dropmergefilter**を実行できるのは、固定サーバーロール**sysadmin**または固定データベースロール**db_owner**のメンバーだけです。  
  
## <a name="see-also"></a>関連項目  
 [パブリケーションとアーティクルのプロパティの変更](../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [sp_addmergefilter &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md)   
 [sp_changemergefilter &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-changemergefilter-transact-sql.md)   
 [sp_helpmergefilter &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-helpmergefilter-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
