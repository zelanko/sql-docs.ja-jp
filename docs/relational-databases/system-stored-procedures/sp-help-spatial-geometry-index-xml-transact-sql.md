---
title: sp_help_spatial_geometry_index_xml (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_spatial_geometry_index_xml_TSQL
- sp_help_spatial_geometry_index_xml
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_spatial_geometry_index_xml procedure
ms.assetid: 9668ae6d-9ed5-418e-bb9a-9e7b66f7dd16
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: a2834652d7a14199ccc4914091a2c8c8b7a99801
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2018
ms.locfileid: "51660821"
---
# <a name="sphelpspatialgeometryindexxml-transact-sql"></a>sp_help_spatial_geometry_index_xml (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  に関する名前と指定した一連のプロパティの値を返します、 **geometry**空間インデックスです。 インデックスのプロパティのコア セットまたはすべてのプロパティのどちらを返すかを選択できます。  
  
 結果は、選択したプロパティの名前と値を表示する XML フラグメントで返されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_help_spatial_geometry_index [ @tabname =] 'tabname'   
     [ , [ @indexname = ] 'indexname' ]   
     [ , [ @verboseoutput = ]'{ 0 | 1 }]   
     [ , [ @query_sample = ] 'query_sample' ]   
     [ ,.[ @xml_output = ] 'xml_output' ]   
```  
  
## <a name="arguments"></a>引数  
 参照してください[ストアド プロシージャの引数と空間インデックスのプロパティ](../../relational-databases/system-stored-procedures/spatial-index-stored-procedures-arguments-and-properties.md)します。  
  
## <a name="properties"></a>[プロパティ]  
 参照してください[ストアド プロシージャの引数と空間インデックスのプロパティ](../../relational-databases/system-stored-procedures/spatial-index-stored-procedures-arguments-and-properties.md)します。  
  
## <a name="permissions"></a>アクセス許可  
 ユーザーのメンバーである必要があります、**パブリック**ロール。 サーバーとオブジェクトに対する READ ACCESS 権限が必要です。  
  
## <a name="remarks"></a>コメント  
 NULL 値を含むプロパティは、返される XML セットに含まれません。  
  
## <a name="example"></a>例  
 次の例では`sp_help_spatial_geometry_index_xml`空間インデックスを調査する**SIndx_SpatialTable_geometry_col2**テーブルで定義された**geometry_col**で指定されたクエリ サンプルの **@qs**. この例では、選択したプロパティの名前と値を表示する XML フラグメントで、指定されたインデックスの主要プロパティを返します。  
  
 [XQuery](../../xquery/xquery-basics.md)結果セットに、特定のプロパティを返すことが実行されます。  
  
```  
DECLARE @qs geometry  
        ='POLYGON((-90.0 -180.0, -90.0 180.0, 90.0 180.0, 90.0 -180.0, -90.0 -180.0))';  
DECLARE @x xml;  
EXEC sp_help_spatial_geometry_index_xml 'geometry_col', 'SIndx_SpatialTable_geometry_col2', 0, @qs, @x output;  
SELECT @x.value('(/Primary_Filter_Efficiency/text())[1]', 'float');  
```  
  
 ような[sp_help_spatial_geometry_index](../../relational-databases/system-stored-procedures/sp-help-spatial-geometry-index-transact-sql.md)、このストアド プロシージャが空間インデックスのプロパティに簡単にプログラムによるアクセスを提供し、セットを XML で結果を報告します。  
  
## <a name="requirements"></a>要件  
  
## <a name="see-also"></a>参照  
 [引数とプロパティの空間インデックス ストアド プロシージャ](../../relational-databases/system-stored-procedures/spatial-index-stored-procedures-arguments-and-properties.md)   
 [空間インデックス ストアド プロシージャ](https://msdn.microsoft.com/library/1be0f34e-3d5a-4a1f-9299-bd482362ec7a)   
 [sp_help_spatial_geometry_index](../../relational-databases/system-stored-procedures/sp-help-spatial-geometry-index-transact-sql.md)   
 [空間インデックスの概要](../../relational-databases/spatial/spatial-indexes-overview.md)   
 [空間データ &#40;SQL Server&#41;](../../relational-databases/spatial/spatial-data-sql-server.md)   
 [XQuery の基礎](../../xquery/xquery-basics.md)   
 [XQuery 言語リファレンス](../../xquery/xquery-language-reference-sql-server.md)  
  
  
