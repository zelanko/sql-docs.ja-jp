---
title: "GeometryCollection | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-spatial"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GeometryCollection geometry サブタイプ [SQL Server]"
  - "geometry 型のサブタイプ [SQL Server]"
ms.assetid: 4445c0d9-a66b-4d7c-88e4-a66fa6f7d9fd
caps.latest.revision: 17
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 17
---
# GeometryCollection
  **GeometryCollection** は、ゼロ以上の **geometry** インスタンスまたは **geography** インスタンスからなるコレクションです。 **GeometryCollection** は空にすることができます。  
  
## GeometryCollection インスタンス  
  
### 許容されるインスタンス  
 **GeometryCollection** インスタンスが許容されるためには、空の **GeometryCollection** インスタンスであるか、**GeometryCollection** インスタンスを構成するすべてのインスタンスが許容されるインスタンスである必要があります。 次の例に、許容されるインスタンスを示します。  
  
```  
DECLARE @g1 geometry = 'GEOMETRYCOLLECTION EMPTY';  
DECLARE @g2 geometry = 'GEOMETRYCOLLECTION(LINESTRING EMPTY,POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
DECLARE @g3 geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1, 3 5),POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
```  
  
 次の例では、**GeometryCollection** インスタンス内の **LinesString** インスタンスが許容されないため、`System.FormatException` がスローされます。  
  
```  
DECLARE @g geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1), POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
```  
  
### 有効なインスタンス  
 **GeometryCollection** インスタンスを構成するすべてのインスタンスが有効である場合、**GeometryCollection** インスタンスは有効です。 次の例に、3 つの有効な **GeometryCollection** インスタンスと 1 つの無効な インスタンスを示します。  
  
```  
DECLARE @g1 geometry = 'GEOMETRYCOLLECTION EMPTY';  
DECLARE @g2 geometry = 'GEOMETRYCOLLECTION(LINESTRING EMPTY,POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
DECLARE @g3 geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1, 3 5),POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
DECLARE @g4 geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1, 3 5),POLYGON((-1 -1, 1 -5, -5 5, -5 -1, -1 -1)))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(), @g4.STIsValid();  
```  
  
 `@g4` は、**GeometryCollection** 内の **Polygon** インスタンスが有効ではないため、有効ではありません。  
  
 受け取られる有効なインスタンスについては、[Point](../../relational-databases/spatial/point.md)、[MultiPoint](../../relational-databases/spatial/multipoint.md)、[LineString](../../relational-databases/spatial/linestring.md)、[MultiLineString](../../relational-databases/spatial/multilinestring.md)、[Polygon](../../relational-databases/spatial/polygon.md)、[MultiPolygon](../../relational-databases/spatial/multipolygon.md) を参照してください。  
  
## 使用例  
 `geometry``GeometryCollection` を、`Point` インスタンスと `Polygon` インスタンスを含む SRID 1 の Z 値でインスタンス化する例を次に示します。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomCollFromText('GEOMETRYCOLLECTION(POINT(3 3 1), POLYGON((0 0 2, 1 10 3, 1 0 4, 0 0 2)))', 1);  
```  
  
## 参照  
 [空間データ &#40;SQL Server&#41;](../../relational-databases/spatial/spatial-data-sql-server.md)  
  
  