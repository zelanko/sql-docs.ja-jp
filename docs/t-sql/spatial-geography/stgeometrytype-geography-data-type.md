---
title: STGeometryType (geography データ型) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STGeometryType (geography Data Type)
- STGeometryType_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STGeometryType method
ms.assetid: 3e169ead-a98e-44af-8d33-fd59a955cae4
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d4f721d552f40fcbb1fe2ae8daac8031c437d35c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47765380"
---
# <a name="stgeometrytype-geography-data-type"></a>STGeometryType (geography データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  **geography** インスタンスで表される Open Geospatial Consortium (OGC) の型名を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
.STGeometryType ( )  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 戻り値の型: **nvarchar(4000)**  
  
 CLR の戻り値の型: **SqlString**  
  
## <a name="remarks"></a>Remarks  
 `STGeometryType()` によって返される OGC の型名は、**Point**、**LineString**、**CircularString**、**CompoundCurve**、**Polygon**、**CurvePolygon**、**GeometryCollection**、**MultiPoint**、**MultiLineString**、**MultiPolygon** および **FullGlobe** です。  
  
## <a name="examples"></a>使用例  
 `Polygon` インスタンスを作成し、`STGeometryType()` を使用してこれが多角形であることを確認する例を次に示します。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326);  
SELECT @g.STGeometryType();  
```  
  
## <a name="see-also"></a>参照  
 [Geography インスタンスの OGC メソッド](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
