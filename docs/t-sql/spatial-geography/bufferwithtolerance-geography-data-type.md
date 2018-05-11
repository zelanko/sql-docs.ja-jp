---
title: BufferWithTolerance (geography データ型) | Microsoft Docs
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
- BufferWithTolerance_TSQL
- BufferWithTolerance
dev_langs:
- TSQL
helpviewer_keywords:
- BefferWithTolerance method
ms.assetid: f1783e6b-0f17-464f-b1c7-1c3f7d8aa042
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d0aa4291944b92dd83f2ce1d5d39704c171d8c76
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="bufferwithtolerance-geography-data-type"></a>BufferWithTolerance (geography データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  **geography** インスタンスから各地点までの距離が指定した許容範囲内にある、すべての地点値の和集合を表すジオメトリック オブジェクトを返します。  
  
 この geography データ型メソッドは、半球より大きい **FullGlobe** インスタンスまたは空間インスタンスをサポートします。  
  
## <a name="syntax"></a>構文  
  
```  
  
.BufferWithTolerance ( distance, tolerance, relative )  
```  
  
## <a name="arguments"></a>引数  
 *distance*  
 バッファー計算の対象となる **geography** インスタンスからの距離を指定する **float** 式です。  
  
 バッファーの最大距離は、0.999 \* *π* * minorAxis \* minorAxis / majorAxis (~0.999 \* 地球の円周の 1/2) で求められる値または全球を超えることはできません。  
  
 *tolerance*  
 バッファー距離の許容範囲を指定する **float** 式です。  
  
 *tolerance* とは、理想的なバッファー距離と返される線形近似との差異の最大値を指します。  
  
 たとえば、ある地点の理想のバッファー距離は円ですが、多角形によって近似された形状になる必要があります。 許容範囲が小さいほど、多角形の頂点の数は多くなります。つまり、計算結果の複雑性が増しますが、元の図形との差が小さくなります。  
  
 最小値は距離の 0.1% で、それより小さい許容範囲はこの最小値に切り上げられます。  
  
 *relative*  
 *tolerance* の値が相対値か絶対値かを指定する **bit** です。 'TRUE' または 1 の場合、許容範囲は相対値です。楕円の角度 \* と赤道半径と *tolerance* パラメーターの積として計算されます。 'FALSE' または 0 の場合、許容範囲は絶対値であり、*tolerance* 値は、返された線形近似の理想的なバッファー距離の絶対最大幅になります。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 戻り値の型: **geography**  
  
 CLR の戻り値の型: **SqlGeography**  
  
## <a name="remarks"></a>Remarks  
 *distance* が非数 (NAN) の場合、または *distance* が正か負の無限大の場合、このメソッドは **ArgumentException** をスローします。  *tolerance* が 0、非数 (NaN)、負の数値、または正か負の無限大の場合も、このメソッドは **ArgumentException** をスローします。  
  
 `STBuffer()` は、**FullGlobe** インスタンスを返すことがあります。たとえば、バッファーの距離が赤道から極地までの距離を超えている場合、`STBuffer()` は 2 つの極地の **FullGlobe** インスタンスを返します。  
  
 このメソッドは、バッファーの距離が次の制限値を超えている場合、**FullGlobe** インスタンスで **ArgumentException** をスローします。  
  
 0.999 \* *π* * minorAxis \* minorAxis / majorAxis (~0.999 \* 地球の円周の 1/2)  
  
 理論上のバッファーと計算されたバッファーの間の誤差は、max(tolerance, extents \* 1.E-7) です。tolerance は *tolerance* パラメーターの値になります。 エクステントの詳細は、「[geography データ型メソッド リファレンス](http://msdn.microsoft.com/library/028e6137-7128-4c74-90a7-f7bdd2d79f5e)」を参照してください。  
  
 このメソッドは正確ではありません。  
  
## <a name="examples"></a>使用例  
 `Point` インスタンスを作成し、`BufferWithTolerance()` を使用して、インスタンスの周りの大まかなバッファーを取得する例を次に示します。  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POINT(-122.34900 47.65100)', 4326);  
SELECT @g.BufferWithTolerance(1, .5, 0).ToString();  
```  
  
## <a name="see-also"></a>参照  
 [STBuffer &#40;geography データ型&#41;](../../t-sql/spatial-geography/stbuffer-geography-data-type.md)   
 [Geography インスタンスの拡張メソッド](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
