---
title: "STCrosses (geometry データ型) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STCrosses (geometry Data Type)
- STCrosses_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STCrosses (geometry Data Type)
ms.assetid: 3e3fc065-555a-4bee-8b71-e92f3dc62a4f
caps.latest.revision: 21
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1ba1dfdf31480a399fdf8c3e4768a9767ccf28f3
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="stcrosses-geometry-data-type"></a>STCrosses (geometry データ型)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

場合 1 を返します、 **geometry**インスタンスでは、他と交差する**geometry**インスタンス。 そうでない場合は、0 を返します。
  
## <a name="syntax"></a>構文  
  
```  
  
.STCrosses ( other_geometry )  
```  
  
## <a name="arguments"></a>引数  
 *other_geometry*  
 もう 1 つ**geometry**対象のインスタンスと比較するインスタンス`STCrosses()`が呼び出されます。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す:**ビット**  
  
 CLR の戻り値の型: **SqlBoolean**  
  
## <a name="remarks"></a>解説  
 2 つ**geometry**のインスタンスが交わるの両方の次の条件に該当する場合。  
  
-   2 つの交差部分**geometry**結果、ジオメトリの次元は、ソースの最大次元数よりも小さいをインスタンス化**geometry**インスタンス。  
  
-   積集合のセットが両方のソースに内部**geometry**インスタンス。  
  
 このメソッドは、場合常に null を返しますの spatial reference Id (Srid)、 **geometry**インスタンスが一致しません。  
  
## <a name="examples"></a>使用例  
 `STCrosses()` を使用して 2 つの `geometry` インスタンスが交差かどうかをテストする例を次に示します。  
  
```  
DECLARE @g geometry;  
DECLARE @h geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 2, 2 0)', 0);  
SET @h = geometry::STGeomFromText('LINESTRING(0 0, 2 2)', 0);  
SELECT @g.STCrosses(@h);  
```  
  
## <a name="see-also"></a>参照  
 [Geometry インスタンスの OGC メソッド](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  


