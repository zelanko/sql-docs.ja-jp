---
title: Oracle 上の外部データにアクセスするための PolyBase の構成 | Microsoft Docs
ms.custom: ''
ms.date: 04/10/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: polybase
ms.topic: conceptual
author: Abiola
ms.author: aboke
manager: craigg
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 4a7484acf7a63b5c2a6804e1f3f7914cabaf8524
ms.sourcegitcommit: 57f7e5f25161dbb4cc446e751ea74b1ac5f86165
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2019
ms.locfileid: "59476647"
---
# <a name="configure-polybase-to-access-external-data-in-oracle"></a>Oracle 上の外部データにアクセスするための PolyBase の構成

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、SQL Server インスタンス上で PolyBase を使用して、Oracle 上の外部データに対してクエリを実行する方法について説明します。

## <a name="prerequisites"></a>Prerequisites

PolyBase をインストールしていない場合は、「[PolyBase のインストール](polybase-installation.md)」をご覧ください。

## <a name="configure-an-external-table"></a>外部テーブルの構成

Oracle データ ソースのデータに対してクエリを実行するには、外部テーブルを作成して外部データを参照する必要があります。 このセクションでは、これらの外部テーブルを作成するサンプル コードを示します。 
 
このセクションでは以下の Transact-SQL コマンドが使用されます。

- [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)
- [CREATE EXTERNAL DATA SOURCE (Transact-SQL)](../../t-sql/statements/create-external-data-source-transact-sql.md) 
- [CREATE EXTERNAL TABLE (Transact-SQL)](../../t-sql/statements/create-external-table-transact-sql.md) 
- [CREATE STATISTICS (Transact-SQL)](../../t-sql/statements/create-statistics-transact-sql.md)

1. まだ存在しない場合は、データベースにマスター キーを作成します。 これは、資格情報のシークレットの暗号化に必須です。

   ```sql
   CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'password';  
   ```

   > [!NOTE]
   > `PASSWORD` ではデータベース内のマスター キーの暗号化に使用されているパスワードを指定します。 これは、SQL Server のインスタンスをホストしている、コンピューターの Windows パスワード ポリシー要件を満たす必要があります。

1. データベース スコープ資格情報を作成します。

   ```sql
   /*  
   * Specify credentials to external data source
   * IDENTITY: user name for external source.  
   * SECRET: password for external source.
   */
   CREATE DATABASE SCOPED CREDENTIAL credential_name
   WITH IDENTITY = 'username', Secret = 'password';
   ```

1. [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md) を使用して外部データ ソースを作成します。 外部データ ソースの場所と、Oracle データ ソースの資格情報を指定します。

   ```sql
   /* 
   * LOCATION: Location string should be of format '<vendor>://<server>[:<port>]'.
   * PUSHDOWN: specify whether computation should be pushed down to the source. ON by default.
   * CONNECTION_OPTIONS: Specify driver location
   * CREDENTIAL: the database scoped credential, created above.
   */  
   CREATE EXTERNAL DATA SOURCE external_data_source_name
   WITH ( 
     LOCATION = 'oracle://<server address>[:<port>]',
     -- PUSHDOWN = ON | OFF,
     CREDENTIAL = credential_name)
   ```

1. [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md) を使用して、外部の Oracle システムに格納されているデータを表す外部テーブルを作成します。

   ```sql
   /*
   * LOCATION: Oracle table/view in '<database_name>.<schema_name>.<object_name>' format
   * DATA_SOURCE: the external data source, created above.
   */
   CREATE EXTERNAL TABLE customers(
   [O_ORDERKEY] DECIMAL(38) NOT NULL,
   [O_CUSTKEY] DECIMAL(38) NOT NULL,
   [O_ORDERSTATUS] CHAR COLLATE Latin1_General_BIN NOT NULL,
   [O_TOTALPRICE] DECIMAL(15,2) NOT NULL,
   [O_ORDERDATE] DATETIME2(0) NOT NULL,
   [O_ORDERPRIORITY] CHAR(15) COLLATE Latin1_General_BIN NOT NULL,
   [O_CLERK] CHAR(15) COLLATE Latin1_General_BIN NOT NULL,
   [O_SHIPPRIORITY] DECIMAL(38) NOT NULL,
   [O_COMMENT] VARCHAR(79) COLLATE Latin1_General_BIN NOT NULL
   )
   WITH (
    LOCATION='customer',
    DATA_SOURCE=  external_data_source_name
   );
   ```

1. **省略可能:** 次のコマンドを使用して、外部テーブルに統計を作成します。

   ```sql
   CREATE STATISTICS statistics_name ON customer (C_CUSTKEY) WITH FULLSCAN; 
   ```

   > [!TIP]
   > 外部テーブルの列、特に結合、フィルター、集計に使用される列に対して統計を作成することをお勧めします。 これにより、最適なクエリ パフォーマンスが得られます。

## <a name="next-steps"></a>次の手順

PolyBase の詳細については、[SQL Server PolyBase の概要](polybase-guide.md)に関する記事をご覧ください。
