---
title: MongoDB 上の外部データにアクセスするための PolyBase の構成 | Microsoft Docs
ms.custom: ''
ms.date: 09/24/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: polybase
ms.topic: conceptual
author: Abiola
ms.author: aboke
manager: craigg
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 68fb5c69d30e9ba30f27bcd23347ed5543c7e792
ms.sourcegitcommit: f62f70298651d6223fa5d215b6a7a0d2ffecbd0d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/19/2018
ms.locfileid: "51947587"
---
# <a name="configure-polybase-to-access-external-data-in-mongodb"></a>MongoDB 上の外部データにアクセスするための PolyBase の構成

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、SQL Server インスタンス上で PolyBase を使用して、MongoDB 上の外部データに対してクエリを実行する方法について説明します。

## <a name="prerequisites"></a>Prerequisites

PolyBase をインストールしていない場合は、「[PolyBase のインストール](polybase-installation.md)」をご覧ください。

## <a name="configure-an-external-table"></a>外部テーブルの構成

MongoDB データ ソースのデータに対してクエリを実行するには、外部テーブルを作成して外部データを参照する必要があります。 このセクションでは、これらの外部テーブルを作成するサンプル コードを示します。

このセクションでは、次のオブジェクトを作成します。

- データベース スコープ ベースの資格情報 (TRANSACT-SQL) の作成します。
- 外部データ ソース (TRANSACT-SQL) を作成します。
- 外部テーブル (TRANSACT-SQL) を作成します。
- CREATE STATISTICS (Transact-SQL)

1. まだ存在しない場合は、データベースにマスター キーを作成します。 これは、資格情報のシークレットの暗号化に必須です。

     ```sql
      CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'password';  
     ```
    ## <a name="arguments"></a>引数
    PASSWORD ='password'

    データベース内のマスター キーの暗号化に使用されているパスワードを指定します。 パスワードは、SQL Server のインスタンスをホストしている、コンピューターの Windows パスワード ポリシー要件を満たす必要があります。

1.   MongoDB ソースにアクセスするために、データベース スコープ資格情報を作成します。

     ```sql
     /*  specify credentials to external data source
     *  IDENTITY: user name for external source.  
     *  SECRET: password for external source.
     */
     CREATE DATABASE SCOPED CREDENTIAL credential_name 
     WITH IDENTITY = 'username', Secret = 'password';
     ```

1.  [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md) を使用して外部データ ソースを作成します。

     ```sql
     /*  LOCATION: Location string should be of format '<type>://<server>[:<port>]'.
    *  PUSHDOWN: specify whether computation should be pushed down to the source. ON by default.
    *CONNECTION_OPTIONS: Specify driver location
    *  CREDENTIAL: the database scoped credential, created above.
    */  
    CREATE EXTERNAL DATA SOURCE external_data_source_name
    WITH (
    LOCATION = mongodb://<server>[:<port>],
    -- PUSHDOWN = ON | OFF,
      CREDENTIAL = credential_name
    );
     ```

1.  [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md) を使用して、外部の MongoDB システムに格納されているデータを表す外部テーブルを作成します。

     ```sql
     /*  LOCATION: MongoDB table/view in '<database_name>.<schema_name>.<object_name>' format
     *  DATA_SOURCE: the external data source, created above.
     */
     CREATE EXTERNAL TABLE customers(
     [O_ORDERKEY] DECIMAL(38) NOT NULL,
     [O_CUSTKEY] DECIMAL(38) NOT NULL,
     [O_ORDERSTATUS] CHAR COLLATE Latin1_General_BIN NOT NULL,
     [O_TOTALPRICE] DECIMAL(15,2) NOT NULL,
     [O_ORDERDATE] DATETIME2(0) NOT NULL,
     [O_COMMENT] VARCHAR(79) COLLATE Latin1_General_BIN NOT NULL
     )
     WITH (
     LOCATION='customer',
     DATA_SOURCE= external_data_source_name
     );
     ```

1. **省略可能:** 外部テーブルの統計を作成します。

    最適なクエリのパフォーマンスを得るために、外部テーブルの列、特に結合、フィルター、集計に使用される列に対して統計を作成することをお勧めします。

     ```sql
      CREATE STATISTICS statistics_name ON customer (C_CUSTKEY) WITH FULLSCAN; 
     ```


## <a name="flattening"></a>フラット化
 フラット化は、MongoDB ドキュメント コレクションの入れ子になったデータと繰り返しデータに対して有効になります。 ユーザーは、入れ子になったデータや繰り返しデータを含む可能性のある MongoDB ドキュメント コレクションに対して `create an external table` を有効にし、リレーショナル スキーマを明示的に指定する必要があります。 その後のマイルストーンで、mongo ドキュメント コレクションに対する自動スキーマ検出を有効にします。
JSON の入れ子になったデータ型/繰り返しデータ型は次のようにフラット化されます

* オブジェクト: 中かっこで囲まれている順序付けられていないキー/値のコレクション (入れ子)

   - 各オブジェクト キーのテーブル列を作成します

     * 列名: objectname_keyname

* 配列: コンマで区切られ、角かっこで囲まれた、順序付けられた値 (繰り返し)

   - 配列項目ごとに新しいテーブル行を追加します

   - 配列ごとの列を作成して配列項目のインデックスを格納します

     * 列名: arrayname_index

     * データ型: bigint

この手法にはいくつかの潜在的な問題があります。そのうちの 2 つを次に示します。

* 空の繰り返しフィールドは、同じレコードのフラット フィールドに含まれるデータを事実上マスクする

* 複数の繰り返しフィールドが存在すると、生成される行数が急増することがある

たとえば、非リレーショナルの JSON 形式で格納されている MongoDB のサンプル データセット レストラン コレクションを評価します。 各レストランには、入れ子になった住所フィールドと、異なる日に割り当てられた採点の配列があります。 次の図は、入れ子になった住所と入れ子になった繰り返しの採点がある一般的なレストランを示しています。

![MongoDB のフラット化](../../relational-databases/polybase/media/mongo-flattening.png "MongoDB レストランのフラット化")

住所オブジェクトは次のようにフラット化されます。

* Nested field restaurant.address.building becomes restaurant.address_building
* Nested field restaurant.address.coord becomes restaurant.address_coord
* Nested field restaurant.address.street becomes restaurant.address_street
* Nested field restaurant.address.zipcode becomes restaurant.address_zipcode

採点配列は次のようにフラット化されます。
| grades_date | grades_grade  | games_score | 
| ------------- | ------------------------- | -------------- |
|1393804800000 |A |2|
|1378857600000|A |6|
|135898560000 |A |10|
|1322006400000|A |9|
|1299715200000 |B |14|

## <a name="cosmos-db-connection"></a>Cosmos DB 接続

Cosmos DB の Mongo API および Mongo DB PolyBase コネクタを使用すると、**Cosmos DB インスタンス**の外部テーブルを作成することができます。 これは、上記と同じ手順に従って行います。 データベースのスコープ資格情報、サーバーのアドレス、ポート、場所の文字列が Cosmos DB サーバーのものを反映していることを確認してください。 

## <a name="next-steps"></a>次の手順

PolyBase の詳細については、[SQL Server PolyBase の概要](polybase-guide.md)に関する記事をご覧ください。
