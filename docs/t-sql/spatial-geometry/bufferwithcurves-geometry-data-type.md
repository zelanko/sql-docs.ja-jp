---
title: "BufferWithCurves (geometry データ型) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords: BufferWithCurves method (geometry)
ms.assetid: 8ffaba3f-d2dd-4e57-9f41-3ced9f14b600
caps.latest.revision: "29"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d68384a06978c598754d96752cfa26449549cc93
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="bufferwithcurves-geometry-data-type"></a>BufferWithCurves (geometry データ型)
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  返します、 **geometry** 、呼び出し元からの距離の地点をすべてのセットを表すインスタンス**geometry**インスタンスは、以下に、*距離*パラメーター。  
  
## <a name="syntax"></a>構文  
  
```  
  
.BufferWithCurves ( distance )  
```  
  
## <a name="arguments"></a>引数  
 *距離*  
 **Float**からするバッファーを形成する地点最大距離を示すことができます、 **geometry**インスタンス。  
  
## <a name="return-types"></a>戻り値の型  
SQL Server 型の戻り値:**ジオメトリ**  
  
 CLR の戻り値の型: **SqlGeometry**  
  
## <a name="exceptions"></a>例外  
 次の条件がスローされます、 **ArgumentException**です。  
  
-   パラメーターがありませんメソッドに渡すなど`@g.BufferWithCurves()`  
  
-   数値以外のパラメーターがなどのメソッドに渡されました。`@g.BufferWithCurves('a')`  
  
-   **NULL**など、メソッドに渡されました。`@g.BufferWithCurves(NULL)`  
  
## <a name="remarks"></a>解説  
 次の図には、このメソッドによって返される geometry インスタンスの例を示しています。  
  
 ![BufferedCurve](../../t-sql/spatial-geometry/media/bufferedcurve.gif)
  
 次の表に、さまざまな distance 値に対して返される結果を示します。  
  
|distance 値|ディメンションの種類|返される空間の種類|  
|--------------------|---------------------|---------------------------|  
|distance < 0|0 または 1|空**GeometryCollection**インスタンス|  
|distance < 0|2 以上|A **CurvePolygon**または**GeometryCollection**バッファーが負の値を持つインスタンス。 **注:**バッファーが負の値は、空を作成することがあります**GeometryCollection**|  
|distance = 0|すべてのディメンション|呼び出し元のコピー **geometry**インスタンス|  
|distance > 0|すべてのディメンション|**CurvePolygon**または**GeometryCollection**インスタンス|  
  
