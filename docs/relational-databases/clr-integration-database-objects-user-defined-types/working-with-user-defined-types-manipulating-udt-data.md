---
title: UDT データを操作する |Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
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
ms.openlocfilehash: 53471adf085fbe9a046d28fa09ce10a46953eae6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68028169"
---
# <a name="working-with-user-defined-types---manipulating-udt-data"></a>ユーザー定義型の使用 - UDT データの操作
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  [!INCLUDE[tsql](../../includes/tsql-md.md)] には、UDT (ユーザー定義型) 列のデータを変更する際に特別な INSERT、UPDATE、または DELETE ステートメント構文は用意されていません。 [!INCLUDE[tsql](../../includes/tsql-md.md)] の CAST 関数または CONVERT 関数を使用して、ネイティブ データ型を UDT 型にキャストします。  
  
## <a name="inserting-data-in-a-udt-column"></a>UDT 列へのデータの挿入  
 次[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントにサンプル データの 3 つの行を挿入、**ポイント**テーブル。 **ポイント**データ型は X と Y の整数値、UDT のプロパティとして公開されます。 CAST または CONVERT のいずれかの関数を使用して、コンマ区切りをキャストする必要があります X と Y 値を**ポイント**型。 最初の 2 つのステートメントでは、CONVERT 関数を使用して、文字列値を変換、**ポイント**型、および 3 番目のステートメントは、CAST 関数を使用します。  
  
```  
INSERT INTO dbo.Points (PointValue) VALUES (CONVERT(Point, '3,4'));  
INSERT INTO dbo.Points (PointValue) VALUES (CONVERT(Point, '1,5'));  
INSERT INTO dbo.Points (PointValue) VALUES (CAST ('1,99' AS Point));  
```  
  
## <a name="selecting-data"></a>データの選択  
 次の SELECT ステートメントでは、UDT のバイナリ値を選択します。  
  
```  
SELECT ID, PointValue FROM dbo.Points  
```  
  
 読みやすい形式で表示される出力を表示するを呼び出して、 **ToString**のメソッド、**ポイント**UDT では、値を文字列表現に変換します。  
  
```  
SELECT ID, PointValue.ToString() AS PointValue   
FROM dbo.Points;  
```  
  
 これには、次の結果が生成されます。  
  
```  
ID PointValue  
-- ----------  
 1 3,4  
 2 1,5  
 3 1,99  
```  
  
 また、[!INCLUDE[tsql](../../includes/tsql-md.md)] の CAST 関数や CONVERT 関数を使用して、同じ結果を得ることもできます。  
  
```  
SELECT ID, CAST(PointValue AS varchar)   
FROM dbo.Points;  
  
SELECT ID, CONVERT(varchar, PointValue)   
FROM dbo.Points;  
```  
  
 **ポイント**UDT が個別に選択し、プロパティとして、X と Y 座標を公開します。 次の、[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントでは、X 座標と Y 座標を個別に選択します。  
  
```  
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
 変数を使用するには、DECLARE ステートメントを使用して、UDT 型にその変数を割り当てます。 次のステートメントを使用して値を割り当てる、[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントを設定し、UDT を呼び出すことによって、結果を表示**ToString**変数メソッド。  
  
```  
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
  
```  
DECLARE @PointValue Point;  
SELECT @PointValue = PointValue FROM dbo.Points  
    WHERE ID = 2;  
SELECT @PointValue.ToString() AS PointValue;  
```  
  
 変数の代入に SELECT ステートメントを使用した場合と SET ステートメントを使用した場合には異なる点が 1 つあります。SELECT ステートメントでは 1 つのステートメントで複数の変数に代入できますが、SET 構文では、1 つ変数に代入するごとに 1 つの SET ステートメントが必要になります。  
  
## <a name="comparing-data"></a>データを比較します。  
 設定した場合、UDT の値を比較する比較演算子を使用することができます、 **IsByteOrdered**プロパティを**true**クラスを定義するときにします。 詳細については、次を参照してください。[ユーザー定義型を作成する](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types.md)します。  
  
```  
SELECT ID, PointValue.ToString() AS Points   
FROM dbo.Points  
WHERE PointValue > CONVERT(Point, '2,2');  
```  
  
 関係なく、UDT の内部の値を比較することができます、 **IsByteOrdered**自体の値が比較可能な場合に設定します。 次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントでは、X の値が Y の値よりも大きい行を選択します。  
  
```  
SELECT ID, PointValue.ToString() AS PointValue   
FROM dbo.Points  
WHERE PointValue.X < PointValue.Y;  
```  
  
 また、一致する PointValue を検索する次のクエリのように、変数と比較演算子を組み合わせて使用することもできます。  
  
```  
DECLARE @ComparePoint Point;  
SET @ComparePoint = CONVERT(Point, '3,4');  
SELECT ID, PointValue.ToString() AS MatchingPoint   
FROM dbo.Points  
WHERE PointValue = @ComparePoint;  
```  
  
## <a name="invoking-udt-methods"></a>UDT メソッドの呼び出し  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] でも、UDT で定義されているメソッドを呼び出すことができます。 **ポイント**クラスには、3 つのメソッドが含まれています。**距離**、 **DistanceFrom**、および**DistanceFromXY**します。 これら 3 つのメソッドを定義するコード リストを参照してください。 [Coding User-Defined 型](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types-coding.md)します。  
  
 次[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントの呼び出し、 **PointValue.Distance**メソッド。  
  
```  
SELECT ID, PointValue.X AS [Point.X],   
    PointValue.Y AS [Point.Y],  
    PointValue.Distance() AS DistanceFromZero   
FROM dbo.Points;  
```  
  
 結果が表示されます、**距離**列。  
  
```  
ID X  Y  Distance  
-- -- -- ----------------  
 1  3  4                5  
 2  1  5 5.09901951359278  
 3  1 99 99.0050503762308  
```  
  
 **DistanceFrom**メソッドの引数を受け取る**ポイント**データ型、および指定した点から PointValue までの距離が表示されます。  
  
```  
SELECT ID, PointValue.ToString() AS Pnt,  
   PointValue.DistanceFrom(CONVERT(Point, '1,99')) AS DistanceFromPoint  
FROM dbo.Points;  
```  
  
 結果の結果を表示する、 **DistanceFrom**テーブルの各行のメソッド。  
  
```  
ID Pnt DistanceFromPoint  
-- --- -----------------  
 1 3,4  95.0210502993942  
 2 1,5                94  
 3 1,9                90  
```  
  
 **DistanceFromXY**メソッドは引数として個別にポイントを取得します。  
  
```  
SELECT ID, PointValue.X as X, PointValue.Y as Y,   
PointValue.DistanceFromXY(1, 99) AS DistanceFromXY   
FROM dbo.Points  
```  
  
 結果セットが同じ、 **DistanceFrom**メソッド。  
  
## <a name="updating-data-in-a-udt-column"></a>UDT 列のデータの更新  
 UDT 列のデータを更新するには、[!INCLUDE[tsql](../../includes/tsql-md.md)] の UPDATE ステートメントを使用します。 また、UDT のメソッドを使用して、オブジェクトの状態を更新することもできます。 次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントでは、テーブルの単一行を更新します。  
  
```  
UPDATE dbo.Points  
SET PointValue = CAST('1,88' AS Point)  
WHERE ID = 3  
```  
  
 また、UDT の要素を個別に更新することもできます。 次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントでは、Y 座標の値のみを更新します。  
  
```  
UPDATE dbo.Points  
SET PointValue.Y = 99  
WHERE ID = 3  
```  
  
 バイト オーダーに設定すると、UDT が定義されてかどうか**true**、 [!INCLUDE[tsql](../../includes/tsql-md.md)] WHERE 句で UDT 列を評価することができます。  
  
```  
UPDATE dbo.Points  
SET PointValue = '4,5'  
WHERE PointValue = '3,4';  
```  
  
### <a name="updating-limitations"></a>更新の制限事項  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] を使用して、複数のプロパティを一度に更新することはできません。 たとえば、1 つの UPDATE ステートメントでは同じ列名を 2 回使用することができないため、次のステートメントは失敗します。  
  
```  
UPDATE dbo.Points  
SET PointValue.X = 5, PointValue.Y = 99  
WHERE ID = 3  
```  
  
 座標の値を個別に更新するには、Point UDT のアセンブリにミューテーター メソッドを作成する必要があります。 ミューテーター メソッドを作成すると、[!INCLUDE[tsql](../../includes/tsql-md.md)] の UPDATE ステートメントでミューテーター メソッドを呼び出して、オブジェクトを更新することができます。次に、例を示します。  
  
```  
UPDATE dbo.Points  
SET PointValue.SetXY(5, 99)  
WHERE ID = 3  
```  
  
## <a name="deleting-data-in-a-udt-column"></a>UDT 列のデータの削除  
 UDT のデータを削除するには、[!INCLUDE[tsql](../../includes/tsql-md.md)] の DELETE ステートメントを使用します。 次のステートメントでは、WHERE 句で指定した条件に一致するテーブル内のすべての行が削除されます。 DELETE ステートメントで WHERE 句を省略すると、テーブル内のすべての行が削除されます。  
  
```  
DELETE FROM dbo.Points  
WHERE PointValue = CAST('1,99' AS Point)  
```  
  
 UDT 列の値を削除し、それ以外の行の値については現状維持する場合は、UPDATE ステートメントを使用します。 次の例では、PointValue に NULL を設定します。  
  
```  
UPDATE dbo.Points  
SET PointValue = null  
WHERE ID = 2  
```  
  
## <a name="see-also"></a>参照  
 [SQL Server でのユーザー定義型の使用](../../relational-databases/clr-integration-database-objects-user-defined-types/working-with-user-defined-types-in-sql-server.md)  
  
  
