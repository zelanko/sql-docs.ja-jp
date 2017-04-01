---
title: "メモリ最適化テーブルのインデックス | Microsoft Docs"
ms.custom: 
  - "MSDN content"
  - "MSDN - SQL DB"
ms.date: "10/24/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.service: "sql-database"
ms.suite: ""
ms.technology: 
  - "database-engine-imoltp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eecc5821-152b-4ed5-888f-7c0e6beffed9
caps.latest.revision: 14
author: "MightyPen"
ms.author: "genemi"
manager: "jhubbard"
caps.handback.revision: 14
---
# メモリ最適化テーブルのインデックス
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  
この記事では、メモリ最適化テーブルで利用可能なインデックスの種類について説明します。 記事の内容は次のとおりです。  
  
- Transact-SQL 構文を説明する短いコード例を示します。  
- メモリ最適化インデックスと従来のディスク ベース インデックスの違いについて説明します。  
- 各種のメモリ最適化インデックスが最適な状況について説明します。  
  
  
*ハッシュ* インデックスについては、[密接に関連する記事](../../relational-databases/in-memory-oltp/hash-indexes-for-memory-optimized-tables.md) で詳細を説明します。  
  
  
*列ストア* インデックスについては、[別の記事](Columnstore%20Indexes%20Guide.xml) で説明します。  
  
  
## A. メモリ最適化インデックスの構文  
  
メモリ最適化テーブルの各 CREATE TABLE ステートメントには、インデックスを宣言する 1 つから 8 つの句を含める必要があります。 インデックスは、次のいずれかにする必要があります。  
  
- ハッシュ インデックス。  
- 非クラスター化インデックス (B ツリーの既定の内部構造を意味します)。  
  
  
既定の DURABILITY = SCHEMA_AND_DATA で宣言するには、メモリ最適化テーブルが主キーを持つ必要があります。 次の CREATE TABLE ステートメントの PRIMARY KEY NONCLUSTERED 句は、2 つの要件を満たします。  
  
- CREATE TABLE ステートメントの 1 つのインデックスの最小要件を満たすためにインデックスを提供します。  
- SCHEMA_AND_DATA 句に必要な主キーを提供します。  
  
  
  
    CREATE TABLE SupportEvent  
    (  
        SupportEventId   int NOT NULL  
            PRIMARY KEY NONCLUSTERED,  
        [...]  
    )  
        WITH (  
            MEMORY_OPTIMIZED = ON,  
            DURABILITY = SCHEMA_AND_DATA);  
  
  
  
### A.1 構文のコード例  
  
ここには、メモリ最適化テーブルのさまざまなインデックスを作成する構文を示す Transact-SQL コード ブロックが含まれています。 コードは、次の操作を示しています。  
  
  
1. メモリ最適化テーブルを作成します。  
2. ALTER TABLE ステートメントを使用して、2 つのインデックスを追加します。  
3. 数行のデータを挿入します。  
  
  
  
    DROP TABLE IF EXISTS SupportEvent;  
    go  
  
    CREATE TABLE SupportEvent  
    (  
      SupportEventId   int               not null   identity(1,1)  
        PRIMARY KEY NONCLUSTERED,  
  
      StartDateTime        datetime2     not null,  
      CustomerName         nvarchar(16)  not null,  
      SupportEngineerName  nvarchar(16)      null,  
      Priority             int               null,  
      Description          nvarchar(64)      null  
    )  
      WITH (  
        MEMORY_OPTIMIZED = ON,  
        DURABILITY = SCHEMA_AND_DATA);  
    go  
      
        --------------------  
      
    ALTER TABLE SupportEvent  
      ADD CONSTRAINT constraintUnique_SDT_CN  
        UNIQUE NONCLUSTERED (StartDateTime DESC, CustomerName);  
    go  
  
    ALTER TABLE SupportEvent  
      ADD INDEX idx_hash_SupportEngineerName  
        HASH (SupportEngineerName) WITH (BUCKET_COUNT = 64);  -- Nonunique.  
    go  
      
        --------------------  
      
    INSERT INTO SupportEvent  
        (StartDateTime, CustomerName, SupportEngineerName, Priority, Description)  
      VALUES  
        ('2016-02-25 13:40:41:123', 'Abby', 'Zeke', 2, 'Display problem.'     ),  
        ('2016-02-25 13:40:41:323', 'Ben' , null  , 1, 'Cannot find help.'    ),  
        ('2016-02-25 13:40:41:523', 'Carl', 'Liz' , 2, 'Button is gray.'      ),  
        ('2016-02-25 13:40:41:723', 'Dave', 'Zeke', 2, 'Cannot unhide column.');  
    go  
  
  
  
