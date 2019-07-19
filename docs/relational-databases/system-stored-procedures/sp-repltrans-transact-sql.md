---
title: sp_repltrans (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_repltrans_TSQL
- sp_repltrans
helpviewer_keywords:
- sp_repltrans
ms.assetid: 738e2322-335b-44fa-820e-f31c02743978
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5b1bdcdcd0f2128a08546e8b322449ec0b28cc29
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68129779"
---
# <a name="sprepltrans-transact-sql"></a>sp_repltrans (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  パブリケーション データベース トランザクション ログ内にあって、レプリケーションのマークは付いているがディストリビュートされたマークがまだ付いていないすべてのトランザクションの結果セットを返します。 このストアド プロシージャは、パブリッシャーのパブリケーション データベースに対して実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_repltrans  
```  
  
## <a name="result-sets"></a>結果セット  
 **sp_repltrans**が実行するためのまだディストリビュートされていないトランザクションを表示することができます、パブリケーション データベースに関する情報を返します (に送信されていないトランザクション ログに残っているトランザクション、ディストリビューターで)。 結果セットは、各トランザクションの最初と最後のレコードのログ シーケンス番号を表示します。 **sp_repltrans**のような[sp_replcmds &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md)がトランザクションのコマンドは返しません。  
  
## <a name="remarks"></a>コメント  
 **sp_repltrans**はトランザクション レプリケーションで使用します。  
  
 **sp_repltrans**はサポートされません以外[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_repltrans**します。  
  
## <a name="see-also"></a>関連項目  
 [sp_repldone &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-repldone-transact-sql.md)   
 [sp_replflush &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replflush-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
