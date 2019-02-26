---
title: Excel から SQL にデータをインポートする | Microsoft Docs
ms.custom: ''
ms.date: 09/23/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: cafc8346cbdd03c99f68ec879601689a7bf90781
ms.sourcegitcommit: a13256f484eee2f52c812646cc989eb0ce6cf6aa
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/25/2019
ms.locfileid: "56802219"
---
# <a name="import-data-from-excel-to-sql-server-or-azure-sql-database"></a>Excel から SQL Server または Azure SQL Database にデータをインポートする
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

Excel ファイルからSQL Server または Azure SQL Database に、データをインポートする方法はいくつかあります。 一部の方法では、Excel ファイルから直接 1 ステップでデータをインポートできます。他の方法では、先に Excel データをテキストとしてエクスポートしてから、インポートする必要があります。 この記事では、よく使われる方法をまとめ、詳細な情報へのリンクを示します。

## <a name="list-of-methods"></a>方法の一覧

-   次のいずれかのツールを使用することで、1 つの手順で Excel から SQL にデータを直接インポートできます。
    -   [SQL Server インポートおよびエクスポート ウィザード](#wiz)
    -   [SQL Server Integration Services (SSIS)](#ssis)
    -   [OPENROWSET](#openrowset) 関数
-   Excel からデータをテキストとしてエクスポートし、次のいずれかのツールを使用してテキスト ファイルをインポートすることで、2 つの手順でデータをインポートできます。
    -   [フラット ファイルのインポート ウィザード](#import-wiz)
    -   [BULK INSERT](#bulk-insert) ステートメント
    -   [BCP](#bcp)
    -   [コピー ウィザード (Azure Data Factory)](#adf-wiz)
    -   [Azure Data Factory](#adf)

Excel ブックから複数のワークシートをインポートする場合は、通常、シートごとに 1 回これらのツールをそれぞれ実行する必要があります。

SSIS や Azure Data Factory のような複雑なツールとサービスの詳細については、このリストの範囲外です。 興味のあるソリューションの詳細については、詳細情報へのリンクを参照してください。

> [!IMPORTANT]
> Excel ファイルへの接続、および Excel から、または Excel へのデータの読み込みに関する制限事項と既知の問題については、「[Load data from or to Excel with SQL Server Integration Services (SSIS)](../../integration-services/load-data-to-from-excel-with-ssis.md)」 (SQL Server Integration Services (SSIS) を使用して Excel から、または Excel にデータを読み込む) を参照してください。

## <a name="wiz"></a> SQL Server インポートおよびエクスポート ウィザード

SQL Server インポートおよびエクスポート ウィザードのページをステップ実行して、Excel ファイルから直接データをインポートします。 必要に応じて、後でカスタマイズして再利用できる SQL Server Integration Services (SSIS) パッケージとして設定を保存します。

ウィザードを起動する方法については、「[SQL Server インポートおよびエクスポート ウィザードを起動する](../../integration-services/import-export-data/start-the-sql-server-import-and-export-wizard.md)」を参照してください。

ウィザードを使用して Excel から SQL Server にインポートする例については、「[Get started with this simple example of the Import and Export Wizard (インポートおよびエクスポート ウィザードのこの簡単な例から始める)](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md)」を参照してください。

![Excel データ ソースに接続する](media/excel-connection.png)

## <a name="ssis"></a> SQL Server Integration Services (SSIS)

SSIS に精通していて、SQL Server インポートおよびエクスポート ウィザードを実行したくない場合は、Excel ソースおよびデータ フロー内の SQL Server 変換先を使用する SSIS パッケージを作成します。

これらの SSIS コンポーネントの詳細については、次のトピックを参照してください。
-   [Excel ソース](../../integration-services/data-flow/excel-source.md)
-   [SQL Server 変換先](../../integration-services/data-flow/sql-server-destination.md)

SSIS パッケージをビルドする方法の学習を開始するには、チュートリアル「[How to Create an ETL Package (ETL パッケージを作成する方法)](../../integration-services/ssis-how-to-create-an-etl-package.md)」を参照してください。

![データ フロー内のコンポーネント](media/excel-to-sql-data-flow.png)

## <a name="openrowset"></a>OPENROWSET およびリンク サーバー

> [!NOTE]
> Azure では、OPENROWSET および OPENDATASOURCE 関数は SQL Database Managed Instance でのみ使用できます。

> [!NOTE]
> Excel データ ソースに接続する ACE プロバイダー (旧称 Jet プロバイダー) は、対話型のクライアント側での使用を対象としています。 特に自動化されたプロセスまたは並列で実行中のプロセスで、サーバー上の ACE プロバイダーを使用すると、予期しない結果になることがあります。

### <a name="distributed-queries"></a>分散クエリ

Transact-SQL `OPENROWSET` または `OPENDATASOURCE` 関数を使用して、Excel ファイルから直接データをインポートします。 このような使用方法は、*"分散クエリ"* と呼ばれます。

分散クエリを実行する前に、次の例で示すように、`ad hoc distributed queries` サーバー構成オプションを有効にする必要があります。 詳しくは、「[ad hoc distributed queries サーバー構成オプション](../../database-engine/configure-windows/ad-hoc-distributed-queries-server-configuration-option.md)」を参照してください。

```sql
sp_configure 'show advanced options', 1;
RECONFIGURE;
GO
sp_configure 'Ad Hoc Distributed Queries', 1;
RECONFIGURE;
GO
```

次のコード サンプルでは、`OPENROWSET` を使用して、Excel `Data` ワークシートから新しいデータベース テーブルにデータをインポートしています。

```sql
USE ImportFromExcel;
GO
SELECT * INTO Data_dq
FROM OPENROWSET('Microsoft.ACE.OLEDB.12.0',
    'Excel 12.0; Database=D:\Desktop\Data.xlsx', [Data$]);
GO
```

`OPENDATASOURCE` と同じ例を次に示します。

```sql
USE ImportFromExcel;
GO
SELECT * INTO Data_dq
FROM OPENDATASOURCE('Microsoft.ACE.OLEDB.12.0',
    'Data Source=D:\Desktop\Data.xlsx;Extended Properties=Excel 12.0')...[Data$];
GO
```

新しいテーブルを作成する代わりに、インポートされたデータを、*"既存"* テーブルに *"追加"* するには、前の例で使用された `SELECT ... INTO ... FROM ...` 構文ではなく `INSERT INTO ... SELECT ... FROM ...` 構文を使用します。

Excel のデータをインポートせずに Excel のデータにクエリを実行するには、標準の `SELECT ... FROM ...` 構文を使用します。

分散クエリの詳細については、次のトピックを参照してください。
-   [分散クエリ](https://msdn.microsoft.com/library/ms188721(v=sql.105).aspx)。 (分散クエリは SQL Server 2016 でもサポートされていますが、この機能のドキュメントは更新されていません。)
-   [OPENROWSET](../../t-sql/functions/openrowset-transact-sql.md)
-   [OPENDATASOURCE](../../t-sql/functions/openquery-transact-sql.md)

### <a name="linked-servers"></a>リンク サーバー

Excel ファイルへの永続的な接続を *"リンク サーバー"* として構成することもできます。 次の例は、既存の Excel のリンク サーバー `EXCELLINK` の `Data` ワークシートからデータを、`Data_ls` という名前の新しいデータベース テーブルにインポートしています。

```sql
USE ImportFromExcel;
GO
SELECT * INTO Data_ls FROM EXCELLINK...[Data$];
GO
```

リンク サーバーは、SQL Server Management Studio から作成するか、次の例に示すように、システム ストアド プロシージャ `sp_addlinkedserver` を実行して作成できます。

```sql
DECLARE @RC int

DECLARE @server     nvarchar(128)
DECLARE @srvproduct nvarchar(128)
DECLARE @provider   nvarchar(128)
DECLARE @datasrc    nvarchar(4000)
DECLARE @location   nvarchar(4000)
DECLARE @provstr    nvarchar(4000)
DECLARE @catalog    nvarchar(128)

-- Set parameter values
SET @server =     'EXCELLINK'
SET @srvproduct = 'Excel'
SET @provider =   'Microsoft.ACE.OLEDB.12.0'
SET @datasrc =    'D:\Desktop\Data.xlsx'
SET @provstr =    'Excel 12.0'

EXEC @RC = [master].[dbo].[sp_addlinkedserver] @server, @srvproduct, @provider,
@datasrc, @location, @provstr, @catalog
```

リンクサーバーの詳細については、次のトピックを参照してください。
-   [リンク サーバーを作成する](../../relational-databases/linked-servers/create-linked-servers-sql-server-database-engine.md)
-   [OPENQUERY](../../t-sql/functions/openquery-transact-sql.md)

リンク サーバーと分散クエリに関する例および詳細な情報については、次のトピックを参照してください。
-   [SQL Server のリンク サーバーおよび分散クエリで Excel を使用する方法](https://support.microsoft.com/help/306397/how-to-use-excel-with-sql-server-linked-servers-and-distributed-queries)
-   [[HOWTO] DTS: Excel から SQL Server にデータをインポートする方法](https://support.microsoft.com/help/321686/how-to-import-data-from-excel-to-sql-server)

## <a name="prereq"></a> 前提条件 - Excel データをテキストとして保存する
このページの BULK INSERT ステートメント、BCP ツール、または Azure Data Factory に記載されているメソッドの残りの部分を使用するには、最初に Excel データをテキスト ファイルにエクスポートする必要があります。

Excel で **[ファイル] メニューから [名前をつけて保存]** を選択し、変換先ファイルの種類として **Text (Tab delimited) (\*.txt)** または **CSV (Comma delimited) (\*.csv)** を選択します。

ブックから複数のワークシートをエクスポートする場合は、各シートを選択して、この手順を繰り返します。 **[名前をつけて保存]** コマンドでは、作業中のシートのみがエクスポートされます。

> [!TIP]
> データ インポート ツールで最適な結果を得るには、列ヘッダーとデータ行のみが含まれているシートを保存します。 保存したデータにページ タイトル、空白行、メモなどが含まれる場合は、後でデータをインポートするときに、予期しない結果になる可能性があります。

## <a name="import-wiz"></a>フラット ファイルのインポート ウィザード

フラット ファイルのインポート ウィザードのページをステップ実行して、テキストファイルとして保存したデータをインポートします。

前述の[前提条件](#prereq)のセクションで説明したとおり、Excel データをテキストとしてエクスポートしてからフラット ファイルのインポート ウィザードを使用してインポートする必要があります。

フラット ファイルのインポート ウィザードについて詳しくは、「[SQL のフラット ファイルのインポート ウィザード](import-flat-file-wizard.md)」をご覧ください。

## <a name="bulk-insert"></a>BULK INSERT コマンド

`BULK INSERT` は、SQL Server Management Studio から実行できる Transact-SQL コマンドです。 次の例では、`Data.csv` コンマ区切りファイルから既存のデータベース テーブルにデータを読み込みます。

前述の[前提条件](#prereq)のセクションで説明したとおり、Excel データをテキストとしてエクスポートしてから BULK INSERT を使用してインポートする必要があります。 BULK INSERT では、Excel ファイルを直接読み取ることはできません。

```sql
USE ImportFromExcel;
GO
BULK INSERT Data_bi FROM 'D:\Desktop\data.csv'
   WITH (
      FIELDTERMINATOR = ',',
      ROWTERMINATOR = '\n'
);
GO
```

詳細については、次のトピックを参照してください。
-   [BULK INSERT または OPENROWSET(BULK...) を使用した一括データのインポート](../../relational-databases/import-export/import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)
-   [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md)

## <a name="bcp"></a>BCP ツール

BCP は、コマンド プロンプトから実行するプログラムです。 次の例では、`Data.csv` コンマ区切りファイルから既存の `Data_bcp` データベース テーブルにデータを読み込みます。

前述の[前提条件](#prereq)のセクションで説明したとおり、Excel データをテキストとしてエクスポートしてから BCP を使用してインポートする必要があります。 BCP では、Excel ファイルを直接読み取ることはできません。

```sql
bcp.exe ImportFromExcel..Data_bcp in "D:\Desktop\data.csv" -T -c -t ,
```

BCP の詳細については、次のトピックを参照してください。
-   [bcp ユーティリティを使用した一括データのインポートとエクスポート](../../relational-databases/import-export/import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md)
-   [bcp ユーティリティ](../../tools/bcp-utility.md)
-   [一括エクスポートまたは一括インポートのデータの準備](../../relational-databases/import-export/prepare-data-for-bulk-export-or-import-sql-server.md)

## <a name="adf-wiz"></a>コピー ウィザード (Azure Data Factory)
Azure Data Factory のコピー ウィザードのページをステップ実行して、テキストファイルとして保存したデータをインポートします。

前述の[前提条件](#prereq)のセクションで説明したとおり、Excel データをテキストとしてエクスポートしてから Azure Data Factory を使用してインポートする必要があります。 Data Factory では、Excel ファイルを直接読み取ることはできません。

コピー ウィザードの詳細については、次のトピックを参照してください。
-   [Data Factory コピー ウィザード](https://docs.microsoft.com/azure/data-factory/data-factory-azure-copy-wizard)
-   [チュートリアル: コピー アクティビティがあるパイプラインを Data Factory コピー ウィザードで作成する](https://docs.microsoft.com/azure/data-factory/data-factory-copy-data-wizard-tutorial)。

## <a name="adf"></a> Azure Data Factory
Azure Data Factory に精通していて、コピー ウィザードを実行したくない場合は、テキスト ファイルから SQL Server または Azure SQL Database にコピーするコピー アクティビティでパイプラインを作成します。

前述の[前提条件](#prereq)のセクションで説明したとおり、Excel データをテキストとしてエクスポートしてから Azure Data Factory を使用してインポートする必要があります。 Data Factory では、Excel ファイルを直接読み取ることはできません。

これらの Data Factory のソースおよびシンクの使用に関する詳細については、次のトピックを参照してください。
-   [ファイル システム](https://docs.microsoft.com/azure/data-factory/data-factory-onprem-file-system-connector)
-   [SQL Server](https://docs.microsoft.com/azure/data-factory/data-factory-sqlserver-connector)
-   [Azure SQL データベース](https://docs.microsoft.com/azure/data-factory/data-factory-azure-sql-connector)

Azure Data Factory でデータをコピーする方法の学習を開始するには、次のトピックを参照してください。
-   [コピー アクティビティを使用したデータの移動](https://docs.microsoft.com/azure/data-factory/data-factory-data-movement-activities)
-   [チュートリアル: コピー アクティビティがあるパイプラインを Azure portal で作成する](https://docs.microsoft.com/azure/data-factory/data-factory-copy-data-from-azure-blob-storage-to-sql-database)

## <a name="see-also"></a>参照
[SQL Server Integration Services (SSIS) を使用して、Excel からデータをインポートする、または Excel にデータをエクスポートする](../../integration-services/load-data-to-from-excel-with-ssis.md)
