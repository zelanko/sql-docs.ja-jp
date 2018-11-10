---
title: CompoundCurve | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: ae357f9b-e3e2-4cdf-af02-012acda2e466
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 6f109dcab6d7cf6280e15cdfb1bb2f5ad3b2f041
ms.sourcegitcommit: 87f29b23d5ab174248dab5d558830eeca2a6a0a4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2018
ms.locfileid: "51018147"
---
# <a name="compoundcurve"></a>CompoundCurve
  `CompoundCurve` は、geometry 型または geography 型の 0 個以上の連続する `CircularString` インスタンスあるいは  `LineString` インスタンスのコレクションです。  
  
> [!IMPORTANT]  
>  詳細な説明と、このリリースの新しい空間機能の例を含む、`CompoundCurve`サブタイプは、ダウンロード、ホワイト ペーパー「 [SQL Server 2012 の新しい空間機能](http://go.microsoft.com/fwlink/?LinkId=226407)します。  
  
 空の `CompoundCurve` インスタンスをインスタンス化することはできますが、`CompoundCurve` を有効にするには、次の条件を満たす必要があります。  
  
1.  1 つ以上の `CircularString` インスタンスまたは `LineString` インスタンスが含まれている。  
  
2.  `CircularString` インスタンスまたは `LineString` インスタンスのシーケンスが連続している。  
  
 場合、`CompoundCurve`複数のシーケンスを含む`CircularString`と`LineString`インスタンスの場合は、最後のインスタンスを除くすべてのインスタンスは、シーケンス内の次のインスタンスの開始エンドポイントである必要があります、終了エンドポイント。 これは、シーケンス内の前のインスタンスの終点が (4 3 7 2) である場合は、シーケンス内の次のインスタンスの始点が (4 3 7 2) になる必要があることを意味します。 点の Z (標高) 値および M (メジャー) 値も同じである必要があることに注意してください。 これら 2 つの点が異なる場合は、 `System.FormatException` がスローされます。 `CircularString` の点は、Z 値または M 値を持つ必要はありません。 前のインスタンスの終点に対して Z 値または M 値が指定されていない場合、次のインスタンスの始点には Z 値または M 値を含めることはできません。 前のシーケンスの終点が (4 3) である場合、次のシーケンスの始点は (4 3) となり、(4 3 7 2) を設定することはできません。 `CompoundCurve` インスタンスのすべての点は、Z 値をまったく持たないか、または同じ Z 値を持つ必要があります。  
  
## <a name="compoundcurve-instances"></a>CompoundCurve インスタンス  
 次の図は、有効な `CompoundCurve` 型を示しています。  
  
 ![](../../database-engine/media/f278742e-b861-4555-8b51-3d972b7602bf.png "f278742e-b861-4555-8b51-3d972b7602bf")  
  
### <a name="accepted-instances"></a>許容されるインスタンス  
 `CompoundCurve` インスタンスは、空のインスタンスであるかまたは次の条件を満たす場合に許容されます。  
  
1.  `CompoundCurve` インスタンスに含まれるすべてのインスタンスが、許容される円弧インスタンスである。 許容される円弧セグメントのインスタンスの詳細については、「 [LineString](linestring.md) 」および「 [CircularString](circularstring.md)」を参照してください。  
  
2.  `CompoundCurve` インスタンス内のすべての円弧が接続されている。 後続のそれぞれの円弧の始点が、前の円弧の終点と同じである必要があります。  
  
    > [!NOTE]  
    >  これには、Z 座標および M 座標が含まれます。 したがって、4 つの座標 (X、Y、Z、M) すべてが同じである必要があります。  
  
3.  含まれているすべてのインスタンスが、空のインスタンスではない。  
  
 次の例は、許容される `CompoundCurve` インスタンスを示しています。  
  
```  
DECLARE @g1 geometry = 'COMPOUNDCURVE EMPTY';  
DECLARE @g2 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 0, 0 1, -1 0), (-1 0, 2 0))';  
```  
  
 許容されない `CompoundCurve` インスタンスを次の例に示します。 これらのインスタンスは、`System.FormatException` をスローします。  
  
```  
DECLARE @g1 geometry = 'COMPOUNDCURVE(CIRCULARSTRING EMPTY)';  
DECLARE @g2 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 0, 0 1, -1 0), (1 0, 2 0))';  
```  
  
### <a name="valid-instances"></a>有効なインスタンス  
 `CompoundCurve` インスタンスは、次の条件を満たす場合に有効です。  
  
1.  `CompoundCurve` インスタンスが許容されている。  
  
2.  `CompoundCurve` インスタンスに含まれるすべての円弧インスタンスが、有効なインスタンスである。  
  
 次の例は、有効な `CompoundCurve` インスタンスを示しています。  
  
```  
DECLARE @g1 geometry = 'COMPOUNDCURVE EMPTY';  
DECLARE @g2 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 0, 0 1, -1 0), (-1 0, 2 0))';  
DECLARE @g3 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 1, 1 1, 1 1), (1 1, 3 5, 5 4))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid();  
  
```  
  
 `@g3` は、`CircularString` インスタンスが有効であるため、有効です。 有効性の詳細については、`CircularString`インスタンスは、「 [CircularString](circularstring.md)します。  
  
 次の例は、無効な `CompoundCurve` インスタンスを示しています。  
  
```  
DECLARE @g1 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 1, 1 1, 1 1), (1 1, 3 5, 5 4, 3 5))';  
DECLARE @g2 geometry = 'COMPOUNDCURVE((1 1, 1 1))';  
DECLARE @g3 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 1, 2 3, 1 1))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid();  
```  
  
 `@g1` は、2 番目のインスタンスが有効な LineString インスタンスではないため、無効です。 `@g2` は、`LineString` インスタンスが有効ではないため、無効です。 `@g3` は、`CircularString` インスタンスが有効ではないため、無効です。 有効なの詳細については`CircularString`と`LineString`インスタンスを参照してください[CircularString](circularstring.md)と[LineString](linestring.md)します。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-instantiating-a-geometry-instance-with-an-empty-compooundcurve"></a>A. 空の CompooundCurve を使用して geometry インスタンスをインスタンス化する  
 次の例は、空の `CompoundCurve` インスタンスを作成する方法を示しています。  
  
```tsql  
DECLARE @g geometry;  
SET @g = geometry::Parse('COMPOUNDCURVE EMPTY');  
```  
  
### <a name="b-declaring-and-instantiating-a-geometry-instance-using-a-compoundcurve-in-the-same-statement"></a>B. CompoundCurve を同じステートメント内で使用して geometry インスタンスを宣言およびインスタンス化する  
 次の例は、 `geometry` を同じステートメント内で使用して `CompoundCurve`インスタンスを宣言および初期化する方法を示しています。  
  
```tsql  
DECLARE @g geometry = 'COMPOUNDCURVE ((2 2, 0 0),CIRCULARSTRING (0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0))';  
```  
  
### <a name="c-instantiating-a-geography-instance-with-a-compoundcurve"></a>C. CompoundCurve を使用して geography インスタンスをインスタンス化する  
 次の例は、`CompoundCurve` を使用して `geography` インスタンスを宣言およびインスタンス化する方法を示しています。  
  
```tsql  
DECLARE @g geography = 'COMPOUNDCURVE(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))';  
```  
  
### <a name="d-storing-a-square-in-a-compoundcurve-instance"></a>D. CompoundCurve インスタンスに正方形を格納する  
 次の例では、2 つの異なる方法で `CompoundCurve` インスタンスを使用して、正方形を格納しています。  
  
```tsql  
DECLARE @g1 geometry, @g2 geometry;  
SET @g1 = geometry::Parse('COMPOUNDCURVE((1 1, 1 3), (1 3, 3 3),(3 3, 3 1), (3 1, 1 1))');  
SET @g2 = geometry::Parse('COMPOUNDCURVE((1 1, 1 3, 3 3, 3 1, 1 1))');  
SELECT @g1.STLength(), @g2.STLength();  
```  
  
 `@g1` と `@g2` の長さは同じです。 この例に示すように、`CompoundCurve` インスタンスは、1 つまたは複数の `LineString` インスタンスを格納できます。  
  
### <a name="e-instantiating-a-geometry-instance-using-a-compoundcurve-with-multiple-circularstrings"></a>E. 複数の CircularString を含む CompoundCurve を使用して geometry インスタンスをインスタンス化する  
 次の例は、2 つの異なる `CircularString` インスタンスを使用して `CompoundCurve`を初期化する方法を示しています。  
  
```tsql  
DECLARE @g geometry;  
SET @g = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(0 2, 2 0, 4 2), CIRCULARSTRING(4 2, 2 4, 0 2))');  
SELECT @g.STLength();  
```  
  
 この場合の出力は、4∏ と等しい 12.566370… となります。 この例の `CompoundCurve` インスタンスは、半径が 2 の円を格納します。 前のコード例のどちらの場合も、 `CompoundCurve`を使用する必要はありません。 最初の例では `LineString` インスタンスを、2 番目の例では `CircularString` インスタンスをより単純化することができました。 ただし、次の例は、 `CompoundCurve` がより優れた代替手段となるケースを示しています。  
  
### <a name="f-using-a-compoundcurve-to-store-a-semicircle"></a>F. CompoundCurve を使用して半円を格納する  
 次の例では、 `CompoundCurve` インスタンスを使用して半円を格納します。  
  
```tsql  
DECLARE @g geometry;  
SET @g = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(0 2, 2 0, 4 2), (4 2, 0 2))');  
SELECT @g.STLength();  
```  
  
### <a name="g-storing-multiple-circularstring-and-linestring-instances-in-a-compoundcurve"></a>G. CompoundCurve に複数の CircularString インスタンスおよび LineString インスタンスを格納する  
 次の例は、 `CircularString` インスタンスを使用して、複数の `LineString` インスタンスおよび `CompoundCurve`インスタンスを格納する方法を示しています。  
  
```tsql  
DECLARE @g geometry  
SET @g = geometry::Parse('COMPOUNDCURVE((3 5, 3 3), CIRCULARSTRING(3 3, 5 1, 7 3), (7 3, 7 5), CIRCULARSTRING(7 5, 5 7, 3 5))');  
SELECT @g.STLength();  
```  
  
### <a name="h-storing-instances-with-z-and-m-values"></a>H. Z 値および M 値を持つインスタンスを格納する  
 次の例は、 `CompoundCurve` インスタンスを使用して、Z 値と M 値の両方を持つ `CircularString` インスタンスおよび `LineString` インスタンスのシーケンスを格納する方法を示しています。  
  
```tsql  
SET @g = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(7 5 4 2, 5 7 4 2, 3 5 4 2), (3 5 4 2, 8 7 4 2))');  
```  
  
### <a name="i-illustrating-why-circularstring-instances-must-be-explicitly-declared"></a>I. CircularString インスタンスを明示的に宣言する必要がある理由を示す  
 次の例は、 `CircularString` を明示的に宣言する必要がある理由を示しています。 この例では、円を `CompoundCurve` インスタンスに格納しようとしています。  
  
```tsql  
DECLARE @g1 geometry;    
DECLARE @g2 geometry;  
SET @g1 = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(0 2, 2 0, 4 2), (4 2, 2 4, 0 2))');  
SELECT 'Circle One', @g1.STLength() AS Perimeter;  -- gives an inaccurate amount  
SET @g2 = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(0 2, 2 0, 4 2), CIRCULARSTRING(4 2, 2 4, 0 2))');  
SELECT 'Circle Two', @g2.STLength() AS Perimeter;  -- now we get an accurate amount  
```  
  
 この場合の出力結果を次に示します。  
  
```  
Circle One11.940039…  
Circle Two12.566370…  
```  
  
 Circle Two の境界は約 4∏ で、これは境界の実際の値です。 ただし、Circle One の境界はきわめて不正確です。 Circle One の `CompoundCurve` インスタンスは、1 つの円弧 (ABC) と 2 つの線分 (CD、DA) を格納します。 `CompoundCurve` インスタンスは、円を定義するために 2 つの円弧 (ABC、CDA) を格納する必要があります。 `LineString` インスタンスは、2 番目の点のセット (4 2, 2 4, 0 2) を Circle One の `CompoundCurve` インスタンスに定義します。 ここで、 `CircularString` 内の `CompoundCurve`インスタンスを明示的に宣言する必要があります。  
  
## <a name="see-also"></a>参照  
 [STIsValid &#40;geometry データ型&#41;](/sql/t-sql/spatial-geometry/stisvalid-geometry-data-type)   
 [STLength &#40;geometry データ型&#41;](/sql/t-sql/spatial-geometry/stlength-geometry-data-type)   
 [STStartPoint &#40;geometry データ型&#41;](/sql/t-sql/spatial-geometry/ststartpoint-geometry-data-type)   
 [STEndpoint &#40;geometry データ型&#41;](/sql/t-sql/spatial-geometry/stendpoint-geometry-data-type)   
 [LineString](linestring.md)   
 [CircularString](circularstring.md)   
 [空間データ型の概要](spatial-data-types-overview.md)   
 [ポイント](point.md)  
  
  
