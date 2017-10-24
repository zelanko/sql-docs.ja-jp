---
title: "STUnion (geography データ型) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STUnion (geography Data Type)
- STUnion_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STUnion method
ms.assetid: 9bf87691-efd8-4c53-bd2f-eefe0acd19ca
caps.latest.revision: 23
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5e200f81a17e9b512986795077fe487e54a489f2
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="stunion-geography-data-type"></a>STUnion (geography データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  和集合を表すオブジェクトを返します、 **geography**インスタンスと別**geography**インスタンス。  
  
## <a name="syntax"></a>構文  
  
```  
  
.STUnion ( other_geography )  
```  
  
## <a name="arguments"></a>引数  
 *other_geography*  
 もう 1 つ**geography**インスタンス STUnion() が呼び出されて、インスタンスとの和集合を形成します。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す: **geography**  
  
 CLR の戻り値の型: **SqlGeography**  
  
## <a name="exceptions"></a>例外  
 このメソッドは、 **ArgumentException**場合は、インスタンスに対蹠が含まれています。  
  
## <a name="remarks"></a>解説  
 このメソッドは、場合常に null を返しますの spatial reference identifier (Srid)、 **geography**インスタンスが一致しません。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]半球より大きい空間インスタンスをサポートしています。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、サーバー上で返される結果セットが拡張されて**FullGlobe**インスタンス。  
  
 結果に円弧が含まれるのは、入力インスタンスに円弧が含まれる場合のみです。  
  
 このメソッドは正確ではありません。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-computing-the-union-of-two-polygons"></a>A. 2 つの多角形の和集合を計算する  
 次の例で`STUnion()`2 つの和集合を計算する`Polygon`インスタンス。  
  
```  
DECLARE @g geography;  
DECLARE @h geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326);  
SET @h = geography::STGeomFromText('POLYGON((-122.351 47.656, -122.341 47.656, -122.341 47.661, -122.351 47.661, -122.351 47.656))', 4326);  
SELECT @g.STUnion(@h).ToString();  
```  
  
### <a name="b-producing-a-fullglobe-result"></a>B. FullGlobe の結果を生成する  
 `FullGlobe` で 2 つの `STUnion()` インスタンスを結合するときに、`Polygon` を生成する例を次に示します。  
  
```
 DECLARE @g geography = 'POLYGON ((-122.358 47.653, -122.358 47.658,-122.348 47.658, -122.348 47.649, -122.358 47.653))';  
 DECLARE @h geography = 'POLYGON ((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))';  
 SELECT @g.STUnion(@h).ToString();
 ```  
  
### <a name="c-producing-a-triagonal-hole-from-a-union-of-a-curvepolygon-and-a-traigonal-hole"></a>C. CurvePolygon と Polygon の和集合から三角形の穴を生成する  
 次の例の和集合から三角形の穴を生成する、`CurvePolygon`で、`Polygon`インスタンス。  
  
```
 DECLARE @g geography = 'POLYGON ((-0.5 0, 0 1, 0.5 0.5, -0.5 0))';  
 DECLARE @h geography = 'CURVEPOLYGON(COMPOUNDCURVE(CIRCULARSTRING(0 0, 0.7 0.7, 0 1), (0 1, 0 0)))';  
 SELECT @g.STUnion(@h).ToString();
 ```  
  
## <a name="see-also"></a>参照  
 [Geography インスタンスの OGC メソッド](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  

