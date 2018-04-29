---
title: catalog.object_versions (SSISDB データベース) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: system-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.assetid: 2fd8c020-1c77-4702-8e6b-efa6a348daab
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c7dd49966f21ec30129ed325d8693cb03aef477c
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="catalogobjectversions-ssisdb-database"></a>catalog.object_versions (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] カタログのオブジェクトのバージョンを示します。 このリリースでは、プロジェクトのバージョンのみがこのビューでサポートされます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|object_version_lsn|**bigint**|オブジェクト バージョンの一意識別子 (ID)。 この番号は、シーケンシャルを保証するものではありません。|  
|object_id|**bigint**|オブジェクトの一意の ID。|  
|object_type|**smallint**|オブジェクトの種類。 プロジェクトには、値 `20` が表示されます。|  
|object_name|**sysname(nvarchar(128))**|オブジェクトの名前。|  
|description|**nvarchar(1024)**|プロジェクトの説明。|  
|created_by|**nvarchar(128)**|オブジェクトをカタログに追加したユーザーの名前。|  
|created_time|**datetimeoffset**|オブジェクトがカタログに追加された日時。|  
|restored_by|**nvarchar(128)**|オブジェクトを復元したユーザーの名前。|  
|last_restored_time|**datetimeoffset**|オブジェクトが前回復元された日時。|  
  
## <a name="remarks"></a>Remarks  
 このビューは、カタログの各オブジェクトの行を表示します。  
  
## <a name="permissions"></a>アクセス許可  
 このビュー内の行を表示するには、次のアクセス権限のいずれかが必要です。  
  
-   オブジェクトの READ 権限  
  
-   **ssis_admin** データベース ロールのメンバーシップ  
  
-   **sysadmin** サーバー ロールのメンバーシップ  
  
> [!NOTE]  
>  行レベルのセキュリティが適用されるため、表示する権限がある行のみが表示されます。  
  
  
