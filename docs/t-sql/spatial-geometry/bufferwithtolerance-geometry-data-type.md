---
title: "BufferWithTolerance (geometry データ型) |Microsoft ドキュメント"
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
- BufferWithTolerance_TSQL
- BufferWithTolerance
dev_langs:
- TSQL
helpviewer_keywords:
- BufferWithTolerance (geometry Data Type)
ms.assetid: 7049d37a-3e72-4e93-87a1-c96a6f0e2b99
caps.latest.revision: 31
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ffa8a350cb4531f9d4a6d1439a4dad0682189266
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="bufferwithtolerance-geometry-data-type"></a>BufferWithTolerance (geometry データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

すべてのポイントの和集合を表すジオメトリック オブジェクトの値からの距離を返します、 **geometry**インスタンスは許容範囲を指定できるように、指定した値に小さいです。
  
## <a name="syntax"></a>構文  
  
```  
  
.BufferWithTolerance ( distance, tolerance, relative )  
```  
  
## <a name="arguments"></a>引数  
 *距離*  
 **Float**からの距離を指定する式、 **geometry**バッファー計算の対象となるインスタンスです。  
  
 *許容範囲*  
 **Float**バッファー距離の許容範囲を指定する式。  
  
 *トレランス*返された線形近似の理想的なバッファー距離の最大幅を指します。  
  
 たとえば、ある地点の理想のバッファー距離は円ですが、多角形によって近似された形状になる必要があります。 許容範囲が小さいほど、多角形の頂点の数は多くなります。つまり、計算結果の複雑性が増しますが、元の図形との差が小さくなります。  
  
 *相対*  
 **ビット**を指定するかどうか、*トレランス*値が相対パスまたは絶対です。 かどうかは 'TRUE' または 1 の場合、許容範囲は相対値との積として計算されます、*トレランス*パラメーターとインスタンスの境界ボックスの直径します。 'FALSE' または 0 の場合、tolerance は絶対値の場合、*トレランス*値は、返された線形近似の理想的なバッファー距離の最大幅。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す:**ジオメトリ**  
  
 CLR の戻り値の型: **SqlGeometry**  
  
## <a name="exceptions"></a>例外  
 *トレランス*パラメーターを 0 より大きい値にする必要があります。 場合*トレランス*< = 0、`System.ArgumentOutOfRangeException`がスローされます。  
  
> [!NOTE]  
>  *トレランス*は、 **float**型、`System.Runtime.InteropServices.COMException`浮動小数点型の丸めの問題があるため、tolerance に指定された値が非常に小さい場合にスローされることができます。  
  
## <a name="remarks"></a>解説  
 ときに*距離*> 0 次のいずれか、**多角形**または**MultiPolygon**インスタンスが返されます。  
  
> [!NOTE]  
>  距離であるため、 **float**、非常に小さい値を計算でゼロと同じことができます。 これが発生すると、呼び出し元のコピー **geometry**インスタンスが返されます。 参照してください[float、real および #40 です。TRANSACT-SQL と #41 です。](../../t-sql/data-types/float-and-real-transact-sql.md).  
  
 ときに*距離*= 0 は、呼び出し元のコピー **geometry**インスタンスが返されます。  
  
 ときに*距離*< 0、  
  
-   空**GeometryCollection**インスタンスのサイズが 0 または 1 インスタンスが返されます。  
  
-   インスタンスの次元数が 2 以上のとき、負の値のバッファーが返されます。  
  
    > [!NOTE]  
    >  バッファーが負の値は、空を作成することも**GeometryCollection**インスタンス。  
  
 バッファーが負の値の境界の指定した距離内のすべての地点を削除する、 **geometry**インスタンス。  
  
 理論上と計算されたバッファー間の誤差が最大 (の許容範囲、エクステント\*1.E ~ 7) の値を許容範囲がここでは、*トレランス*パラメーター。 エクステントの詳細については、次を参照してください。 [geometry データ型メソッド リファレンス](http://msdn.microsoft.com/library/d88e632b-6b2f-4466-a15f-9fbef1a347a7)です。  
  
## <a name="examples"></a>使用例  
 `Point` インスタンスを作成し、`BufferWithTolerance()` を使用して、インスタンスの周りの大まかなバッファーを取得する例を次に示します。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POINT(3 3)', 0);  
SELECT @g.BufferWithTolerance(1, .5, 0).ToString();  
```  
  
## <a name="see-also"></a>参照  
 [STBuffer (&) #40";"geometry データ型"&"#41;](../../t-sql/spatial-geometry/stbuffer-geometry-data-type.md)   
 [Geometry インスタンスの拡張メソッド](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  


