---
title: SQL Server の機能と機能の使用 |Microsoft Docs
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 06f89721-8478-4abc-8ada-e9c73b08bf51
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4a60b0c11e787945d381cf3c6a8ec305761fef46
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47764296"
---
# <a name="use-of-sql-server-features-and-capabilities"></a>SQL Server の機能と機能の使用
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
SQL Server の機能と、OLTP データベースの機能の WideWorldImporters を使用します。

SQL Server 2016 で導入された最新の機能を含め、SQL Server の主な機能の多くを紹介することは、WideWorldImporters は設計されています。 次に SQL Server の機能と機能、および WideWorldImporters での使用方法の説明の一覧を示します。

|SQL Server の機能または機能|WideWorldImporters での使用|
|-----------------------------|---------------------|
|テンポラル テーブル|すべての参照スタイル参照テーブルと StockItems、顧客、サプライヤーなどの主要なエンティティを含む多くのテンポラル テーブルがあります。 簡単に追跡するこれらのエンティティの履歴により、テンポラル テーブルを使用します。|
|Json の AJAX 呼び出し|アプリケーションがこれらのテーブルを照会する AJAX 呼び出しを頻繁に使用します。 担当者、顧客、サプライヤー、および StockItems します。 呼び出しは、JSON のペイロード (つまりで返されるデータは JSON データとして書式設定) を返します。 、たとえば、ストアド プロシージャを参照してください`Website.SearchForCustomers`します。|
|JSON のプロパティと値のバッグ|複数のテーブルでは、テーブル内のリレーショナル データを拡張する JSON データを保持する列があります。 たとえば、`Application.SystemParameters`アプリケーション設定の列があると`Application.People`レコードのユーザーの基本設定の列があります。 これらのテーブルを使用して、`nvarchar(max)`組み込み関数を使用して CHECK 制約と共に、JSON データを記録する列`ISJSON`値が有効な JSON を列を確認します。|
|行レベル セキュリティ (RLS)|行レベル セキュリティ (RLS) を使用して、ロールのメンバーシップに基づいて、顧客テーブルへのアクセスを制限できます。 販売区域ごとには、ロールとユーザーがあります。 アクションの表示は、するには、含まれているサンプル script.zip で対応するスクリプトを使用の[サンプルのリリース](http://go.microsoft.com/fwlink/?LinkID=800630)します。|
|リアルタイム運用分析|(データベースの完全バージョン)コア トランザクション テーブル`Sales.InvoiceLines`と`Sales.OrderLines`運用ワークロードの影響を最小限に抑える、トランザクション データベースでの分析クエリを効率的に実行をサポートするために非クラスター化列ストア インデックスを持つ両方。 同じデータベース内のトランザクションと分析を実行するいると呼ばれるもを[ハイブリッド トランザクション/分析処理 (HTAP)](https://wikipedia.org/wiki/Hybrid_Transactional/Analytical_Processing_(HTAP))します。 アクションの表示は、するには、含まれているサンプル script.zip で対応するスクリプトを使用の[サンプルのリリース](http://go.microsoft.com/fwlink/?LinkID=800630)します。|
|PolyBase|この Azure ブログのストレージでホストされているパブリック データ セットで、外部テーブルを使用してアクションで、PolyBase を表示するには、含まれているサンプル script.zip で対応するスクリプトを使用の[サンプルのリリース](http://go.microsoft.com/fwlink/?LinkID=800630)します。|
|インメモリ OLTP|(データベースの完全バージョン)テーブル型ではテーブル値パラメーター (Tvp すべて) がメモリ最適化からメリットをすべてメモリの最適化します。<br/><br/>2 つの監視テーブル`Warehouse.VehicleTemperatures`と`Warehouse.ColdRoomTemperatures`、メモリ最適化されます。 これにより、従来のディスク ベース テーブルよりも高速にデータを設定する ColdRoomTemperatures テーブルです。 VehicleTemperatures テーブルでは、JSON ペイロードを保持し、IoT シナリオに拡張機能に適しています。 VehicleTemperatures テーブルをさらには、event Hubs、Stream Analytics、および Power BI に関連するシナリオに適しています。<br/><br/>ストアド プロシージャ`Website.RecordColdRoomTemperatures`をネイティブでコンパイルをさらにコールド部屋の温度の記録のパフォーマンスを強化します。<br/><br/>動作には、インメモリ OLTP での例を参照してくださいに含まれているワークロード drivers.zip 車両場所ワークロード ドライバーを参照してください。 の、[サンプルのリリース](http://go.microsoft.com/fwlink/?LinkID=800630)します。|
|クラスター化列ストア インデックス|(データベースの完全バージョン)テーブル`Warehouse.StockItemTransactions`はクラスター化列ストア インデックスを使用します。 大きく、このテーブル内の行の数が必要ですし、クラスター化列ストア インデックスは大幅に、テーブルのディスクのサイズを縮小し、クエリのパフォーマンスが向上します。 このテーブルに変更が挿入のみで、更新/削除 - オンライン ワークロードには、このテーブルではありません - と挿入ワークロードに対してもクラスター化列ストア インデックスを実行します。|
|動的なデータ マスキング|データベース スキーマにデータ マスクが適用された銀行の詳細の表に、サプライヤーに保持されている`Purchasing.Suppliers`します。 管理者以外のスタッフには、この情報へのアクセスはありません。|
|Always Encrypted|Always Encrypted のデモが含まれているダウンロード可能な samples.zip に含まれているは[サンプルのリリース](http://go.microsoft.com/fwlink/?LinkID=800630). 今回のデモでは、暗号化キー、機密性の高いデータと、テーブルにデータを挿入する小規模なサンプル アプリケーションの暗号化を使用してテーブルを作成します。|
|Stretch Database|`Warehouse.ColdRoomTemperatures`テーブルは、テンポラル テーブルとして実装されているし、は、サンプル データベースの完全バージョンでは、メモリ最適化します。 アーカイブ テーブルはディスク ベースであり、Azure に拡張できます。|
|フルテキスト インデックス|フルテキスト インデックスには、ユーザー、顧客、および StockItems 検索が向上します。 フルテキスト インデックスが、SQL Server インスタンスにインストールされている場合にのみ、インデックスがクエリに適用されます。 非永続的な計算列は、StockItems テーブルでインデックスがフルテキストをされているデータの作成に使用されます。<br/><br/>`CONCAT` SearchData は、フルテキスト インデックスを作成する、フィールドの連結に使用されます。<br/>有効にするのには、サンプルでは、フルテキスト インデックスの使用は、データベースで、次のステートメントを実行します。<br/><br/>    `EXECUTE [Application].[Configuration_ConfigureFullTextIndexing]`<br/><br/>プロシージャを作成します既定のフルテキスト カタログが既に存在していずれかの場合は、フルテキストのバージョンをこれらのビューの検索ビューを置き換えます)。<br/><br/>SQL Server でフルテキスト インデックスを使用するには、インストール中に、フルテキストのオプションを選択が必要だことに注意してください。 Azure SQL Database は必要ありませんし、特定の構成、フルテキスト インデックスを有効にします。|
|保存される計算列のインデックスを作成します。|SupplierTransactions および CustomerTransactions で使用される、保存される計算列のインデックスを作成します。|
|CHECK 制約|比較的複雑な check 制約が`Sales.SpecialDeals`します。 これにより、1 つ、DiscountAmount、DiscountPercentage の 1 つだけあり、UnitPrice が構成されます。|
|Unique 制約|多対多の構築 (と一意制約) は、Warehouse.StockItemStockGroups' に設定されます。|
|テーブルのパーティション分割|(データベースの完全バージョン)テーブル`Sales.CustomerTransactions`と`Purchasing.SupplierTransactions`パーティション関数を使用して年でパーティション分割両方`PF_TransactionDate`およびパーティション構成`PS_TransactionDate`します。 パーティション分割は、大きなテーブルの管理性を向上させるために使用されます。|
|リストの処理|例のテーブル型`Website.OrderIDList`提供されます。 手順の例で使用されて`Website.InvoiceCustomerOrders`します。 手順が、アプリケーションからのラウンド トリップを最小限に抑える、1 つの注文だけではなく、注文の一覧を処理する機能について説明する共通テーブル式 (Cte)、TRY/CATCH、JSON_MODIFY、XACT_ABORT、NOCOUNT、THROW と XACT_STATE を使用しますデータベース エンジン。|
|GZip 圧縮|`Warehouse.VehicleTemperature`センサー データを保持するテーブルが、このデータが数か月以内の場合は、GZip 圧縮を使用する圧縮関数を使用して領域を節約するために圧縮します。<br/><br/>ビュー `Website.VehicleTemperatures` DECOMPRESS 関数を使って、以前に圧縮されたデータを取得するときにします。|
|クエリ ストア|クエリ ストアは、データベースで有効にします。 いくつかのクエリを実行すると、Management Studio でデータベースを開き、ノードの下にある、データベース、クエリ ストアを開くおよびトップ リソース コンシューマー クエリ、クエリの実行と実行したクエリのプランを表示するレポートを開きます。|
|STRING_SPLIT|列`DeliveryInstructions`表内の`Sales.Invoices`STRING_SPLIT を示すために使用できるコンマ区切りの値を持ちます。|
|監査|データベースで、次のステートメントを実行して、このサンプル データベースの SQL Server Audit を有効にできます。<br/><br/>    `EXECUTE [Application].[Configuration_ApplyAuditing]`<br/><br/>を通じて、Azure SQL database の監査が有効になっている、 [Azure portal](https://portal.azure.com/)します。<br/><br/>ログインに関連するセキュリティ操作では、ロールとアクセス許可は、(standard edition のシステム) を含む監査が有効になっているすべてのシステムで記録されます。 これはすべてのシステムで使用可能な追加の権限は必要ありませんので、アプリケーション ログに監査が送られます。 警告は、セキュリティを強化する必要がありますリダイレクトされる必要がセキュリティ ログに、またはセキュリティで保護されたフォルダー内のファイルにいるです。 必要な追加の構成を記述するリンクが提供されます。<br/><br/>評価/開発者/エンタープライズ エディションのシステムでは、すべての財務トランザクション データへのアクセスが監査されます。|
