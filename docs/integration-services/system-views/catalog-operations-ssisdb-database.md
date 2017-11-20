---
title: "catalog.operations (SSISDB データベース) |Microsoft ドキュメント"
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
- operations view [Integration Services]
- catalog.operations view [Integration Services]
ms.assetid: 9455c5b1-60ff-45fc-8599-cc3abbd6daf5
caps.latest.revision: 29
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: f9d1969e9fe7bcb2104003cfab057effcd35da5d
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="catalogoperations-ssisdb-database"></a>catalog.operations (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] カタログのすべての操作の詳細を表示します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|operation_id|**bigint**|操作の一意識別子 (ID)。|  
|operation_type|**smallint**|操作の種類。|  
|created_time|**datetimeoffset**|操作が作成された時間。|  
|object_type|**smallint**|操作の影響を受けるオブジェクトの種類。 オブジェクトは、フォルダーにあります (`10`)、プロジェクト (`20`)、パッケージ (`30`)、環境 (`40`)、または実行のインスタンス (`50`)。|  
|object_id|**bigint**|操作の影響を受けるオブジェクトの ID。|  
|object_name|**nvarchar (260)**|オブジェクトの名前。|  
|ステータス|**int**|操作の状態。 使用可能な値が作成されます (`1`)、実行中 (`2`)、取り消し済み (`3`) に失敗しました (`4`)、保留中 (`5`)、予期しない終了 (`6`)、成功 (`7`)、(を停止しています`8`)、および完了した (`9`)。|  
|start_time|**datetimeoffset**|操作が開始された時刻。|  
|end_time|**datetimeoffsset**|操作が終了時刻。|  
|caller_sid|**varbinary (85)**|ログオンに Windows 認証が使用された場合はユーザーのセキュリティ ID (SID)。|  
|させていただきたいと|**nvarchar (128)**|操作を実行したアカウントの名前。|  
|process_id|**int**|外部プロセスのプロセス ID (該当する場合)。|  
|stopped_by_sid|**varbinary (85)**|操作を停止したユーザーの SID。|  
|stopped_by_name|**nvarchar (128)**|操作を停止したユーザーの名前。|  
|server_name|**nvarchar (128)**|指定のインスタンスの Windows サーバーとインスタンス情報[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。|  
|machine_name|**nvarchar (128)**|サーバー インスタンスが稼働しているコンピューターの名前。|  
  
## <a name="remarks"></a>解説  
 このビュー内の各操作の 1 つの行を表示、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]カタログ。 管理者は、プロジェクトの配置、パッケージの実行など、サーバーで実行されたすべての論理操作を列挙します。  
  
 この表示は、次の操作の種類に記載されている、 **operation_type**列。  
  
|**operation_type**値|**operation_type**の説明|**object_id**の説明|**object_name**の説明|  
|-------------------------------|-------------------------------------|--------------------------------|----------------------------------|  
|`1`|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] の初期化|**NULL**|**NULL**|  
|`2`|保有期間ウィンドウ<br /><br /> (SQL エージェント ジョブ)|**NULL**|**NULL**|  
|`3`|MaxProjectVersion<br /><br /> (SQL エージェント ジョブ)|**NULL**|**NULL**|  
|`101`|**deploy_project**<br /><br /> (ストアド プロシージャ)|プロジェクト ID|プロジェクト名|  
|`106`|**restore_project**<br /><br /> (ストアド プロシージャ)|プロジェクト ID|プロジェクト名|  
|`200`|**create_execution**と**start_execution**<br /><br /> (ストアド プロシージャ)|プロジェクト ID|**NULL**|  
|`202`|**stop_operation**<br /><br /> (ストアド プロシージャ)|プロジェクト ID|**NULL**|  
|`300`|**validate_project**<br /><br /> (ストアド プロシージャ)|プロジェクト ID|プロジェクト名|  
|`301`|**validate_package**<br /><br /> (ストアド プロシージャ)|プロジェクト ID|パッケージ名|  
|`1000`|**configure_catalog**<br /><br /> (ストアド プロシージャ)|**NULL**|**NULL**||  
  
## <a name="permissions"></a>Permissions  
 このビューには、次の権限のいずれかが必要です。  
  
-   この操作の READ 権限  
  
-   メンバーシップを**ssis_admin**データベース ロール  
  
-   メンバーシップを**sysadmin**サーバーの役割  
  
> [!NOTE]  
>  サーバー上で操作を実行する権限がある場合は、操作に関する情報を表示する権限もあります。 行レベルのセキュリティが適用されるため、表示する権限がある行のみが表示されます。  
  
  

