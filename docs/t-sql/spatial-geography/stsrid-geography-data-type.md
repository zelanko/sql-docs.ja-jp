---
title: "STSrid (geography データ型) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STSrid (geography Data Type)
- STSrid_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STSrid method
ms.assetid: 6b04f5a7-2e69-4d34-901e-b61ba6ca9c14
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c93ccfc28eb3dfe3b24a817394bf3481a86e89d3
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="stsrid-geography-data-type"></a>STSrid (geography データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  **STSrid**インスタンスの spatial reference identifier (SRID) を表す整数します。  
  
## <a name="syntax"></a>構文  
  
```  
  
.STSrid  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型: **int**  
  
 CLR 型: **SqlInt32**  
  
## <a name="remarks"></a>解説  
 このプロパティは変更できます。  
  
## <a name="examples"></a>使用例  
 最初の例では、作成、`geography`使用してインスタンスの SRID 値 4326 (WGS84) `STSrid` SRID を確認します。  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STSrid;  
```  
  
 2 番目の例では使用`STSrid`にインスタンスの SRID 値を 4267 (NAD27) に変更し、変更された SRID 値を確認します。  
  
```  
SET @g.STSrid = 4267;  
SELECT @g.STSrid;  
```  
  
## <a name="see-also"></a>参照  
 [Geography インスタンスの OGC メソッド](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)   
 [空間参照識別子 & #40 です。Srid &#41;](../../relational-databases/spatial/spatial-reference-identifiers-srids.md)  
  
  

