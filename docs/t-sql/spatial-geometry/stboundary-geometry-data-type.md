---
title: STBoundary (geometry データ型) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STBoundary (geometry Data Type)
- STBoundary_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STBoundary (geometry Data Type)
ms.assetid: f0551674-e6e8-4926-9038-df03f2c807d7
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 94862dc99312cb495aa8f9dceba4959c8f4fa706
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85748762"
---
# <a name="stboundary-geometry-data-type"></a>STBoundary (geometry データ型)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  **geometry** インスタンスの境界を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
.STBoundary ( )  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の戻り値の型: **geometry**  
  
 CLR 戻り値の型: **SqlGeometry**  
  
## <a name="remarks"></a>解説  
 **LineString**、**CircularString**、または **CompoundCurve** インスタンスのエンドポイントが同じである場合、`STBoundary()` は空白の **GeometryCollection** を返します。  
  
## <a name="examples"></a>例  
  
### <a name="a-using-stboundary-on-a-linestring-instance-with-different-endpoints"></a>A. エンドポイントが異なる LineString インスタンスに STBoundary() を使用する  
 次の例では、`LineString``geometry` インスタンスを作成します。 `STBoundary()` は、`LineString` の境界を返します。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 0 2, 2 0)', 0);  
SELECT @g.STBoundary().ToString();  
```  
  
### <a name="b-using-stboundary-on-a-linestring-instance-with-the-same-endpoints"></a>B. エンドポイントが同じである LineString インスタンスに STBoundary() を使用する  
 次の例では、同じエンドポイントを持つ有効な `LineString` インスタンスを作成します。 `STBoundary()` は空の `GeometryCollection` を返します。  
  
```
 DECLARE @g geometry;  
 SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 0 2, -2 2, 0 0)', 0);  
 SELECT @g.STBoundary().ToString();
 ```  
  
### <a name="c-using-stboundary-on-a-curvepolygon-instance"></a>C. CurvePolygon インスタンスに STBoundary() を使用する  
 `STBoundary()` インスタンスで `CurvePolygon` を使用する例を次に示します。 `STBoundary()` は `CircularString` インスタンスを返します。  
  
```
 DECLARE @g geometry;  
 SET @g = geometry::STGeomFromText('CURVEPOLYGON(CIRCULARSTRING(0 0, 2 2, 0 2, -2 2, 0 0))', 0);  
 SELECT @g.STBoundary().ToString();
 ```  
  
## <a name="see-also"></a>参照  
 [Geometry インスタンスの OGC メソッド](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  
