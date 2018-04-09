---
title: WideWorldImporters OLAP データベース カタログ - SQL |Microsoft ドキュメント
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: ''
ms.component: samples
ms.technology:
- samples
ms.custom: ''
ms.date: 04/04/2018
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: article
author: BarbKess
ms.author: barbkess
manager: craigg
robots: noindex,nofollow
ms.workload: On Demand
ms.openlocfilehash: 8039efbdb9157b45f8fcc67d0b8f72d367d81e52
ms.sourcegitcommit: d6b1695c8cbc70279b7d85ec4dfb66a4271cdb10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2018
---
# <a name="wideworldimportersdw-database-catalog"></a>WideWorldImportersDW database catalog
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
スキーマ、テーブル、および WideWorldImportersDW データベース内のストアド プロシージャの説明。 

WideWorldImportersDW データベースは、データ ウェアハウスと分析処理に使用されます。 売り上げ高と購入に関するトランザクションのデータが、WideWorldImporters データベースに生成され、WideWorldImportersDW を使用してデータベースに読み込まれる、**毎日の ETL プロセス**です。

WideWorldImportersDW 内のデータしたがって WideWorldImporters、内のデータをミラー化が、テーブルは異なる方法で整理されています。 WideWorldImportersDW WideWorldImporters には、従来の正規化されたスキーマが、使用して、[スター スキーマ](https://wikipedia.org/wiki/Star_schema)そのテーブルのデザインのアプローチです。 データベースには、ファクト テーブルとディメンション テーブルだけでなく、ETL プロセスで使用されるステージング テーブルの数が含まれます。

## <a name="schemas"></a>スキーマ

テーブルのさまざまな種類は、3 つのスキーマで構成されます。

|スキーマ|Description|
|-----------------------------|---------------------|
|[ディメンション]|ディメンション テーブル。|
|[ファクト]|ファクト テーブルです。|  
|統合|ステージング テーブルと ETL に必要なその他のオブジェクト。|  

## <a name="tables"></a>テーブル

ディメンションとファクト テーブルは次のとおりです。 統合スキーマ内のテーブルは、ETL プロセスにのみ使用され、は表示されません。

### <a name="dimension-tables"></a>ディメンション テーブル

WideWorldImportersDW には、次のディメンション テーブルがあります。 説明には、WideWorldImporters データベース内のソース テーブルとの関係が含まれています。

|Table|ソース テーブル|
|-----------------------------|---------------------|
|City|`Application.Cities`, `Application.StateProvinces`, `Application.Countries`.|
|Customer|`Sales.Customers`, `Sales.BuyingGroups`, `Sales.CustomerCategories`.|
|日付|日付、会計年度をなどに関する情報を含む新しいテーブル (年 11 月 1 日に基づく会計年度の開始)。|
|Employee|`Application.People`」を参照してください。|
|StockItem|`Warehouse.StockItems`, `Warehouse.Colors`, `Warehouse.PackageType`.|
|業者|`Purchasing.Suppliers`, `Purchasing.SupplierCategories`.|
|PaymentMethod|`Application.PaymentMethods`」を参照してください。|
|TransactionType|`Application.TransactionTypes`」を参照してください。|

### <a name="fact-tables"></a>ファクト テーブル

WideWorldImportersDW には、次のファクト テーブルがあります。 説明には、WideWorldImporters データベースだけでなく分析/レポート クエリの各ファクト テーブルを使用して通常のクラスのソース テーブルとの関係が含まれています。

|Table|ソース テーブル|サンプルの分析|
|-----------------------------|---------------------|---------------------|
|書|`Sales.Orders` と `Sales.OrderLines`|売上は、人、ピッカー/ため生産性とでは、注文を取得する時間です。 さらに、注文をバックアップするのには先頭の在庫の状況が低い。|
|販売|`Sales.Invoices` と `Sales.InvoiceLines`|販売日、出荷日、時間の経過と共に収益性、販売員による収益性。|
|注文書|`Purchasing.PurchaseOrderLines`|予期される vs 実際リード タイム|
|トランザクション|`Sales.CustomerTransactions` と `Purchasing.SupplierTransactions`|発行日 vs 終了日、および金額を測定します。|
|移動|`Warehouse.StockTransactions`|時間の経過と共に移動します。|
|ストックの保持|`Warehouse.StockItemHoldings`|手の形で在庫レベルと値。|

## <a name="stored-procedures"></a>ストアド プロシージャ

ストアド プロシージャは、主に、ETL プロセスと構成のために使用されます。

サンプルのすべての拡張機能を使用することをお勧め、 `Reports` Reporting Services レポートのスキーマと`PowerBI`Power BI へのアクセス用のスキーマです。

### <a name="application-schema"></a>アプリケーションのスキーマ

これらの手順は、サンプルの構成に使用されます。 PolyBase, を追加、サンプルの standard edition のバージョンに enterprise edition の機能を適用し、reseed ETL に使用されます。

|手順|用途|
|-----------------------------|---------------------|
|Configuration_ApplyPartitionedColumnstoreIndexing|ファクト テーブルのパーティション分割と列ストア インデックスに適用されます。|
|Configuration_ConfigureForEnterpriseEdition|パーティション分割、列ストア インデックスとメモリ内に適用されます。|
|Configuration_EnableInMemory|ETL のパフォーマンスを向上させる SCHEMA_ONLY メモリ最適化テーブルの統合ステージング テーブルを置換します。|
|Configuration_ApplyPolybase|外部データ ソース、ファイル形式、およびテーブルを構成します。|
|Configuration_PopulateLargeSaleTable|Enterprise エディションの変更を適用し、追加の履歴と 2012年のカレンダー年度の大量のデータのデータを格納します。|
|Configuration_ReseedETL|既存のデータを削除し、ETL シードを再起動します。 これにより、OLAP データベースを再作成に、OLTP データベースの更新された行と一致します。|

### <a name="integration-schema"></a>統合スキーマ

ETL プロセスで使用されるプロシージャは、これらのカテゴリに分類されます。
- ETL パッケージのすべての Get * プロシージャのヘルパー プロシージャです。
- 移行するため、ETL パッケージで使用されるプロシージャは、DW のテーブルのすべての移行 * プロシージャにデータをステージングします。
- `PopulateDateDimensionForYear` -1 年間でその年のすべての日付が設定されていることを確認、`Dimension.Date`テーブル。

### <a name="sequences-schema"></a>シーケンス スキーマ

データベースのシーケンスを構成する手順。

|手順|用途|
|-----------------------------|---------------------|
|ReseedAllSequences|プロシージャが呼び出される`ReseedSequenceBeyondTableValue`のすべてのシーケンス。|
|ReseedSequenceBeyondTableValue|同じシーケンスを使用する任意のテーブルで値に加えて、次のシーケンス値の位置を変更するために使用します。 (と同様に、`DBCC CHECKIDENT`可能性のある複数のテーブルが、シーケンスの identity 列のと同じにします)。|
