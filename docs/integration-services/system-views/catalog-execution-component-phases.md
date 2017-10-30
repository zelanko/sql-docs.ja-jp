---
title: "catalog.execution_component_phases |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 07a9a163-4787-40f7-b371-ac5c6cb4b095
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: c3e47e4a5ae297202ba43679fba393421880a7ea
ms.openlocfilehash: b3459ce6d7e9eb0b9580ffa54e3b87e16f3e8fb0
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="catalogexecutioncomponentphases"></a>catalog.execution_component_phases
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  各実行フェーズでデータ フロー コンポーネントが費やした時間を表示します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|phase_stats_id|**bigint**|フェーズの一意識別子 (ID)。|  
|execution_id|**bigint**|実行のインスタンスの一意の ID。|  
|package_name|**nvarchar (260)**|実行中に開始された最初のパッケージの名前。|  
|task_name|**nvarchar (4000)**|データ フロー タスクの名前。|  
|subcomponent_name|**nvarchar (4000)**|データ フロー コンポーネントの名前。|  
|phase|**nvarchar (128)**|実行フェーズの名前。|  
|start_time|**datetimeoffset (7)**|フェーズの開始時刻。|  
|end_time|**datetimeoffset (7)**|フェーズの終了時刻。|  
|execution_path|**nvarchar(max)**|データ フロー タスクの実行パス。|  
  
## <a name="remarks"></a>解説  
 このビューには、Validate、Pre-Execute、Post-Execute、PrimeOutput、ProcessInput など、データ フロー コンポーネントの実行フェーズごとに 1 行表示されます。 各行には、特定の実行フェーズの開始時刻と終了時刻が表示されます。  
  
## <a name="example"></a>例  
 次の例は、catalog.execution_component_phases ビューを使用しての特定のパッケージがすべてのフェーズで実行に費やした時間の合計を検索する (**active_time**)、およびパッケージの経過時間の合計 (**total_time**)。  
  
> [!WARNING]  
>  catalog.execution_component_phases ビューでは、パッケージ実行のログ記録レベルが [パフォーマンス] または [詳細] に設定されている場合のみ、この情報が表示されます。 詳細については、「 [Enable Logging for Package Execution on the SSIS Server](../../integration-services/performance/integration-services-ssis-logging.md#server_logging)」を参照してください。  
  
```sql
use SSISDB  
select package_name, task_name, subcomponent_name, execution_path,  
    SUM(DATEDIFF(ms,start_time,end_time)) as active_time,  
    DATEDIFF(ms,min(start_time), max(end_time)) as total_time  
from catalog.execution_component_phases  
where execution_id = 1841  
group by package_name, task_name, subcomponent_name, execution_path  
order by package_name, task_name, subcomponent_name, execution_path  
```  
  
## <a name="permissions"></a>権限  
 このビューには、次の権限のいずれかが必要です。  
  
-   実行のインスタンスの READ 権限  
  
-   メンバーシップを**ssis_admin**データベース ロール  
  
-   メンバーシップを**sysadmin**サーバーの役割  
  
> [!NOTE]  
>  サーバー上で操作を実行する権限がある場合は、操作に関する情報を表示する権限もあります。 行レベルのセキュリティが適用されるため、表示する権限がある行のみが表示されます。  
  
  

