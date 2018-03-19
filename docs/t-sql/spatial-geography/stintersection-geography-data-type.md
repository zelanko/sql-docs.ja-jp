---
title: "STIntersection (geography データ型) | Microsoft Docs"
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
- STIntersection_TSQL
- STIntersection (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STIntersection method
ms.assetid: 7e09468f-499f-4a38-ba4b-bb30b8821e3b
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d0028c4877326d6f51689101dfe4389ed2a2222a
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="stintersection-geography-data-type"></a>STIntersection (geography データ型)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  **geography** インスタンスが別の **geography** インスタンスと交差する地点を表すオブジェクトを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
.STIntersection ( other_geography )  
```  
  
## <a name="arguments"></a>引数  
 *other_geography*  
 STIntersection() を呼び出したインスタンスと比較される、別の **geography** インスタンスです。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 戻り値の型: **geography**  
  
 CLR の戻り値の型: **SqlGeography**  
  
## <a name="remarks"></a>Remarks  
 2 つの geography インスタンスが交差する地点が返されます。  
  
 **geography** インスタンスの SRID (spatial reference ID) が一致しない場合、STIntersection() は常に null を返します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、半球より大きい空間インスタンスをサポートしています。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のサーバーに返される結果セットには、**FullGlobe** インスタンスが含まれる場合があります。  
  
 結果に円弧が含まれるのは、入力インスタンスに円弧が含まれる場合のみです。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-computing-the-intersection-of-a-polygon-and-a-linestring"></a>A. Polygon と LineString が交差する地点を計算する  
 `STIntersection()` を使用して、`Polygon` と `LineString` が交差する地点を計算する例を次に示します。  
  
```  
DECLARE @g geography;  
DECLARE @h geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326);  
SET @h = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STIntersection(@h).ToString();  
```  
  
### <a name="b-computing-the-intersection-of-a-polygon-and-a-curvepolygon"></a>B. Polygon と CurvePolygon が交差する地点を計算する  
 次の例は、円弧が含まれたインスタンスを返します。  
  
```  
DECLARE @g geography;  
DECLARE @h geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326);  
SET @h = geography::STGeomFromText('CURVEPOLYGON(CIRCULARSTRING(-122.351 47.656, -122.341 47.656, -122.341 47.661, -122.351 47.661, -122.351 47.656))', 4326);  
SELECT @g.STIntersection(@h).ToString();  
```  
  
### <a name="c-computing-the-symmetric-difference-with-fullglobe"></a>C. FullGlobe を使用して、対称差を計算する  
 `FullGlobe` を使用して、`Polygon` の対称差を比較する例を次に示します。  
  
```  
DECLARE @g geography = 'POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))';  
SELECT @g.STIntersection('FULLGLOBE').ToString();  
```  
  
## <a name="see-also"></a>参照  
 [Geography インスタンスの OGC メソッド](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
