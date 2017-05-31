---
title: "インメモリ OLTP を使用した JSON の処理の最適化 | Microsoft Docs"
ms.custom: 
ms.date: 02/03/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9c5adb1-3209-4186-bc10-8e41a26f5e57
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 4e0331c288665fd9f69444d0d14366dfa69a668f
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="optimize-json-processing-with-in-memory-oltp"></a>インメモリ OLTP を使用した JSON の処理の最適化
[!INCLUDE[tsql-appliesto-ssvNxt-asdb-xxxx-xxx](../../includes/tsql-appliesto-ssvnxt-asdb-xxxx-xxx.md)]

SQL Server と Azure SQL Database では、JSON 形式のテキストを使用できます。 JSON データを処理する OLTP クエリのパフォーマンスを上げるには、標準の文字列型の列 (NVARCHAR 型) を使用してメモリ最適化テーブルに JSON ドキュメントを格納します。

## <a name="store-json-in-memory-optimized-tables"></a>メモリ最適化テーブルへの JSON の格納
次に、`Tags` と `Data` という 2 つの JSON 列があるメモリ最適化 `Product` テーブルの例を示します。

```tsql
CREATE SCHEMA xtp;
GO
CREATE TABLE xtp.Product(
    ProductID int PRIMARY KEY NONCLUSTERED, --standard column
    Name nvarchar(400) NOT NULL, --standard column
    Price float, --standard column

    Tags nvarchar(400),--json stored in string column
    Data nvarchar(4000) --json stored in string column

) WITH (MEMORY_OPTIMIZED=ON);
```
JSON データをメモリ最適化テーブルに格納すると、ロックはされることがなく、データはインメモリでアクセスされるので、クエリのパフォーマンスが向上します。

## <a name="optimize-json-with-additional-in-memory-features"></a>その他のインメモリ機能での JSON の最適化
SQL Server と Azure SQL Database の新機能を使用すると、既存のインメモリ OLTP のテクノロジに JSON の機能を完全に統合できます。 たとえば、次を実行できます。
 - ネイティブ コンパイルの CHECK 制約を使用して、メモリ最適化テーブルに格納された JSON ドキュメントの構造を検証できます。
 - 計算列を使用して JSON ドキュメントに格納された値を公開し、型を厳密に指定できます。
 - メモリ最適化インデックスを使用して JSON ドキュメントの値にインデックスを作成できます。
 - JSON ドキュメントの値を使用する SQL クエリをネイティブでコンパイルしたり、結果を JSON テキストとして書式設定できます。

## <a name="validate-json-columns"></a>JSON の列の検証
SQL Server と Azure SQL Database では、次の例のように、文字列の列に格納された JSON ドキュメントの内容を検証するネイティブ コンパイルの CHECK 制約を追加できます。

```tsql
DROP TABLE IF EXISTS xtp.Product;
GO
CREATE TABLE xtp.Product(
    ProductID int PRIMARY KEY NONCLUSTERED,
    Name nvarchar(400) NOT NULL,
    Price float,

    Tags nvarchar(400)
            CONSTRAINT [Tags should be formatted as JSON]
                CHECK (ISJSON(Tags)=1),
    Data nvarchar(4000)

) WITH (MEMORY_OPTIMIZED=ON);
```

ネイティブ コンパイルの CHECK 制約は、JSON の列がある作成済みのテーブルに追加できます。

```tsql
ALTER TABLE xtp.Product
    ADD CONSTRAINT [Data should be JSON]
        CHECK (ISJSON(Data)=1)
```

ネイティブ コンパイルされた JSON の CHECK 制約では、メモリ最適化テーブルに格納されている JSON テキストの書式が正しいことを保証します。

## <a name="expose-json-values-using-computed-columns"></a>計算列を使用した JSON 値の公開
計算列では、JSON テキストの値が公開されます。それらの値へは、JSON テキストから値を取得する式を再評価したり、JSON の構造を再解析することがなくアクセスできます。 計算列で公開される値の型は厳密に指定され、物理的に保存されます。 保存される計算列を使用した JSON 値へのアクセスは、JSON ドキュメント内の値へのアクセスよりも高速です。

次の例では、JSON の `Data` 列から次の 2 つの値を公開する方法を示します。
-   製品の製造国。
-   製品の製造コスト。

```tsql
DROP TABLE IF EXISTS xtp.Product;
GO
CREATE TABLE xtp.Product(
    ProductID int PRIMARY KEY NONCLUSTERED,
    Name nvarchar(400) NOT NULL,
    Price float,

    Data nvarchar(4000),

    MadeIn AS CAST(JSON_VALUE(Data, '$.MadeIn') as NVARCHAR(50)) PERSISTED,
    Cost   AS CAST(JSON_VALUE(Data, '$.ManufacturingCost') as float)

) WITH (MEMORY_OPTIMIZED=ON);
```

