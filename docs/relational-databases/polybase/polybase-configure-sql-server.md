---
title: SQL Server 上の外部データにアクセスするための PolyBase の構成 | Microsoft Docs
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
ms.openlocfilehash: 4729d78f0cfecf80f65dbff0f7bc2d6abe2ebbfa
ms.sourcegitcommit: 8dccf20d48e8db8fe136c4de6b0a0b408191586b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/09/2018
ms.locfileid: "48874260"
---
# <a name="configure-polybase-to-access-external-data-in-sql-server"></a>SQL Server 上の外部データにアクセスするための PolyBase の構成

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、SQL Server インスタンス上で PolyBase を使用して、別の SQL Server インスタンス上の外部データに対してクエリを実行する方法について説明します。

## <a name="prerequisites"></a>Prerequisites

PolyBase をインストールしていない場合は、「[PolyBase のインストール](polybase-installation.md)」をご覧ください。 インストールに関する記事では、前提条件について説明します。

## <a name="configure-an-external-table"></a>外部テーブルの構成

SQL Server データ ソースのデータに対してクエリを実行するには、外部テーブルを作成して外部データを参照する必要があります。 このセクションでは、これらの外部テーブルを作成するサンプル コードを示します。 
 
クエリのパフォーマンスを最適にするために、外部テーブルの列、特に結合、フィルター、集計に使用される列に対して統計を作成することをお勧めします。

このセクションでは、次のオブジェクトを作成します。

- データベース スコープ ベースの資格情報 (TRANSACT-SQL) の作成します。 
- 外部データ ソース (TRANSACT-SQL) を作成します。 
- 外部テーブル (TRANSACT-SQL) を作成します。 
- CREATE STATISTICS (Transact-SQL)。

1. データベースにマスター キーを作成します。 これは、資格情報シークレットの暗号化に必要です。

     ```sql
      CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'S0me!nfo';  
     ```

1. データベース スコープ資格情報を作成します。

     ```sql
     /*  specify credentials to external data source
     *  IDENTITY: user name for external source.  
     *  SECRET: password for external source.
     */
     CREATE DATABASE SCOPED CREDENTIAL SqlServerCredentials   
     WITH IDENTITY = 'username', Secret = 'password';
     ```

1. [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md) を使用して外部データ ソースを作成します。外部データ ソースの場所と SQL Server の資格情報を指定します。

     ```sql
    /*  LOCATION: Location string should be of format '<vendor>://<server>[:<port>]'.
    *  PUSHDOWN: specify whether computation should be pushed down to the source. ON by default.
    *  CREDENTIAL: the database scoped credential, created above.
    */  
    CREATE EXTERNAL DATA SOURCE SQLServerInstance
    WITH ( 
    LOCATION = sqlserver://SqlServer,
    -- PUSHDOWN = ON | OFF,
      CREDENTIAL = TeradataCredentials
    );

     ```

1. 外部データのスキーマを作成します

     ```sql
     CREATE SCHEMA sqlserver;
     GO
     ```

1.  [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md) を使用して、外部の SQL Server に格納されているデータを表す外部テーブルを作成します。
 
     ```sql
     /*  LOCATION: sql server table/view in 'database_name.schema_name.object_name' format
     *  DATA_SOURCE: the external data source, created above.
     */
     CREATE EXTERNAL TABLE sqlserver.customer(
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
      LOCATION='tpch_10.dbo.customer',
      DATA_SOURCE=SqlServerInstance
     );
      ```

1. 外部テーブルに対する統計を作成します。

     ```sql
      CREATE STATISTICS CustomerCustKeyStatistics ON sqlserver.customer (C_CUSTKEY) WITH FULLSCAN; 
     ```

## <a name="next-steps"></a>次の手順

PolyBase について詳しくは、[SQL Server PolyBase の概要](polybase-guide.md)に関する記事をご覧ください。
