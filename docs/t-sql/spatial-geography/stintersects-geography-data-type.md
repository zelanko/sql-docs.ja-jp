---
title: "STIntersects (geography データ型) |Microsoft ドキュメント"
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
- STIntersects (geography Data Type)
- STIntersects_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STIntersects method
ms.assetid: c9db8b42-83c7-48c6-8963-fce54eb34c05
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c59aaf7950bde5bc167ed75d38d2d54e9c348387
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="stintersects-geography-data-type"></a>STIntersects (geography データ型)
[!INCLUDE[tsql-appliesto-ss2012-asdb-asdw-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-asdw-xxx-md.md)]

  場合 1 を返します、 **geography**インスタンスでは、他と交差する**geography**インスタンス。 そうでない場合は、0 を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
.STIntersects ( other_geography )  
```  
  
## <a name="arguments"></a>引数  
 *other_geography*  
 もう 1 つ**geography**対象のインスタンスと比較する`STIntersects()`が呼び出されます。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す:**ビット**  
  
 CLR の戻り値の型: **SqlBoolean**  
  
## <a name="remarks"></a>解説  
 このメソッドは常に返します**NULL**場合の spatial reference Id (Srid)、 **geography**インスタンスが一致しません。  
  
## <a name="examples"></a>使用例  
 `STIntersects()` を使用して 2 つの `geography` インスタンスが相互に交差しているかどうかを調べる例を次に示します。  
  
```  
DECLARE @g geography;  
DECLARE @h geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326);  
SET @h = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
```  
  
 `SELECT CASE @g.STIntersects(@h)`  
  
 `WHEN 1 THEN '@g intersects @h'`  
  
 `ELSE '@g does not intersect @h'`  
  
 `END;`  
  
## <a name="see-also"></a>参照  
 [Geography インスタンスの OGC メソッド](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
