---
title: CircularString | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- dbe-spatial
ms.topic: conceptual
ms.assetid: 9fe06b03-d98c-4337-9f89-54da98f49f9f
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4602b251d7e0674c206fe85830b0abc35d92684b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48128892"
---
# <a name="circularstring"></a>CircularString
  A `CircularString` 0 個以上の連続する円弧セグメントのコレクションです。 円弧セグメントは、2 次元平面内の 3 つの点によって定義された曲線セグメントです。最初のポイントを 3 番目のポイントと同じにすることはできません。 円弧セグメントの 3 つのポイントすべてが同一線上にある場合は、円弧セグメントが直線セグメントとして扱われます。  
  
> [!IMPORTANT]  
>  詳細な説明とで導入された新しい空間機能の例の[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]など、`CircularString`サブタイプは、ダウンロード、ホワイト ペーパー「 [SQL Server 2012 の新しい空間機能](http://go.microsoft.com/fwlink/?LinkId=226407)します。  
  
## <a name="circularstring-instances"></a>CircularString インスタンス  
 次の図は有効な表示`CircularString`インスタンス。  
  
 ![](../../database-engine/media/5ff17e34-b578-4873-9d33-79500940d0bc.png "5ff17e34-b578-4873-9d33-79500940d0bc")  
  
### <a name="accepted-instances"></a>許容されるインスタンス  
 A`CircularString`いずれかが空、または奇数ポイント、n、には n が含まれていますがある場合、インスタンスは許容 > 1。 次`CircularString`インスタンスは許容されます。  
  
```  
DECLARE @g1 geometry = 'CIRCULARSTRING EMPTY';  
DECLARE @g2 geometry = 'CIRCULARSTRING(1 1, 2 0, -1 1)';  
DECLARE @g3 geometry = 'CIRCULARSTRING(1 1, 2 0, 2 0, 2 0, 1 1)';  
```  
  
 `@g3` 示しています`CircularString`インスタンスは、受理ですが有効でない可能性があります。 次に示す CircularString インスタンスの宣言は許容されません。 この宣言は `System.FormatException`をスローします。  
  
```  
DECLARE @g geometry = 'CIRCULARSTRING(1 1, 2 0, 2 0, 1 1)';  
```  
  
### <a name="valid-instances"></a>有効なインスタンス  
 有効な`CircularString`インスタンスを空にするか、次の属性を持つ必要があります。  
  
-   少なくとも 1 つの円弧のセグメントが含まれている (つまり、最低限 3 つのポイントがある)。  
  
-   最後のセグメントを除き、シーケンス内の各円弧セグメントの最後エンドポイントが、シーケンス内の次のセグメントの最初のエンドポイントになっている。  
  
-   ポイントの数が奇数である。  
  
-   このインスタンス自体を間隔に重ねることはできない。  
  
-   ただし`CircularString`インスタンスは直線セグメントを含めることができます、次の 3 つ同一線上のポイントでこれらの線分を定義する必要があります。  
  
 次の例は有効な`CircularString`インスタンス。  
  
```  
DECLARE @g1 geometry = 'CIRCULARSTRING EMPTY';  
DECLARE @g2 geometry = 'CIRCULARSTRING(1 1, 2 0, -1 1)';  
DECLARE @g3 geometry = 'CIRCULARSTRING(1 1, 2 0, 2 0, 1 1, 0 1)';  
DECLARE @g4 geometry = 'CIRCULARSTRING(1 1, 2 2, 2 2)';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(),@g4.STIsValid();  
```  
  
 `CircularString` インスタンスでは、完全な円を定義するためには、少なくとも 2 つの円弧セグメントを含める必要があります。 A`CircularString`インスタンスが 1 つの円弧セグメントを使用できません (など、(1 1, 3 1, 1 1))、完全な円を定義します。 (1 1, 2 2, 3 1, 2 0, 1 1) を使用して円を定義してください。  
  
 次の例は、無効な CircularString インスタンスを示しています。  
  
```  
DECLARE @g1 geometry = 'CIRCULARSTRING(1 1, 2 0, 1 1)';  
DECLARE @g2 geometry = 'CIRCULARSTRING(0 0, 0 0, 0 0)';  
SELECT @g1.STIsValid(), @g2.STIsValid();  
```  
  
### <a name="instances-with-collinear-points"></a>同一線上のポイントを持つインスタンス  
 次の場合、円弧セグメントは直線セグメントとして扱われます。  
  
-   3 つのすべてのポイントが同一直線上にある場合 (例: (1 3, 4 4, 7 5))。  
  
-   最初のポイントと中間のポイントは同一だが、3 番目のポイントが異なる場合 (例: (1 3, 1 3, 7 5))。  
  
-   中間のポイントと最後のポイントは同一だが、最初のポイントが異なる場合 (例: (1 3, 4 4, 4 4))。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-instantiating-a-geometry-instance-with-an-empty-circularstring"></a>A. 空の CircularString を使用して geometry インスタンスをインスタンス化する  
 次の例は、空の `CircularString` インスタンスを作成する方法を示しています。  
  
```tsql  
DECLARE @g geometry;  
SET @g = geometry::Parse('CIRCULARSTRING EMPTY');  
```  
  
### <a name="b-instantiating-a-geometry-instance-using-a-circularstring-with-one-circular-arc-segment"></a>B. 1 つの CircularString を含む CircularString を使用して geometry インスタンスをインスタンス化する  
 次の例は、1 つの円弧のセグメント (半円) を持つ `CircularString`インスタンスを作成する方法を示しています。  
  
```tsql  
DECLARE @g geometry;  
SET @g = geometry:: STGeomFromText('CIRCULARSTRING(2 0, 1 1, 0 0)', 0);  
SELECT @g.ToString();  
```  
  
### <a name="c-instantiating-a-geometry-instance-using-a-circularstring-with-multiple-circular-arc-segments"></a>C. 複数の円弧セグメントを含む CircularString を使用して geometry インスタンスをインスタンス化する  
 次の例を作成する方法を示しています、`CircularString`インスタンスは、複数の円弧のセグメント (完全な円)。  
  
```tsql  
DECLARE @g geometry;  
SET @g = geometry::Parse('CIRCULARSTRING(2 1, 1 2, 0 1, 1 0, 2 1)');  
SELECT 'Circumference = ' + CAST(@g.STLength() AS NVARCHAR(10));    
```  
  
 結果は、次のようになります。  
  
```  
Circumference = 6.28319  
```  
  
 `LineString` の代わりに `CircularString` が使用される場合は出力結果を比較してください。  
  
```tsql  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(2 1, 1 2, 0 1, 1 0, 2 1)', 0);  
SELECT 'Perimeter = ' + CAST(@g.STLength() AS NVARCHAR(10));  
```  
  
 結果は、次のようになります。  
  
```  
Perimeter = 5.65685  
```  
  
 注意の値、`CircularString`例がある 2 ∏、円の実際の円周の近くにあります。  
  
### <a name="d-declaring-and-instantiating-a-geometry-instance-with-a-circularstring-in-the-same-statement"></a>D. CircularString を同じステートメント内で使用して geometry インスタンスを宣言およびインスタンス化する  
 このコード スニペットは、`geometry` を同じステートメント内で使用して `CircularString` インスタンスを宣言およびインスタンス化する方法を示しています。  
  
```tsql  
DECLARE @g geometry = 'CIRCULARSTRING(0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0)';  
```  
  
### <a name="e-instantiating-a-geography-instance-with-a-circularstring"></a>E. CircularString を使用して geometry インスタンスをインスタンス化する  
 次の例は、`geography` を使用して `CircularString` インスタンスを宣言およびインスタンス化する方法を示しています。  
  
```tsql  
DECLARE @g geography = 'CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';  
```  
  
### <a name="f-instantiating-a-geometry-instance-with-a-circularstring-that-is-a-straight-line"></a>F. 直線の CircularString を使用して geometry インスタンスをインスタンス化する  
 次の例は、直線の `CircularString` インスタンスを作成する方法を示しています。  
  
```tsql  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('CIRCULARSTRING(0 0, 1 2, 2 4)', 0);  
```  
  
## <a name="see-also"></a>参照  
 [空間データ型の概要](spatial-data-types-overview.md)   
 [CompoundCurve](compoundcurve.md)   
 [MakeValid &#40;geography データ型&#41;](/sql/t-sql/spatial-geography/makevalid-geography-data-type)   
 [MakeValid &#40;geometry データ型&#41;](/sql/t-sql/spatial-geometry/makevalid-geometry-data-type)   
 [STIsValid &#40;geometry データ型&#41;](/sql/t-sql/spatial-geometry/stisvalid-geometry-data-type)   
 [STIsValid &#40;geography データ型&#41;](/sql/t-sql/spatial-geography/stisvalid-geography-data-type)   
 [STLength &#40;geometry データ型&#41;](/sql/t-sql/spatial-geometry/stlength-geometry-data-type)   
 [STStartPoint &#40;geometry データ型&#41;](/sql/t-sql/spatial-geometry/ststartpoint-geometry-data-type)   
 [STEndpoint &#40;geometry データ型&#41;](/sql/t-sql/spatial-geometry/stendpoint-geometry-data-type)   
 [STPointN &#40;geometry データ型&#41;](/sql/t-sql/spatial-geometry/stpointn-geometry-data-type)   
 [STNumPoints &#40;geometry データ型&#41;](/sql/t-sql/spatial-geometry/stnumpoints-geometry-data-type)   
 [STIsRing &#40;geometry データ型&#41;](/sql/t-sql/spatial-geometry/stisring-geometry-data-type)   
 [STIsClosed &#40;geometry データ型&#41;](/sql/t-sql/spatial-geometry/stisclosed-geometry-data-type)   
 [STPointOnSurface &#40;geometry データ型&#41;](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type)   
 [CircularString](linestring.md)  
  
  
