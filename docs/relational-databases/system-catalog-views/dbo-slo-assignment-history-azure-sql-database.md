---
title: "dbo.slo_assignment_history (Azure SQL データベース) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: 
ms.reviewer: 
ms.suite: sql
ms.prod_service: sql-database
ms.service: sql-database
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dbo.slo_assignment_history
- slo_assignment_history
- slo_assignment_history_TSQL
- dbo.slo_assignment_history_TSQL
dev_langs: TSQL
helpviewer_keywords:
- dbo.slo_assignment_history
- slo_assignment_history
ms.assetid: 048a6fb5-2fc2-4d12-a436-4c53ecd413f3
caps.latest.revision: "9"
author: CarlRabeler
ms.author: carlrab
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: fcff1c5141e6556f8cb4184284769e3be537f80a
ms.sourcegitcommit: b603dcac7326bba387befe68544619e026e6a15e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="dbosloassignmenthistory-azure-sql-database"></a>dbo.slo_assignment_history (Azure SQL データベース)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

    
> [!IMPORTANT]  
>  **これにのみ適用されます[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]V11 します。**  
>   
>  この機能は現在プレビュー状態です。 この機能は将来のリリースで変更または削除される可能性があるので、この機能の特定の実装に依存する設定は行わないでください。  
  
 サーバーのデータベース SLO 割り当ての履歴を返します。これには、次の情報が含まれます。  
  
-   サーバーのデータベース SLO 割り当ての履歴。  
  
-   各データベース SLO 変更要求の開始時刻と終了時刻。  
  
-   error_code 列と error_desc 列に記録されている SLO 割り当てエラー。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|database_name|**sysname**|データベースの名前です。|  
|database_id|**int**|データベースの ID です。|  
|create_date|**datetimeoffset(7)**|データベースの作成日。|  
|service_objective_name|**sysname**|サービス レベル目標 (SLO) の名前。|  
|service_objective_id|**uniqueidentifier**|SLO の ID。|  
|operation_id|**uniqueidentifier**|操作の ID。|  
|operation_start_time|**datetimeoffset(7)**|データベース SLO 変更要求の開始時刻。|  
|operation_end_time|**datetimeoffset(7)**|データベース SLO 変更要求の終了時刻。|  
|error_code|**int**|データベース SLO 変更要求のエラー コード。|  
|error_desc|**nvarchar**|データベース SLO 変更要求のエラーの説明。|  
  
## <a name="permissions"></a>アクセス許可  
 このビューは、仮想に接続する権限を持つすべてのユーザー ロールに利用可能な**マスター**データベース。  
  
## <a name="examples"></a>使用例  
 次の例では、指定されたデータベースのデータベース SLO 割り当ての履歴が返されます。  
  
```  
SELECT *  
FROM dbo.slo_assignment_history   
WHERE database_name = '<DB NAME>’   
ORDER BY operation_start_time DESC;  
  
```  
  
## <a name="see-also"></a>参照  
 [Premium データベースの管理](http://go.microsoft.com/fwlink/?LinkID=311927)  
  
  
