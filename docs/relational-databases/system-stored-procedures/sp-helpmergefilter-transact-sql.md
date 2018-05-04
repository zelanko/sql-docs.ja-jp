---
title: sp_helpmergefilter (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
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
- sp_helpmergefilter
- sp_helpmergefilter_TSQL
helpviewer_keywords:
- sp_helpmergefilter
ms.assetid: f133a094-0009-4771-b93b-e86a5c01e40b
caps.latest.revision: 15
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 2819008bf7790558d39fb893fbd9de4ed52eaa99
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sphelpmergefilter-transact-sql"></a>sp_helpmergefilter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  マージ フィルターに関する情報を返します。 このストアド プロシージャは、任意のデータベース上のパブリッシャー側で実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helpmergefilter [ @publication= ] 'publication'   
    [ , [ @article= ] 'article']  
    [ , [ @filtername= ] 'filtername']  
```  
  
## <a name="arguments"></a>引数  
 [ **@publication=**] **'***publication***'**  
 パブリケーションの名前です。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [  **@article=**] **'***記事***'**  
 アーティクルの名前を指定します。 *記事*は**sysname**、既定値は**%**、すべてのアーティクルの名前が返されます。  
  
 [  **@filtername=**] **'***filtername***'**  
 情報を返すフィルターの名前を指定します。 *filtername*は**sysname**、既定値は**%**、アーティクルまたはパブリケーションで定義されているすべてのフィルターに関する情報が返されます。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**join_filterid**|**int**|結合フィルターの ID。|  
|**filtername**|**sysname**|フィルターの名前。|  
|**結合アーティクル名**|**sysname**|結合アーティクルの名前。|  
|**join_filterclause**|**nvarchar(2000)**|結合を修飾するフィルター句。|  
|**join_unique_key**|**int**|一意なキーを基に結合を行うかどうかを示します。|  
|**ベース テーブルの所有者**|**sysname**|テーブル所有者の名前。|  
|**ベース テーブル名**|**sysname**|ベース テーブルの名前。|  
|**結合テーブルの所有者**|**sysname**|ベース テーブルに結合するテーブルの所有者の名前。|  
|**結合テーブルの名前**|**sysname**|ベース テーブルに結合するテーブルの名前。|  
|**アーティクルの名前**|**sysname**|ベース テーブルに結合するテーブル アーティクルの名前。|  
|**filter_type**|**tinyint**|マージ フィルターの種類。次のいずれかになります。<br /><br /> **1** = 結合フィルターのみ<br /><br /> **2** = 論理レコードのリレーションシップ<br /><br /> **3** = 両方|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_helpmergefilter**はマージ レプリケーションで使用します。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールおよび**db_owner**固定データベース ロールが実行できる**sp_helpmergefilter**です。  
  
## <a name="see-also"></a>参照  
 [sp_addmergefilter (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md)   
 [sp_changemergefilter (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changemergefilter-transact-sql.md)   
 [sp_dropmergefilter (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-dropmergefilter-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
