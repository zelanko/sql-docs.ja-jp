---
title: "例 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- parentheses [SQL Server]
- GROUP BY clause, SELECT statement
- query hints [SQL Server]
- ALL keyword
- ROLLUP operator
- SELECT statement [SQL Server], examples
- correlated subqueries, SELECT statement
- SELECT INTO statement
- ORDER BY clause [Transact-SQL]
- GROUPING function
- index hints [SQL Server]
- HAVING clause, SELECT statement
- DISTINCT keyword
- CUBE operator
- UNION operator [SQL Server]
- computed sums
- WHERE clause, SELECT statement
ms.assetid: 9b9caa3d-e7d0-42e1-b60b-a5572142186c
caps.latest.revision: 45
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 432739177dee13fcd474b081509e0c34ab8ba504
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="select-examples-transact-sql"></a>SELECT の例 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  このトピックの使用例を提供する、[選択](../../t-sql/queries/select-transact-sql.md)ステートメントです。  
  
## <a name="a-using-select-to-retrieve-rows-and-columns"></a>A. SELECT を使用して行および列を取得する  
 3 つのプログラム例を次に示します。 最初の例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベース内の `*` テーブルから、WHERE 句を指定せずにすべての行を返し、また `Product` を使用してすべての列を返しています。  
  
 [!code-sql[選択 #selectexamples1](../../t-sql/queries/codesnippet/tsql/select-examples-transact_1.sql)]  
  
 この例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベース内の `Name` テーブルから、WHERE 句を指定せずにすべての行と、一部の列 (`ProductNumber`、`ListPrice`、`Product`) のみを返しています。 さらに、列ヘッダーが追加されています。  
  
 [!code-sql[選択 #selectexamples2](../../t-sql/queries/codesnippet/tsql/select-examples-transact_2.sql)]  
  
 この例の行のみを返します`Product`製品の行がある`R`いて、つまり製造までの日数より小さい`4`です。  
  
 [!code-sql[選択 #selectexamples3](../../t-sql/queries/codesnippet/tsql/select-examples-transact_3.sql)]  
  
## <a name="b-using-select-with-column-headings-and-calculations"></a>B. 列ヘッダーおよび計算処理と共に SELECT を使用する  
 次の例は、のすべての行を返す、`Product`テーブル。 最初の例では、各製品の売上合計と売上割引を返します。 2 番目の例では、製品ごとの合計収入が計算されます。  
  
 [!code-sql[選択 #selectexamples4](../../t-sql/queries/codesnippet/tsql/select-examples-transact_4.sql)]  
  
 次の例は、販売注文ごとに各製品の収入を計算するクエリです。  
  
 [!code-sql[選択 #selectexamples5](../../t-sql/queries/codesnippet/tsql/select-examples-transact_5.sql)]  
  
## <a name="c-using-distinct-with-select"></a>C. DISTINCT を SELECT と共に使用する  
 次の例では`DISTINCT`重複しているタイトルを取得しないようにします。  
  
 [!code-sql[選択 #selectexamples6](../../t-sql/queries/codesnippet/tsql/select-examples-transact_6.sql)]  
  
## <a name="d-creating-tables-with-select-into"></a>D. SELECT INTO を使用してテーブルを作成する  
 次の最初の例では、`#Bicycles` 内に `tempdb` という一時テーブルを作成します。  
  
 [!code-sql[選択 #selectexamples7](../../t-sql/queries/codesnippet/tsql/select-examples-transact_7.sql)]  
  
 この 2 番目の例は、永続的なテーブルを作成`NewProducts`です。  
  
 [!code-sql[選択 #selectexamples8](../../t-sql/queries/codesnippet/tsql/select-examples-transact_8.sql)]  
  
## <a name="e-using-correlated-subqueries"></a>E. 相関サブクエリを使用する  
 次の例では、`EXISTS` キーワードと `IN` キーワードを使用した意味的に等しいクエリと、それらの違いを示します。 いずれも、製品モデルが長袖ジャージで、`ProductModelID` テーブルと `Product` テーブルの間で `ProductModel` 番号が一致する各製品名の 1 つのインスタンスを取得する有効なサブクエリの例です。  
  
 [!code-sql[選択 #selectexamples9](../../t-sql/queries/codesnippet/tsql/select-examples-transact_9.sql)]  
  
 次の例では、相関または繰り返しサブクエリ内で `IN` を使用しています。 これは、外側のクエリによって値が決まるクエリです。 このクエリは、外側のクエリが選択する行に対して 1 回ずつ、繰り返し実行されます。 このクエリは、`SalesPerson` テーブルのボーナス額が `5000.00` で、従業員の ID 番号が `Employee` テーブルと `SalesPerson` テーブルで一致する各従業員の姓名のインスタンスを 1 つ取得します。  
  
 [!code-sql[選択 #selectexamples10](../../t-sql/queries/codesnippet/tsql/select-examples-transact_10.sql)]  
  
 上記のステートメントのサブクエリは、外側のクエリから独立して評価できません。 このサブクエリは `Employee.EmployeeID` の値を必要としますが、この値は、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]が調べる `Employee` の行によって変化します。  
  
 相関サブクエリは、外側のクエリの `HAVING` 句でも使えます。 この例では、表示価格がモデルの平均値の 2 倍以上の製品モデルを検索します。  
  
 [!code-sql[選択 #selectexamples11](../../t-sql/queries/codesnippet/tsql/select-examples-transact_11.sql)]  
  
 この例では、2 つの相関サブクエリを使って、特定の製品を販売した従業員の名前を検索します。  
  
 [!code-sql[選択 #selectexamples12](../../t-sql/queries/codesnippet/tsql/select-examples-transact_12.sql)]  
  
## <a name="f-using-group-by"></a>F. GROUP BY を使用する  
 次の例は、データベース内の各販売注文の合計を検索します。  
  
 [!code-sql[選択 #selectexamples13](../../t-sql/queries/codesnippet/tsql/select-examples-transact_13.sql)]  
  
 `GROUP BY` 句があるため、各販売注文につき 1 行だけが返され、この行にその販売注文のすべての売上合計が含まれます。  
  
## <a name="g-using-group-by-with-multiple-groups"></a>G. GROUP BY を複数のグループと共に使用する  
 次の例では、平均価格および今年に入ってからの売り上げの合計を、製品 ID と特価品 ID でグループ化して返します。  
  
 [!code-sql[選択 #selectexamples14](../../t-sql/queries/codesnippet/tsql/select-examples-transact_14.sql)]  
  
## <a name="h-using-group-by-and-where"></a>H. GROUP BY と WHERE を使用する  
 次の例では、表示価格が `$1000` より多い行だけを取得した後、結果をグループ化します。  
  
 [!code-sql[選択 #selectexamples15](../../t-sql/queries/codesnippet/tsql/select-examples-transact_15.sql)]  
  
## <a name="i-using-group-by-with-an-expression"></a>I. 1 つの式と共に GROUP BY を使用する  
 次の例では、式によってグループ化します。 式に集計関数が含まれない限り、式によってグループ化することができます。  
  
 [!code-sql[選択 #selectexamples16](../../t-sql/queries/codesnippet/tsql/select-examples-transact_16.sql)]  
  
## <a name="j-using-group-by-with-order-by"></a>J. ORDER BY と共に GROUP BY を使用する  
 次の例では、それぞれの製品の種類別の平均価格を求め、その結果を平均価格の順序で表示しています。  
  
 [!code-sql[選択 #selectexamples18](../../t-sql/queries/codesnippet/tsql/select-examples-transact_17.sql)]  
  
## <a name="k-using-the-having-clause"></a>K. HAVING 句を使用する  
 最初の例、`HAVING`句、集計関数と共に使用します。 `SalesOrderDetail` テーブルの行を製品 ID 別にグループ化し、平均注文数が 5 以下の製品を除外しています。 2 番目の例では、`HAVING` 句を集計関数なしで使用しています。  
  
 [!code-sql[選択 #selectexamples19](../../t-sql/queries/codesnippet/tsql/select-examples-transact_18.sql)]  
  
 次のクエリでは、`LIKE` 句の中で `HAVING` 句を使用しています。  
  
```  
USE AdventureWorks2012 ;  
GO  
SELECT SalesOrderID, CarrierTrackingNumber   
FROM Sales.SalesOrderDetail  
GROUP BY SalesOrderID, CarrierTrackingNumber  
HAVING CarrierTrackingNumber LIKE '4BD%'  
ORDER BY SalesOrderID ;  
GO  
```  
  
## <a name="l-using-having-and-group-by"></a>L. HAVING と GROUP BY を使用する  
 次の例を使用して`GROUP BY`、 `HAVING`、 `WHERE`、および`ORDER BY`のいずれかの句`SELECT`ステートメントです。 これによって、$25 より高く平均注文数量が 5 未満の製品を除外した、グループとサマリー値が作成されます。 この結果は `ProductID` 別にまとめられます。  
  
 [!code-sql[選択 #selectexamples21](../../t-sql/queries/codesnippet/tsql/select-examples-transact_19.sql)]  
  
## <a name="m-using-having-with-sum-and-avg"></a>M. HAVING を SUM および AVG と共に使用する  
 次の例では、`SalesOrderDetail` テーブルから、注文合計額が `$1000000.00` を超え、かつ平均注文数が `3` 未満の製品を製品 ID 別にグループ化します。  
  
 [!code-sql[選択 #selectexamples22](../../t-sql/queries/codesnippet/tsql/select-examples-transact_20.sql)]  
  
 大きいの総売り上げ高を持っている製品を表示する`$2000000.00`、このクエリを使用します。  
  
 [!code-sql[選択 #selectexamples23](../../t-sql/queries/codesnippet/tsql/select-examples-transact_21.sql)]  
  
 各製品の集計に最低 1,500 の品目が含まれているようにするには、`HAVING COUNT(*) > 1500` を使って、`1500` 未満の合計を返す製品を除外します。 クエリは次のようになります。  
  
 [!code-sql[選択 #selectexamples24](../../t-sql/queries/codesnippet/tsql/select-examples-transact_22.sql)]  
  
## <a name="n-using-the-index-optimizer-hint"></a>N. INDEX オプティマイザー ヒントを使用する  
 次の例を使用する 2 つの方法を示しています、`INDEX`オプティマイザー ヒント。 最初の例では、オプティマイザーで非クラスター化インデックスを使用し、テーブルから行を取得しています。2 番目の例では、index = 0 を使ってテーブル スキャンを実行しています。  
  
 [!code-sql[選択 #selectexamples45](../../t-sql/queries/codesnippet/tsql/select-examples-transact_23.sql)]  
  
## <a name="m-using-option-and-the-group-hints"></a>M. OPTION ヒントと GROUP ヒントを使用する  
 次の例では、`OPTION (GROUP)` 句と共に `GROUP BY` 句を使用する方法を示します。  
  
 [!code-sql[選択 #selectexamples46](../../t-sql/queries/codesnippet/tsql/select-examples-transact_24.sql)]  
  
## <a name="o-using-the-union-query-hint"></a>O.  UNION クエリ ヒントを使用する  
 次の例では、`MERGE UNION`クエリ ヒントです。  
  
 [!code-sql[選択 #selectexamples47](../../t-sql/queries/codesnippet/tsql/select-examples-transact_25.sql)]  
  
## <a name="p-using-a-simple-union"></a>P. 単純な UNION を使用する  
 次の例では、結果セットに `ProductModelID` テーブルと `Name` テーブルの `ProductModel` 列と `Gloves` 列の内容が含まれています。  
  
 [!code-sql[選択 #selectexamples48](../../t-sql/queries/codesnippet/tsql/select-examples-transact_26.sql)]  
  
## <a name="q-using-select-into-with-union"></a>Q.  UNION と共に SELECT INTO を使用する  
 この例では、2 番目の `INTO` ステートメントの `SELECT` 句で、`ProductResults` および `ProductModel` テーブルの指定された列のユニオンの最終的な結果セットを `Gloves` という名前のテーブルに格納することを指定します。 `Gloves` テーブルは、最初の `SELECT` ステートメントで作成されます。  
  
 [!code-sql[選択 #selectexamples49](../../t-sql/queries/codesnippet/tsql/select-examples-transact_27.sql)]  
  
## <a name="r-using-union-of-two-select-statements-with-order-by"></a>R.  ORDER BY 句を指定した 2 つの SELECT ステートメントで UNION 句を使用する  
 UNION 句で使用するある種のパラメーターの順序には重要な意味があります。 次の例では、誤った方法と正しい使用`UNION`を 2 つ`SELECT`ステートメントは、列の出力に名前を変更します。  
  
 [!code-sql[選択 #selectexamples50](../../t-sql/queries/codesnippet/tsql/select-examples-transact_28.sql)]  
  
## <a name="s-using-union-of-three-select-statements-to-show-the-effects-of-all-and-parentheses"></a>S.  3 つの SELECT ステートメントで UNION を使用して、ALL とかっこの効果を示す  
 次の例を使用して`UNION`3 つのテーブルが同じ 5 行のデータがあるすべての結果を結合します。 最初の例では、`UNION ALL` を使用して、重複するレコードも含めて 15 行すべてを返します。 2 番目の例では`UNION`せず`ALL`、3 つの結合された結果から重複する行を削除する`SELECT`ステートメント、および 5 行を返します。  
  
 3 番目の例では、最初の `ALL` と共に `UNION` を使用し、`UNION` を使用していない 2 番目の `ALL` をかっこで囲んでいます。 2 番目`UNION`最初に処理されますが、かっこでは、5 行を返すため、`ALL`オプションを使用しないと、重複を削除します。 これらの 5 行は、最初の結果の結合`SELECT`を使用して、`UNION ALL`キーワード。 これによって 2 組の 5 行の間での重複が削除されることはありません。 最終的な結果は 10 行になります。  
  
 [!code-sql[選択 #selectexamples51](../../t-sql/queries/codesnippet/tsql/select-examples-transact_29.sql)]  
  
## <a name="see-also"></a>参照  
 [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)   
 [CREATE VIEW &#40;Transact-SQL&#41;](../../t-sql/statements/create-view-transact-sql.md)   
 [DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)   
 [EXECUTE &#40;Transact-SQL&#41;](../../t-sql/language-elements/execute-transact-sql.md)   
 [式 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/expressions-transact-sql.md)   
 [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)   
 [ような & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/like-transact-sql.md)   
 [共用体 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/set-operators-union-transact-sql.md)   
 [除くおよび INTERSECT と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/set-operators-except-and-intersect-transact-sql.md)   
 [UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md)   
 [ここで & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/where-transact-sql.md)   
 [パス名 & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-functions/pathname-transact-sql.md)   
 [句と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/select-into-clause-transact-sql.md)  
  
  
