---
title: UDT データの操作 |マイクロソフトドキュメント
description: この資料では、SQL Server データベースの UDT 列のデータを挿入、選択、および更新する方法について説明します。
ms.custom: ''
ms.date: 12/05/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- TSQL
helpviewer_keywords:
- CAST function
- data deletions [CLR integration]
- data insertions [CLR integration]
- CONVERT function
- data updates [CLR integration]
- comparing data
- updating data [CLR integration]
- removing data
- IsByteOrdered property
- variables [CLR integration]
- data manipulation [CLR integration]
- user-defined types [CLR integration], data manipulation
- deleting data
- UDTs [CLR integration], data manipulation
- invoking UDT methods
- inserting data
ms.assetid: 51b1a5f2-7591-4e11-bfe2-d88e0836403f
author: rothja
ms.author: jroth
ms.openlocfilehash: 4ff4b620f2f06243b23b4c540f4c99b3c3cafa41
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81486930"
---
# <a name="working-with-user-defined-types---manipulating-udt-data"></a>ユーザー定義型の使用 - UDT データの操作
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  [!INCLUDE[tsql](../../includes/tsql-md.md)] には、UDT (ユーザー定義型) 列のデータを変更する際に特別な INSERT、UPDATE、または DELETE ステートメント構文は用意されていません。 [!INCLUDE[tsql](../../includes/tsql-md.md)] の CAST 関数または CONVERT 関数を使用して、ネイティブ データ型を UDT 型にキャストします。  
  
## <a name="inserting-data-in-a-udt-column"></a>UDT 列へのデータの挿入  
 次[!INCLUDE[tsql](../../includes/tsql-md.md)]のステートメントは **、3**行のサンプル データを Points テーブルに挿入します。 **Point**データ型は、UDT のプロパティとして公開される X および Y の整数値で構成されます。 コンマで区切られた X 値と Y 値を**Point**型にキャストするには、CAST 関数または CONVERT 関数を使用する必要があります。 最初の 2 つのステートメントは CONVERT 関数を使用して文字列値を**Point**型に変換し、3 番目のステートメントでは CAST 関数を使用します。  
  
```sql  
INSERT INTO dbo.Points (PointValue) VALUES (CONVERT(Point, '3,4'));  
INSERT INTO dbo.Points (PointValue) VALUES (CONVERT(Point, '1,5'));  
INSERT INTO dbo.Points (PointValue) VALUES (CAST ('1,99' AS Point));  
```  
  
## <a name="selecting-data"></a>データの選択  
 次の SELECT ステートメントでは、UDT のバイナリ値を選択します。  
  
```sql  
SELECT ID, PointValue FROM dbo.Points  
```  
  
 読み取り可能な形式で表示される出力を確認するには、値を文字列形式に変換する**Point** UDT の**ToString**メソッドを呼び出します。  
  
```sql  
SELECT ID, PointValue.ToString() AS PointValue   
FROM dbo.Points;  
```  
  
 これにより、次の結果が生成されます。  
  
```  
ID PointValue  
-- ----------  
 1 3,4  
 2 1,5  
 3 1,99  
```  
  
 また、[!INCLUDE[tsql](../../includes/tsql-md.md)] の CAST 関数や CONVERT 関数を使用して、同じ結果を得ることもできます。  
  
