---
title: ODBC ジェネリック型の外部データにアクセスするための PolyBase の構成 | Microsoft Docs
ms.custom: ''
ms.date: 10/16/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: polybase
ms.topic: conceptual
author: Abiola
ms.author: aboke
manager: craigg
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 414c9650a1ae933e6e472ab09a26e6d26ae503fd
ms.sourcegitcommit: 70e47a008b713ea30182aa22b575b5484375b041
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49947420"
---
# <a name="configure-polybase-to-access-external-data-in-sql-server"></a>SQL Server 上の外部データにアクセスするための PolyBase の構成

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server 2019 で PolyBase を使用すると、ODBC コネクタから ODBC と互換性のあるデータ ソースに接続できます。 

## <a name="prerequisites"></a>Prerequisites

"=" 機能は Windows 上の SQL Server でのみ機能することに注意してください。 

PolyBase をインストールしていない場合は、「[PolyBase のインストール](polybase-installation.md)」をご覧ください。

まず、それぞれの PolyBase ノードで接続するデータ ソースの ODBC ドライバーをダウンロードしてインストールします。 ドライバーが適切にインストールされたら、[ODBC データ ソースの管理者] からドライバーを表示してテストできます。

![PolyBase スケールアウト グループ](../../relational-databases/polybase/media/polybase-odbc-admin.png) 

  > **重要:**
  >
  > クエリのパフォーマンスを向上させるために、ドライバーで接続プールを有効にしていることを確認します。 この操作は [ODBC データ ソースの管理者] から実現できます。

> **注**
> 
>ドライバーの名前 (上記の囲まれた例) は、外部データ ソースの作成時 (以下の手順 3) に指定する必要がります。

## <a name="create-an-external-table"></a>外部テーブルの作成

ODBC データ ソースのデータに対してクエリを実行するには、外部テーブルを作成して外部データを参照する必要があります。 このセクションでは、外部テーブルを作成するサンプル コードを示します。

このセクションでは、次のオブジェクトが作成されます。

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

1. ODBC データ ソースにアクセスするために、データベースを対象とする資格情報を作成します。

     ```sql
     /*  specify credentials to external data source
     *  IDENTITY: user name for external source.  
     *  SECRET: password for external source.
     */
     CREATE DATABASE SCOPED CREDENTIAL credential_name
     WITH IDENTITY = 'username', Secret = 'password';
     ```

1. [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md) を使用して外部データ ソースを作成します。

     ```sql
    /*  LOCATION: Location string should be of format '<type>://<server>[:<port>]'.
    *  PUSHDOWN: specify whether computation should be pushed down to the source. ON by default.
    *CONNECTION_OPTIONS: Specify driver location
    *  CREDENTIAL: the database scoped credential, created above.
    */  
    CREATE EXTERNAL DATA SOURCE external_data_source_name
    WITH ( 
    LOCATION = odbc://<ODBC server address>[:<port>],
    CONNECTION_OPTIONS = 'SSL=0;sslAllowInvalidCertificates=1;Driver={<Name of Installed Driver>};HOST=%s;AUTHMECH=0',
    -- PUSHDOWN = ON | OFF,
      CREDENTIAL = credential_name
    );

     ```


1.  [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md) を使用して、外部データ ソースのデータを表す外部テーブルを作成します。
 
     ```sql
     /*  LOCATION: ODBC data source table/view
     *  DATA_SOURCE: the external data source, created above.
     */
     CREATE EXTERNAL TABLE customer(
     C_CUSTKEY INT NOT NULL,
     C_NAME VARCHAR(25) NOT NULL,
     C_ADDRESS VARCHAR(40) NOT NULL,
     C_NATIONKEY INT NOT NULL,
     C_PHONE CHAR(15) NOT NULL,
     C_ACCTBAL DECIMAL(15,2) NOT NULL,
     C_MKTSEGMENT CHAR(10) NOT NULL,
     C_COMMENT VARCHAR(117) NOT NULL
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

## <a name="next-steps"></a>次の手順

PolyBase の詳細については、[SQL Server PolyBase の概要](polybase-guide.md)に関する記事をご覧ください。
