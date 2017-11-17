---
title: "STBuffer (geography データ型) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
- STBuffer (geography Data Type)
- STBuffer_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STBuffer (geography Data Type)
ms.assetid: cb4deab8-642b-44d9-b3d9-85114d64021e
caps.latest.revision: 19
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2fa06f270ad653e9c8e43a5ec5456257e785670e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="stbuffer-geography-data-type"></a>STBuffer (geography データ型)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  すべての和集合を表す geography オブジェクトからの距離の地点を返します、 **geography**インスタンスは小さい値を指定します。  
  
 この geography データ型メソッドでサポート**FullGlobe**インスタンスまたは空間インスタンスは、半球より大きいをします。  
  
## <a name="syntax"></a>構文  
  
```  
  
.STBuffer ( distance )  
```  
  
## <a name="arguments"></a>引数  
 *距離*  
 型の値は、 **float** (**二重**.NET Framework の) からの距離を指定する、 **geography**バッファー計算の対象となるインスタンスです。  
  
 バッファーの最大距離は、0.999 を超えることはできません\* *π* * minorAxis \* minorAxis/#42/majoraxis (~0.999 \* 1/2 地球の円周) または全球。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す: **geography**  
  
 CLR の戻り値の型: **SqlGeography**  
  
## <a name="remarks"></a>解説  
 STBuffer() と同じ方法でバッファーを計算する[BufferWithTolerance](../../t-sql/spatial-geography/bufferwithtolerance-geography-data-type.md)を指定して、*トレランス*= abs (distance) \* .001 と*相対* = **false**です。  
  
 バッファーが負の値の境界の指定した距離内のすべての地点を削除する、 **geography**インスタンス。  
  
 `STBuffer()`返されます、 **FullGlobe**場合インスタンスなど、`STBuffer()`を返します、 **FullGlobe**インスタンス バッファーの距離が赤道から極地までの距離を超える場合。 バッファーは全球を超えることはできません。  
  
 このメソッドはスロー、 **ArgumentException**で**FullGlobe**インスタンスが、バッファーの距離が次の制限を超えています。  
  
 0.999 \* *π* * minorAxis \* minorAxis/#42/majoraxis (~0.999 \* 1/2 地球の円周の)  
  
 最大距離の制限により、バッファーを構築する際の柔軟性が最大限に高まります。  
  
 理論上と計算されたバッファー間の誤差が最大 (の許容範囲、エクステント * 1.E ~ 7) での許容範囲 = 距離\*.001 です。 エクステントの詳細については、次を参照してください。 [geography データ型メソッド リファレンス](http://msdn.microsoft.com/library/028e6137-7128-4c74-90a7-f7bdd2d79f5e)です。  
  
## <a name="examples"></a>使用例  
 次の例を作成、`LineString``geography`インスタンス。 使用して、 `STBuffer()` 1 メートル以内、インスタンスの領域を返します。  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STBuffer(1).ToString();  
```  
  
## <a name="see-also"></a>参照  
 [BufferWithTolerance (&) #40";"geography データ型"&"#41;](../../t-sql/spatial-geography/bufferwithtolerance-geography-data-type.md)   
 [Geography インスタンスの OGC メソッド](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  

