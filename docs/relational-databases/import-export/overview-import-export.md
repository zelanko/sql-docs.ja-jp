---
title: "SQL Server および Azure SQL Database のデータをインポートおよびエクスポートする | Microsoft Docs"
ms.custom: 
ms.date: 09/12/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: 6e754198cf82a7ba0752fe8f20c3780a8ac551d7
ms.openlocfilehash: 3c41be0642b13b63367c5601b716b506808472e7
ms.contentlocale: ja-jp
ms.lasthandoff: 09/14/2017

---
# <a name="import-and-export-data-from-sql-server-and-azure-sql-database"></a>SQL Server および Azure SQL Database のデータをインポートおよびエクスポートする
さまざまな方法を使って、SQL Server と Azure SQL Database のデータをインポートしておよびエクスポートできます。 Transact-SQL ステートメント、コマンドライン ツール、ウィザードなどの方法があります。

また、インポートおよびエクスポートするデータの形式にもさまざまな種類があります。 フラット ファイル、Excel、主要なリレーショナル データベース、さまざまなクラウド サービスなどの形式があります。

## <a name="methods-for-importing-and-exporting-data"></a>データのインポートとエクスポートの方法

### <a name="use-transact-sql-statements"></a>Transact-SQL ステートメントを使用する
`BULK INSERT` または `OPENROWSET(BULK...)` コマンドでデータをインポートできます。 通常は、SQL Server Management Studio (SSMS) でこれらのコマンドを実行します。 詳しくは、「[BULK INSERT または OPENROWSET(BULK...) を使用した一括データのインポート](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)」をご覧ください。

### <a name="use-bcp-from-the-command-prompt"></a>コマンド プロンプトから BCP を使用する
BCP コマンドライン ユーティリティを使って、データをインポートおよびエクスポートできます。 詳しくは、「[bcp ユーティリティを使用した一括データのインポートとエクスポート](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)」をご覧ください。

### <a name="use-the-sql-server-import-and-export-wizard"></a>SQL Server インポートおよびエクスポート ウィザードを使用する
SQL Server インポートおよびエクスポート ウィザードを使って、さまざまなソースとデスティネーションの間で、データをインポートおよびエクスポートできます。 ウィザードを使うには、SQL Server Integration Services (SSIS) または SQL Server Data Tools (SSDT) がインストールされている必要があります。 詳しくは、「[SQL Server インポートおよびエクスポート ウィザードを使用してデータをインポートおよびエクスポートする](../../integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md)」をご覧ください。

### <a name="design-your-own-import-or-export"></a>独自のインポートまたはエクスポートを設計する
カスタム データ インポートを設計する場合は、次のいずれかの機能またはサービスを使うことができます。
-   SQL Server Integration Services。 詳しくは、「[SQL Server Integration Services](../../integration-services/sql-server-integration-services.md)」をご覧ください。
-   Azure Data Factory。 詳しくは、「[Azure Data Factory の概要](https://docs.microsoft.com/azure/data-factory/data-factory-introduction)」をご覧ください。

## <a name="data-formats-for-import-and-export"></a>インポートおよびエクスポートのデータ形式

### <a name="supported-formats"></a>サポートされている形式

フラット ファイルまたはその他のさまざまなファイル形式、リレーショナル データベース、およびクラウド サービスで、データをインポートおよびエクスポートできます。 特定のツールでのこれらのオプションについて詳しくは、次のトピックをご覧ください。
-   SQL Server インポートおよびエクスポート ウィザードについては、「[Connect to Data Sources with the SQL Server Import and Export Wizard](../../integration-services/import-export-data/connect-to-data-sources-with-the-sql-server-import-and-export-wizard.md)」(SQL Server インポートおよびエクスポート ウィザードを使用してデータ ソースに接続する) をご覧ください。
-   SQL Server Integration Services については、「[Integration Services (SSIS) の接続](../../integration-services/connection-manager/integration-services-ssis-connections.md)」をご覧ください。
-   Azure Data Factory については、「[Azure Data Factory を使用して Amazon Redshift からデータを移動する](https://docs.microsoft.com/en-us/azure/data-factory/data-factory-amazon-redshift-connector)」をご覧ください。

### <a name="commonly-used-data-formats"></a>よく使われるデータ形式

一部のよく使われるデータ形式には、特別な考慮事項と例があります。 これらのデータ形式について詳しくは、次のトピックをご覧ください。
-   Excel については、「[Excel から SQL Server または Azure SQL Database にデータをインポートする](import-data-from-excel-to-sql.md)」をご覧ください。
-   JSON については、「[JSON ドキュメントのインポート](../json/import-json-documents-into-sql-server.md)」をご覧ください。
-   XML については、「[XML ドキュメントのインポートおよびエクスポート](examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)」をご覧ください。
-   Azure Blob Storage については、「[Azure BLOB ストレージからのインポートおよびエクスポート](examples-of-bulk-access-to-data-in-azure-blob-storage.md)」をご覧ください。

## <a name="next-steps"></a>次の手順
インポートまたはエクスポート タスクをどこから始めればよいかわからない場合は、SQL Server インポートおよびエクスポート ウィザードを検討してください。 概要については、「[簡単な例によるインポートおよびエクスポート ウィザードの概要](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md)」をご覧ください。

