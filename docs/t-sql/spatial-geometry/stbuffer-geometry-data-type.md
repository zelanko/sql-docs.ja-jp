---
title: "STBuffer (geometry データ型) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/03/2017
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
- STBuffer (geometry Data Type)
- STBuffer_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STBuffer (geometry Data Type)
ms.assetid: ca6bf2dc-1d38-4503-b87e-f2ea033d36ba
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ff65df2a1216a29b15a0458e9e4537c748140714
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="stbuffer-geometry-data-type"></a>STBuffer (geometry データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

すべての和集合を表すジオメトリック オブジェクトからの距離の地点を返します、 **geometry**インスタンスは小さい値を指定します。
  
## <a name="syntax"></a>構文  
  
```  
  
.STBuffer ( distance )  
```  
  
## <a name="arguments"></a>引数  
 *distance*  
 型の値は、 **float** (**二重**.NET framework) バッファー計算の対象となる geometry インスタンスからの距離を指定します。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す:**ジオメトリ**  
  
 CLR の戻り値の型: **SqlGeometry**  
  
## <a name="remarks"></a>解説  
 `STBuffer()`ようにバッファーを計算[BufferWithTolerance](../../t-sql/spatial-geometry/bufferwithtolerance-geometry-data-type.md)を指定して、*トレランス*= 距離\*.001 と*相対* =  **false**です。  
  
 ときに*距離*> 0 次のいずれか、**多角形**または**MultiPolygon**インスタンスが返されます。  
  
> [!NOTE]  
>  距離であるため、 **float**、非常に小さい値を計算でゼロと同じことができます。  これが発生すると、呼び出し元のコピー **geometry**インスタンスが返されます。  参照してください[float、real および #40 です。TRANSACT-SQL と #41 です。](../../t-sql/data-types/float-and-real-transact-sql.md)  
  
 ときに*距離*0 の場合、呼び出し元のコピーを = **geometry**インスタンスが返されます。  
  
 ときに*距離*< 0、し、  
  
-   空**GeometryCollection**インスタンスのサイズが 0 または 1 インスタンスが返されます。  
  
-   インスタンスのサイズが 2 つ以上のバッファーが負の値が返されます。  
  
    > [!NOTE]  
    >  バッファーが負の値は、空を作成することも**GeometryCollection**インスタンス。  
  
 バッファーに負の値を指定すると、geometry インスタンスの境界から、指定された距離の範囲内にある地点がすべて削除されます。  
  
 理論上と計算されたバッファー間の誤差が最大 (の許容範囲、エクステント * 1.E ~ 7) での許容範囲 = 距離\*.001 です。 エクステントの詳細については、次を参照してください。 [geometry データ型メソッド リファレンス](http://msdn.microsoft.com/library/d88e632b-6b2f-4466-a15f-9fbef1a347a7)です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-calling-stbuffer-with-parametervalue--0-on-one-dimensional-geometry-instance"></a>A. 1 次元の geometry インスタンスに対して、パラメーターに 0 を下回る (< 0) 値を指定して、STBuffer() を呼び出す  
 次の例は、空白を返します`GeometryCollection`インスタンス。  
  
```
 DECLARE @g geometry= 'LINESTRING(3 4, 8 11)'; 
 SELECT @g.STBuffer(-1).ToString();
 ```  
  
### <a name="b-calling-stbuffer-with-parametervalue--0-on-a-polygon-instance"></a>B. Polygon インスタンスに対して、パラメーターに 0 を下回る (< 0) 値を指定して、STBuffer() を呼び出す  
 次の例を返します、`Polygon`バッファーが負の値を持つインスタンス。  
  
```
 DECLARE @g geometry = 'POLYGON((1 1, 1 5, 5 5, 5 1, 1 1))'; 
 SELECT @g.STBuffer(-1).ToString();
 ```  
  
### <a name="c-calling-stbuffer-with-parametervalue--0-on-a-curvepolygon-instance"></a>C. CurvePolygon インスタンスに対して、パラメーターに 0 を下回る (< 0) 値を指定して、STBuffer() を呼び出す  
 次の例を返します、`Polygon`からバッファーが負の値を持つインスタンス、`CurvePolygon`インスタンス。  
  
```
 DECLARE @g geometry = 'CURVEPOLYGON(COMPOUNDCURVE(CIRCULARSTRING(0 4, 4 0, 8 4), (8 4, 0 4)))'; 
 SELECT @g.STBuffer(-1).ToString();
 ```  
  
> [!NOTE]  
>  A`Polygon`の代わりにインスタンスが返されます、`CurvePolygon`インスタンス。  返される、`CurvePolygon`インスタンスは、「 [BufferWithCurves (& a) #40; geometry データ型 &#41;](../../t-sql/spatial-geometry/bufferwithcurves-geometry-data-type.md)  
  
### <a name="d-calling-stbuffer-with-a-negative-parameter-value-that-returns-an-empty-instance"></a>D. 負のパラメーター値を指定して STBuffer() を呼び出し、空のインスタンスを取得する  
 次の例は、何が発生したときに、*距離*パラメーターが-2 の前の例です。  
  
```
 DECLARE @g geometry = 'CURVEPOLYGON(COMPOUNDCURVE(CIRCULARSTRING(0 4, 4 0, 8 4), (8 4, 0 4)))'; 
 SELECT @g.STBuffer(-2).ToString();
 ```  
  
 これは、**選択**ステートメントから返される、`GEOMETRYCOLLECTION EMPTY.`  
  
### <a name="e-calling-stbuffer-with-parametervalue--0"></a>E. パラメーターに 0 を指定して STBuffer() を呼び出す  
 次の例は、呼び出し元のコピーを返します`geometry`インスタンス。  
  
```
 DECLARE @g geometry = 'LINESTRING(3 4, 8 11)'; 
 SELECT @g.STBuffer(0).ToString();
 ```  
  
### <a name="f-calling-stbuffer-with-a-non-zero-parameter-value-that-is-extremely-small"></a>F. パラメーターに 0 以外の非常に小さい値を指定して、STBuffer() を呼び出す  
 次の例では、呼び出し元のコピーも返されます`geometry`インスタンス。  
  
```
 DECLARE @g geometry = 'LINESTRING(3 4, 8 11)';  
 DECLARE @distance float = 1e-20;  
 SELECT @g.STBuffer(@distance).ToString();
 ```  
  
### <a name="g-calling-stbuffer-with-parametervalue--0"></a>G. パラメーターに 0 を上回る (> 0) 値を指定して STBuffer() を呼び出す  
 次の例を返します、`Polygon`インスタンス。  
  
```
 DECLARE @g geometry= 'LINESTRING(3 4, 8 11)'; 
 SELECT @g.STBuffer(2).ToString();
 ```  
  
### <a name="h-calling-stbuffer-with-a-string-parameter-value"></a>H. 文字列のパラメーター値を指定して STBuffer() を呼び出す  
 次の例は、同じを返します`Polygon`前述のインスタンスが、文字列パラメーターがメソッドに渡されます。  
  
```
 DECLARE @g geometry= 'LINESTRING(3 4, 8 11)'; 
 SELECT @g.STBuffer('2').ToString();
 ```  
  
 次の例では、エラーがスローされます。  
  
```
 DECLARE @g geometry = 'LINESTRING(3 4, 8 11)'; 
 SELECT @g.STBuffer('a').ToString();
 ```  
  
> [!NOTE]  
>  前の 2 つの例では、リテラルの文字列が渡さ、`STBuffer()`です。  最初の方の例は、文字列リテラルを数値に変換できるので機能します。 ただし、2 番目の例では、スロー、`ArgumentException`です。  
  
### <a name="i-calling-stbuffer-on-a-multipoint-instance"></a>I. MultiPoint インスタンスに対して STBuffer() を呼び出す  
 次の例では、2 つを返します`MultiPolygon`インスタンスと 1 つ`Polygon`インスタンス。  
  
```
 DECLARE @g geometry = 'MULTIPOINT((1 1),(1 4))'; 
 SELECT @g.STBuffer(1).ToString(); 
 SELECT @g.STBuffer(1.5).ToString(); 
 SELECT @g.STBuffer(1.6).ToString();
 ```  
  
 最初の 2 つ**選択**ステートメントを返します、`MultiPolygon`インスタンスため、パラメーター*距離*と同じかそれよりも少ない 1/2、2 つの間の距離が指す (1 1) と (1 4)。 3 番目**選択**ステートメントから返される、`Polygon`インスタンスは、2 つのバッファー内のインスタンス (1 1) を参照するためと (1 4) が重複します。  
  
## <a name="see-also"></a>参照  
 [BufferWithTolerance &#40;geometry データ型&#41;](../../t-sql/spatial-geometry/bufferwithtolerance-geometry-data-type.md)   
 [Geometry インスタンスの OGC メソッド](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

