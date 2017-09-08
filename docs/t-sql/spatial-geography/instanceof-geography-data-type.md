---
title: "InstanceOf (geography データ型) |Microsoft ドキュメント"
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
- InstanceOf
- InstanceOf_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- InstanceOf method
ms.assetid: 1eaed0e4-1c72-45a9-9926-5b513335cf33
caps.latest.revision: 28
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0edbebbb6754fd09ff834e4ffe8d453853b6f240
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="instanceof-geography-data-type"></a>InstanceOf (geography データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  かどうか、 **geography**インスタンスが指定した型と同じです。  
  
## <a name="syntax"></a>構文  
  
```  
  
.InstanceOf ( 'geography_type')  
```  
  
## <a name="arguments"></a>引数  
 *geography_type*  
 **Nvarchar (4000)**で公開されている 16 種類のいずれかを指定する文字列、 **geography**階層を入力します。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す:**ビット**  
  
 CLR の戻り値の型: **SqlBoolean**  
  
## <a name="remarks"></a>解説  
 場合 1 を返しますの種類、 **geography**インスタンスは、指定された型と同じまたは指定した型が、インスタンスの型の先祖である場合は、0 を返しますそれ以外の場合。  
  
 これは、 **geography**データ型メソッドでサポート**FullGlobe**インスタンスまたは空間インスタンスは、半球より大きいをします。  
  
 メソッドの入力は、次のいずれかにする必要がありますジオメトリ、ポイント、曲線、LineString、CircularString、画面、Polygon、CurvePolygon、 **GeometryCollection**、 **MultiSurface**、  **。MultiPolygon、MultiCurve、MultiLineString**、 **MultiPoint**、または**FullGlobe**です。  
  
 このメソッドはスロー、`ArgumentException`と、入力の他の文字列が使用されます。  
  
 このメソッドは正確ではありません。  
  
## <a name="examples"></a>使用例  
 次の例を作成、`MultiPoint`使用して、インスタンス`InstanceOf()`かどうかをインスタンス、`GeometryCollection`です。  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('MULTIPOINT(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.InstanceOf('GEOMETRYCOLLECTION');  
```  
  
## <a name="see-also"></a>参照  
 [Geography インスタンスの拡張メソッド](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
