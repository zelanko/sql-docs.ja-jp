---
title: CircularString | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 9fe06b03-d98c-4337-9f89-54da98f49f9f
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: e14aafe004ffd94f0711161fac73ce59c57cd810
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "78176722"
---
# <a name="circularstring"></a>CircularString
  `CircularString` は、0 個以上の連続する円弧セグメントのコレクションです。 円弧セグメントは、2 次元平面内の 3 つの点によって定義された曲線セグメントです。最初のポイントを 3 番目のポイントと同じにすることはできません。 円弧セグメントの 3 つのポイントすべてが同一線上にある場合は、円弧セグメントが直線セグメントとして扱われます。

> [!IMPORTANT]
>  サブタイプを含め、で[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]導入された新しい空間機能の詳細な説明と例については、ホワイトペーパー「 [SQL Server 2012 の新しい空間機能](https://go.microsoft.com/fwlink/?LinkId=226407)」をダウンロードしてください。 `CircularString`

## <a name="circularstring-instances"></a>CircularString インスタンス
 次の図は有効な `CircularString` インスタンスを示しています。

 ![](../../database-engine/media/5ff17e34-b578-4873-9d33-79500940d0bc.png "5ff17e34-b578-4873-9d33-79500940d0bc")

### <a name="accepted-instances"></a>許容されるインスタンス
 `CircularString`インスタンスは、空であるか、または奇数 (n > 1) である場合に許容されます。 次`CircularString`のインスタンスが受け入れられます。

```sql
DECLARE @g1 geometry = 'CIRCULARSTRING EMPTY';
DECLARE @g2 geometry = 'CIRCULARSTRING(1 1, 2 0, -1 1)';
DECLARE @g3 geometry = 'CIRCULARSTRING(1 1, 2 0, 2 0, 2 0, 1 1)';
```

 `@g3` の場合、`CircularString` インスタンスは許容されることがありますが、有効ではありません。 次に示す CircularString インスタンスの宣言は許容されません。 この宣言は `System.FormatException`をスローします。

```sql
DECLARE @g geometry = 'CIRCULARSTRING(1 1, 2 0, 2 0, 1 1)';
```

### <a name="valid-instances"></a>有効なインスタンス
 有効な `CircularString` インスタンスは、空であるか、または次の属性を持つ必要があります。

-   少なくとも 1 つの円弧のセグメントが含まれている (つまり、最低限 3 つのポイントがある)。

-   最後のセグメントを除き、シーケンス内の各円弧セグメントの最後エンドポイントが、シーケンス内の次のセグメントの最初のエンドポイントになっている。

-   ポイントの数が奇数である。

-   このインスタンス自体を間隔に重ねることはできない。

-   `CircularString` が直線セグメントを含んでいてもかまわないが、これらの直線セグメントは、3 つ同一線上のポイントで定義する。

 次の例は、有効な `CircularString` インスタンスを示しています。

```sql
DECLARE @g1 geometry = 'CIRCULARSTRING EMPTY';
DECLARE @g2 geometry = 'CIRCULARSTRING(1 1, 2 0, -1 1)';
DECLARE @g3 geometry = 'CIRCULARSTRING(1 1, 2 0, 2 0, 1 1, 0 1)';
DECLARE @g4 geometry = 'CIRCULARSTRING(1 1, 2 2, 2 2)';
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(),@g4.STIsValid();
```

 `CircularString` インスタンスでは、完全な円を定義するためには、少なくとも 2 つの円弧セグメントを含める必要があります。 `CircularString` インスタンスでは、(1 1, 3 1, 1 1) など 1 つの円弧セグメントを使用して完全な円を定義することはできません。 (1 1, 2 2, 3 1, 2 0, 1 1) を使用して円を定義してください。

 次の例は、無効な CircularString インスタンスを示しています。

```sql
DECLARE @g1 geometry = 'CIRCULARSTRING(1 1, 2 0, 1 1)';
DECLARE @g2 geometry = 'CIRCULARSTRING(0 0, 0 0, 0 0)';
SELECT @g1.STIsValid(), @g2.STIsValid();
```

### <a name="instances-with-collinear-points"></a>同一線上のポイントを持つインスタンス
 次の場合、円弧セグメントは直線セグメントとして扱われます。

-   3 つのすべてのポイントが同一直線上にある場合 (例: (1 3, 4 4, 7 5))。

-   最初のポイントと中間のポイントは同一だが、3 番目のポイントが異なる場合 (例: (1 3, 1 3, 7 5))。

-   中間のポイントと最後のポイントは同一だが、最初のポイントが異なる場合 (例: (1 3, 4 4, 4 4))。

## <a name="examples"></a>例

### <a name="a-instantiating-a-geometry-instance-with-an-empty-circularstring"></a>A. 空の CircularString を使用して geometry インスタンスをインスタンス化する
 次の例は、空の `CircularString` インスタンスを作成する方法を示しています。

```sql
DECLARE @g geometry;
SET @g = geometry::Parse('CIRCULARSTRING EMPTY');
```

### <a name="b-instantiating-a-geometry-instance-using-a-circularstring-with-one-circular-arc-segment"></a>B. 1 つの CircularString を含む CircularString を使用して geometry インスタンスをインスタンス化する
 次の例は、1 つの円弧のセグメント (半円) を持つ `CircularString`インスタンスを作成する方法を示しています。

```sql
DECLARE @g geometry;
SET @g = geometry:: STGeomFromText('CIRCULARSTRING(2 0, 1 1, 0 0)', 0);
SELECT @g.ToString();
```

### <a name="c-instantiating-a-geometry-instance-using-a-circularstring-with-multiple-circular-arc-segments"></a>C. 複数の円弧セグメントを含む CircularString を使用して geometry インスタンスをインスタンス化する
 次の例は、1 つ以上の円弧のセグメント (完全な円) を持つ `CircularString` インスタンスを作成する方法を示しています。

```sql
DECLARE @g geometry;
SET @g = geometry::Parse('CIRCULARSTRING(2 1, 1 2, 0 1, 1 0, 2 1)');
SELECT 'Circumference = ' + CAST(@g.STLength() AS NVARCHAR(10));  
```

 結果は、次のようになります。

```
Circumference = 6.28319
```

 `LineString` の代わりに `CircularString` が使用される場合は出力結果を比較してください。

```sql
DECLARE @g geometry;
SET @g = geometry::STGeomFromText('LINESTRING(2 1, 1 2, 0 1, 1 0, 2 1)', 0);
SELECT 'Perimeter = ' + CAST(@g.STLength() AS NVARCHAR(10));
```

 結果は、次のようになります。

```
Perimeter = 5.65685
```

 この`CircularString`例の値は、円の実際の円周である 2&#x03c0; (2 * pi) に近いことに注意してください。

### <a name="d-declaring-and-instantiating-a-geometry-instance-with-a-circularstring-in-the-same-statement"></a>D. CircularString を同じステートメント内で使用して geometry インスタンスを宣言およびインスタンス化する
 このコード スニペットは、`geometry` を同じステートメント内で使用して `CircularString` インスタンスを宣言およびインスタンス化する方法を示しています。

```sql
DECLARE @g geometry = 'CIRCULARSTRING(0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0)';
```

### <a name="e-instantiating-a-geography-instance-with-a-circularstring"></a>E. CircularString を使用して geometry インスタンスをインスタンス化する
 次の例は、`geography` を使用して `CircularString` インスタンスを宣言およびインスタンス化する方法を示しています。

```sql
DECLARE @g geography = 'CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';
```

### <a name="f-instantiating-a-geometry-instance-with-a-circularstring-that-is-a-straight-line"></a>F. 直線の CircularString を使用して geometry インスタンスをインスタンス化する
 次の例は、直線の `CircularString` インスタンスを作成する方法を示しています。

```sql
DECLARE @g geometry;
SET @g = geometry::STGeomFromText('CIRCULARSTRING(0 0, 1 2, 2 4)', 0);
```

## <a name="see-also"></a>参照
 [空間データ型の概要](spatial-data-types-overview.md) [CompoundCurve](compoundcurve.md) [makevalid &#40;geography データ型&#41;](/sql/t-sql/spatial-geography/makevalid-geography-data-type) [makevalid &#40;geometry データ型&#41;](/sql/t-sql/spatial-geometry/makevalid-geometry-data-type) [stisvalid &#40;geometry データ型&#41;](/sql/t-sql/spatial-geometry/stisvalid-geometry-data-type) [Stisvalid &#40;geography データ](/sql/t-sql/spatial-geography/stisvalid-geography-data-type)型&#41;[stisvalid &#40;geometry データ型&#41;](/sql/t-sql/spatial-geometry/stlength-geometry-data-type) [STStartPoint &#40;geometry データ型&#41;](/sql/t-sql/spatial-geometry/ststartpoint-geometry-data-type) [stisvalid &#40;geometry データ型&#41;](/sql/t-sql/spatial-geometry/stendpoint-geometry-data-type) [stpointn &#40;geometry データ型&#41;](/sql/t-sql/spatial-geometry/stpointn-geometry-data-type) [stnumpoints](/sql/t-sql/spatial-geometry/stnumpoints-geometry-data-type) &#40;geometry データ型&#41;stisring &#40;geometry データ型&#41;[STIsRing &#40;geometry Data Type&#41;](/sql/t-sql/spatial-geometry/stisring-geometry-data-type) [stisclosed](/sql/t-sql/spatial-geometry/stisclosed-geometry-data-type) &#40;geometry データ型&#41;[stpointonsurface &#40;geometry](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type)データ型&#41;[LineString](linestring.md)


