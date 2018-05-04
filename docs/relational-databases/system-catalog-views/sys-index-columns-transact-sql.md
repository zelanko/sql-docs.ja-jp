---
title: sys.index_columns (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.index_columns
- sys.index_columns_TSQL
- index_columns
- index_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.index_columns catalog view
ms.assetid: 211471aa-558a-475c-9b94-5913c143ed12
caps.latest.revision: 47
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 2214c79199206dd7cf0cfc398399f1bcda66b9c6
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sysindexcolumns-transact-sql"></a>sys.index_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  一部である列ごとに 1 行が含まれています、 **sys.indexes**インデックスまたは順序付けられていないテーブル (ヒープ) です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|インデックスが定義されているオブジェクトの ID。|  
|**index_id**|**int**|列が定義されているインデックスの ID です。|  
|**index_column_id**|**int**|インデックス列の ID です。 **index_column_id**内でのみ一意では**index_id**です。|  
|**column_id**|**int**|内の列の ID **object_id**です。<br /><br /> 0 = 非クラスター化インデックス内の行識別子 (RID) です。<br /><br /> **column_id**内でのみ一意では**object_id**です。|  
|**key_ordinal**|**tinyint**|一連のキー列内での 1 から始まる序数です。<br /><br /> 0 = キー列ではないか、XML インデックス、列ストア インデックス、または空間インデックスです。<br /><br /> 注: XML インデックスまたは空間インデックス キーにできません基になる列が、比較ではないため、値を並べ替えることはできないことを意味します。|  
|**partition_ordinal**|**tinyint**|一連のパーティション分割列内での 1 から始まる序数です。 クラスター化列ストア インデックスには、最大で 1 個のパーティション分割列を含めることができます。<br /><br /> 0 = パーティション分割列ではありません。|  
|**is_descending_key**|**bit**|1 = インデックス キー列に降順の並べ替え方向が設定されています。<br /><br /> 0 = インデックス キー列に昇順の並べ替え方向が設定されているか、列が列ストア インデックスまたはハッシュ インデックスの一部です。|  
|**is_included_column**|**bit**|1 = 列は、CREATE INDEX INCLUDE 句を使用してインデックスに追加された非キー列です。または、列は列ストア インデックスの一部です。<br /><br /> 0 = 列は付加列ではありません。<br /><br /> 列のクラスター化キーの一部であるために、暗黙的に追加するように表示されていない**sys.index_columns**です。<br /><br /> パーティション分割列であるために暗黙的に追加された列は、0 として返されます。|  
  
## <a name="permissions"></a>権限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」をご覧ください。  
  
## <a name="examples"></a>使用例  
 次の例では、`Production.BillOfMaterials` テーブルのすべてのインデックスおよびインデックス列を返します。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT i.name AS index_name  
    ,COL_NAME(ic.object_id,ic.column_id) AS column_name  
    ,ic.index_column_id  
    ,ic.key_ordinal  
,ic.is_included_column  
FROM sys.indexes AS i  
INNER JOIN sys.index_columns AS ic   
    ON i.object_id = ic.object_id AND i.index_id = ic.index_id  
WHERE i.object_id = OBJECT_ID('Production.BillOfMaterials');  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
  
index_name                                                 column_name        index_column_id key_ordinal is_included_column  
---------------------------------------------------------- -----------------  --------------- ----------- -------------  
AK_BillOfMaterials_ProductAssemblyID_ComponentID_StartDate ProductAssemblyID  1               1           0  
AK_BillOfMaterials_ProductAssemblyID_ComponentID_StartDate ComponentID        2               2           0  
AK_BillOfMaterials_ProductAssemblyID_ComponentID_StartDate StartDate          3               3           0  
PK_BillOfMaterials_BillOfMaterialsID                       BillOfMaterialsID  1               1           0  
IX_BillOfMaterials_UnitMeasureCode                         UnitMeasureCode    1               1           0  
  
(5 row(s) affected)  
  
```  
  
## <a name="see-also"></a>参照  
 [オブジェクト カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)   
 [sys.columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [SQL Server システム カタログに対するクエリに関してよくあるご質問](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
