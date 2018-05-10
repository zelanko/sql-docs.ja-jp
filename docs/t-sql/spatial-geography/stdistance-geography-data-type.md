---
title: STDistance (geography データ型) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|spatial-geography
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d33ab796fc056c77844ef0555e0e5036b21451b5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="stdistance-geography-data-type"></a>STDistance (geography データ型)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  任意の **geography** インスタンスの地点と別の **geography** インスタンスの地点との最短距離を返します。  
  
> [!NOTE]  
>  `STDistance()` は、2 つの geography 型の間の最短の **LineString** を返します。 これは測地距離にほぼ一致します。 一般的な地球モデルの `STDistance()` の正確な測地距離からの偏差は 0.25% 以下です。 これにより、geodesic 型の長さと距離の間の微妙な違いに関する混乱が回避されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
.STDistance ( other_geography )  
```  
  
## <a name="arguments"></a>引数  
 *other_geography*  
 STDistance() を呼び出したインスタンスまでの距離が測定される、別の **geography** インスタンスです。 *other_geography* が空のセットの場合、STDistance() は null を返します。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 戻り値の型: **float**  
  
 CLR の戻り値の型: **SqlDouble**  
  
## <a name="remarks"></a>Remarks  
 **geography** インスタンスの SRID (spatial reference ID) が一致しない場合、STDistance() は常に null を返します。  
  
> [!NOTE]  
>  面積や距離を計算する、**geography** データ型のメソッドの結果は、メソッドで使用されるインスタンスの SRID に応じて異なります。   SRID の詳細については、「[&#40;SRIDs&#41; Spatial Reference Identifiers](../../relational-databases/spatial/spatial-reference-identifiers-srids.md)」を参照してください。  
  
## <a name="examples"></a>使用例  
 2 つの **geography** インスタンスの間の距離を計算する例を次に示します。  
  
```  
DECLARE @g geography;  
DECLARE @h geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SET @h = geography::STGeomFromText('POINT(-122.34900 47.65100)', 4326);  
SELECT @g.STDistance(@h);  
```  
  
## <a name="see-also"></a>参照  
 [Geography インスタンスの OGC メソッド](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
