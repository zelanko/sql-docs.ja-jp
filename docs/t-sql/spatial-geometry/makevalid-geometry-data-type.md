---
title: "MakeValid (geometry データ型) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/03/2017
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
- MakeValid
- MakeValid_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MakeValid (geometry Data Type)
ms.assetid: 38673010-ab77-4ebb-9c4d-b26b79e3b7ea
caps.latest.revision: 22
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7cbb400b17584ef349609d876b2e700b8257ca4a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="makevalid-geometry-data-type"></a>MakeValid (geometry データ型)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

変換の無効な**geometry**インスタンスを**geometry**有効な Open Geospatial Consortium (OGC) 型のインスタンス。
  
## <a name="syntax"></a>構文  
  
```  
  
.MakeValid ()  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す:**ジオメトリ**  
  
 CLR の戻り値の型: **SqlGeometry**  
  
## <a name="remarks"></a>解説  
 このメソッドの型で、変更が発生する可能性があります、 **geometry**インスタンスだけでなく、ポイント、 **geometry**わずかに移動するインスタンス。  
  
## <a name="examples"></a>使用例  
 最初の例では、無効な`LineString`自体が重なるし、使用するインスタンス`STIsValid()`無効なインスタンスであることを確認します。 `STIsValid()`無効なインスタンスの場合は 0 の値を返します。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 2, 1 1, 1 0, 1 1, 2 2)', 0);  
SELECT @g.STIsValid();  
```  
  
 2 番目の例では`MakeValid()`インスタンスを有効にするため、インスタンスが実際に有効であるかをテストします。 `STIsValid()`有効なインスタンスの 1 の値を返します。  
  
```  
SET @g = @g.MakeValid();  
SELECT @g.STIsValid();  
```  
  
 最後に、このインスタンスがどのようにして有効なインスタンスに変換されたかを検証する例を示します。  
  
```  
SELECT @g.ToString();  
```  
  
 この例では、ときに、`LineString`インスタンスが選択されている、値を返す有効なと`MultiLineString`インスタンス。  
  
```  
MULTILINESTRING ((0 2, 1 1, 2 2), (1 1, 1 0))  
```  
  
 次の例では、CircularString インスタンスを Point インスタンスに変換します。  
  
```  
DECLARE @g geometry = 'CIRCULARSTRING(1 1, 1 1, 1 1)';  
SELECT @g.MakeValid().ToString();  
```  
  
## <a name="see-also"></a>参照  
 [STIsValid &#40;geometry データ型&#41;](../../t-sql/spatial-geometry/stisvalid-geometry-data-type.md)   
 [Geometry インスタンスの拡張メソッド](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  


