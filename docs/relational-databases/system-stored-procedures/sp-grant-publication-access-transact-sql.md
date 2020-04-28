---
title: sp_grant_publication_access (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_grant_publication_access_TSQL
- sp_grant_publication_access
helpviewer_keywords:
- sp_grant_publication_access
ms.assetid: 17993952-def6-4a16-b1c1-323ec42967f8
ms.author: vanto
author: VanMSFT
ms.openlocfilehash: 4a94c22c7f524572a4b629c27d49ad35a84c3b02
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68123810"
---
# <a name="sp_grant_publication_access-transact-sql"></a>sp_grant_publication_access (Transact-sql)

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  パブリケーションのアクセスリストにログインを追加します。 このストアドプロシージャは、パブリッシャー側でパブリケーションデータベースに対して実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
sp_grant_publication_access [ @publication = ] 'publication', [ @login = ] 'login'   
    [ , [ @reserved = ] 'reserved' ]  
```  
  
## <a name="arguments"></a>引数  
`[ @publication = ] 'publication'`アクセスするパブリケーションの名前を指定します。 **'***publication***'** は**sysname**,、既定値はありません。  
  
`[ @login = ] 'login'`ログイン ID を示します。 **'***login***'** は**sysname**,、既定値はありません。  
  
`[ @reserved = ] 'reserved'` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>Remarks  
 **sp_grant_publication_access**は、スナップショットレプリケーション、トランザクションレプリケーション、およびマージレプリケーションで使用します。  
  
 このストアドプロシージャは、繰り返し呼び出すことができます。  
  
## <a name="permissions"></a>アクセス許可  
 **Sp_grant_publication_access**を実行できるのは、固定サーバーロール**sysadmin**または固定データベースロール**db_owner**のメンバーだけです。  
  
## <a name="see-also"></a>参照  
 [sp_help_publication_access &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-help-publication-access-transact-sql.md)   
 [sp_revoke_publication_access &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-revoke-publication-access-transact-sql.md)   
 [パブリッシャーのセキュリティ保護](../../relational-databases/replication/security/secure-the-publisher.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
