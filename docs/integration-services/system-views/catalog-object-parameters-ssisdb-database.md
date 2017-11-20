---
title: "catalog.object_parameters (SSISDB データベース) |Microsoft ドキュメント"
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
ms.assetid: d7b04903-2d61-4159-9456-475942d1f732
caps.latest.revision: 18
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 9d538e5b55ef4e8880afb2d008b11c17d9a03189
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="catalogobjectparameters-ssisdb-database"></a>catalog.object_parameters (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  すべてのパッケージのパラメーターを表示し、プロジェクトで、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]カタログ。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|parameter_id|**bigint**|パラメーターの一意識別子 (ID)。|  
|project_id|**bigint**|プロジェクトの一意な ID。|  
|object_type|**smallint**|パラメーターの型。 値が`20`パラメーターと、値は、プロジェクトの`30`パッケージ パラメーターです。|  
|object_name|**sysname**|対応するプロジェクトまたはパッケージの名前。|  
|parameter_name|**sysname(nvarchar(128))**|パラメーターの名前。|  
|data_type|**nvarchar (128)**|パラメーターのデータ型です。|  
|required|**bit**|値が `1` の場合、実行を開始するためパラメーター値が必要です。 値が `0` の場合、実行を開始するためのパラメーター値は不要です。|  
|sensitive|**bit**|値が`1`パラメーター値はセンシティブです。 値が `0` の場合、パラメーター値はセンシティブではありません。|  
|description|**nvarchar (1024)**|パッケージのオプションの説明。|  
|design_default_value|**sql_variant**|プロジェクトまたはパッケージの設計中に割り当てられたパラメーターの既定値。|  
|default_value|**sql_variant**|サーバーで現在使用されている既定値。|  
|value_type|**char (1)**|パラメーター値の型を示します。 このフィールドが表示される`V`パラメーターがリテラル値と`R`環境変数を参照することで、値が割り当てられている場合。|  
|value_set|**bit**|値が`1`パラメーター値が割り当てられています。 値が`0`パラメーターの値が割り当てられていません。|  
|referenced_variable_name|**nvarchar (128)**|パラメーターの値が割り当てられる環境変数の名前。 既定値は**NULL**です。|  
|validation_status|**char (1)**|単に情報を示すためだけに特定されます。 は使用されません[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]です。|  
|last_validation_time|**datetimeoffset (7)**|単に情報を示すためだけに特定されます。 は使用されません[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]です。|  
  
## <a name="permissions"></a>Permissions  
 このビュー内の行を表示するには、次のアクセス権限のいずれかが必要です。  
  
-   プロジェクトに対する READ 権限  
  
-   メンバーシップを**ssis_admin**データベース ロール  
  
-   メンバーシップ、 **sysadmin**サーバーの役割です。  
  
 行レベルのセキュリティが適用されるため、表示する権限がある行のみが表示されます。  
  
  

