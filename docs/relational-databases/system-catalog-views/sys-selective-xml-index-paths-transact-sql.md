---
title: sys.selective_xml_index_paths (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
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
ms.assetid: 07a73d71-ec3e-4894-947a-5859ca62c606
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 997dfbb99fd4e7fa95b6eb2ebd91e50b112f90b7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sysselectivexmlindexpaths-transact-sql"></a>sys.selective_xml_index_paths (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  以降で使用できる[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]Service Pack 1 では、sys.selective_xml_index_paths の各行は、特定の選択的 xml インデックスの 1 つの上位変換されたパスを表します。  
  
 次のステートメントを使用して、テーブル T の xmlcol に対して選択的 XML インデックスを作成すると、  
  
```  
CREATE SELECTIVE XML INDEX sxi1 ON T(xmlcol)   
FOR ( path1 = '/a/b/c' AS XQUERY 'xs:string',  
      path2 = '/a/b/d' AS XQUERY 'xs:double'  
    )  
```  
  
 sys.selective_xml_index_paths に、インデックス sxi1 に対応する 2 つの新しい行ができます。  

  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|XML 列を持つテーブルの ID。|  
|**index_id**|**int**|選択的 XML インデックスの一意の ID。|  
|**path_id**|**int**|上位変換された XML パス ID。|  
|**path**|**nvarchar (4000)**|上位変換されたパス。 たとえば、"/a/b/c/d/e" です。|  
|**name**|**sysname**|パス名。|  
|**path_type**|**tinyint**|0 = XQUERY<br /><br /> 1 = SQL|  
|**path_type_desc**|**sysname**|基づく**path_type** "XQUERY"または 'SQL' の値します。|  
|**xml_component_id**|**int**|データベース内の XML スキーマ コンポーネントの一意の ID。|  
|**xquery_type_description**|**nvarchar (4000)**|指定された XSD 型の名前。|  
|**is_xquery_type_inferred**|**bit**|1 = 型が推測される。|  
|**xquery_max_length**|**smallint**|最大長 (XSD 型の文字で表される)。|  
|**is_xquery_max_length_inferred**|**bit**|1 = 最大長が推測される。|  
|**is_node**|**bit**|0 = node() ヒントが存在しない。<br /><br /> 1 = node() 最適化ヒントが適用される。|  
|**system_type_id**|**tinyint**|列のシステム型の ID。|  
|**user_type_id**|**tinyint**|列のユーザー型の ID。|  
|**max_length**|**smallint**|型の最大長 (バイト単位)。<br /><br /> -1 の場合、列のデータ型は varchar(max)、nvarchar(max)、varbinary(max)、または xml です。|  
|**有効桁数 (precision)**|**tinyint**|型が数値型の場合は、最大有効桁数。 それ以外の場合は、0。|  
|**scale**|**tinyint**|型が数値型の場合は、最大小数点以下桁数。 それ以外の場合は、0 に設定されます。|  
|**collation_name**|**sysname**|型が文字型の場合は、照合順序名。 それ以外の場合は、NULL。|  
|**is_singleton**|**bit**|0 = SINGLETON ヒントが存在しない。<br /><br /> 1 = SINGLETON 最適化ヒントが適用される。|  
  
## <a name="permissions"></a>権限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [XML スキーマ&#40;XML 型システム&#41;カタログ ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)  
  
  
