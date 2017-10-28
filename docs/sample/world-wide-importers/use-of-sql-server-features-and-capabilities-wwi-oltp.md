---
title: "SQL Server の機能と機能の使用 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- samples
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 06f89721-8478-4abc-8ada-e9c73b08bf51
caps.latest.revision: 2
author: BarbKess
ms.author: barbkess
manager: jhubbard
robots: noindex,nofollow
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 90b1cd86f2fcc282922111ac9325470635bcfcad
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="use-of-sql-server-features-and-capabilities"></a>SQL Server の機能と機能の使用
SQL Server の機能と、OLTP データベースの機能の WideWorldImporters を使用します。

SQL Server 2016 で導入された最新の機能をなど、SQL Server の主な機能の多くに対応させることは、WideWorldImporters は設計されています。 SQL Server の機能や機能、WideWorldImporters での使用方法の説明の一覧を次に示します。

|SQL Server の機能または機能|WideWorldImporters で使用します。|
|-----------------------------|---------------------|
|テンポラル テーブル|すべての参照スタイル参照テーブルと StockItems、顧客、仕入先などの主要なエンティティを含む多くのテンポラル テーブルがあります。 簡単に追跡するこれらのエンティティの履歴により、テンポラル テーブルを使用します。|
|For JSON の AJAX 呼び出し|アプリケーションがこれらのテーブルを照会する AJAX 呼び出しを頻繁に使用します。 担当者、顧客、仕入先、および StockItems です。 呼び出しでは、JSON ペイロード (つまりで返されるデータは JSON データとして書式設定) を返します。 たとえば、ストアド プロシージャを参照して`Website.SearchForCustomers`です。|
|JSON のプロパティと値のバッグ|複数のテーブルには、テーブル内のリレーショナル データを拡張する JSON データを保持する列があります。 たとえば、`Application.SystemParameters`アプリケーション設定の列があると`Application.People`レコードのユーザー設定に列があります。 これらのテーブルを使用して、`nvarchar(max)`組み込み関数を使用して CHECK 制約と共に、JSON データを記録する列`ISJSON`値は、有効な JSON を列を確認します。|
|行レベル セキュリティ (RLS)|行レベル セキュリティ (RLS) を使用して、ロールのメンバーシップに基づいて、顧客テーブルへのアクセスを制限できます。 販売区域ごとには、ロールとユーザーがあります。 この動作を確認、含まれているサンプル script.zip に対応するスクリプトを使用します。 の、[サンプルのリリース](http://go.microsoft.com/fwlink/?LinkID=800630)です。|
|リアルタイム運用分析|(フル バージョンのデータベース)コア トランザクション テーブル`Sales.InvoiceLines`と`Sales.OrderLines`運用ワークロードの最小限の影響でトランザクション データベースで効率的に実行する分析クエリをサポートするために非クラスター化列ストア インデックスを持つ両方です。 同じデータベース内のトランザクションと分析を実行しているとも呼びます[ハイブリッド トランザクション/分析処理 (HTAP)](https://wikipedia.org/wiki/Hybrid_Transactional/Analytical_Processing_(HTAP))です。 この動作を確認、含まれているサンプル script.zip に対応するスクリプトを使用します。 の、[サンプルのリリース](http://go.microsoft.com/fwlink/?LinkID=800630)です。|
|PolyBase|Azure ブログの記憶域でホストされているパブリック データ セットで、外部テーブルを使用して、アクションでこの PolyBase を表示するには、含まれているサンプル script.zip で対応するスクリプトを使用の[サンプルのリリース](http://go.microsoft.com/fwlink/?LinkID=800630)です。|
|インメモリ OLTP|(フル バージョンのデータベース)テーブルの種類は、すべてのメモリ最適化、テーブル値パラメーター (Tvp) すべてがメモリ最適化によるメリットになるようです。<br/><br/>2 つの監視テーブル`Warehouse.VehicleTemperatures`と`Warehouse.ColdRoomTemperatures`、メモリ最適化されます。 これにより、従来のディスク ベース テーブルよりも高速にデータを設定する ColdRoomTemperatures テーブルです。 VehicleTemperatures の表は、JSON ペイロードを保持しているし、IoT シナリオに向けて拡張機能に適しています。 VehicleTemperatures 表に、さらには、EventHubs、Stream Analytics と Power BI が関係するシナリオに適しています。<br/><br/>ストアド プロシージャ`Website.RecordColdRoomTemperatures`コールド ルーム温度を記録するためのパフォーマンスをさらに強化をネイティブでコンパイルします。<br/><br/>アクションで、インメモリ OLTP のサンプルを参照してください vehicle 場所ワークロード ドライバーに含まれているワークロード drivers.zip の[サンプルのリリース](http://go.microsoft.com/fwlink/?LinkID=800630)です。|
|クラスター化列ストア インデックス|(フル バージョンのデータベース)テーブル`Warehouse.StockItemTransactions`はクラスター化列ストア インデックスを使用します。 このテーブルの行の数が大きく、予期されたとクラスター化列ストア インデックスは大幅に、テーブルのディスク上のサイズを縮小し、クエリのパフォーマンスが向上します。 このテーブルの変更は挿入のみで - 更新/削除 - オンライン ワークロード内の次の表ではありません、クラスター化列ストア インデックスを挿入ワークロードの実行|
|動的なデータ マスキング|データベース スキーマにデータ マスクに適用されている、テーブルにサプライヤーの保持銀行詳細`Purchasing.Suppliers`です。 管理者以外のスタッフには、この情報へのアクセスはありません。|
|Always Encrypted|Always Encrypted のデモが含まれているダウンロード可能な samples.zip に含まれるは[サンプルのリリース](http://go.microsoft.com/fwlink/?LinkID=800630). デモでは、暗号化キー、暗号化を使用して、デリケートなデータと、テーブルにデータを挿入する小さなサンプル アプリケーションのテーブルを作成します。|
|Stretch database|`Warehouse.ColdRoomTemperatures`テーブルは、テンポラル テーブルとして実装されているし、は、サンプル データベースの完全バージョンではメモリ最適化されています。 アーカイブ テーブルはディスク ベースであり、Azure にストレッチできます。|
|フルテキスト インデックス|フルテキスト インデックスには、ユーザー、顧客、および StockItems の検索が向上します。 インデックスは、フルテキスト インデックスが、SQL Server インスタンスにインストールされている場合にのみ、クエリに適用されます。 フルテキスト StockItems テーブルでインデックス付けされているデータを作成するには、非永続的な計算列が使用します。<br/><br/>`CONCAT`フルテキスト インデックスは、SearchData を作成するフィールドを連結することの使用されます。<br/>有効にするには、サンプルのフルテキスト インデックスの使用はデータベースで、次のステートメントを実行します。<br/><br/>    `EXECUTE [Application].[Configuration_ConfigureFullTextIndexing]`<br/><br/>プロシージャを作成、既定のフルテキスト カタログが既に存在しないいずれかの場合は、フルテキストのバージョンのこれらのビューの検索ビューに置換) します。<br/><br/>SQL Server でのフルテキスト インデックスを使用するには、インストール中に、フルテキスト オプションの選択が必要だことに注意してください。 Azure SQL データベースは必要ありません、特定の構成、フルテキスト インデックスを有効にします。|
|保存される計算列のインデックスを作成します。|SupplierTransactions および CustomerTransactions で使用される保存される計算列のインデックスを作成します。|
|CHECK 制約|比較的複雑な check 制約`Sales.SpecialDeals`です。 これにより、1 つの DiscountAmount、DiscountPercentage、1 つだけと、UnitPrice が構成されています。|
|Unique 制約|多対多の構築 (および unique 制約) Warehouse.StockItemStockGroups' に対して設定されます。|
|テーブルのパーティション分割|(フル バージョンのデータベース)テーブル`Sales.CustomerTransactions`と`Purchasing.SupplierTransactions`年ごとのパーティション関数を使用してパーティション分割両方`PF_TransactionDate`およびパーティション構成`PS_TransactionDate`です。 パーティション分割は、大きなテーブルの管理性を向上させるために使用されます。|
|リストの処理|例のテーブル型`Website.OrderIDList`が指定されています。 サンプル プロシージャによって使用されている`Website.InvoiceCustomerOrders`です。 プロシージャでは、共通テーブル式 (Cte)、TRY ブロックと CATCH、JSON_MODIFY、XACT_ABORT、NOCOUNT、THROW、および XACT_STATE を使用して、アプリケーションからデータベース エンジンへのラウンド トリップを最小限に抑える、1 つの注文だけではなく、注文の一覧を処理する機能を示します。|
|GZip 圧縮|`Warehouse.VehicleTemperature`のテーブルは、センサー データを保持しているが、このデータが数か月以内の場合は、GZip で圧縮を使用して圧縮する関数を使用して領域を節約するために圧縮します。<br/><br/>ビュー`Website.VehicleTemperatures`既に圧縮されているデータを取得するときに、DECOMPRESS 関数を使用します。|
|クエリ ストア|クエリ ストアは、データベースで有効にします。 いくつかのクエリを実行すると、Management Studio でデータベースを開く、ノードの下にある、データベース、クエリ ストアを開くおよび上位リソース消費のクエリのクエリの実行、および実行したクエリのプランを表示するレポートを開きます。|
|STRING_SPLIT|列`DeliveryInstructions`表内の`Sales.Invoices`STRING_SPLIT を示すために使用できるカンマ区切りの値を持ちます。|
|監査|SQL Server Audit は、データベースで、次のステートメントを実行してこのサンプル データベースに対して有効にすることができます。<br/><br/>    `EXECUTE [Application].[Configuration_ApplyAuditing]`<br/><br/>を介して、Azure SQL データベースの監査が有効になっている、 [Azure ポータル](https://portal.azure.com/)です。<br/><br/>ログインに関連するセキュリティ操作、役割とアクセス許可は、(standard edition のシステム) を含む監査が有効になっているすべてのシステムで記録されます。 これは、すべてのシステムで使用可能な追加の権限は必要ないために、アプリケーション ログに監査が送られます。 警告より高いセキュリティにリダイレクトされる、セキュリティ ログに、またはセキュリティで保護されたフォルダー内のファイルにいるです。 リンクは、必要な追加の構成を記述するものです。<br/><br/>評価/developer または enterprise edition のシステムでは、すべての財務トランザクション データへのアクセスを監査します。|

