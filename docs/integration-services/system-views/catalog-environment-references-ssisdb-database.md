---
title: "catalog.environment_references (SSISDB データベース) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: efec53ef-3e5a-4b76-b71d-a0cf9e11ac00
caps.latest.revision: 18
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: ee6f15af7a5384fea850aa67c7b5a95483530740
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="catalogenvironmentreferences-ssisdb-database"></a>catalog.environment_references (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  すべてのプロジェクトに対する環境参照を表示、 **SSISDB**カタログ。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|reference_id|**bigint**|参照の一意識別子 (ID)。|  
|project_id|**bigint**|プロジェクトの一意な ID。|  
|reference_type|**char (1)**|環境をプロジェクトと同じフォルダーに配置できるか (相対参照)、または別のフォルダーに配置できるか (絶対参照) を示します。 値が `R` の場合、環境は相対参照を使用して配置されます。 値が`A`、絶対の参照を使用して、環境を配置します。|  
|environment_folder_name|**sysname**|環境が絶対参照を使用して配置される場合は、フォルダーの名前。|  
|environment_name|**sysname**|プロジェクトによって参照される環境の名前。|  
|validation_status|**char (1)**|検証の状態。|  
|last_validation_time|**datatimeoffset(7)**|前回の検証操作の時刻。|  
  
## <a name="remarks"></a>解説  
 このビューは、カタログの各環境参照の行を表示します。  
  
## <a name="permissions"></a>Permissions  
 このビューには、次の権限のいずれかが必要です。  
  
-   対応するプロジェクトに対する READ 権限  
  
-   メンバーシップを**ssis_admin**データベース ロール  
  
-   メンバーシップを**sysadmin**サーバーの役割です。  
  
> [!NOTE]  
>  プロジェクトの READ 権限がある場合は、そのプロジェクトに関連付けられたすべてのパッケージおよび環境の READ 権限もあります。 行レベルのセキュリティが適用されるため、表示する権限がある行のみが表示されます。  
  
## <a name="remarks"></a>解説  
 プロジェクトでは、相対または絶対環境参照を使用できます。 相対参照では、環境を名前で参照され、プロジェクトと同じフォルダーに格納されている必要があります。 絶対参照の場合、名前とフォルダーによって環境を参照します。プロジェクトとは異なるフォルダーに格納されている環境を参照する場合があります。 プロジェクトでは複数の環境を参照できます。  
  
  
