---
title: "sys.xml_schema_attributes (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- xml_schema_attributes_TSQL
- xml_schema_attributes
- sys.xml_schema_attributes_TSQL
- sys.xml_schema_attributes
dev_langs:
- TSQL
helpviewer_keywords:
- sys.xml_schema_attributes catalog view
ms.assetid: dd0c98aa-5e72-4df6-96d9-482786c8dbb1
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0cbb4458a97ceb00ae0c71cbad5f492e345876e1
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sysxmlschemaattributes-transact-sql"></a>sys.xml_schema_attributes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  属性である XML スキーマ コンポーネントごとに 1 行を返します**symbol_space**の**A**です。  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**\<継承された列 >**|--|継承[sys.xml_schema_components](../../relational-databases/system-catalog-views/sys-xml-schema-components-transact-sql.md)です。|  
|**is_default_fixed**|**bit**|1 = デフォルト値は固定値です。 この値は、XML インスタンスでオーバーライドされることはできません。<br /><br /> 0 = デフォルト値は属性の固定値ではありません  (既定値)。|  
|**must_be_qualified**|**bit**|1 = 属性には明示的に名前空間の修飾名を追加する必要があります。<br /><br /> 0 = 属性には暗黙的に名前空間の修飾名を追加できます  (既定値)。|  
|**default_value です。**|**nvarchar**<br /><br /> **(4000)**|属性の既定値。 既定値が提供されない場合は NULL になります。|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [XML スキーマと #40 です。XML 型システム &#41;カタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
