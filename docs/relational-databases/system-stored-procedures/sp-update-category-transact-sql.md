---
title: sp_update_category (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_update_category
- sp_update_category_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_update_category
ms.assetid: 098b926a-b078-4122-a5e1-3ef54b979dd4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 22cb6ac1283c0ad8e7b423d73f6ec768c90af11c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47670520"
---
# <a name="spupdatecategory-transact-sql"></a>sp_update_category (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  カテゴリ名を変更します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_update_category  
     [@class =] 'class' ,   
     [@name =] 'old_name' ,  
     [@new_name =] 'new_name'  
```  
  
## <a name="arguments"></a>引数  
 [  **@class =**] **'***クラス***'**  
 更新するカテゴリのクラスを指定します。 *クラス*は**varchar (8)**, で、既定値はありませんはこれらの値のいずれかを指定します。  
  
|値|説明|  
|-----------|-----------------|  
|**アラートを生成します。**|警告カテゴリを更新します。|  
|**JOB**|ジョブ カテゴリを更新します。|  
|**演算子**|オペレーター カテゴリを更新します。|  
  
 [ **@name =**] **'***old_name***'**  
 カテゴリの現在の名前を指定します。 *古い名前*は**sysname**、既定値はありません。  
  
 [ **@new_name =**] **'***new_name***'**  
 カテゴリの新しい名前を指定します。 *新しい名前*は**sysname**、既定値はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_update_category**から実行する必要があります、 **msdb**データベース。  
  
## <a name="permissions"></a>アクセス許可  
 このストアド プロシージャを実行するユーザーに付与する必要があります、 **sysadmin**固定サーバー ロール。  
  
## <a name="examples"></a>使用例  
 次の例では、ジョブ カテゴリの名前を `AdminJobs` から `Administrative Jobs` に変更します。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_update_category  
  @class = N'JOB',  
  @name = N'AdminJobs',  
  @new_name = N'Administrative Jobs' ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sp_add_category &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-category-transact-sql.md)   
 [sp_delete_category &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-category-transact-sql.md)   
 [sp_help_category &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-category-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
