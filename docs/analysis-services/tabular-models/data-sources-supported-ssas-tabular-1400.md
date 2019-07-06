---
title: SQL Server Analysis Services 表形式 1400 モデルでサポートされるデータ ソース |Microsoft Docs
ms.date: 07/02/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 246375015786cf67685c89f368f83662539da36b
ms.sourcegitcommit: d9c5b9ab3c282775ed61712892eeb3e150ccc808
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/05/2019
ms.locfileid: "67597350"
---
# <a name="data-sources-supported-in-sql-server-analysis-services-tabular-1400-models"></a>SQL Server Analysis Services 表形式 1400 モデルにサポートされるデータ ソース

[!INCLUDE[ssas-appliesto-sql2017](../../includes/ssas-appliesto-sql2017.md)]

この記事では、1400 互換性レベルの SQL Server Analysis Services (SSAS) 表形式モデルで使用できるデータ ソースの種類について説明します。 

SSAS 表形式モデル 1200 と下限の互換性レベルはを参照してください。 [SQL Server Analysis Services 表形式 1200 モデルでサポートされるデータ ソース](data-sources-supported-ssas-tabular.md)します。

Azure Analysis Services では、次を参照してください。 [Azure Analysis Services でサポートされるデータ ソース](https://docs.microsoft.com/azure/analysis-services/analysis-services-datasource)します。


## <a name="cloud-data-sources"></a>クラウドのデータ ソース

|データ ソース  |メモリ内  |DirectQuery  |
|---------|---------|---------|
|Azure SQL Database <sup> [1](#ae)</sup>    |   はい      |    はい      |
|Azure SQL Data Warehouse     |   はい      |   はい       |
|Azure Blob Storage     |   はい       |    いいえ      |
|Azure Table Storage    |   はい       |    いいえ      |
|Azure Cosmos DB     |  はい        |  いいえ        |
|Azure Data Lake Store (Gen1)<sup>[2](#gen2)</sup>      |   [はい]       |    いいえ      |
|Azure HDInsight HDFS    |     はい     |   いいえ       |
|Azure HDInsight Spark <sup> [3](#databricks)</sup>     |   はい       |   いいえ       |
||||

<a name="ae">1</a> -azure SQL Database の Always Encrypted はサポートされていません。   
<a name="gen2">2</a> -ADLS Gen2 は現在サポートされていません。   
<a name="databricks">3</a> - azure Databricks の使用、Spark コネクタは現在サポートされていません。   




**プロバイダー**   
インメモリおよび DirectQuery モデルの Azure データ ソースへの接続は、SQL Server の .NET Framework Data Provider を使用します。

## <a name="on-premises-data-sources"></a>オンプレミス データ ソース

### <a name="supported-by-in-memory-and-directquery-models"></a>インメモリおよび DirectQuery モデルでサポートされています。

|データ ソース | メモリ内プロバイダー | DirectQuery プロバイダー |
|  --- | --- | --- |
| SQL Server <sup> [4](#aeop)</sup> |SQL Server Native Client 11.0、Microsoft OLE DB Provider for SQL Server、.NET Framework Data Provider for SQL Server | .NET Framework Data Provider for SQL Server |
| SQL Server データ ウェアハウス |SQL Server Native Client 11.0、Microsoft OLE DB Provider for SQL Server、.NET Framework Data Provider for SQL Server | .NET Framework Data Provider for SQL Server |
| Oracle |Microsoft OLE DB Provider for Oracle で Oracle Data Provider for .NET |Oracle Data Provider for .NET | |
| Teradata |OLE DB Provider for Teradata、Teradata Data Provider for .NET |Teradata Data Provider for .NET | |
| | | |

<a name="aeop">4</a> -azure SQL Database と SQL Server のデータベースが Always Encrypted は、DirectQuery としてサポートされて[クライアント データソース](data-sources-supported-ssas-tabular.md#bkmk_supported_ds_dq)で SQL Server Analysis Services 表形式モデル 1200 互換性レベルでのみです。 Azure SQL Database と SQL Server のデータベースが Always Encrypted は Azure Analysis Services でサポートされていません。       

> [!NOTE]
> インメモリ モデルでは、OLE DB プロバイダーは、大規模なデータのパフォーマンス向上を提供できます。 同じデータ ソースごとに異なるプロバイダーの間を選択するときは、まず、OLE DB プロバイダーを試してください。  

### <a name="supported-by-in-memory-models-only"></a>インメモリ モデルのみでサポートされています。

|[データベース]  |
|---------|---------|---------|
|Access データベース     | 
|SQL Server Analysis Services     | 
|IBM Informix (ベータ) | 
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
|Exchange Online     |
|Saleforce オブジェクト    | 
|Salesforce レポート     |
|SharePoint Online リスト     |
|||

|その他  |  
|---------|---------|
|Active Directory      | 
|Exchange     |  
|OData フィード     | 
|ODBC クエリ     | 
|OLE DB (OLE DB)  | 
|SharePoint リスト | 
|||

## <a name="see-also"></a>関連項目

[SQL Server Analysis Services 表形式モデル 1200 にサポートされるデータ ソース](data-sources-supported-ssas-tabular.md)

[Azure Analysis Services でサポートされるデータ ソース](https://docs.microsoft.com/azure/analysis-services/analysis-services-datasource)   
