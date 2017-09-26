---
title: "catalog.environments (SSISDB データベース) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 7014c0e3-65dc-4a46-842e-4decf3737748
caps.latest.revision: 16
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 6e7ba1ba0bd8a444e4609a2f3d011da9cd233b73
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="catalogenvironments-ssisdb-database"></a>catalog.environments (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  すべての環境に対する環境の詳細を表示、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]カタログ。 環境には、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトが参照できる変数が含まれています。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|environment_id|**bigint**|環境の一意識別子 (ID)。|  
|name|**sysname**|環境の名前。|  
|folder_id|**bigint**|環境が存在するフォルダーの一意の ID。|  
|description|**nvarchar (1024)**|環境の説明。 この値は省略可能です。|  
|created_by_sid|**varbinary (85)**|環境を作成したユーザーのセキュリティ識別子 (SID)。|  
|created_by_name|**nvarchar (128)**|環境を作成したユーザーの名前。|  
|created_time|**datetimeoffset**|環境が作成された日時。|  
  
## <a name="remarks"></a>解説  
 このビューは、カタログの各環境の行を表示します。 環境名は、環境が配置されているフォルダーに関してのみ一意です。 たとえば、という名前の環境`E1`カタログに 1 つ以上のフォルダーに存在できますが、各フォルダーが 1 つだけの環境がという名前を持つことができます`E1`です。  
  
## <a name="permissions"></a>Permissions  
 このビューには、次の権限のいずれかが必要です。  
  
-   環境に対する READ 権限  
  
-   メンバーシップを**ssis_admin**データベース ロール  
  
-   メンバーシップを**sysadmin**サーバーの役割  
  
> [!NOTE]  
>  行レベルのセキュリティが適用されるため、表示する権限がある行のみが表示されます。  
  
  
