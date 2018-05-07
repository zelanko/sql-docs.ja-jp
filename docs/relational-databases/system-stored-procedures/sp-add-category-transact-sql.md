---
title: sp_add_category (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_add_category
- sp_add_category_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_category
ms.assetid: 6cca32cd-d941-4378-aed6-a7c90cb7520a
caps.latest.revision: 29
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d6f98fd4dbccc6b47297c8b0ebb2073dd23d35c6
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="spaddcategory-transact-sql"></a>sp_add_category (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定されたジョブ、警告、またはオペレーターのカテゴリをサーバーに追加します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_add_category   
     [ [ @class = ] 'class', ]   
     [ [ @type = ] 'type', ]   
     { [ @name = ] 'name' }  
```  
  
## <a name="arguments"></a>引数  
 [  **@class =** ] **'***クラス***'**  
 追加するカテゴリのクラスを指定します。 *クラス*は**varchar (8)** ジョブの既定値は、これらの値のいずれかを指定できます。  
  
|値|Description|  
|-----------|-----------------|  
|JOB|ジョブ カテゴリを追加します。|  
|ALERT|警告カテゴリを追加します。|  
|OPERATOR|オペレーター カテゴリを追加します。|  
  
 [ **@type =** ] **'***type***'**  
 追加するカテゴリの種類を指定します。 *型*は**varchar (12)**、既定値は**ローカル**、これらの値のいずれかを指定できます。  
  
|値|Description|  
|-----------|-----------------|  
|LOCAL|ローカル ジョブ カテゴリ|  
|マルチ サーバー|マルチサーバー ジョブ カテゴリ|  
|なし|JOB 以外のクラスのカテゴリ**です。**|  
  
 [ **@name =** ] **'***name***'**  
 追加するカテゴリの名前を指定します。 名前は指定したクラス内で一意であることが必要です。 *名前*は**sysname**、既定値はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>解説  
 **sp_add_category**から実行する必要があります、 **msdb**データベース。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールが実行できる**sp_add_category**です。  
  
## <a name="examples"></a>使用例  
 次の例では、`AdminJobs` というローカル ジョブ カテゴリを作成します。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_category  
    @class=N'JOB',  
    @type=N'LOCAL',  
    @name=N'AdminJobs' ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sp_delete_category &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-category-transact-sql.md)   
 [sp_help_category &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-category-transact-sql.md)   
 [sp_update_category &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-category-transact-sql.md)   
 [dbo.sysjobs & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/dbo-sysjobs-transact-sql.md)   
 [dbo.sysjobservers &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/dbo-sysjobservers-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
