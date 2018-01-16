---
title: "SQL Server または SQL Database に JSON ドキュメントを保存する | Microsoft Docs"
ms.description: This article describes why and how to store and index JSON documents in SQL Server or SQL Database, and how to optimize queries over the JSON documents.
ms.custom: 
ms.date: 01/04/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: json
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-json
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 26aed92ee48c2dfd13605a9b830d1b33b4fd7f66
ms.sourcegitcommit: 4aeedbb88c60a4b035a49754eff48128714ad290
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/05/2018
---
# <a name="store-json-documents-in-sql-server-or-sql-database"></a>SQL Server または SQL Database に JSON ドキュメントを保存する
SQL Server と Azure SQL Database には、ネイティブ JSON 機能があります。標準 SQL 言語を利用し、JSON ドキュメントを解析できます。 SQL Server または SQL Database に JSON ドキュメントを保存したり、NoSQL データベースの場合のように JSON データを問い合わせたりできます。 この記事では、SQL Server または SQL Database に JSON ドキュメントを保存するためのオプションについて説明します。

## <a name="classic-tables"></a>クラシック テーブル

SQL Server または SQL Database に JSON ドキュメントを保存する最も簡単な方法は、ドキュメントの ID とドキュメントのコンテンツが含まれる単純な 2 列のテーブルを作成することです。 例 :

```sql
create table WebSite.Logs (
    _id bigint primary key identity,
    log nvarchar(max)
);
```

この構造は、クラシック ドキュメント データベースで見られるコレクションと同じです。 プライマリ キー `_id` は自動的に増分される値であり、あらゆるドキュメントに一意の ID を与え、短時間の検索を可能にします。 ID でドキュメントを検索したり、保存されているドキュメントを ID 別に更新したりする、従来の NoSQL シナリオには、この構造が最適です。

データ型 nvarchar(max) では、サイズが最大 2GB の JSON ドキュメントを保存できます。 ただし、JSON ドキュメントが間違いなく 8KB を超えない場合、パフォーマンス上の理由から、NVARCHAR(max) ではなく NVARCHAR(4000) を利用することをお勧めします。

先の例で作成したサンプル テーブルでは、有効な JSON ドキュメントが `log` 列に保存されているものと想定しています。 有効な JSON が `log` 列に間違いなく保存されている場合、その列で CHECK 制約を追加できます。 例 :

```sql
ALTER TABLE WebSite.Logs
    ADD CONSTRAINT \[Log record should be formatted as JSON\]
                   CHECK (ISJSON(log)=1)
```

誰かがテーブルにドキュメントを挿入したり、テーブルのドキュメントを更新したりするたびに、JSON ドキュメントが正しく書式設定されていることがこの制約により検証されます。 制約がないとき、テーブルは挿入のために最適化されます。JSON ドキュメントは何の処理もなく列に直接追加されるためです。

テーブルに JSON ドキュメントを保存するとき、標準の Transact-SQL 言語を使用し、ドキュメントにクエリを実行できます。 例 :

```sql
SELECT TOP 100 JSON\_VALUE(log, ‘$.severity’), AVG( CAST( JSON\_VALUE(log,’$.duration’) as float))
 FROM WebSite.Logs
 WHERE CAST( JSON_VALUE(log,’$.date’) as datetime) > @datetime
 GROUP BY JSON_VALUE(log, ‘$.severity’)
 HAVING AVG( CAST( JSON_VALUE(log,’$.duration’) as float) ) > 100
 ORDER BY CAST( JSON_VALUE(log,’$.duration’) as float) ) DESC
```

*あらゆる* T-SQL 関数とクエリ句を利用して JSON ドキュメントにクエリを実行できることは大きな利点です。 SQL Server と SQL Database のクエリには、JSON ドキュメントの分析に利用できる制約がありません。 `JSON_VALUE` 関数で JSON ドキュメントから値を抽出し、それを他の値と同様にクエリで利用できます。

これが SQL Server および SQL Database と従来の NoSQL データベースの大きな違いです。Transact-SQL では、ほとんどの場合、JSON データの処理に必要な関数がありません。

## <a name="indexes"></a>インデックス

クエリを実行する際、一部のプロパティでドキュメントが検索されることがよくある場合 (JSON ドキュメントの `severity` プロパティなど)、そのプロパティに従来の NONCLUSTERED インデックスを追加し、クエリを速めることができます。

指定のパスで (つまり、パス `$.severity` で) JSON 列から JSON 値を公開する計算列を作成し、この計算列で標準インデックスを作成できます。 例 :

```sql
create table WebSite.Logs (
    _id bigint primary key identity,
    log nvarchar(max),

    severity AS JSON_VALUE(log, '$.severity'),
    index ix_severity (severity)
);
```

この例で使用されている計算列は永続ではない列または仮想の列であり、テーブルにスペースを追加しません。 インデックス `ix_severity` で使用され、次の例のようなクエリのパフォーマンスを改善します。

```sql
SELECT log
FROM Website.Logs
WHERE JSON_VALUE(log, '$.severity') = 'P4'
```

