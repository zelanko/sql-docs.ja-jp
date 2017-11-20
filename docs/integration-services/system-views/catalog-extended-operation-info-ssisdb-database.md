---
title: "catalog.extended_operation_info (SSISDB データベース) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
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
ms.assetid: db299b45-557d-4c62-8e14-355cdb051f63
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 4d89a9adbf89dcc89715832664dcca176cd7f2ff
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="catalogextendedoperationinfo-ssisdb-database"></a>catalog.extended_operation_info (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] カタログのすべての操作に対する拡張された情報を表示します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|info_id|**bigint**|拡張された情報の一意識別子 (ID)。|  
|operation_id|**bigint**|拡張された情報に対応する操作の一意の ID。|  
|object_name|**nvarchar (260)**|オブジェクトの名前。|  
|object_type|**smallint**|操作の影響を受けるオブジェクトの種類。 オブジェクトは、フォルダーにあります (`10`)、プロジェクト (`20`)、パッケージ (`30`)、環境 (`40`)、または実行のインスタンス (`50`)。|  
|reference_id|**bigint**|操作で使用される参照の一意の ID。|  
|ステータス|**int**|操作の状態。 使用可能な値が作成されます (`1`)、実行中 (`2`)、取り消し済み (`3`) に失敗しました (`4`)、保留中 (`5`)、予期しない終了 (`6`)、成功 (`7`)、(を停止しています`8`)、および完了した (`9`)。|  
|start_time|**datetimeoffset (7)**|操作が開始された日時。|  
|end_time|**datetimeoffset (7)**|操作が終了した日時。|  
  
## <a name="remarks"></a>解説  
 1 回の操作で、複数の拡張された情報行を指定できます。  
  
## <a name="permissions"></a>Permissions  
 このビューには、次の権限のいずれかが必要です。  
  
-   この操作の READ 権限  
  
-   メンバーシップを**ssis_admin**データベース ロール  
  
-   メンバーシップを**sysadmin**サーバーの役割  
  
> [!NOTE]  
>  サーバー上で操作を実行する権限がある場合は、操作に関する情報を表示する権限もあります。 行レベルのセキュリティが適用されるため、表示する権限がある行のみが表示されます。  
  
  

