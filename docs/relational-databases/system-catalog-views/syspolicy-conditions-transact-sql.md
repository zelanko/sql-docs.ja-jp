---
title: syspolicy_conditions (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- syspolicy_conditions
- syspolicy_conditions_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- syspolicy_conditions view
ms.assetid: af97d26c-4bd5-4b08-be51-8419e3b2832c
author: stevestein
ms.author: sstein
ms.openlocfilehash: ee0f269fcfda93733d36a0b7396fd72d16bc01d9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68121172"
---
# <a name="syspolicy_conditions-transact-sql"></a>syspolicy_conditions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  インスタンスのポリシーベースの管理条件ごとに1つの行を[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]表示します。 syspolicy_conditions は、msdb データベースの dbo スキーマに属します。 次の表では、syspolicy_conditions ビュー内の列について説明します。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|condition_id|**int**|この条件の識別子。 各条件は、1つまたは複数の条件式のコレクションを表します。|  
|name|**sysname**|条件の名前。|  
|date_created|**DATETIME**|条件が作成された日付と時刻。|  
|description|**nvarchar(max)**|条件の説明。 この説明の列は省略可能であり、NULL の場合もあります。|  
|created_by|**sysname**|条件を作成したログイン。|  
|modified_by|**sysname**|最後に条件を変更したログイン。 変更されていない場合は NULL になります。|  
|date_modified|**DATETIME**|条件が作成された日付と時刻。 変更されていない場合は NULL になります。|  
|is_name_condition|**smallint**|条件が名前付け条件であるかどうかを指定します。<br /><br /> 0 = 条件式には @Name 変数が含まれません。<br /><br /> 1 = 条件式には、 @Name変数が含まれています。|  
|ファセット (facet)|**nvarchar(max)**|条件の基になっているファセットの名前。|  
|式|**nvarchar(max)**|ファセットの状態の式。|  
|obj_name|**sysname**|条件式にこの変数@Nameが含まれている場合にに割り当てられるオブジェクト名。|  
  
## <a name="remarks"></a>解説  
 ポリシー ベースの管理のトラブルシューティングを行う場合に、条件を作成または最後に変更したユーザーを特定するには、syspolicy_conditions ビューを照会します。  
  
## <a name="permissions"></a>アクセス許可  
 msdb データベースの PolicyAdministratorRole ロールのメンバーシップが必要です。  
  
## <a name="see-also"></a>参照  
 [ポリシーベースの管理を使用してサーバーを管理する](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [ポリシーベースの管理ビュー &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)  
  
  
