---
title: sp_replflush (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replflush
- sp_replflush_TSQL
helpviewer_keywords:
- sp_replflush
ms.assetid: 20809f5f-941d-427f-8f0c-de7a6c487584
author: stevestein
ms.author: sstein
ms.openlocfilehash: eaf42b746fca4999e7a67e0aff220ff2d09772cf
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67950727"
---
# <a name="spreplflush-transact-sql"></a>sp_replflush (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  アーティクル キャッシュをフラッシュします。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
> [!IMPORTANT]  
>  このプロシージャを手動で実行する必要はありません。 **sp_replflush**サポート プロフェッショナルの経験豊富なレプリケーションのレプリケーションのトラブルシューティングにのみ使用する必要があります。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_replflush  
```  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_replflush**はトランザクション レプリケーションで使用します。  
  
 効率を上げるため、アーティクル定義がキャッシュに格納されます。 **sp_replflush**アーティクル定義を変更または削除されるときに、その他のレプリケーションのストアド プロシージャによって使用されます。  
  
 1 つのみのクライアント接続、特定のデータベースに対するログ リーダー アクセス権ことができます。 実行するとき、クライアントは、データベースに対するログ リーダー アクセス権を持っている、 **sp_replflush**により、クライアントのアクセスを解放します。 他のクライアントでは、トランザクション ログを使用してをスキャンできますし、 **sp_replcmds**または**sp_replshowcmds**します。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_replflush**します。  
  
## <a name="see-also"></a>関連項目  
 [sp_replcmds &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md)   
 [sp_repldone &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-repldone-transact-sql.md)   
 [sp_repltrans &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-repltrans-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
