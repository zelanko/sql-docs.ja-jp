---
title: sp_validatemergepublication (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_validatemergepublication
- sp_validatemergepublication_TSQL
helpviewer_keywords:
- sp_validatemergepublication
ms.assetid: 5a862f1a-2be1-4758-9954-4cdc8c77d149
author: stevestein
ms.author: sstein
ms.openlocfilehash: f14b74786b70a280f4b3576537ab89041e0eb6a8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68119372"
---
# <a name="spvalidatemergepublication-transact-sql"></a>sp_validatemergepublication (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  1 つのパブリケーション全体の検証を実行し、すべてのサブスクリプション (プッシュ、プル、および匿名) を 1 回で検証します。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_validatemergepublication [@publication=] 'publication'  
        , [ @level = ] level  
```  
  
## <a name="arguments"></a>引数  
 [**\@publication=**] **'***publication***'** 
 パブリケーションの名前です。 *パブリケーション* は **sysname** 、既定値はありません。  
  
`[ @level = ] level` 実行する検証の種類です。 *レベル*は**tinyint**、既定値はありません。 レベルには次のいずれかの値を指定できます。  
  
|レベル値|説明|  
|-----------------|-----------------|  
|**1**|行数のみの検証。|  
|**2**|行数とチェックサムの検証。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]サブスクライバー、これは自動的に設定**3**します。|  
|**3**|これは、推奨値です。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_validatemergepublication**はマージ レプリケーションで使用します。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールが実行できる**sp_validatemergepublication**します。  
  
## <a name="see-also"></a>関連項目  
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [レプリケートされたデータを検証します。](../../relational-databases/replication/validate-data-at-the-subscriber.md)   
 [sp_validatemergesubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-validatemergesubscription-transact-sql.md)  
  
  