> [!NOTE]  
>  *距離*は、 **float**、非常に小さい値が、計算でゼロに時と見なされます。 その場合、呼び出し元のコピー **geometry**インスタンスが返されます。 参照してください[float、real および #40 です。TRANSACT-SQL と #41 です。](../../t-sql/data-types/float-and-real-transact-sql.md).  
  
 バッファーが負の値は、ジオメトリの境界の指定した距離の地点がすべてを削除します。 次の図には、負の値のバッファーを薄い網掛けがある円の領域として示しています。 点線は元の多角形の境界を示しており、実線は結果として得られる多角形の境界を示しています。  
  
 場合、**文字列**パラメーターは、メソッドに渡されますしに変換されます、 **float**スローするか、`ArgumentException`です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-calling-bufferwithcurves-with-a-parameter-value--0-on-one-dimensional-geometry-instance"></a>A. 1 次元の geometry インスタンスに対して、パラメーターに 0 を下回る値を指定して、BufferWithCurves() を呼び出す  
 次の例は、空白を返します`GeometryCollection`インスタンス。  
  
```
 DECLARE @g geometry= 'LINESTRING(3 4, 8 11)'; 
 SELECT @g.BufferWithCurves(-1).ToString(); 
 ```
  
### <a name="b-calling-bufferwithcurves-with-a-parameter-value--0-on-a-two-dimensional-geometry-instance"></a>B. 2 次元の geometry インスタンスに対して、パラメーターに 0 を下回る値を指定して、BufferWithCurves() を呼び出す  
 次の例を返します、`CurvePolygon`バッファーが負の値を持つインスタンス。  
  
```
 DECLARE @g geometry = 'CURVEPOLYGON(COMPOUNDCURVE(CIRCULARSTRING(0 4, 4 0, 8 4), (8 4, 0 4)))'; 
 SELECT @g.BufferWithCurves(-1).ToString()
 ```  
  
### <a name="c-calling-bufferwithcurves-with-a-parameter-value--0-that-returns-an-empty-geometrycollection"></a>C. パラメーターに 0 を下回る (< 0) 値を指定して、BufferWithCurves() を呼び出し、空の GeometryCollection を返す  
 次の例は、何が発生したときに、*距離*パラメーターが-2。  
  
```
 DECLARE @g geometry = 'CURVEPOLYGON(COMPOUNDCURVE(CIRCULARSTRING(0 4, 4 0, 8 4), (8 4, 0 4)))'; 
 SELECT @g.BufferWithCurves(-2).ToString();
 ```  
  
 これは、**選択**ステートメントから返される`GEOMETRYCOLLECTION EMPTY`  
  
### <a name="d-calling-bufferwithcurves-with-a-parameter-value--0"></a>D. パラメーター値に 0 を指定して、BufferWithCurves() を呼び出す  
 次の例は、呼び出し元のコピーを返します**geometry**インスタンス。  
  
```
 DECLARE @g geometry = 'LINESTRING(3 4, 8 11)'; 
 SELECT @g.BufferWithCurves(0).ToString();
 ```  
  
### <a name="e-calling-bufferwithcurves-with-a-non-zero-parameter-value-that-is-extremely-small"></a>E. パラメーターに 0 以外の非常に小さい値を指定して、BufferWithCurves() を呼び出す  
 次の例では、呼び出し元のコピーも返されます**geometry**インスタンス。  
  
```
 DECLARE @g geometry = 'LINESTRING(3 4, 8 11)'; 
 DECLARE @distance float = 1e-20; 
 SELECT @g.BufferWithCurves(@distance).ToString();
 ```  
  
### <a name="f-calling-bufferwithcurves-with-a-parameter-value--0"></a>F. パラメーターに 0 を上回る (> 0) 値を指定して、BufferWithCurves() を呼び出す  
 次の例を返します、`CurvePolygon`インスタンス。  
  
```
 DECLARE @g geometry= 'LINESTRING(3 4, 8 11)'; 
 SELECT @g.BufferWithCurves(2).ToString();
 ```  
  
### <a name="g-passing-a-valid-string-parameter"></a>G. 有効な文字列パラメーターを渡す  
 次の例は、同じを返します`CurvePolygon`前述のインスタンスが、文字列パラメーターがメソッドに渡されます。  
  
```
 DECLARE @g geometry= 'LINESTRING(3 4, 8 11)'; 
 SELECT @g.BufferWithCurves('2').ToString();
 ```  
  
### <a name="h-passing-an-invalid-string-parameter"></a>H. 無効な文字列パラメーターを渡す  
 次の例では、エラーがスローされます。  
  
```
 DECLARE @g geometry = 'LINESTRING(3 4, 8 11)' 
 SELECT @g.BufferWithCurves('a').ToString();
 ```  
  
 前の 2 つの例では、文字列リテラルを `BufferWithCurves()` メソッドに渡しています。 最初の方の例は、文字列リテラルを数値に変換できるので機能します。 ただし、2 番目の例では、スロー、`ArgumentException`です。  
  
### <a name="i-calling-bufferwithcurves-on-multipoint-instance"></a>I. MultiPoint インスタンスに対して BufferWithCurves() を呼び出す  
 次の例では、2 つを返します`GeometryCollection`インスタンスと 1 つ`CurvePolygon`インスタンス。  
  
```
 DECLARE @g geometry = 'MULTIPOINT((1 1),(1 4))'; 
 SELECT @g.BufferWithCurves(1).ToString(); 
 SELECT @g.BufferWithCurves(1.5).ToString(); 
 SELECT @g.BufferWithCurves(1.6).ToString();
 ```  
  
 最初の 2 つ**選択**ステートメントを返します、`GeometryCollection`インスタンスため、パラメーター*距離*と同じかそれよりも少ない 1/2、2 つの間の距離が指す (1 1) と (1 4)。 3 番目**選択**ステートメントから返される、`CurvePolygon`インスタンスは、2 つのバッファー内のインスタンス (1 1) を参照するためと (1 4) が重複します。  
  
## <a name="see-also"></a>参照  
 [Geometry インスタンスの拡張メソッド](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
 
