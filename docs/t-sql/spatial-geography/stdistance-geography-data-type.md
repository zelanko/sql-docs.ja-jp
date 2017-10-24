---
title: "STDistance (geography データ型) |Microsoft ドキュメント"
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
- STDistance_TSQL
- STDistance (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STDistance method
ms.assetid: 063d8722-e019-4d3d-8fcf-dbf5325823e7
caps.latest.revision: 22
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9f79891d789938a6f4615c0e4be9cc3ba5d361f1
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="stdistance-geography-data-type"></a>STDistance (geography データ型)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  ポイント間の最短距離を返します、 **geography**インスタンスと別のポイント**geography**インスタンス。  
  
> [!NOTE]  
>  `STDistance()`返しますが、最短**LineString** 2 つの geography 型の間です。 これは測地距離にほぼ一致します。 偏差`STDistance()`正確な測地距離からの一般的な地球モデルでは以下。 25% です。 これにより、geodesic 型の長さと距離の間の微妙な違いに関する混乱が回避されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
.STDistance ( other_geography )  
```  
  
## <a name="arguments"></a>引数  
 *other_geography*  
 もう 1 つ**geography** STDistance() が呼び出されるインスタンスの間の距離を測定する対象のインスタンス。 場合*other_geography*空は設定されている、STDistance() は null を返します。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す: **float**  
  
 CLR の戻り値の型: **SqlDouble**  
  
## <a name="remarks"></a>解説  
 STDistance() は、場合常に null を返しますの spatial reference Id (Srid)、 **geography**インスタンスが一致しません。  
  
> [!NOTE]  
>  メソッドを**geography**面積や距離を計算するデータ型は、メソッドで使用されるインスタンスの srid に応じて、異なる結果を返します。   Srid の詳細については、次を参照してください。 [Spatial Reference Id & #40 です。Srid &#41;](../../relational-databases/spatial/spatial-reference-identifiers-srids.md).  
  
## <a name="examples"></a>使用例  
 次の例は、2 つの間の距離を検索**geography**インスタンス。  
  
```  
DECLARE @g geography;  
DECLARE @h geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SET @h = geography::STGeomFromText('POINT(-122.34900 47.65100)', 4326);  
SELECT @g.STDistance(@h);  
```  
  
## <a name="see-also"></a>参照  
 [Geography インスタンスの OGC メソッド](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  

