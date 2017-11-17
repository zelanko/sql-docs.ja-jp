---
title: "STNumPoints (geography データ型) |Microsoft ドキュメント"
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
- STNumPoints (geography Data Type)
- STNumPoints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STNumPoints method
ms.assetid: 25ff7ad1-ba5f-4cfb-816a-59255ac1591d
caps.latest.revision: 21
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 803e631cb1e0250ebedd28a97afe4e20476396cf
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="stnumpoints-geography-data-type"></a>STNumPoints (geography データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  図形の各ポイントの合計数を返します、 **geography**インスタンス。  
  
## <a name="syntax"></a>構文  
  
```  
  
.STNumPoints ( )  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す: **int**  
  
 CLR の戻り値の型: **SqlInt32**  
  
## <a name="remarks"></a>解説  
 このメソッドの説明内のポイントの数、 **geography**インスタンス。 重複する地点はカウントされます。ただし、セグメント間の接続点は 1 つとしてカウントされます。 対象となるインスタンスがコレクションの場合、このメソッドは、コレクション内の地点の合計数を返します。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-retrieving-the-total-number-of-points-in-a-linestring"></a>A. LineString 内の地点の合計数を取得する  
 `LineString` インスタンスを作成し、`STNumPoints()` を使用して、インスタンスの記述で使用されている地点の数を確認する例を次に示します。  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STNumPoints();  
```  
  
### <a name="b-retrieving-the-total-number-of-points-in-a-geometrycollection"></a>B. GeometryCollection 内の地点の合計数を取得する  
 次の例は、すべての要素のポイントの合計を返して、`GeometryCollection`です。  
  
```  
DECLARE @g geography = 'GEOMETRYCOLLECTION(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)  
    ,CURVEPOLYGON(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)))';  
SELECT @g.STNumPoints();  
```  
  
### <a name="c-returning-the-number-of-points-in-a-compoundcurve"></a>C. CompoundCurve 内の地点の数を返す  
 次の例では、CompoundCurve インスタンスに含まれる地点の数を返します。 STNumPoints() はセグメント間の接続点を 1 つとしてカウントするため、このクエリは 6 ではなく 5 を返します。  
  
```
 DECLARE @g geography = 'COMPOUNDCURVE(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658),( -122.348 47.658, -121.56 48.12, -122.358 47.653))'  
 SELECT @g.STNumPoints();
 ```  
  
## <a name="see-also"></a>参照  
 [Geography インスタンスの OGC メソッド](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  

