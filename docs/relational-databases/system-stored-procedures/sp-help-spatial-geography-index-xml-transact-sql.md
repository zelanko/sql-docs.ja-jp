---
title: "sp_help_spatial_geography_index_xml (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_help_spatial_geography_index_xml_TSQL
- sp_help_spatial_geography_index_xml
dev_langs: TSQL
helpviewer_keywords: sp_help_spatial_geography_index_xml procedure
ms.assetid: 821d4127-3ce5-4474-8561-043404a20d81
caps.latest.revision: "14"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ffc4f49e8087189e9fd7d364d4d9ee3cc668573a
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="sphelpspatialgeographyindexxml-transact-sql"></a>sp_help_spatial_geography_index_xml (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  に関する名前と指定された一連のプロパティの値を返します、 **geography**空間インデックスです。 インデックスのプロパティのコア セットまたはすべてのプロパティのどちらを返すかを選択できます。  
  
 結果は、選択したプロパティの名前と値を表示する XML フラグメントで返されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_help_spatial_geography_index_xml [ @tabname =] 'tabname'   
     [ , [ @indexname = ] 'indexname' ]   
     [ , [ @verboseoutput = ] 'verboseoutput' ]   
     [ , [ @query_sample = ] 'query_sample' ]   
     [ ,.[ @xml_output = ] 'xml_output' ]   
```  
  
## <a name="arguments"></a>引数  
 参照してください[ストアド プロシージャの引数と空間インデックスのプロパティ](../../relational-databases/system-stored-procedures/spatial-index-stored-procedures-arguments-and-properties.md)です。  
  
## <a name="properties"></a>[プロパティ]  
 参照してください[ストアド プロシージャの引数と空間インデックスのプロパティ](../../relational-databases/system-stored-procedures/spatial-index-stored-procedures-arguments-and-properties.md)です。  
  
## <a name="permissions"></a>Permissions  
 ユーザーには、プロシージャにアクセスするための PUBLIC ロールを割り当てる必要があります。 サーバーとオブジェクトに対する READ ACCESS 権限が必要です。  
  
## <a name="remarks"></a>解説  
 NULL 値を含むプロパティは、返されるセットに含まれません。  
  
## <a name="example"></a>例  
 次の例で`sp_help_spatial_geography_index_xml`空間インデックスを調査する**SIndx_SpatialTable_geography_col2**テーブルで定義された**geography_col**で指定されたクエリ サンプルの**@qs**. この例では、選択したプロパティの名前と値を表示する XML フラグメントで、指定されたインデックスの主要プロパティを返します。  
  
 [XQuery](../../xquery/xquery-basics.md)結果セットに、特定のプロパティを返すことが実行されます。  
  
```  
declare @qs geography  
        ='POLYGON((-90.0 -180, -90 180.0, 90 180.0, 90 -180, -90 -180.0))';  
declare @x xml;  
exec sp_help_spatial_geography_index_xml 'geography_col', 'SIndx_SpatialTable_geography_col2', 0, @qs, @x output;  
select @x.value('(/Primary_Filter_Efficiency/text())[1]', 'float');  
```  
  
 ような[sp_help_spatial_geography_index](../../relational-databases/system-stored-procedures/sp-help-spatial-geography-index-transact-sql.md)、このストアド プロシージャのプロパティに簡単にプログラムによるアクセスを提供する、 **geography**空間インデックスおよび XML の結果セットをレポートします。  
  
 境界ボックスの**geography**は、地球全体です。  
  
## <a name="requirements"></a>必要条件  
  
## <a name="see-also"></a>参照  
 [空間インデックス ストアド プロシージャ](http://msdn.microsoft.com/library/1be0f34e-3d5a-4a1f-9299-bd482362ec7a)   
 [sp_help_spatial_geography_index](../../relational-databases/system-stored-procedures/sp-help-spatial-geography-index-transact-sql.md)   
 [空間インデックスの概要](../../relational-databases/spatial/spatial-indexes-overview.md)   
 [空間データ &#40;SQL Server&#41;](../../relational-databases/spatial/spatial-data-sql-server.md)   
 [XQuery の基礎](../../xquery/xquery-basics.md)   
 [XQuery 言語リファレンス](../../xquery/xquery-language-reference-sql-server.md)  
  
  
