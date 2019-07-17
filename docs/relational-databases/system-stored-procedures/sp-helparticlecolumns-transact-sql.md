---
title: sp_helparticlecolumns (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helparticlecolumns
- sp_helparticlecolumns_TSQL
helpviewer_keywords:
- sp_helparticlecolumns
ms.assetid: 9ea55df3-2e99-4683-88ad-bde718288bc7
author: stevestein
ms.author: sstein
ms.openlocfilehash: fd7a493a3126aecbf816d364e5b7497f2bf494d5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68084962"
---
# <a name="sphelparticlecolumns-transact-sql"></a>sp_helparticlecolumns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  基になるテーブル内のすべての列を返します。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。 Oracle パブリッシャーの場合、このストアド プロシージャは、任意のデータベース上のディストリビューター側で実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helparticlecolumns [ @publication = ] 'publication'   
        , [ @article = ] 'article'  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>引数  
`[ @publication = ] 'publication'` アーティクルを含むパブリケーションの名前です。 *パブリケーション* は **sysname** 、既定値はありません。  
  
`[ @article = ] 'article'` 列を返すアーティクルの名前です。 *記事*は**sysname**、既定値はありません。  
  
`[ @publisher = ] 'publisher'` 以外を指定[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。 *パブリッシャー*は**sysname**、既定値は NULL です。  
  
> [!NOTE]  
>  *パブリッシャー*によって要求された記事が公開されると指定しないで、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (列がパブリッシュされていない) または**1** (パブリッシュされる列)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**列 id**|**int**|列の識別子です。|  
|**column**|**sysname**|列の名前です。|  
|**公開**|**bit**|列をパブリッシュしたかどうかを示します。<br /><br /> **0** = いいえ<br /><br /> **1** = はい|  
|**パブリッシャーの種類**|**sysname**|パブリッシャーの列のデータ型。|  
|**サブスクライバーの種類**|**sysname**|サブスクライバー側で列のデータ型。|  
  
## <a name="remarks"></a>コメント  
 **sp_helparticlecolumns**スナップショットおよびトランザクション レプリケーションで使用されます。  
  
 **sp_helparticlecolumns**垂直方向のパーティションを調べるときに便利です。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロール、 **db_owner**固定データベース ロール、または現在のパブリケーションのパブリケーション アクセス リストが実行できる**sp_helparticlecolumns**.  
  
## <a name="see-also"></a>関連項目  
 [Define and Modify a Column Filter](../../relational-databases/replication/publish/define-and-modify-a-column-filter.md)   
 [sp_addarticle &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)   
 [sp_articlecolumn (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md)   
 [sp_changearticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)   
 [sp_droparticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-droparticle-transact-sql.md)   
 [sp_droppublication &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droppublication-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
