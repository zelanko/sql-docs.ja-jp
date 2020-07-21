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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 45fea43b9d7d35fd674a566982d67b4043403d06
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85900602"
---
# <a name="syspolicy_conditions-transact-sql"></a>syspolicy_conditions (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  インスタンスのポリシーベースの管理条件ごとに1つの行を表示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] します。 syspolicy_conditions は、msdb データベースの dbo スキーマに属します。 次の表では、syspolicy_conditions ビュー内の列について説明します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|condition_id|**int**|この条件の識別子。 各条件は、1つまたは複数の条件式のコレクションを表します。|  
|name|**sysname**|条件の名前。|  
|date_created|**datetime**|条件が作成された日付と時刻。|  
|description|**nvarchar(max)**|条件の説明。 この説明の列は省略可能であり、NULL の場合もあります。|  
|created_by|**sysname**|条件を作成したログイン。|  
|modified_by|**sysname**|最後に条件を変更したログイン。 変更されていない場合は NULL になります。|  
|date_modified|**datetime**|条件が作成された日付と時刻。 変更されていない場合は NULL になります。|  
|is_name_condition|**smallint**|条件が名前付け条件であるかどうかを指定します。<br /><br /> 0 = 条件式には @Name 変数が含まれません。<br /><br /> 1 = 条件式には、変数が含まれてい @Name ます。|  
|facet|**nvarchar(max)**|条件の基になっているファセットの名前。|  
|Expression|**nvarchar(max)**|ファセットの状態の式。|  
|obj_name|**sysname**|@Name条件式にこの変数が含まれている場合にに割り当てられるオブジェクト名。|  
  
## <a name="remarks"></a>注釈  
 ポリシー ベースの管理のトラブルシューティングを行う場合に、条件を作成または最後に変更したユーザーを特定するには、syspolicy_conditions ビューを照会します。  
  
## <a name="permissions"></a>アクセス許可  
 msdb データベースの PolicyAdministratorRole ロールのメンバーシップが必要です。  
  
## <a name="see-also"></a>関連項目  
 [ポリシーベースの管理を使用してサーバーを管理する](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [ポリシーベースの管理ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)  
  
  
