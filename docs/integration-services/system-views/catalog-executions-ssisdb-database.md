---
title: "catalog.executions (SSISDB データベース) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: system-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- executions view [Integration Services]
- catalog.executions view [Integration Services]
ms.assetid: 879f13b0-331d-4dee-a079-edfaca11ae5b
caps.latest.revision: 32
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 5e60664352054cd8f62250cc7c6b8082e84f607f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="catalogexecutions-ssisdb-database"></a>catalog.executions (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] カタログのパッケージ実行のインスタンスを表示します。 パッケージ実行タスクで実行されるパッケージは、親パッケージと同じ実行のインスタンスで実行されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|execution_id|**bigint**|実行のインスタンスの一意の識別子 (ID)。|  
|folder_name|**sysname(nvarchar(128))**|プロジェクトを含むフォルダーの名前。|  
|project_name|**sysname(nvarchar(128))**|プロジェクトの名前。|  
|package_name|**nvarchar (260)**|実行中に開始された最初のパッケージの名前。|  
|reference_id|**bigint**|実行のインスタンスによって参照される環境。|  
|reference_type|**char (1)**|環境をプロジェクトと同じフォルダーに配置できるか (相対参照)、または別のフォルダーに配置できるか (絶対参照) を示します。 値が `R` の場合、環境は相対参照を使用して配置されます。 値が`A`、絶対の参照を使用して、環境を配置します。|  
|environment_folder_name|**nvarchar (128)**|環境を含むフォルダーの名前。|  
|environment_name|**nvarchar (128)**|実行中に参照された環境の名前。|  
|project_lsn|**bigint**|実行のインスタンスに対応するプロジェクトのバージョン。 この番号は、シーケンシャルを保証するものではありません。|  
|executed_as_sid|**varbinary (85)**|実行のインスタンスを起動したユーザーの SID。|  
|executed_as_name|**nvarchar (128)**|実行のインスタンスを起動するために使用されたデータベース プリンシパルの名前。|  
|use32bitruntime|**bit**|64 ビット オペレーティング システムで 32 ビットのランタイムを使用してパッケージを実行するかどうかを示します。 値が`1`、32 ビット ランタイムで実行します。 値が`0`、64 ビット ランタイムで実行します。|  
|object_type|**smallint**|オブジェクトの種類。 オブジェクトは、プロジェクトである可能性があります (`20`) またはパッケージ (`30`)。|  
|object_id|**bigint**|操作の影響を受けるオブジェクトの ID。|  
|ステータス|**int**|操作の状態。 使用可能な値が作成されます (`1`)、実行中 (`2`)、取り消し済み (`3`) に失敗しました (`4`)、保留中 (`5`)、予期しない終了 (`6`)、成功 (`7`)、(を停止しています`8`)、および完了した (`9`)。|  
|start_time|**datetimeoffset**|実行のインスタンスが起動された時間。|  
|end_time|**datetimeoffsset**|実行のインスタンスが終了した時間。|  
|caller_sid|**varbinary (85)**|ログオンに Windows 認証が使用された場合はユーザーのセキュリティ ID (SID)。|  
|させていただきたいと|**nvarchar (128)**|操作を実行したアカウントの名前。|  
|process_id|**int**|外部プロセスのプロセス ID (該当する場合)。|  
|stopped_by_sid|**varbinary (85)**|実行のインスタンスを停止したユーザーのセキュリティ ID (SID)。|  
|stopped_by_name|**nvarchar (128)**|実行のインスタンスを停止したユーザーの名前。|  
|total_physical_memory_kb|**bigint**|実行開始時にサーバーに搭載されている物理メモリの合計 (MB 単位)。|  
|available_physical_memory_kb|**bigint**|実行開始時にサーバーで利用可能な物理メモリの量 (MB 単位)。|  
|total_page_file_kb|**bigint**|実行開始時にサーバーに搭載されているページ メモリの合計 (MB 単位)。|  
|available_page_file_kb|**bigint**|実行開始時にサーバーで利用可能なページ メモリの量 (MB 単位)。|  
|cpu_count|**int**|実行開始時のサーバー上の論理 CPU の数。|  
|server_name|**nvarchar (128)**|指定のインスタンスの Windows サーバーとインスタンス情報[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。|  
|machine_name|**nvarchar (128)**|サーバー インスタンスが稼働しているコンピューターの名前。|  
|dump_id|**uniqueidentifier**|実行ダンプの ID。|  
  
## <a name="remarks"></a>解説  
 このビューは、カタログの実行の各インスタンスの行を表示します。  
  
## <a name="permissions"></a>Permissions  
 このビューには、次の権限のいずれかが必要です。  
  
-   実行のインスタンスの READ 権限  
  
-   メンバーシップを**ssis_admin**データベース ロール  
  
-   メンバーシップを**sysadmin**サーバーの役割  
  
> [!NOTE]  
>  行レベルのセキュリティが適用されるため、表示する権限がある行のみが表示されます。  
  
  

