---
title: "STCurveToLine (geometry データ型) |Microsoft ドキュメント"
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
helpviewer_keywords: STCurveToLine method (geometry)
ms.assetid: abc80b32-4152-4e10-b816-798b901e0ac5
caps.latest.revision: "19"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 59e40c95212420ed5f2dd46c46cf11eca623fd29
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="stcurvetoline-geometry-data-type"></a>STCurveToLine (geometry データ型)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

多角形近似を返します、 **geometry**の円弧セグメントを格納しているインスタンス。
  
## <a name="syntax"></a>構文  
  
```  
  
.STCurveToLine ( )  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す:**ジオメトリ**  
  
 CLR の戻り値の型: **SqlGeometry**  
  
## <a name="remarks"></a>解説  
 空白を返します**GeometryCollection**空のインスタンス**geometry**インスタンス変数、および返します**NULL**初期化されていない**geometry**変数。  
  
 メソッドを表す多角形近似によって異なります、 **geometry**メソッドを呼び出すために使用するインスタンス。  
  
-   返します、 **LineString**インスタンスの場合、 **CircularString**または**CompoundCurve**インスタンス。  
  
-   返します、**多角形**インスタンスの場合、 **CurvePolygon**インスタンス。  
  
-   コピーを返します、 **geometry**インスタンスのインスタンスでない場合、 **CircularString**、 **CompoundCurve**、または**CurvePolygon**インスタンス. たとえば、`STCurveToLine`メソッドを返します、**ポイント**インスタンスの場合、 **geometry**インスタンス化されている、**ポイント**インスタンス。  
  
 SQL/MM 仕様とは異なり、`STCurveToLine`メソッドは多角形近似の計算に z 座標値を使用しません。 メソッドは、呼び出し元に存在する任意の z 座標値を無視**geometry**インスタンス。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-an-uninitialized-geometry-variable-and-empty-instance"></a>A. 初期化されていないジオメトリ変数と空のインスタンスを使用する  
 次の例では、最初の**選択**ステートメントを使用して、初期化されていない**geometry**を呼び出すインスタンス、`STCurveToLine`メソッド、および 2 番目**選択**ステートメントは、空を使用して**geometry**インスタンス。 そのため、このメソッドが返されます**NULL**最初のステートメントに、 **GeometryCollection** 2 番目のステートメントのコレクション。  
  
```
 DECLARE @g geometry; 
 SET @g = @g.STCurveToLine(); 
 SELECT @g.STGeometryType(); 
 SET @g = geometry::Parse('LINESTRING EMPTY'); 
 SELECT @g.STGeometryType();
 ```  
  
### <a name="b-using-a-linestring-instance"></a>B. LineString インスタンスを使用する  
 **選択**ステートメントは次の例では使用して、 **LineString** STCurveToLine メソッドを呼び出すインスタンス。 そのため、このメソッドが返されます、 **LineString**インスタンス。  
  
```
 DECLARE @g geometry; 
 SET @g = geometry::Parse('LINESTRING(1 3, 5 5, 4 3, 1 3)'); 
 SET @g = @g.STCurveToLine(); 
 SELECT @g.STGeometryType();
 ```  
  
### <a name="c-using-a-circularstring-instance"></a>C. CircularString インスタンスを使用する  
 最初の**選択**ステートメントは次の例では使用して、 **CircularString** STCurveToLine メソッドを呼び出すインスタンス。 そのため、このメソッドが返されます、 **LineString**インスタンス。 これは、**選択**ステートメントも同じでは約 2 つのインスタンスの長さの比較できます。  最後に、2 つ目**選択**ステートメントの各インスタンスのポイントの数を返します。  5 ポイントのみが返されます、 **CircularString**インスタンスは 65 個のポイントに対して、 **LineString**インスタンス。  
  
```
 DECLARE @g1 geometry, @g2 geometry; 
 SET @g1 = geometry::Parse('CIRCULARSTRING(10 0, 0 10, -10 0, 0 -10, 10 0)'); 
 SET @g2 = @g1.STCurveToLine(); 
 SELECT @g1.STGeometryType() AS [G1 Type], @g2.STGeometryType() AS [G2 Type], @g1.STLength() AS [G1 Perimeter], @g2.STLength() AS [G2 Perimeter], @g2.ToString() AS [G2 Def]; 
 SELECT @g1.STNumPoints(), @g2.STNumPoints();
 ```  
  
### <a name="d-using-a-curvepolygon-instance"></a>D. CurvePolygon インスタンスを使用する  
 **選択**ステートメントは次の例では使用して、 **CurvePolygon** STCurveToLine メソッドを呼び出すインスタンス。 そのため、このメソッドが返されます、**多角形**インスタンス。  
  
```
 DECLARE @g1 geometry, @g2 geometry; 
 SET @g1 = geometry::Parse('CURVEPOLYGON(CIRCULARSTRING(10 0, 0 10, -10 0, 0 -10, 10 0))'); 
 SET @g2 = @g1.STCurveToLine(); 
 SELECT @g1.STGeometryType() AS [G1 Type], @g2.STGeometryType() AS [G2 Type];
 ```  
  
## <a name="see-also"></a>参照  
 [空間データ型の概要](../../relational-databases/spatial/spatial-data-types-overview.md)   
 [STLength &#40;geometry データ型&#41;](../../t-sql/spatial-geometry/stlength-geometry-data-type.md)   
 [STNumPoints &#40;geometry データ型&#41;](../../t-sql/spatial-geometry/stnumpoints-geometry-data-type.md)   
 [STGeometryType &#40;geometry データ型&#41;](../../t-sql/spatial-geometry/stgeometrytype-geometry-data-type.md)  
  
  

