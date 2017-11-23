---
title: "CurveToLineWithTolerance (geography データ型) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CurveToLineWithTolerance_TSQL
- CurveToLineWithTolerance
dev_langs: TSQL
helpviewer_keywords: CurveToLineWithTolerance method (geography)
ms.assetid: 74369c76-2cf6-42ae-b9cc-e7a051db2767
caps.latest.revision: "11"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d27a256db89add06815ab65346216d3a9b013b5f
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="curvetolinewithtolerance-geography-data-type"></a>CurveToLineWithTolerance (geography データ型)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  多角形近似を返します、 **geography**の円弧セグメントを格納しているインスタンス。  
  
## <a name="syntax"></a>構文  
  
```  
  
.CurveToLineWithTolerance( tolerance, relative )  
```  
  
## <a name="arguments"></a>引数  
 *許容範囲*  
 **二重**元の円弧とその線形近似の間の最大誤差を定義する式。  
  
 *相対*  
 **Bool**偏差に相対最大値を使用するかどうかを示す式。 relative を false (0) に設定すると、線形近似で許容される偏差に絶対最大値が設定されます。  relative を true (1) に設定すると、tolerance は tolerance パラメーターと空間オブジェクトに外接する四角形の直径の積として計算されます。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す: **geography**  
  
 CLR の戻り値の型: **SqlGeography**  
  
## <a name="exceptions"></a>例外  
 許容範囲を設定 < = 0 がスローされます、 **ArgumentOutOfRange**例外。  
  
## <a name="remarks"></a>解説  
 この方法により、結果を指定する許容誤差量**LineString**です。  
  
 **CurveToLineWithTolerance**メソッドは、 **LineString**インスタンスの場合、 **CircularString**または**CompoundCurve**インスタンスと**多角形**インスタンスの場合、 **CurvePolygon**インスタンス。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-different-tolerance-values-on-a-circularstring-instance"></a>A. CircularString インスタンスに対して異なる tolerance 値を使用する  
 次の例は、許容範囲の設定方法に影響を示しています、`LineString`から返されるインスタンス、`CircularString`インスタンス。  
  
 ```
 DECLARE @g geography;  
 SET @g = geography::Parse('CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)');  
 SELECT @g.CurveToLineWithTolerance(0.1,0).STNumPoints(), @g.CurveToLineWithTolerance(0.01, 0).STNumPoints();
```  
  
### <a name="b-using-the-method-on-a-multilinestring-instance-containing-one-linestring"></a>B. 1 つの LineString を含む MultiLineString インスタンスに対してこのメソッドを使用する  
 次の例では、`MultiLineString` インスタンスを 1 つだけ含む `LineString` インスタンスから返される結果を示します。  
  
 ```
 DECLARE @g geography;  
 SET @g = geography::Parse('MULTILINESTRING((-122.358 47.653, -122.348 47.649))');  
 SELECT @g.CurveToLineWithTolerance(0.1,0).ToString();
 ```  
  
### <a name="c-using-the-method-on-a-multilinestring-instance-containing-multiple-linestrings"></a>C. 複数の LineString を含む MultiLineString インスタンスに対してこのメソッドを使用する  
 次の例では、複数の `MultiLineString` インスタンスを含む `LineString` インスタンスから返される結果を示します。  
  
 ```
 DECLARE @g geography;  
 SET @g = geography::Parse('MULTILINESTRING((-122.358 47.653, -122.348 47.649),(-123.358 47.653, -123.348 47.649))');  
 SELECT @g.CurveToLineWithTolerance(0.1,0).ToString();
 ```  
  
### <a name="d-setting-relative-to-true-for-an-invoking-curvepolygon-instance"></a>D. 呼び出し元の CurvePolygon インスタンスに対して relative を true に設定する  
 次の例では、`CurvePolygon`を呼び出すインスタンス`CurveToLineWithTolerance()`で*相対*true に設定します。  
  
 ```
 DECLARE @g geography = 'CURVEPOLYGON(COMPOUNDCURVE(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658), (-122.348 47.658, -122.358 47.658, -122.358 47.653)))';  
 SELECT @g.CurveToLineWithTolerance(.5,1).ToString();
 ```  
  
## <a name="see-also"></a>参照  
 [Geography インスタンスの拡張メソッド](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
