---
title: "Excel から SQL にデータをインポートする | Microsoft Docs"
ms.custom: 
ms.date: 08/02/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 3541efebe50e19ce56e528dc575084c2c5bb1d07
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="import-data-from-excel-to-sql-server-or-azure-sql-database"></a>Excel から SQL Server または Azure SQL Database にデータをインポートする
Excel ファイルからSQL Server または Azure SQL Database に、データをインポートする方法はいくつかあります。 この記事では、これらの各オプションの概要と、詳細な手順へのリンクを提供します。
-   次のいずれかのツールを使用することで、1 つの手順で Excel から SQL にデータをインポートできます。
    -   SQL Server インポートおよびエクスポート ウィザード
    -   SQL Server Integration Services (SSIS)
    -   OPENROWSET 関数
-   データをテキストとして保存してから、次のいずれかのツールを使用することで、2 つの手順でデータをインポートできます。
    -   BULK INSERT ステートメント
    -   BCP
    -   Azure Data Factory

> [!IMPORTANT]
> SSIS や Azure Data Factory のような複雑なツールとサービスの詳細については、この概要の範囲外です。 興味のあるソリューションの詳細については、詳細情報へのリンクを参照してください。

## <a name="sql-server-import-and-export-wizard"></a>SQL Server インポートおよびエクスポート ウィザード

SQL Server インポートおよびエクスポート ウィザードのページをステップ実行して、Excel ファイルから直接データをインポートします。 必要に応じて、カスタマイズして再利用できる SQL Server Integration Services (SSIS) パッケージとして、インポート/エクスポートの設定を保存します。

![Excel データ ソースに接続する](media/excel-connection.png)

ウィザードを使用して Excel から SQL Server にインポートする例については、「[Get started with this simple example of the Import and Export Wizard (インポートおよびエクスポート ウィザードのこの簡単な例から始める)](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md)」を参照してください。

## <a name="sql-server-integration-services-ssis"></a>SQL Server Integration Services (SSIS)

SSIS に精通していて、SQL Server インポートおよびエクスポート ウィザードを実行したくない場合は、Excel ソースおよびデータ フロー内の SQL Server 変換先を使用する SSIS パッケージを作成します。

![データ フロー内のコンポーネント](media/excel-to-sql-data-flow.png)

これらの SSIS コンポーネントの詳細については、次のトピックを参照してください。
-   [Excel ソース](../../integration-services/data-flow/excel-source.md)
-   [SQL Server 変換先](../../integration-services/data-flow/sql-server-destination.md)

SSIS パッケージをビルドする方法の学習を開始するには、チュートリアル「[How to Create an ETL Package (ETL パッケージを作成する方法)](../../integration-services/ssis-how-to-create-an-etl-package.md)」を参照してください。

## <a name="openrowset-and-linked-servers"></a>OPENROWSET およびリンク サーバー
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

## <a name="prerequisite---save-excel-data-as-text"></a>前提条件 - Excel データをテキストとして保存する
このページの BULK INSERT ステートメント、BCP ツール、または Azure Data Factory に記載されているメソッドの残りの部分を使用するには、最初に Excel データをテキスト ファイルにエクスポートする必要があります。

Excel で **[ファイル] メニューから [名前をつけて保存]** を選択し、変換先ファイルの種類として **Text (Tab delimited) (\*.txt)** または **CSV (Comma delimited) (\*.csv)** を選択します。

> [!TIP]
> データ インポート ツールで最適な結果を得るには、列ヘッダーとデータ行のみが含まれているシートを保存します。 保存したデータにページ タイトル、空白行、メモなどが含まれる場合は、後でデータをインポートするときに、予期しない結果になる可能性があります。

## <a name="bulk-insert-command"></a>BULK INSERT コマンド

`BULK INSERT` は、SQL Server Management Studio から実行できる Transact-SQL コマンドです。 次の例では、`Data.csv` コンマ区切りファイルから既存のデータベース テーブルにデータを読み込みます。

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

## <a name="bcp-tool"></a>BCP ツール

BCP は、コマンド プロンプトから実行するプログラムです。 次の例では、`Data.csv` コンマ区切りファイルから既存の `Data_bcp` データベース テーブルにデータを読み込みます。

```sql
bcp.exe ImportFromExcel..Data_bcp in "D:\Desktop\data.csv" -T -c -t ,
```

BCP の詳細については、次のトピックを参照してください。
-   [bcp ユーティリティを使用した一括データのインポートとエクスポート](../../relational-databases/import-export/import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md)
-   [bcp ユーティリティ](../../tools/bcp-utility.md)
-   [一括エクスポートまたは一括インポートのデータの準備](../../relational-databases/import-export/prepare-data-for-bulk-export-or-import-sql-server.md)

## <a name="copy-wizard-azure-data-factory"></a>コピー ウィザード (Azure Data Factory)
コピー ウィザードのページをステップ実行して、テキストファイルとして保存したデータをインポートします。

コピー ウィザードの詳細については、次のトピックを参照してください。
-   [Data Factory コピー ウィザード](https://docs.microsoft.com/azure/data-factory/data-factory-azure-copy-wizard)
-   [チュートリアル: コピー アクティビティがあるパイプラインを Data Factory コピー ウィザードで作成する](https://docs.microsoft.com/azure/data-factory/data-factory-copy-data-wizard-tutorial)。

## <a name="azure-data-factory"></a>Azure Data Factory
Azure Data Factory に精通していて、コピー ウィザードを実行したくない場合は、テキスト ファイルから SQL Server または Azure SQL Database にコピーするコピー アクティビティでパイプラインを作成します。

これらの Data Factory のソースおよびシンクの使用に関する詳細については、次のトピックを参照してください。
-   [ファイル システム](https://docs.microsoft.com/azure/data-factory/data-factory-onprem-file-system-connector)
-   [SQL Server](https://docs.microsoft.com/azure/data-factory/data-factory-sqlserver-connector)
-   [Azure SQL データベース](https://docs.microsoft.com/azure/data-factory/data-factory-azure-sql-connector)

Azure Data Factory でデータをコピーする方法の学習を開始するには、次のトピックを参照してください。
-   [コピー アクティビティを使用したデータの移動](https://docs.microsoft.com/azure/data-factory/data-factory-data-movement-activities)
-   [チュートリアル: コピー アクティビティがあるパイプラインを Azure Portal で作成する](https://docs.microsoft.com/azure/data-factory/data-factory-copy-data-from-azure-blob-storage-to-sql-database)

## <a name="next-steps"></a>次の手順

興味のあるソリューションの詳細については、詳細情報へのリンクを参照してください。
