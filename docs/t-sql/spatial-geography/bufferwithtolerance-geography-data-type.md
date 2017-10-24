---
title: "BufferWithTolerance (geography データ型) |Microsoft ドキュメント"
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
- BufferWithTolerance_TSQL
- BufferWithTolerance
dev_langs:
- TSQL
helpviewer_keywords:
- BefferWithTolerance method
ms.assetid: f1783e6b-0f17-464f-b1c7-1c3f7d8aa042
caps.latest.revision: 20
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: feaa401cfd6e2077035d164412941392412011ae
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="bufferwithtolerance-geography-data-type"></a>BufferWithTolerance (geography データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  すべてのポイントの和集合を表すジオメトリック オブジェクトの値からの距離を返します、 **geography**インスタンスは許容範囲を指定できるように、指定した値に小さいです。  
  
 この geography データ型メソッドでサポート**FullGlobe**インスタンスまたは空間インスタンスは、半球より大きいをします。  
  
## <a name="syntax"></a>構文  
  
```  
  
.BufferWithTolerance ( distance, tolerance, relative )  
```  
  
## <a name="arguments"></a>引数  
 *距離*  
 **Float**からの距離を指定する式、 **geography**バッファー計算の対象となるインスタンスです。  
  
 バッファーの最大距離は、0.999 を超えることはできません\* *π* * minorAxis \* minorAxis/#42/majoraxis (~0.999 \* 1/2 地球の円周) または全球。  
  
 *許容範囲*  
 **Float**バッファー距離の許容範囲を指定する式。  
  
 *トレランス*値は、返された線形近似の理想的なバッファー距離の最大幅を表します。  
  
 たとえば、ある地点の理想のバッファー距離は円ですが、多角形によって近似された形状になる必要があります。 許容範囲が小さいほど、多角形の頂点の数は多くなります。つまり、計算結果の複雑性が増しますが、元の図形との差が小さくなります。  
  
 最小値は距離の 0.1% で、それより小さい許容範囲はこの最小値に切り上げられます。  
  
 *相対*  
 **ビット**を指定するかどうか、*トレランス*値が相対パスまたは絶対です。 かどうかは 'TRUE' または 1 が、許容範囲は相対値との積として計算されます、*トレランス*パラメーターと角度\*楕円の赤道半径。 'FALSE' または 0 の場合、tolerance は絶対値の場合、*トレランス*値は、返された線形近似の理想的なバッファー距離の最大幅。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す: **geography**  
  
 CLR の戻り値の型: **SqlGeography**  
  
## <a name="remarks"></a>解説  
 このメソッドはスロー、 **ArgumentException**場合、*距離*数 (NAN) ではない場合、または*距離*正または負の無限大します。  このメソッドはスローされても、 **ArgumentException**場合*トレランス*数 (NaN)、負または正か負の無限大ではありません、ゼロ (0) は、します。  
  
 `STBuffer()`返されます、 **FullGlobe**場合インスタンスなど、`STBuffer()`を返します、 **FullGlobe**バッファーの距離に赤道からの距離を超える場合、2 つの極地のインスタンス極地です。  
  
 このメソッドはスロー、 **ArgumentException**で**FullGlobe**インスタンスが、バッファーの距離が次の制限を超えています。  
  
 0.999 \* *π* * minorAxis \* minorAxis/#42/majoraxis (~0.999 \* 1/2 地球の円周の)  
  
 理論上と計算されたバッファー間の誤差が最大 (の許容範囲、エクステント\*1.E ~ 7) の値を許容範囲がここでは、*トレランス*パラメーター。 エクステントの詳細については、次を参照してください。 [geography データ型メソッド リファレンス](http://msdn.microsoft.com/library/028e6137-7128-4c74-90a7-f7bdd2d79f5e)です。  
  
 このメソッドは正確ではありません。  
  
## <a name="examples"></a>使用例  
 `Point` インスタンスを作成し、`BufferWithTolerance()` を使用して、インスタンスの周りの大まかなバッファーを取得する例を次に示します。  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POINT(-122.34900 47.65100)', 4326);  
SELECT @g.BufferWithTolerance(1, .5, 0).ToString();  
```  
  
## <a name="see-also"></a>参照  
 [STBuffer (&) #40";"geography データ型"&"#41;](../../t-sql/spatial-geography/stbuffer-geography-data-type.md)   
 [Geography インスタンスの拡張メソッド](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  

