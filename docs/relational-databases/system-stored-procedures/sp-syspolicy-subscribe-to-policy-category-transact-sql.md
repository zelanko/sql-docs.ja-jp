---
title: "sp_syspolicy_subscribe_to_policy_category は (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_syspolicy_subscribe_to_policy_category
- sp_syspolicy_subscribe_to_policy_category_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_syspolicy_subscribe_to_policy_category
ms.assetid: de88cc49-bcc8-4dc6-8e59-ad85cfbfb2fb
caps.latest.revision: "7"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5d3ae8b6f35b5135066d9ab7164524406e165219
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="spsyspolicysubscribetopolicycategory-transact-sql"></a>sp_syspolicy_subscribe_to_policy_category (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定したデータベースにポリシー カテゴリのサブスクリプションを追加します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_syspolicy_subscribe_to_policy_category [ @policy_category = ] 'policy_category'  
```  
  
## <a name="arguments"></a>引数  
 [  **@policy_category=** ] **'***policy_category***'**  
 データベースでサブスクライブするポリシー カテゴリの名前を指定します。 *policy_category*は**sysname**が必要とします。  
  
 値を取得する*policy_category*、msdb.dbo.syspolicy_policy_categories システム ビューにクエリします。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 sp_syspolicy_subscribe_to_policy_category は、ポリシー カテゴリを追加するデータベースのコンテキストで実行する必要があります。  
  
## <a name="permissions"></a>Permissions  
 db_owner 固定データベース ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、指定したデータベースの 'Finance' ポリシーのカテゴリにサブスクリプションを追加します。  
  
```  
USE <database_name>;  
  
EXEC sys.sp_syspolicy_subscribe_to_policy_category @policy_category = N'Finance';  
  
GO  
```  
  
## <a name="see-also"></a>参照  
 [ポリシー ベースの管理ストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)   
 [sp_syspolicy_unsubscribe_from_policy_category は &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-syspolicy-unsubscribe-from-policy-category-transact-sql.md)  
  
  
