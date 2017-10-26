---
title: "BufferWithCurves (geography データ型) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/11/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- BufferWithCurves
- BufferWithCurves_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- BufferWithCurves method (geography)
ms.assetid: abf0a11c-c99c-4faa-bf80-3ae8e04d7bfb
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 80f16777999a029e1063305a0d1b8501af7e05d7
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="bufferwithcurves-geography-data-type"></a>BufferWithCurves (geography データ型)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  返します、 **geography** 、呼び出し元からの距離の地点をすべてのセットを表すインスタンス**geography**インスタンスは、以下に、*距離*パラメーター。  
  
## <a name="syntax"></a>構文  
  
```  
  
.BufferWithCurves ( distance )  
```  
  
## <a name="arguments"></a>引数  
 *距離*  
 **Float** geography インスタンスからするバッファーを形成する地点最大距離を示すことができます。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す: **geography**  
  
 CLR の戻り値の型: **SqlGeography**  
  
## <a name="exceptions"></a>例外  
 次の条件がスローされます、 **ArgumentException**です。  
  
-   パラメーター (`@g.BufferWithCurves()` など) がこのメソッドに渡されない。  
  
-   数値以外のパラメーターがなどのメソッドに渡されました。`@g.BufferWithCurves('a')`  
  
-   **NULL**など、メソッドに渡されました。`@g.BufferWithCurves(NULL)`  
  
## <a name="remarks"></a>解説  
 次の表に、さまざまな distance 値に対して返される結果を示します。  
  
|distance 値|ディメンションの種類|返される空間の種類|  
|--------------------|---------------------|---------------------------|  
|distance < 0|0 または 1|空**GeometryCollection**インスタンス|  
|距離\<0|2 以上|A **CurvePolygon**または**GeometryCollection**バッファーが負の値を持つインスタンス。<br /><br /> 注: バッファーが負の値は、空を作成できます**GeometryCollection**|
|distance = 0|すべてのディメンション|呼び出し元のコピー **geography**インスタンス|  
|distance > 0|すべてのディメンション|**CurvePolygon**または**GeometryCollection**インスタンス|  
  
> [!NOTE]  
>  *距離*は、 **float**、非常に小さい値が、計算でゼロに時と見なされます。  これが発生すると、呼び出し元のコピー **geography**インスタンスが返されます。  
  
 場合、**文字列**パラメーターは、メソッドに渡されますしに変換されます、 **float**スローするか、`ArgumentException`です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-calling-bufferwithcurves-with-a-parameter-value--0-on-one-dimensional-geography-instance"></a>A. 1 次元の geography インスタンスに対して、パラメーターに 0 を下回る (< 0) 値を指定して、BufferWithCurves() を呼び出す  
 次の例は、空白を返します`GeometryCollection`インスタンス。  
  
 ```sql
 DECLARE @g geography= 'LINESTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';  
 SELECT @g.BufferWithCurves(-1).ToString();
``` 
  
### <a name="b-calling-bufferwithcurves-with-a-parameter-value--0-on-a-two-dimensional-geography-instance"></a>B. 2 次元の geography インスタンスに対して、パラメーターに 0 を下回る (< 0) 値を指定して、BufferWithCurves() を呼び出す  
 次の例を返します、`CurvePolygon`バッファーが負の値を持つインスタンス。  
  
 ```sql
 DECLARE @g geography = 'CURVEPOLYGON(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))';  
 SELECT @g.BufferWithCurves(-1).ToString()
 ```  
  
### <a name="c-calling-bufferwithcurves-with-a-parameter-value--0-that-returns-an-empty-geometrycollection"></a>C. パラメーターに 0 を下回る (< 0) 値を指定して、BufferWithCurves() を呼び出し、空の GeometryCollection を返す  
 次の例は、何が発生したときに、*距離*パラメーターが-2。  
  
 ```sql
 DECLARE @g geography = 'CURVEPOLYGON(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))';  
 SELECT @g.BufferWithCurves(-2).ToString();
 ```  
  
 これは、**選択**ステートメントから返される`GEOMETRYCOLLECTION EMPTY`  
  
### <a name="d-calling-bufferwithcurves-with-a-parameter-value--0"></a>D. パラメーター値に 0 を指定して、BufferWithCurves() を呼び出す  
 次の例は、呼び出し元のコピーを返します**geography**インスタンス。  

 ```sql
 DECLARE @g geography = 'LINESTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';  
 SELECT @g.BufferWithCurves(0).ToString();
 ```  
  
### <a name="e-calling-bufferwithcurves-with-a-non-zero-parameter-value-that-is-extremely-small"></a>E. パラメーターに 0 以外の非常に小さい値を指定して、BufferWithCurves() を呼び出す  
 次の例では、呼び出し元のコピーも返されます**geography**インスタンス。  

 ```sql
 DECLARE @g geography = 'LINESTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';  
 DECLARE @distance float = 1e-20;  
 SELECT @g.BufferWithCurves(@distance).ToString();
 ```  
  
### <a name="f-calling-bufferwithcurves-with-a-parameter-value--0"></a>F. パラメーターに 0 を上回る (> 0) 値を指定して、BufferWithCurves() を呼び出す  
 次の例を返します、`CurvePolygon`インスタンス。  

 ```sql
 DECLARE @g geography= 'LINESTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';  
 SELECT @g.BufferWithCurves(2).ToString();
 ```  
### <a name="g-passing-a-valid-string-parameter"></a>G. 有効な文字列パラメーターを渡す  
 次の例は、同じを返します`CurvePolygon`前述のインスタンスが、文字列パラメーターがメソッドに渡されます。  

 ```sql
 DECLARE @g geography= 'LINESTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';  
 SELECT @g.BufferWithCurves('2').ToString();
```  
  
### <a name="h-passing-an-invalid-string-parameter"></a>H. 無効な文字列パラメーターを渡す  
 次の例では、エラーがスローされます。  

 ```sql
 DECLARE @g geography = 'LINESTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)'  
 SELECT @g.BufferWithCurves('a').ToString();
 ```  
  
 前の 2 つの例では、文字列リテラルを `BufferWithCurves()` メソッドに渡しています。 最初の方の例は、文字列リテラルを数値に変換できるので機能します。 ただし、2 番目の例では、スロー、`ArgumentException`です。  
  
## <a name="see-also"></a>参照  
 [Geography インスタンスの拡張メソッド](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [BufferWithCurves &#40;geometry データ型"&"#41;](../../t-sql/spatial-geometry/bufferwithcurves-geometry-data-type.md)  
  
  

