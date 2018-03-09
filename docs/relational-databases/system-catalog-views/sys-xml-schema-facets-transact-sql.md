---
title: "sys.xml_schema_facets (TRANSACT-SQL) |Microsoft ドキュメント"
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
- sys.xml_schema_facets
- xml_schema_facets_TSQL
- sys.xml_schema_facets_TSQL
- xml_schema_facets
dev_langs:
- TSQL
helpviewer_keywords:
- sys.xml_schema_facets catalog view
ms.assetid: 4402dde9-1877-4872-8550-140dc2a177d2
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4faca09a59029aeb2f2499b4236e24ea946823e3
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sysxmlschemafacets-transact-sql"></a>sys.xml_schema_facets (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Xml 型定義のファセット (制約) ごとに 1 行を返します (に対応する**sys.xml_types**)。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**xml_component_id**|**int**|ファセットが属する XML コンポーネント (型) の ID。|  
|**facet_id**|**int**|ファセットの ID (1 から始まる序数)。コンポーネント ID 内で一意です。|  
|**kind**|**char(2)**|ファセットの種類。<br /><br /> LG = 長さ<br /><br /> LN = 最小の長さ<br /><br /> LX = 最大の長さ<br /><br /> PT = パターン (正規表現)<br /><br /> EU = 列挙<br /><br /> IN = 最小の包含値<br /><br /> IX = 最大の包含値<br /><br /> EN = 最小の排他値<br /><br /> EX = 最大の排他値<br /><br /> DT = 総桁数<br /><br /> DF = 小数点以下桁数<br /><br /> WS = 空白の正規化|  
|**kind_desc**|**nvarchar (60)**|ファセットの種類の説明。<br /><br /> [LENGTH]<br /><br /> MINIMUM_LENGTH<br /><br /> MAXIMUM_LENGTH<br /><br /> PATTERN<br /><br /> ENUMERATION<br /><br /> MINIMUM_INCLUSIVE_VALUE<br /><br /> MAXIMUM_INCLUSIVE_VALUE<br /><br /> MINIMUM_EXCLUSIVE_VALUE<br /><br /> MAXIMUM_EXCLUSIVE_VALUE<br /><br /> TOTAL_DIGITS<br /><br /> FRACTION_DIGITS<br /><br /> WHITESPACE_NORMALIZATION|  
|**is_fixed**|**bit**|1 = ファセットには事前に指定された固定値があります。<br /><br /> 0 = 固定値はありません  (既定値)。|  
|**value**|**nvarchar (4000)**|事前に指定されたファセットの固定値。|  
  
## <a name="permissions"></a>権限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [XML スキーマと #40 です。XML 型システム &#41;カタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)  
  
  
