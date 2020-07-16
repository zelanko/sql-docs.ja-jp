---
title: 外部データへのアクセス:ODBC ジェネリック型 - PolyBase
description: SQL Server で PolyBase を使用すると、ODBC コネクタから互換性のあるデータ ソースに接続できます。 ODBC ドライバーをインストールし、外部テーブルを作成します。
ms.date: 02/19/2020
ms.custom: seo-lt-2019
ms.prod: sql
ms.technology: polybase
ms.topic: conceptual
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mikeray
monikerRange: '>= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions'
ms.openlocfilehash: ab118c18b2656701470a22b6987a659b45f2fdc7
ms.sourcegitcommit: d1535944bff3f2580070cc036ece30f1d43ee2ce
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2020
ms.locfileid: "86406115"
---
# <a name="configure-polybase-to-access-external-data-in-sql-server"></a>SQL Server 上の外部データにアクセスするための PolyBase の構成

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

SQL Server 2019 で PolyBase を使用すると、ODBC コネクタから ODBC と互換性のあるデータ ソースに接続できます。

この記事では、ODBC ドライバーの使用例をいくつか示します。 特定の例については、ODBC プロバイダーにお問い合わせください。 適切な接続文字列のオプションを決定するには、データ ソースの ODBC ドライバーに関するドキュメントを参照してください。 この記事の例は、特定の ODBC ドライバーには適用されない場合があります。

## <a name="prerequisites"></a>前提条件

>[!NOTE]
>この機能を使用するには、SQL Server on Windows が必要です。

* [PolyBase のインストール](polybase-installation.md)。

* データベース スコープ資格情報より前に、[マスター キー](../../t-sql/statements/create-master-key-transact-sql.md)を作成しておく必要があります。

## <a name="install-the-odbc-driver"></a>ODBC ドライバーをインストールする

まず、各 PolyBase ノードで、接続するデータ ソースの ODBC ドライバーをダウンロードしてインストールします。 ドライバーが適切にインストールされたら、 **[ODBC データ ソースの管理者]** からドライバーを表示してテストできます。

![PolyBase スケールアウト グループ](../../relational-databases/polybase/media/polybase-odbc-admin.png) 

上の例で、赤色の円で囲んでいるのがドライバーの名前です。 外部データ ソースを作成するときに、この名前を使用します。

> [!IMPORTANT]
> クエリのパフォーマンスを向上させるために、接続プールを有効にします。 この操作は、 **[ODBC データ ソースの管理者]** から実行できます。

## <a name="create-an-external-table"></a>外部テーブルを作成する

ODBC データ ソースのデータに対してクエリを実行するには、外部テーブルを作成して外部データを参照する必要があります。 このセクションでは、外部テーブルを作成するサンプル コードを示します。

このセクションでは以下の Transact-SQL コマンドが使用されます。

* [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)
* [CREATE EXTERNAL DATA SOURCE (Transact-SQL)](../../t-sql/statements/create-external-data-source-transact-sql.md) 
* [CREATE STATISTICS (Transact-SQL)](../../t-sql/statements/create-statistics-transact-sql.md)

1. ODBC ソースにアクセスするために、データベース スコープ資格情報を作成します。

    ```sql
    CREATE DATABASE SCOPED CREDENTIAL <credential_name> WITH IDENTITY = '<username>', Secret = '<password>';
    ```

    たとえば、次の例では、`username` という ID と複雑なパスワードを使用して、`credential_name` という名前の資格情報を作成します。

    ```sql
    CREATE DATABASE SCOPED CREDENTIAL credential_name WITH IDENTITY = 'username', Secret = 'BycA4ZjrE#*2W%!';
    ```

1. [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md) を使用して外部データ ソースを作成します。

    ```sql
    CREATE EXTERNAL DATA SOURCE <external_data_source_name>
    WITH ( LOCATION = 'odbc://<ODBC server address>[:<port>]',
    CONNECTION_OPTIONS = 'Driver={<Name of Installed Driver>};
    ServerNode = <name of server  address>:<Port>',
    -- PUSHDOWN = [ON] | OFF,
    CREDENTIAL = <credential_name> );
    ```

    次の例では、以下の条件で外部データ ソースを作成します。
    * `external_data_source_name` という名前
    * ODBC `SERVERNAME` およびポート `4444`に配置する
    * `CData ODBC Driver For SAP 2015` に接続する - これは、「[ODBC ドライバーをインストールする](#install-the-odbc-driver)」で作成したドライバーです。
    * `ServerNode``sap_server_node` のポート `5555`
    * サーバーへのプッシュ ダウンを処理できるように構成する (`PUSHDOWN = ON`)
    * 資格情報 `credential_name` を使用する

    ```sql
    CREATE EXTERNAL DATA SOURCE external_data_source_name
    WITH ( LOCATION = 'odbc://SERVERNAME:4444',
    CONNECTION_OPTIONS = 'Driver={CData ODBC Driver For SAP 2015};
    ServerNode = sap_server_node:5555',
    PUSHDOWN = ON,
    CREDENTIAL = credential_name );
    ```

1. **省略可能:** 外部テーブルの統計を作成します。

    クエリのパフォーマンスを最適化するには、外部テーブルの列、特に結合、フィルター、集計に使用される列に統計を作成することをお勧めします。

    ```sql
    CREATE STATISTICS statistics_name ON customer (C_CUSTKEY) WITH FULLSCAN; 
    ```

>[!IMPORTANT]
>外部データ ソースを作成したら、[CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md) コマンドを使用して、そのソース上でクエリ可能なテーブルを作成します。

## <a name="next-steps"></a>次のステップ

PolyBase の詳細については、[SQL Server PolyBase の概要](polybase-guide.md)に関する記事をご覧ください。