```sql  
SELECT ID, CAST(PointValue AS varchar)   
FROM dbo.Points;  
  
SELECT ID, CONVERT(varchar, PointValue)   
FROM dbo.Points;  
```  
  
 **ポイント**UDT は、X 座標と Y 座標をプロパティとして公開し、個別に選択できます。 次の、[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントでは、X 座標と Y 座標を個別に選択します。  
  
```sql  
SELECT ID, PointValue.X AS xVal, PointValue.Y AS yVal   
FROM dbo.Points;  
```  
  
 X プロパティと Y プロパティから整数値が返され、結果セットに表示されます。  
  
```  
ID xVal yVal  
-- ---- ----  
 1    3    4  
 2    1    5  
 3    1   99  
```  
  
## <a name="working-with-variables"></a>変数を使用した作業  
 変数を使用するには、DECLARE ステートメントを使用して、UDT 型にその変数を割り当てます。 次のステートメントは、SET ステートメント[!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して値を割り当て、変数に対して UDT の**ToString**メソッドを呼び出して結果を表示します。  
  
```sql  
DECLARE @PointValue Point;  
SET @PointValue = (SELECT PointValue FROM dbo.Points  
    WHERE ID = 2);  
SELECT @PointValue.ToString() AS PointValue;  
```  
  
 結果セットには、次のように変数の値が表示されます。  
  
```  
PointValue  
----------  
-1,5  
```  
  
 次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントでは、変数の代入で SET ステートメントの代わりに SELECT ステートメントを使用して、同じ結果を得ています。  
  
```sql  
DECLARE @PointValue Point;  
SELECT @PointValue = PointValue FROM dbo.Points  
    WHERE ID = 2;  
SELECT @PointValue.ToString() AS PointValue;  
```  
  
 変数の代入に SELECT ステートメントを使用した場合と SET ステートメントを使用した場合には異なる点が 1 つあります。SELECT ステートメントでは 1 つのステートメントで複数の変数に代入できますが、SET 構文では、1 つ変数に代入するごとに 1 つの SET ステートメントが必要になります。  
  
## <a name="comparing-data"></a>データの比較  
 クラスを定義するときに**IsByteOrdered**プロパティを**true**に設定している場合は、比較演算子を使用して UDT の値を比較できます。 詳細については、「[ユーザー定義型の作成](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types.md)」を参照してください。  
  
```sql  
SELECT ID, PointValue.ToString() AS Points   
FROM dbo.Points  
WHERE PointValue > CONVERT(Point, '2,2');  
```  
  
 値自体が同等である場合は **、IsByteOrdered**設定に関係なく、UDT の内部値を比較できます。 次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントでは、X の値が Y の値よりも大きい行を選択します。  
  
```sql  
SELECT ID, PointValue.ToString() AS PointValue   
FROM dbo.Points  
WHERE PointValue.X < PointValue.Y;  
```  
  
 また、一致する PointValue を検索する次のクエリのように、変数と比較演算子を組み合わせて使用することもできます。  
  
```sql  
DECLARE @ComparePoint Point;  
SET @ComparePoint = CONVERT(Point, '3,4');  
SELECT ID, PointValue.ToString() AS MatchingPoint   
FROM dbo.Points  
WHERE PointValue = @ComparePoint;  
```  
  
## <a name="invoking-udt-methods"></a>UDT メソッドの呼び出し  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] でも、UDT で定義されているメソッドを呼び出すことができます。 **ポイント**クラスには、**距離**、**距離**、および**距離の 3**つのメソッドが含まれています。 これら 3 つのメソッドを定義するコードの一覧については、「[ユーザー定義型のコーディング](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types-coding.md)」を参照してください。  
  
 次[!INCLUDE[tsql](../../includes/tsql-md.md)]のステートメントは **、PointValue.Distance**メソッドを呼び出します。  
  
```sql  
SELECT ID, PointValue.X AS [Point.X],   
    PointValue.Y AS [Point.Y],  
    PointValue.Distance() AS DistanceFromZero   
FROM dbo.Points;  
```  
  
 結果は[**距離**]列に表示されます。  
  
```  
ID X  Y  Distance  
-- -- -- ----------------  
 1  3  4                5  
 2  1  5 5.09901951359278  
 3  1 99 99.0050503762308  
```  
  
 **DistanceFrom**メソッドは **、Point**データ型の引数を受け取り、指定したポイントから PointValue までの距離を表示します。  
  
```sql  
SELECT ID, PointValue.ToString() AS Pnt,  
   PointValue.DistanceFrom(CONVERT(Point, '1,99')) AS DistanceFromPoint  
FROM dbo.Points;  
```  
  
 結果には、テーブル内の各行の**DistanceFrom**メソッドの結果が表示されます。  
  
```  
ID Pnt DistanceFromPoint  
-- --- -----------------  
 1 3,4  95.0210502993942  
 2 1,5                94  
 3 1,9                90  
```  
  
 **DistanceFromXY**メソッドは、各ポイントを引数として個別に受け取ります。  
  
```sql  
SELECT ID, PointValue.X as X, PointValue.Y as Y,   
PointValue.DistanceFromXY(1, 99) AS DistanceFromXY   
FROM dbo.Points  
```  
  
 結果セットは **、DistanceFrom**メソッドと同じです。  
  
## <a name="updating-data-in-a-udt-column"></a>UDT 列のデータの更新  
 UDT 列のデータを更新するには、[!INCLUDE[tsql](../../includes/tsql-md.md)] の UPDATE ステートメントを使用します。 また、UDT のメソッドを使用して、オブジェクトの状態を更新することもできます。 次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントでは、テーブルの単一行を更新します。  
  
```sql  
UPDATE dbo.Points  
SET PointValue = CAST('1,88' AS Point)  
WHERE ID = 3  
```  
  
 また、UDT の要素を個別に更新することもできます。 次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントでは、Y 座標の値のみを更新します。  
  
```sql  
UPDATE dbo.Points  
SET PointValue.Y = 99  
WHERE ID = 3  
```  
  
 UDT がバイト順に true**に設定**されて定義[!INCLUDE[tsql](../../includes/tsql-md.md)]されている場合は、WHERE 句の UDT 列を評価できます。  
  
```sql  
UPDATE dbo.Points  
SET PointValue = '4,5'  
WHERE PointValue = '3,4';  
```  
  
### <a name="updating-limitations"></a>更新の制限事項  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] を使用して、複数のプロパティを一度に更新することはできません。 たとえば、1 つの UPDATE ステートメントでは同じ列名を 2 回使用することができないため、次のステートメントは失敗します。  
  
```sql  
UPDATE dbo.Points  
SET PointValue.X = 5, PointValue.Y = 99  
WHERE ID = 3  
```  
  
 座標の値を個別に更新するには、Point UDT のアセンブリにミューテーター メソッドを作成する必要があります。 ミューテーター メソッドを作成すると、[!INCLUDE[tsql](../../includes/tsql-md.md)] の UPDATE ステートメントでミューテーター メソッドを呼び出して、オブジェクトを更新することができます。次に、例を示します。  
  
```sql  
UPDATE dbo.Points  
SET PointValue.SetXY(5, 99)  
WHERE ID = 3  
```  
  
## <a name="deleting-data-in-a-udt-column"></a>UDT 列のデータの削除  
 UDT のデータを削除するには、[!INCLUDE[tsql](../../includes/tsql-md.md)] の DELETE ステートメントを使用します。 次のステートメントでは、WHERE 句で指定した条件に一致するテーブル内のすべての行が削除されます。 DELETE ステートメントで WHERE 句を省略すると、テーブル内のすべての行が削除されます。  
  
```sql  
DELETE FROM dbo.Points  
WHERE PointValue = CAST('1,99' AS Point)  
```  
  
 UDT 列の値を削除し、それ以外の行の値については現状維持する場合は、UPDATE ステートメントを使用します。 次の例では、PointValue に NULL を設定します。  
  
```sql  
UPDATE dbo.Points  
SET PointValue = null  
WHERE ID = 2  
```  
  
## <a name="see-also"></a>参照  
 [SQL Server でのユーザー定義型の使用](../../relational-databases/clr-integration-database-objects-user-defined-types/working-with-user-defined-types-in-sql-server.md)  
  
  
