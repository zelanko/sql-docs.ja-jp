---
title: sys.xml_schema_component_placements (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.xml_schema_component_placements
- xml_schema_component_placements_TSQL
- xml_schema_component_placements
- sys.xml_schema_component_placements_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.xml_schema_component_placements catalog view
ms.assetid: 2d3c8828-e4b3-423d-bf11-990464c1341b
caps.latest.revision: 32
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f45959897408779385e598353fb900b0403af80b
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="sysxmlschemacomponentplacements-transact-sql"></a>sys.xml_schema_component_placements (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  XML スキーマ コンポーネントの配置ごとに 1 行のデータを返します。  
   
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**xml_component_id**|**int**|配置を所有する XML スキーマ コンポーネントの ID。|  
|**placement_id**|**int**|配置の ID。 配置を所有する XML スキーマ コンポーネント内で一意です。|  
|**placed_xml_component_id**|**int**|配置された XML スキーマ コンポーネントの ID。|  
|**is_default_fixed**|**bit**|1 = デフォルト値は固定値です。 この値は、XML インスタンスでオーバーライドされることはできません。<br /><br /> 0 = 値は無効にできます (既定)。|  
|**min_occurrences**|**int**|配置されたコンポーネントが出現する最小数。|  
|**max_occurrences**|**int**|配置されたコンポーネントが出現する最大数。|  
|**default_value**|**nvarchar (4000)**|既定値が提供される場合はその値。 既定値が提供されない場合は NULL になります。|  
  
## <a name="permissions"></a>権限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [XML スキーマ&#40;XML 型システム&#41;カタログ ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)  
  
  