## B. メモリ最適化インデックスの性質  
  
メモリ最適化テーブルでは、すべてのインデックスもメモリ最適化されます。 メモリ最適化インデックスのインデックスと、ディスク ベース テーブルの従来のインデックスとはさまざまな点で違いがあります。  
  
各メモリ最適化インデックスは、アクティブ メモリにのみ存在します。 インデックスには、ディスク上の表現がありません。  
  
- メモリ最適化インデックスは、データベースがオンライに戻ったときに再構築されます。  
  
  
SQL UPDATE ステートメントでメモリ最適化テーブルのデータが変更された場合、そのインデックスへの対応する変更はログに書き込まれません。  
  
  
メモリ最適化インデックスのエントリには、テーブルの行のダイレクト メモリ アドレスが含まれます。  
  
- 対照的に、ディスク上の従来の B ツリー インデックスのエントリには、関連付けられたテーブル行のメモリ アドレスを検出するためにシステムがまず使用する必要のあるキー値が含まれます。  
  
  
メモリ最適化インデックスには、ディスク ベース インデックスが持っている固定ページはありません。  
  
- それらはページ内で断片化の従来の種類を計上しないため、fillfactor を持ちません。  
  
## C. 重複するインデックス キー値

重複するインデックス キーの値は、メモリ最適化テーブルに対する操作のパフォーマンスに影響します。 重複するチェーンはほとんどのインデックス操作についてスキャンされる必要があるため、多数の重複 (たとえば、100+) はインデックスを維持するジョブを非効率にします。 メモリ最適化テーブルでの INSERT、UPDATE、および DELETE の操作において影響が見られます。 この問題は、ハッシュ インデックスの場合、より顕著になります。これは、ハッシュ インデックスの操作あたりのコスト削減と、ハッシュ競合チェーンを持つ大規模な重複チェーンの干渉の両方に起因します。 インデックス内の重複を減らすために、非クラスター化インデックスを使用し、重複の数を減らすために (たとえば、主キーから) インデックス キーの末尾に列を追加します。

例として、主キーが CustomerId に、インデックスが CustomerCategoryID 列に設定された Customers テーブルを考えます。 通常は特定のカテゴリに顧客の多くが含まれるため、CustomerCategoryID のインデックスに含まれる特定のキーに対して多くの値が重複すると考えられます。 こうしたシナリオでは、(CustomerCategoryID, CustomerId) で非クラスター化インデックスを使用することをお勧めします。 このインデックスを使用して、CustomerCategoryID を含む述語を使用したクエリを実行できます。また重複がないため、インデックスのメンテナンスでムダが生じることはありません。

