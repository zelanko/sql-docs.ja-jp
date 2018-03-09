---
title: "sys.xml_indexes (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
- sys.xml_indexes_TSQL
- xml_indexes_TSQL
- sys.xml_indexes
- xml_indexes
dev_langs:
- TSQL
helpviewer_keywords:
- sys.xml_indexes catalog view
ms.assetid: 3408de72-b067-4fda-b5d5-8e856dfd9db3
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8656efb7be654a4249f36784995b6e3d904e53ac
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="sysxmlindexes-transact-sql"></a>sys.xml_indexes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  XML インデックスごとに 1 行のデータを返します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**\<継承された列 >**||列を継承[sys.indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)です。|  
|**using_xml_index_id**|**int**|NULL = プライマリ XML インデックス<br /><br /> Nonnull = セカンダリ XML インデックス<br /><br /> Nonnull は、プライマリ XML インデックスへの自己結合参照です。|  
|**secondary_type**|**char (1)**|セカンダリ インデックスの種類の説明。<br /><br /> P = PATH セカンダリ XML インデックス<br /><br /> V = VALUE セカンダリ XML インデックス<br /><br /> R = PROPERTY セカンダリ XML インデックス<br /><br /> NULL = プライマリ XML インデックス|  
|**secondary_type_desc**|**nvarchar (60)**|セカンダリ インデックスの種類の説明。<br /><br /> PATH = PATH セカンダリ XML インデックス<br /><br /> VALUE = VALUE セカンダリ XML インデックス<br /><br /> PROPERTY = PROPERTY セカンダリ XML インデックス<br /><br /> NULL = プライマリ XML インデックス|  
|**xml_index_type**|**tinyint**|インデックスの種類:<br /><br /> 0 = プライマリ XML インデックス<br /><br /> 1 = セカンダリ XML インデックス<br /><br /> 2 = 選択的な XML インデックス<br /><br /> 3 = 選択的セカンダリ XML インデックス|  
|**xml_index_type_description**|**nvarchar (60)**|インデックスの種類の説明。<br /><br /> PRIMARY_XML<br /><br /> セカンダリ XML インデックス<br /><br /> 選択的な XML インデックス<br /><br /> 選択的セカンダリ XML インデックス|  
|**path_id と**|**int**|選択的セカンダリ XML インデックスを除くすべての XML インデックスの場合は NULL です。<br /><br /> それ以外の場合は、選択的セカンダリ XML インデックスを構築する上位変換されたパスの ID です。 この値は、sys.selective_xml_index_paths システム ビューからの path_id と同じ値です。|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [オブジェクト カタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)  
  
  
