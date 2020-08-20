---
description: sp_helpmergefilter (Transact-SQL)
title: sp_helpmergefilter (Transact-sql) |Microsoft Docs
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 7051213a6543a1dc964fe011f95f48d15cd788ce
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88474016"
---
# <a name="sp_helpmergefilter-transact-sql"></a>sp_helpmergefilter (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  マージ フィルターに関する情報を返します。 このストアドプロシージャは、パブリッシャー側で任意のデータベースに対して実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helpmergefilter [ @publication= ] 'publication'   
    [ , [ @article= ] 'article']  
    [ , [ @filtername= ] 'filtername']  
```  
  
## <a name="arguments"></a>引数  
`[ @publication = ] 'publication'` パブリケーションの名前を指定します。 *publication* は **sysname**,、既定値はありません。  
  
`[ @article = ] 'article'` アーティクルの名前を指定します。 *アーティクル* は **sysname**で、既定値はです **%** 。これにより、すべてのアーティクルの名前が返されます。  
  
`[ @filtername = ] 'filtername'` 情報を返すフィルターの名前を指定します。 *filtername* のデータ型は **sysname**で、既定値はです **%** 。これは、アーティクルまたはパブリケーションで定義されているすべてのフィルターに関する情報を返します。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**join_filterid**|**int**|結合フィルターの ID。|  
|**filtername**|**sysname**|フィルターの名前。|  
|**join article name**|**sysname**|結合アーティクルの名前。|  
|**join_filterclause**|**nvarchar (2000)**|結合を修飾するフィルター句。|  
|**join_unique_key**|**int**|一意なキーを基に結合を行うかどうかを示します。|  
|**base table owner**|**sysname**|ベーステーブルの所有者の名前。|  
|**base table name**|**sysname**|ベーステーブルの名前。|  
|**join table owner**|**sysname**|ベース テーブルに結合するテーブルの所有者の名前。|  
|**結合テーブル名**|**sysname**|ベーステーブルに結合されているテーブルの名前。|  
|**アーティクル名**|**sysname**|ベーステーブルに結合されているテーブルアーティクルの名前。|  
|**filter_type**|**tinyint**|マージフィルターの種類。次のいずれかを指定できます。<br /><br /> **1** = 結合フィルターのみ<br /><br /> **2** = 論理レコードリレーションシップ<br /><br /> **3** = 両方|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または **1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_helpmergefilter** は、マージレプリケーションで使用します。  
  
## <a name="permissions"></a>アクセス許可  
 **Sp_helpmergefilter**を実行できるのは、 **sysadmin**固定サーバーロールおよび**db_owner**固定データベースロールのメンバーだけです。  
  
## <a name="see-also"></a>参照  
 [sp_addmergefilter &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md)   
 [sp_changemergefilter &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-changemergefilter-transact-sql.md)   
 [sp_dropmergefilter &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-dropmergefilter-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