次のクエリでは、[WideWorldImporters](https://msdn.microsoft.com/library/mt734199(v=sql.1).aspx) サンプル データベースの `Sales.Customers` テーブルに含まれる `CustomerCategoryID` 上のインデックスについて、インデックス キー値の平均重複数がわかります。

```Transact-SQL
    SELECT AVG(row_count) FROM
       (SELECT COUNT(*) AS row_count 
        FROM Sales.Customers
        GROUP BY CustomerCategoryID) a
```

ご使用のテーブルとインデックスについてインデックス キーの平均重複数を調べるには、`Sales.Customers` をテーブル名、`CustomerCategoryID` をインデックス キー列のリストで置き換えてください。

## D. 各種のインデックスを使用する状況の比較  
  
  
どの種類のインデックスが最善の選択であるかは、特定のクエリの性質によって決まります。  

既存のアプリケーションでメモリ最適化テーブルを実装するときは、非クラスター化インデックスから開始することが一般的に推奨されます。その機能が、ディスクベースのテーブルにおける、従来のクラスター化インデックスおよび非クラスター化インデックスの機能により近くなるためです。 
  
  
### D.1 非クラスター化インデックスの強み  
  
  
非クラスター化インデックスは、次に該当する場合にハッシュ インデックスよりも適しています。  
  
- クエリに、インデックス付き列に対する ORDER BY 句がある。  
- 複数列インデックスの最初の列のみをテストするクエリ。  
- クエリで、次の WHERE 句を使用してインデックス付き列をテストする。  
  - 非等値: *WHERE StatusCode != 'Done'*  
  - 値の範囲: *WHERE Quantity >= 100*  
  
  
次のすべての SELECT では、ハッシュ インデックスよりも非クラスター化インデックスのほうが適しています。  
  
  
  
    SELECT col2 FROM TableA  
        WHERE StartDate > DateAdd(day, -7, GetUtcDate());  
      
    SELECT col3 FROM TableB  
        WHERE ActivityCode != 5;  
      
    SELECT StartDate, LastName  
        FROM TableC  
        ORDER BY StartDate;  
      
    SELECT IndexKeyColumn2  
        FROM TableD  
        WHERE IndexKeyColumn1 = 42;  
  
  
  
### D.2 ハッシュ インデックスの強み  
  
  
[ハッシュ インデックス](../../relational-databases/in-memory-oltp/hash-indexes-for-memory-optimized-tables.md) は、次に該当する場合に非クラスター化インデックスよりも適しています。  
  
- クエリで、次に示すように、すべてのインデックス キー列で厳密な等値を指定する WHERE 句を使用してインデックス付き列をテストします。  
  
  
  
    SELECT col9 FROM TableZ  
        WHERE Z_Id = 2174;  
  
  
  
### D.3 インデックスの強みを比較する概要表  
  
  
次の表は、異なるインデックスの種類でサポートされるすべての操作を示しています。  
  
  
| 操作 | メモリ最適化、 <br/> ハッシュ | メモリ最適化、 <br/> 非クラスター化 | ディスク ベース、 <br/> (非) クラスター化 |  
| :-------- | :--------------------------- | :----------------------------------- | :------------------------------------ |  
| インデックス スキャン、すべてのテーブルの行を取得する。 | はい | [ユーザー アカウント制御] | 可 |  
| 等値述語 (=) でのインデックス シーク。 | はい <br/> (フル キーが必要です。) | 可  | 可 |  
| 非等値述語と範囲述語でのインデックス シーク  <br/> (>, <, \<=, >=, BETWEEN)。 | いいえ <br/> (インデックス スキャンが実行される) | 可 | 可 |  
| インデックス定義と一致する行を並べ替え順序で取得する。 | いいえ | [ユーザー アカウント制御] | はい |  
| インデックス定義の反対と一致する行を並べ替え順序で取得する。 | いいえ | いいえ | 可 |  
  
  
この表では、可はインデックスが要求に十分に対応できることを意味し、不可はインデックスが要求に十分に対応できないことを意味します。  


  
  
\<!--   
Indexes_for_Memory-Optimized_Tables.md , which is....  
CAPS guid: {eecc5821-152b-4ed5-888f-7c0e6beffed9}  
mt670614.aspx  
  
Application-Level%20Partitioning.xml , {162d1392-39d2-4436-a4d9-ee5c47864c5a}  
  
/Image/hekaton_tables_23d.png , fbc511a0-304c-42f7-807d-d59f3193748f  
  
  
Replaces dn511012.aspx , which is....  
CAPS guid: {86805eeb-6972-45d8-8369-16ededc535c7}  
  
GeneMi  ,  2016-05-05  Thursday  17:25pm  (Hash content moved to new child article, e922cc3a-3d6e-453b-8d32-f4b176e98488.)  
-->  
  
  
  
