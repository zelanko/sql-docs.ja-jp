---
title: "catalog.execution_data_statistics |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 6f51407e-0e4e-4b44-af33-db14c9d40ded
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: c3e47e4a5ae297202ba43679fba393421880a7ea
ms.openlocfilehash: fa1d87489ff6d0a10d95bf160ded3d038ca39d81
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="catalogexecutiondatastatistics"></a>catalog.execution_data_statistics
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  このビューは、特定のパッケージ実行で、データ フロー コンポーネントが下流コンポーネントへデータを送信するたびに 1 行を表示します。 このビューの情報が使用して、コンポーネントのデータ スループットを計算できます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|data_stats_id|**bigint**|データの一意識別子 (ID)。|  
|execution_id|**bigint**|実行のインスタンスの一意の ID。|  
|package_name|**nvarchar (260)**|実行中に開始された最初のパッケージの名前。|  
|task_name|**nvarchar (4000)**|データ フロー タスクの名前。|  
|dataflow_path_id_string|**nvarchar (4000)**|データ フロー パスの識別文字列です。|  
|dataflow_path_name|**nvarchar (4000)**|データ フロー パスの名前。|  
|source_component_name|**nvarchar (4000)**|データを送信したデータ フロー コンポーネントの名前。|  
|destination_component_name|**nvarchar (4000)**|データを受信したデータ フロー コンポーネントの名前。|  
|rows_sent|**bigint**|送信元コンポーネントから送信された行の数。|  
|created_time|**datatimeoffset(7)**|値の取得時刻。|  
|execution_path|**nvarchar(max)**|コンポーネントの実行パス。|  
  
## <a name="remarks"></a>解説  
  
-   コンポーネントから複数の出力がある場合、出力ごとに 1 行追加されます。  
  
-   既定では、実行開始時には、送信される行数に関する情報はログに記録されません。  
  
-   特定のパッケージ実行用には、このデータを表示するログ レベルを設定**Verbose**です。 詳細については、「 [Enable Logging for Package Execution on the SSIS Server](../../integration-services/performance/integration-services-ssis-logging.md#server_logging)」を参照してください。  
  
## <a name="permissions"></a>権限  
 このビューには、次の権限のいずれかが必要です。  
  
-   実行のインスタンスの READ 権限  
  
-   メンバーシップを**ssis_admin**データベース ロール  
  
-   メンバーシップを**sysadmin**サーバーの役割  
  
> [!NOTE]  
>  サーバー上で操作を実行する権限がある場合は、操作に関する情報を表示する権限もあります。 行レベルのセキュリティが適用されるため、表示する権限がある行のみが表示されます。  
  
  
