---
title: "CurveToLineWithTolerance (geometry データ型) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/03/2017
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
helpviewer_keywords: CurveToLineWithTolerance method (geometry)
ms.assetid: 96871075-1998-4cd9-86b1-3fc55577aee4
caps.latest.revision: "16"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: caa3a00f6ed962122288fa0d71a4f2d2f92bd6f7
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="curvetolinewithtolerance-geometry-data-type"></a>CurveToLineWithTolerance (geometry データ型)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

多角形近似を返します、 **geometry**の円弧セグメントを格納しているインスタンス。
  
## <a name="syntax"></a>構文  
  
```  
  
.CurveToLineWithTolerance ( tolerance, relative )  
```  
  
## <a name="arguments"></a>引数  
 *許容範囲*  
 **二重**元の円弧とその線形近似の間の最大誤差を定義する式。  
  
 *相対*  
 **Bool**偏差に相対最大値を使用するかどうかを示す式です。 relative を false (0) に設定すると、線形近似で許容される偏差に絶対最大値が設定されます。 relative を true (1) に設定すると、tolerance は tolerance パラメーターと空間オブジェクトに外接する四角形の直径の積として計算されます。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す:**ジオメトリ**  
  
 CLR の戻り値の型: **SqlGeometry**  
  
## <a name="exceptions"></a>例外  
 許容範囲を設定 < = 0 がスローされます、`ArgumentOutOfRange`例外。  
  
## <a name="remarks"></a>解説  
 このメソッドは、結果の許容誤差量を指定できます**LineString**です。  
  
 次の表には、さまざまな種類の `CurveToLineWithTolerance()` によって返されるインスタンスの種類を示しています。  
  
|呼び出し元のインスタンスの種類|返される空間の種類|  
|----------------------------|---------------------------|  
|空の geometry インスタンス|空**GeometryCollection**インスタンス|  
|**ポイント**と**MultiPoint**|**ポイント**インスタンス|  
|**MultiPoint**|**ポイント**または**MultiPoint**インスタンス|  
|**CircularString**、 **CompoundCurve**、または**LineString**|**LineString**インスタンス|  
|**MultiLineString**|**LineString**または**MultiLineString**インスタンス|  
|**CurvePolygon**と**多角形**|**多角形**インスタンス|  
|**MultiPolygon**|**多角形**または**MultiPolygon**インスタンス|  
|**GeometryCollection**円弧セグメントが含まれていないインスタンスを 1 つ持つ|含まれているインスタンス、 **GeometryCollection**返されるインスタンスの種類を決定します。|  
|**GeometryCollection** 1 つの 1 次元の円弧セグメントのインスタンスに (**CircularString**、 **CompoundCurve**)|**LineString**インスタンス|  
|**GeometryCollection** 1 つの 2 次元の円弧セグメントのインスタンスに (**CurvePolygon**)|**多角形**インスタンス|  
|**GeometryCollection**インスタンスを複数持つ 1 次元|**MultiLineString**インスタンス|  
|**GeometryCollection**で複数の 2 次元のインスタンス|**MultiPolygon**インスタンス|  
|**GeometryCollection**さまざまなディメンションの複数のインスタンス|**GeometryCollection**インスタンス|  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-different-tolerance-values-on-a-circularstring-instance"></a>A. CircularString インスタンスに対して異なる tolerance 値を使用する  
 次の例は、許容範囲の設定方法に影響を示しています、`LineString`から返されるインスタンス、`CircularString`インスタンス。  
  
```
 DECLARE @g geometry; 
 SET @g = geometry::Parse('CIRCULARSTRING(0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0)'); 
 SELECT @g.CurveToLineWithTolerance(0.1,0).STNumPoints(), @g.CurveToLineWithTolerance(0.01, 0).STNumPoints();
 ```  
  
### <a name="b-using-the-method-on-a-multilinestring-instance-containing-one-linestring"></a>B. 1 つの LineString を含む MultiLineString インスタンスに対してこのメソッドを使用する  
 次の例では、`MultiLineString` インスタンスを 1 つだけ含む `LineString` インスタンスから返される結果を示します。  
  
```
 DECLARE @g geometry; 
 SET @g = geometry::Parse('MULTILINESTRING((1 3, 4 8, 6 9))'); 
 SELECT @g.CurveToLineWithTolerance(0.1,0).ToString();
 ```  
  
### <a name="c-using-the-method-on-a-multilinestring-instance-containing-multiple-linestrings"></a>C. 複数の LineString を含む MultiLineString インスタンスに対してこのメソッドを使用する  
 次の例では、複数の `MultiLineString` インスタンスを含む `LineString` インスタンスから返される結果を示します。  
  
```
 DECLARE @g geometry; 
 SET @g = geometry::Parse('MULTILINESTRING((1 3, 4 8, 6 9),(4 4, 9 18))'); 
 SELECT @g.CurveToLineWithTolerance(0.1,0).ToString();
 ```  
  
### <a name="d-setting-relative-to-true-for-an-invoking-curvepolygon-instance"></a>D. 呼び出し元の CurvePolygon インスタンスに対して relative を true に設定する  
 次の例では、`CurvePolygon`を呼び出すインスタンス`CurveToLineWithTolerance()`で*相対*true に設定します。  
  
```
 DECLARE @g geometry = 'CURVEPOLYGON(COMPOUNDCURVE(CIRCULARSTRING(0 4, 4 0, 8 4), (8 4, 0 4)))'; 
 SELECT @g.CurveToLineWithTolerance(.5,1).ToString();
 ```  
  
### <a name="e-using-the-method-on-a-geometrycollection-instance"></a>E. GeometryCollection インスタンスに対してメソッドを使用する  
 次の例では`CurveToLineWithTolerance()`上、`GeometryCollection`を含む、2 次元`CurvePolygon`インスタンスと 1 次元`CircularString`インスタンス。 `CurveToLineWithTolerance()`線のセグメントの種類を両方の円弧型を変換しで返されます、`GeometryCollection`型です。  
  
```
 DECLARE @g geometry; 
 SET @g = geometry::Parse('GEOMETRYCOLLECTION(CURVEPOLYGON( COMPOUNDCURVE(CIRCULARSTRING(0 2, 2 0, 4 2), (4 2, 0 2))), CIRCULARSTRING(4 4, 8 6, 9 5))'); 
 SELECT @g.CurveToLineWithTolerance(0.1,0).STNumPoints(), @g.CurveToLineWithTolerance(0.1, 0).ToString();
 ```  
  
## <a name="see-also"></a>参照  
 [CurveToLineWithTolerance &#40;geography データ型&#41;](../../t-sql/spatial-geography/curvetolinewithtolerance-geography-data-type.md)   
 [STCurveToLine &#40;geometry データ型&#41;](../../t-sql/spatial-geometry/stcurvetoline-geometry-data-type.md)  
  
  

