---
title: SQL Server Analysis Services 表形式の 1400 モデルでサポートされるデータ ソース |Microsoft ドキュメント
ms.date: 03/26/2018
ms.prod: analysis-services
ms.suite: pro-bi
ms.topic: conceptual
ms.assetid: ''
author: Minewiskan
ms.author: owend
manager: kfile
monikerRange: '>= sql-analysis-services-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 7f2ae9498b0d177234fd75bb0de9ea0b61d15746
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="data-sources-supported-in-sql-server-analysis-services-tabular-1400-models"></a>データ ソースが SQL Server Analysis Services で 1400 の表形式モデルをサポート

[!INCLUDE[ssas-appliesto-sql2017](../../includes/ssas-appliesto-sql2017.md)]

この記事では、1400 互換性レベルの SQL Server Analysis Services (SSAS) 表形式モデルで使用できるデータ ソースの種類について説明します。 

SSAS 表形式モデル 1200 と下限の互換性レベルはを参照してください。 [SQL Server Analysis Services 表形式の 1200 モデルでサポートされるデータ ソース](data-sources-supported-ssas-tabular.md)です。

Azure Analysis Services では、次を参照してください。 [Azure Analysis Services でサポートされるデータ ソース](https://docs.microsoft.com/azure/analysis-services/analysis-services-datasource)です。


## <a name="cloud-data-sources"></a>クラウド データ ソース

|Azure のデータ ソース  |メモリ内  |DirectQuery  |
|---------|---------|---------|
|Azure SQL Database     |   はい      |    はい      |
|Azure SQL データ ウェアハウス     |   はい      |   はい       |
|Azure BLOB ストレージ     |   はい       |    いいえ      |
|Azure テーブル ストレージ    |   はい       |    いいえ      |
|Azure Cosmos DB      |  はい        |  いいえ        |
|Azure Data Lake Store     |   はい       |    いいえ      |
|Azure HDInsight HDFS     |     はい     |   いいえ       |
|Azure HDInsight Spark (ベータ版)     |   はい       |   いいえ       |
||||

**プロバイダー**   
インメモリと DirectQuery モデルの Azure データ ソースへの接続は、SQL Server の .NET Framework データ プロバイダーを使用します。

## <a name="on-premises-data-sources"></a>オンプレミス データ ソース

### <a name="supported-by-in-memory-and-directquery-models"></a>インメモリと DirectQuery モデルでサポートされています。

|データ ソース | メモリ内のプロバイダー | DirectQuery プロバイダー |
|  --- | --- | --- |
| SQL Server |SQL Server Native Client 11.0、Microsoft OLE DB Provider for SQL Server、.NET Framework Data Provider for SQL Server | .NET Framework Data Provider for SQL Server |
| SQL Server データ ウェアハウス |SQL Server Native Client 11.0、Microsoft OLE DB Provider for SQL Server、.NET Framework Data Provider for SQL Server | .NET Framework Data Provider for SQL Server |
| Oracle |Microsoft OLE DB Provider for Oracle、.NET 用の Oracle データ プロバイダー |.NET 用の oracle データ プロバイダー | |
| Teradata |OLE DB Provider for Teradata、.NET の Teradata データ プロバイダー |.NET の Teradata データ プロバイダー | |
| | | |

> [!NOTE]
> OLE DB プロバイダーは、インメモリ モデルでは、大規模なデータのパフォーマンスが向上を提供できます。 選択すると、同じデータ ソースごとに異なるプロバイダーの間で、最初の OLE DB プロバイダーを試してください。  

### <a name="supported-by-in-memory-models-only"></a>インメモリ モデルでのみでサポートされています。

|データベース  |
|---------|---------|---------|
|Access データベース     | 
|SQL Server Analysis Services (SQL Server Analysis Services)     | 
|IBM Informix (ベータ版) | 
|JSON ドキュメント     | 
|バイナリからの行     | 
|MySQL データベース     | 
|PostgreSQL データベース    | はい | いいえ
|SAP HANA   | はい | いいえ
|SAP Business Warehouse    | はい | いいえ
|Sybase データベース     | はい | いいえ
|||

|ファイル  |  
|---------|---------|
|Excel ブック     |
|フォルダー     | 
|JSON | 
|テキスト/CSV    | 
|XML テーブル    | 
|||

|オンライン サービス  |  
|---------|---------|
|Dynamics 365      |
|オンラインのやり取り     |
|Saleforce オブジェクト    | 
|Salesforce レポート     |
|SharePoint Online リスト     |
|||

|その他  |  
|---------|---------|
|Active Directory      | 
|やり取り     |  
|OData フィード     | 
|ODBC クエリ     | 
|OLE DB (OLE DB)  | 
|SharePoint リスト | 
|||

## <a name="see-also"></a>参照

[SQL Server Analysis Services 表形式モデル 1200 にサポートされるデータ ソース](data-sources-supported-ssas-tabular.md)

[Azure Analysis Services でサポートされるデータ ソース](https://docs.microsoft.com/azure/analysis-services/analysis-services-datasource)   