計算列の `MadeIn` と `Cost` は、`Data` 列に格納された JSON ドキュメントが変更されるたびに更新されます。

## <a name="index-values-in-json-columns"></a>JSON の列のインデックス値
SQL Server と Azure SQL Database では、メモリ最適化インデックスを使用して JSON の列の値にインデックスを作成できます。 インデックスが作成されている JSON 値は、次の例のように、計算列を使用して公開され、型が厳密に指定されている必要があります。

```tsql
DROP TABLE IF EXISTS xtp.Product;
GO
CREATE TABLE xtp.Product(
    ProductID int PRIMARY KEY NONCLUSTERED,
    Name nvarchar(400) NOT NULL,
    Price float,

    Data nvarchar(4000),

    MadeIn AS CAST(JSON_VALUE(Data, '$.MadeIn') as NVARCHAR(50)) PERSISTED,
    Cost   AS CAST(JSON_VALUE(Data, '$.ManufacturingCost') as float) PERSISTED,

    INDEX [idx_Product_MadeIn] NONCLUSTERED (MadeIn)

) WITH (MEMORY_OPTIMIZED=ON)

ALTER TABLE Product
    ADD INDEX [idx_Product_Cost] NONCLUSTERED HASH(Cost)
        WITH (BUCKET_COUNT=20000)
```
JSON の列の値には、標準の非クラスター化インデックスとハッシュ インデックスの両方を使用してインデックスを作成できます。
-   非クラスター化インデックスは、いくつかの JSON 値による行範囲の選択または JSON 値による結果の並べ替えを行うクエリを最適化します。
-   ハッシュ インデックスは、検索する値を正確に指定し、1 行または少数の行がフェッチされるときにパフォーマンスが最適化されます。

## <a name="native-compilation-of-json-queries"></a>JSON クエリのネイティブ コンパイル
最後に、JSON 関数が使用されたクエリを含む TRANSACT-SQL プロシージャ、関数、およびトリガーのネイティブ コンパイルは、クエリのパフォーマンスを向上し、プロシージャの実行に必要な CPU サイクルを短縮します。 次に、JSON_VALUE、OPENJSON、JSON_MODIFY の JSON 関数をいくつか使用するネイティブ コンパイル プロシージャの例を示します。

```tsql
CREATE PROCEDURE xtp.ProductList(@ProductIds nvarchar(100))
WITH SCHEMABINDING, NATIVE_COMPILATION
AS BEGIN
    ATOMIC WITH (transaction isolation level = snapshot,  language = N'English')

    SELECT ProductID,Name,Price,Data,Tags, JSON_VALUE(data,'$.MadeIn') AS MadeIn
    FROM xtp.Product
        JOIN OPENJSON(@ProductIds)
            ON ProductID = value

END;

CREATE PROCEDURE xtp.UpdateProductData(@ProductId int, @Property nvarchar(100), @Value nvarchar(100))
WITH SCHEMABINDING, NATIVE_COMPILATION
AS BEGIN
    ATOMIC WITH (transaction isolation level = snapshot,  language = N'English')

    UPDATE xtp.Product
    SET Data = JSON_MODIFY(Data, @Property, @Value)
    WHERE ProductID = @ProductId;

END
```

## <a name="next-steps"></a>次の手順
インメモリの OLTP のネイティブ モジュールの JSON は、SQL Server と Azure SQL Database で使用できる組み込みの JSON 機能のパフォーマンスを改善します。

JSON を使用する主なシナリオについては、次の資料を参照してください。

-   [TechNet のブログ](https://blogs.technet.microsoft.com/dataplatforminsider/2016/01/05/json-in-sql-server-2016-part-1-of-4/)
-   [MSDN のドキュメント](https://msdn.microsoft.com/library/dn921897.aspx)
-   [Channel 9 のビデオ](https://channel9.msdn.com/Shows/Data-Exposed/SQL-Server-2016-and-JSON-Support)

JSON をアプリケーションに組み込むさまざまなシナリオについては、次の資料を参照してください。
-   デモは、[Channel 9 のビデオ](https://channel9.msdn.com/Events/DataDriven/SQLServer2016/JSON-as-a-bridge-betwen-NoSQL-and-relational-worlds)でご確認ください。
-   ユース ケースに合うシナリオは、[JSON のブログの投稿記事](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/)でご確認ください。
-   例については、[GitHub リポジトリ](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/json/)でご確認ください。


