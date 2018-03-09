---
title: "sp_help_spatial_geography_index (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_help_spatial_geography_index
- sp_help_spatial_geography_index_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_spatial_geography_index procedure
ms.assetid: c9bf5675-eafc-4d71-bfdb-da963384fa0c
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 11b7354ee38138d991ab1127db8960d255a57223
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="sphelpspatialgeographyindex-transact-sql"></a>sp_help_spatial_geography_index (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  に関する名前と指定された一連のプロパティの値を返します、 **geography**空間インデックスです。 テーブル形式で結果が返されます。 インデックスのプロパティのコア セットまたはすべてのプロパティのどちらを返すかを選択できます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_help_spatial_geography_index [ @tabname =] 'tabname'   
     [ , [ @indexname = ] 'indexname' ]   
     [ , [ @verboseoutput = ] 'verboseoutput' ]   
     [ , [ @query_sample = ] 'query_sample' ]   
```  
  
## <a name="arguments"></a>引数  
 参照してください[ストアド プロシージャの引数と空間インデックスのプロパティ](../../relational-databases/system-stored-procedures/spatial-index-stored-procedures-arguments-and-properties.md)です。  
  
## <a name="properties"></a>[プロパティ]  
 参照してください[ストアド プロシージャの引数と空間インデックスのプロパティ](../../relational-databases/system-stored-procedures/spatial-index-stored-procedures-arguments-and-properties.md)です。  
  
## <a name="permissions"></a>Permissions  
 ユーザーには、プロシージャにアクセスするための PUBLIC ロールを割り当てる必要があります。 サーバーとオブジェクトに対する READ ACCESS 権限が必要です。  
  
## <a name="remarks"></a>解説  
  
## <a name="example"></a>例  
 次の例で`sp_help_spatial_geography_index`調査するために、 **geography**空間インデックス**SIndx_SpatialTable_geography_col2**テーブルで定義された**geography_col**指定されたクエリ サンプルの **@qs**です。 この例では、指定されたインデックスの主要プロパティのみを返します。  
  
```  
declare @qs geography  
        ='POLYGON((-90.0 -180, -90 180.0, 90 180.0, 90 -180, -90 -180.0))';  
exec sp_help_spatial_geography_index 'geography_col', 'SIndx_SpatialTable_geography_col2', 0, @qs;  
```  
  
 境界ボックスの**geography**インスタンスは、地球全体です。  
  
## <a name="requirements"></a>必要条件  
  
## <a name="see-also"></a>参照  
 [空間インデックス ストアド プロシージャ](http://msdn.microsoft.com/library/1be0f34e-3d5a-4a1f-9299-bd482362ec7a)   
 [sp_help_spatial_geography_index](../../relational-databases/system-stored-procedures/sp-help-spatial-geography-index-transact-sql.md)   
 [空間インデックスの概要](../../relational-databases/spatial/spatial-indexes-overview.md)   
 [空間データ &#40;SQL Server&#41;](../../relational-databases/spatial/spatial-data-sql-server.md)  
  
  
