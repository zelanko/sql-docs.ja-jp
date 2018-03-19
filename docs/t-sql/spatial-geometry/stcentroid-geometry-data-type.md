---
title: "STCentroid (geometry データ型) | Microsoft Docs"
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
- STCentroid_TSQL
- STCentroid (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STCentroid (geometry Data Type)
ms.assetid: 4dc5a004-7a53-4cce-81dd-9f5e1dd0db78
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 7b818474bff0f7f233eb3ee06ba1b2a8dfb8c567
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="stcentroid-geometry-data-type"></a>STCentroid (geometry データ型)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

1 つ以上の多角形で構成されている **geometry** インスタンスの重心を返します。
  
## <a name="syntax"></a>構文  
  
```  
  
.STCentroid ( )  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 戻り値の型: **geometry**  
  
 CLR の戻り値の型: **SqlGeometry**  
  
 Open Geospatial Consortium (OGC) の型: **Point**  
  
## <a name="remarks"></a>Remarks  
 **geometry** インスタンスが **Polygon, CurvePolygon** 型または **MultiPolygon** 型ではない場合、`STCentroid()` は NULL を返します。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-computing-the-centroid-of-a-polygon-instance"></a>A. Polygon インスタンスの重心を計算する  
 `STCentroid()` を使用して `polygon``geometry` インスタンスの重心を計算する例を次に示します。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 3 0, 3 3, 0 3, 0 0),(2 2, 2 1, 1 1, 1 2, 2 2))', 0);  
SELECT @g.STCentroid().ToString();  
```  
  
### <a name="b-computing-the-centroid-of-a-curvepolygon-instance"></a>B. CurvePolygon インスタンスの重心を計算する  
 `CurvePolygon` インスタンスの重心を計算する例を次に示します。  
  
```
 DECLARE @g geometry = 'CURVEPOLYGON(CIRCULARSTRING(0 4, 4 0, 8 4, 4 8, 0 4), CIRCULARSTRING(2 4, 4 2, 6 4, 4 6, 2 4))';  
 SELECT @g.STCentroid().ToString() AS Centroid
 ```  
  
## <a name="see-also"></a>参照  
 [Geometry インスタンスの OGC メソッド](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

