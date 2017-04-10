---
title: "データ フローの分析 | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5654cb30-cad2-470c-97b3-59cb331033e5
caps.latest.revision: 11
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 11
---
# データ フローの分析
  [catalog.execution_data_statistics](../../integration-services/system-views/catalog-execution-data-statistics.md) **SSISDB** データベース ビューを使用して、パッケージのデータ フローを分析できます。 このビューは、データ フロー コンポーネントが下流コンポーネントへデータを送信するたびに 1 行表示します。 この情報を使用して、各コンポーネントに送信される行をより詳しく理解できます。  
  
> [!NOTE]  
>  catalog.execution_data_statistics ビューに関する情報を取得するために、ログ レベルは**詳細**に設定する必要があります。  
  
 次の例では、パッケージのコンポーネント間で送信された行の数が表示されます。  
  
```  
use SSISDB  
select package_name, task_name, source_component_name, destination_component_name, rows_sent  
from catalog.execution_data_statistics  
where execution_id = 132  
order by source_component_name, destination_component_name  
  
```  
  
 以下の例では、特定の実行で各コンポーネントによって送信された 1 ミリ秒あたりの行数が計算されます。 計算される値は次のとおりです。  
  
-   **total_rows** - コンポーネントによって送信されたすべての行の合計数  
  
-   **wall_clock_time_ms** – コンポーネントごとの実行の合計経過時間 (ミリ秒単位)  
  
-   **num_rows_per_millisecond** – 各コンポーネントによって送信された 1 ミリ秒あたりの行数  
  
 計算時の 0 除算エラーを防止するために **HAVING** 句が使用されています。  
  
```  
use SSISDB  
select source_component_name, destination_component_name,  
    sum(rows_sent) as total_rows,  
    DATEDIFF(ms,min(created_time),max(created_time)) as wall_clock_time_ms,  
    ((0.0+sum(rows_sent)) / (datediff(ms,min(created_time),max(created_time)))) as [num_rows_per_millisecond]  
from [catalog].[execution_data_statistics]  
where execution_id = 132  
group by source_component_name, destination_component_name  
having (datediff(ms,min(created_time),max(created_time))) > 0  
order by source_component_name desc  
  
```  
  
## 関連タスク  
 [データ フローのデバッグ](../../integration-services/troubleshooting/debugging-data-flow.md)  
  
 [パッケージ実行のトラブルシューティング ツール](../../integration-services/troubleshooting/troubleshooting-tools-for-package-execution.md)  
  
## 参照  
 [データ フロー内のデータ](../../integration-services/data-flow/data-in-data-flows.md)  
  
  