---
title: GeometryCollection | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-spatial
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- GeomCollection geometry subtype [SQL Server]
- geometry subtypes [SQL Server]
ms.assetid: 4445c0d9-a66b-4d7c-88e4-a66fa6f7d9fd
caps.latest.revision: 17
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 1a5c21c01ab776a17d3e160fee51167c426dfa0c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36173451"
---
# <a name="geometrycollection"></a>GeometryCollection
  A `GeometryCollection` 0 個以上のコレクションは、`geometry`または`geography`インスタンス。 A`GeometryCollection`空にすることができます。  
  
## <a name="geometrycollection-instances"></a>GeometryCollection インスタンス  
  
### <a name="accepted-instances"></a>許容されるインスタンス  
 `GeometryCollection` インスタンスが許容されるためには、空の `GeometryCollection` インスタンスであるか、`GeometryCollection` インスタンスを構成するすべてのインスタンスが許容されるインスタンスである必要があります。 次の例に、許容されるインスタンスを示します。  
  
```  
DECLARE @g1 geometry = 'GEOMETRYCOLLECTION EMPTY';  
DECLARE @g2 geometry = 'GEOMETRYCOLLECTION(LINESTRING EMPTY,POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
DECLARE @g3 geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1, 3 5),POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
```  
  
 次の例をスロー、`System.FormatException`ため、`LinesString`インスタンス、`GeometryCollection`インスタンスは許容されません。  
  
```  
DECLARE @g geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1), POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
```  
  
### <a name="valid-instances"></a>有効なインスタンス  
 `GeometryCollection` インスタンスを構成するすべてのインスタンスが有効である場合、`GeometryCollection` インスタンスは有効です。 次の例 3 つの有効な`GeometryCollection`インスタンスと 1 つのインスタンスは無効です。  
  
```  
DECLARE @g1 geometry = 'GEOMETRYCOLLECTION EMPTY';  
DECLARE @g2 geometry = 'GEOMETRYCOLLECTION(LINESTRING EMPTY,POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
DECLARE @g3 geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1, 3 5),POLYGON((-1 -1, -1 -5, -5 -5, -5 -1, -1 -1)))';  
DECLARE @g4 geometry = 'GEOMETRYCOLLECTION(LINESTRING(1 1, 3 5),POLYGON((-1 -1, 1 -5, -5 5, -5 -1, -1 -1)))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(), @g4.STIsValid();  
```  
  
 `@g4` は、`Polygon` 内の `GeometryCollection` インスタンスが有効ではないため、有効ではありません。  
  
 受け取られる有効なインスタンスについては、 [Point](point.md)、 [MultiPoint](multipoint.md)、 [LineString](linestring.md)、 [MultiLineString](multilinestring.md)、 [Polygon](polygon.md)、 [MultiPolygon](multipolygon.md)を参照してください。  
  
## <a name="examples"></a>使用例  
 `geometry``GeometryCollection` を、 `Point` インスタンスと `Polygon` インスタンスを含む SRID 1 の Z 値でインスタンス化する例を次に示します。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomCollFromText('GEOMETRYCOLLECTION(POINT(3 3 1), POLYGON((0 0 2, 1 10 3, 1 0 4, 0 0 2)))', 1);  
```  
  
## <a name="see-also"></a>参照  
 [空間データ &#40;SQL Server&#41;](spatial-data-sql-server.md)  
  
  