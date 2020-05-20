---
title: xml_schema_wildcards (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.xml_schema_wildcards
- sys.xml_schema_wildcards_TSQL
- xml_schema_wildcards
- xml_schema_wildcards_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.xml_schema_wildcards catalog view
ms.assetid: 7cedfe9a-e99e-4777-8a28-98674b6e5cff
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d7687acb160e872fbe85dc7789115a14e14e875f
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82833862"
---
# <a name="sysxml_schema_wildcards-transact-sql"></a>sys.xml_schema_wildcards (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  XML スキーマコンポーネントごとに1行を返します。これは、属性ワイルド**カード (** **V**) または要素**kind**ワイルドカード ( **W**) であり、どちらも**symbol_space** **N**です。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**\<継承された列>**||[Xml_schema_components](../../relational-databases/system-catalog-views/sys-xml-schema-components-transact-sql.md)から列を継承します。|  
|**process_content**|**char (1)**|コンテンツの処理方法を示します。<br /><br /> S = 厳密な検証 (検証が必要)<br /><br /> L = 厳密でない検証 (可能であれば検証)<br /><br /> P = スキップ検証|  
|**process_content_desc**|**nvarchar(60)**|コンテンツの処理方法の説明。<br /><br /> **STRICT_VALIDATION**<br /><br /> **LAX_VALIDATION**<br /><br /> **SKIP_VALIDATION**|  
|**disallow_namespaces**|**bit**|0 = [xml_schema_wildcard_namespaces](../../relational-databases/system-catalog-views/sys-xml-schema-wildcard-namespaces-transact-sql.md)で列挙された名前空間は、許可されているもののみです。<br /><br /> 1 = 許可されていない名前空間だけが列挙されています。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Transact-sql&#41;&#40;カタログビュー](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Xml スキーマ &#40;XML 型システム&#41; カタログビュー &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)  
  
  
