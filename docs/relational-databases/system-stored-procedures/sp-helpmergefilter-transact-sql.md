---
title: sp_helpmergefilter (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpmergefilter
- sp_helpmergefilter_TSQL
helpviewer_keywords:
- sp_helpmergefilter
ms.assetid: f133a094-0009-4771-b93b-e86a5c01e40b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 668233ad7ee79617caa60933a9eef33c5a810164
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62502803"
---
# <a name="sphelpmergefilter-transact-sql"></a>sp_helpmergefilter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  マージ フィルターに関する情報を返します。 このストアド プロシージャは、任意のデータベースのパブリッシャーで実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helpmergefilter [ @publication= ] 'publication'   
    [ , [ @article= ] 'article']  
    [ , [ @filtername= ] 'filtername']  
```  
  
## <a name="arguments"></a>引数  
`[ @publication = ] 'publication'` パブリケーションの名前です。 *パブリケーション* は **sysname** 、既定値はありません。  
  
`[ @article = ] 'article'` アーティクルの名前です。 *記事*は**sysname**、既定値は **%** 、すべてのアーティクルの名前が返されます。  
  
`[ @filtername = ] 'filtername'` に関する情報を返すフィルターの名前です。 *filtername*は**sysname**、既定値は **%** 、アーティクルまたはパブリケーションで定義されているすべてのフィルターに関する情報が返されます。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**join_filterid**|**int**|結合フィルターの ID。|  
|**filtername**|**sysname**|フィルターの名前。|  
|**結合アーティクル名**|**sysname**|結合アーティクルの名前です。|  
|**join_filterclause**|**nvarchar(2000)**|結合を修飾するフィルター句。|  
|**join_unique_key**|**int**|一意なキーを基に結合を行うかどうかを示します。|  
|**ベース テーブルの所有者**|**sysname**|ベース テーブルの所有者の名前。|  
|**ベース テーブルの名前**|**sysname**|ベース テーブルの名前です。|  
|**結合テーブルの所有者**|**sysname**|ベース テーブルに結合するテーブルの所有者の名前。|  
|**結合テーブルの名前**|**sysname**|ベース テーブルに結合するテーブルの名前。|  
|**アーティクルの名前**|**sysname**|ベース テーブルに結合するテーブル アーティクルの名前です。|  
|**filter_type**|**tinyint**|マージ フィルターは、次のいずれかの種類です。<br /><br /> **1** = 結合フィルターのみ<br /><br /> **2** = 論理レコードのリレーションシップ<br /><br /> **3** = 両方|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_helpmergefilter**はマージ レプリケーションで使用します。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールおよび**db_owner**固定データベース ロールが実行できる**sp_helpmergefilter**します。  
  
## <a name="see-also"></a>参照  
 [sp_addmergefilter (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md)   
 [sp_changemergefilter (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changemergefilter-transact-sql.md)   
 [sp_dropmergefilter (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-dropmergefilter-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