このインデックスの重要な特性の 1 つは、それが照合順序対応であることです。 元の NVARCHAR 列に COLLATION プロパティがある場合 (大文字小文字の区別や日本語など)、インデックスは言語ルールまたは NVARCHAR 列に関連付けられている大文字小文字の区別ルールに基づいて整理されます。 JSON ドキュメントの処理時にカスタムの言語ルールを使用する必要があるアプリケーションを世界市場向けに開発する場合、これは重要な機能かもしれません。

## <a name="large-tables--columnstore-format"></a>大きなテーブルと列ストア形式

コレクションに大量の JSON ドキュメントが予想される場合、コレクションに CLUSTERED COLUMNSTORE インデックスを追加することをお勧めします。次の例をご覧ください。

```sql
create sequence WebSite.LogID as bigint;
go
create table WebSite.Logs (
    _id bigint default(next value for WebSite.LogID),
    log nvarchar(max),

    INDEX cci CLUSTERED COLUMNSTORE
);
```

CLUSTERED COLUMNSTORE インデックスはデータの圧縮率が高く (最大 25x)、ストレージの領域要件を大幅に減らし、ストレージ コストを下げ、ワークロードの I/O パフォーマンスを増やします。 また、CLUSTERED COLUMNSTORE インデックスは JSON ドキュメントのテーブル スキャンと分析のために最適化されます。ログ分析には最適な選択肢かもしれません。

先の例ではシーケンス オブジェクトを利用し、値を `_id` 列に割り当てています。 ID 列では、シーケンスと ID はいずれも有効なオプションです。

## <a name="frequently-changing-documents--memory-optimized-tables"></a>頻繁に変更されるドキュメントとメモリ最適化テーブル

コレクションに頻繁な更新、挿入、削除が予想される場合、メモリ最適化テーブルに JSON ドキュメントを保存できます。 メモリ最適化 JSON コレクションでは、データが常にメモリ内に保持されます。そのため、ストレージの I/O オーバーヘッドがありません。 また、メモリ最適化 JSON コレクションにはロック制御がまったくありません。つまり、ドキュメントを操作したとき、他の操作がブロックされることはありません。

クラシック コレクションをメモリ最適化コレクションに変換しなければならない場合、テーブル定義の後に、 **(memory_optimized=on)** を指定します。次の例をご覧ください。 これで JSON コレクションがメモリ最適化されます。

```sql
create table WebSite.Logs (
  _id bigint identity primary key nonclustered,
  log nvarchar(4000)
) with (memory_optimized=on)
```

メモリ最適化テーブルは、頻繁に変更するドキュメントに最適な選択肢です。 メモリ最適化テーブルの利用を検討するとき、パフォーマンスについても考慮してください。 メモリ最適化コレクションでは、可能であれば、JSON ドキュメントに NVARCHAR(max) ではなく NVARCHAR(4000) を使用してください。パフォーマンスが劇的に改善されることがあります。

クラシック テーブルの場合と同様に、計算列を利用し、メモリ最適化テーブルで公開するフィールドでインデックスを追加できます。 例 :

```sql
create table WebSite.Logs (

  _id bigint identity primary key nonclustered,
  log nvarchar(4000),

  severity AS cast(JSON_VALUE(log, '$.severity') as tinyint) persisted,
  index ix_severity (severity)

) with (memory_optimized=on)
```

パフォーマンスを最大化するために、プロパティの値を保持できるよう、JSON 値をできるだけ小さい型にキャスト変換します。 先の例では、**tinyint** が使用されていました。

また、ストアド プロシージャに JSON ドキュメントを更新する SQL クエリを置き、ネイティブ コンパイルの利点を活かすことができます。 例 :

```sql
CREATE PROCEDURE WebSite.UpdateData(@Id int, @Property nvarchar(100), @Value nvarchar(100))
WITH SCHEMABINDING, NATIVE_COMPILATION

AS BEGIN
    ATOMIC WITH (transaction isolation level = snapshot,  language = N'English')

    UPDATE WebSite.Logs
    SET log = JSON_MODIFY(log, @Property, @Value)
    WHERE _id = @Id;

END
```

ネイティブ コンパイルされたこのプロシージャはクエリを受け取り、それを実行する .DLL コードを作成します。 これでデータのクエリ実行と更新が速くなります。

## <a name="conclusion"></a>まとめ

SQL Server と SQL Database でネイティブ JSON 関数を利用すると、NoSQL データベースの場合と同様に JSON ドキュメントを処理できます。 リレーショナルであれ、NoSQL であれ、JSON データの処理に関しては、あらゆるデータベースに良し悪しがあります。 SQL Server または SQL Database に JSON ドキュメントを保存することの主な利点は SQL 言語の完全サポートにあります。 充実した Transact-SQL 言語を利用し、さまざまストレージ オプションを構成できます (圧縮率の高い列ストア インデックス、高速の分析によるロックのない処理を可能にするメモリ最適化テーブルなど)。 同時に、発展したセキュリティ機能や国際化機能が与えられ、NoSQL シナリオで再利用できます。 これは SQL Server または SQL Database に JSON ドキュメントを保存する十分な理由となります。

## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>SQL Server に組み込まれている JSON サポートの詳細情報  
多くの具体的なソリューション、ユース ケース、推奨事項については、Microsoft のプログラム マネージャー Jovan Popovic による SQL Server および Azure SQL Database に[組み込まれている JSON のサポートに関するブログ投稿](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/)をご覧ください。
