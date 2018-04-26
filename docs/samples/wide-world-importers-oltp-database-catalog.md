---
title: WideWorldImporters OLTP データベース カタログ - SQL |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: sql
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
ms.openlocfilehash: d7240025e36f64ac6a11194d81ba563d4e7c49b0
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="wideworldimporters-database-catalog"></a>WideWorldImporters データベース カタログ
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
WideWorldImporters データベースには、すべてのトランザクション情報と販売と購入の毎日のデータだけでなく車両とコールド ルームのセンサー データが含まれています。

## <a name="schemas"></a>スキーマ

WideWorldImporters は、データを格納する、ユーザーが、データにアクセスする方法を定義するオブジェクトを提供するデータ ウェアハウスの開発との統合などのさまざまな目的のスキーマを使用します。

### <a name="data-schemas"></a>データのスキーマ

これらのスキーマには、データが含まれます。 テーブルの数は他のすべてのスキーマで必要とし、アプリケーション スキーマ内にあります。

|スキーマ|Description|
|-----------------------------|---------------------|
|アプリケーション|アプリケーション全体のユーザー、連絡先、およびパラメーター。 これも参照テーブルに複数のスキーマで使用されるデータが含まれています|
|Purchasing|サプライヤーと仕入先に関する詳細から在庫品目を購入します。|  
|売上|ストック小売業者および顧客と販売のユーザーについて詳細に販売項目。 |  
|Warehouse|在庫品目の在庫およびトランザクションです。|  

### <a name="secure-access-schemas"></a>セキュリティで保護されたアクセス スキーマ

データ テーブルに直接アクセスできない外部のアプリケーションの場合、これらのスキーマが使用されます。 ビューと、外部アプリケーションから使用するストアド プロシージャが含まれます。

|スキーマ|Description|
|-----------------------------|---------------------|
|[Web サイト]|会社の web サイトからデータベースへすべてのアクセスは、このスキーマでです。|
|レポート|Reporting Services レポートからデータベースへすべてのアクセスは、このスキーマでです。|
|PowerBI|Enterprise Gateway 経由で Power BI のダッシュ ボードからデータベースへすべてのアクセスは、このスキーマでです。|

注意してください、レポートと PowerBI スキーマは、サンプル データベースの最初のリリースでは使用されません。 ただし、このデータベース上に構築されるすべての Reporting Services と Power BI のサンプルは、これらのスキーマを使用を推奨します。

### <a name="development-schemas"></a>スキーマの開発

特殊なスキーマ

|スキーマ|Description|
|-----------------------------|---------------------|
|統合|オブジェクトとデータ ウェアハウスの統合に必要な手順 (WideWorldImportersDW データベースには、データを移行など)。|
|シーケンス|アプリケーション内のすべてのテーブルで使用される順序を保持します。|

## <a name="tables"></a>テーブル

データベース内のすべてのテーブルは、データのスキーマでです。

### <a name="application-schema"></a>アプリケーションのスキーマ

パラメーターと共通の参照テーブル (その他の複数のスキーマに共通) と共に、ユーザー (ユーザーおよび連絡先) の詳細です。

|Table|Description|
|-----------------------------|---------------------|
|SystemParameters|システム全体の構成可能なパラメーターが含まれています。|
|ユーザー|ユーザー名、および、ユーザーがお客様の組織において、Wide World importers 社を処理するため、アプリケーションを使用しているすべての連絡先の情報が含まれています。 これには、スタッフ、顧客、仕入先、およびその他の連絡先が含まれます。 システムまたは web サイトを使用するアクセス許可が付与されたユーザーのための情報には、ログインの詳細が含まれます。|
|都市|人々 にとって、お客様の組織の配送先住所、ピックアップ アドレス suppliers など、システムに格納されている多くのアドレスがあります。アドレスが格納されているときに、次の表で、市区町村への参照。 市区町村ごとの所在地もあります。|
|StateProvinces|州または郡の一部である市区町村。 このテーブルは、州や都道府県など、境界を記述する空間データの詳細情報を持っています。|
|Countries|州または郡の国の一部であります。 このテーブルには、各国の境界を記述する空間データをなどの詳細があります。|
|DeliveryMethods|ストック項目 (例: トラック/van、post、ピックアップ、媒体使用など) を実現する選択肢|
|PaymentMethods|支払いを行うための選択肢 (など、キャッシュ、チェック、EFT などです)。|
|TransactionTypes|種類の顧客、仕入先、株価のトランザクション (たとえば、請求書、貸方など)|

### <a name="purchasing-schema"></a>スキーマの購入

在庫品目の購入および仕入先の詳細です。

|Table|Description|
|-----------------------------|---------------------|
|Suppliers|仕入先 (組織) のメイン エンティティ テーブル|
|SupplierCategories|Suppliers (例: novelties、toys、clothing、パッケージ化など) のカテゴリ|
|SupplierTransactions|供給業者に関連する (請求書払い) は、すべての財務トランザクション|
|次の使用|供給業者の注文書の詳細|
|PurchaseOrderLines|発注書を業者から詳細行|

 
### <a name="sales-schema"></a>販売スキーマ

顧客、販売員、および在庫品目の売上の詳細です。

|Table|Description|
|-----------------------------|---------------------|
|Customers|お客様 (組織や個人) にメイン エンティティ テーブル|
|CustomerCategories|お客様 (ie 新奇ストア、スーパー マーケットなど) のカテゴリ|
|BuyingGroups|お客様の組織が大きい購入の電源をより細かくグループの一部にすることができます。|
|CustomerTransactions|顧客に関連する (請求書払い) は、すべての財務トランザクション|
|SpecialDeals|特別な価格設定です。 これにより、固定価格を含めることができます、割引ドル、割引率。|
|Orders|顧客の注文の詳細|
|Orderlines を追加|顧客の注文からの詳細行|
|請求書|顧客の請求書の詳細|
|InvoiceLines|顧客の請求書から詳細行|

### <a name="warehouse-schema"></a>ウェアハウスのスキーマ

品目の在庫、保有およびトランザクションの詳細です。

|Table|Description|
|-----------------------------|---------------------|
|StockItems|ストックの項目のメイン エンティティ テーブル|
|StockItemHoldings|品目の在庫の非テンポラル列です。 これらは、頻繁に更新される列です。|
|StockGroups|ストックの項目 (例: novelties、toys、活用 novelties など) を分類するためのグループ|
|StockItemStockGroups|在庫が (多対多) にグループがストック項目です。|
|色|品目の在庫が色を持つことができます (省略可能)|
|PackageTypes|在庫品目の方法をパッケージ化することができます (たとえば、ボックス、carton、パレット、kg などです。|
|StockItemTransactions|すべてのストック アイテム (受信確認、販売、損金処理) のすべての動きをカバーするトランザクション|
|VehicleTemperatures|Vehicle 冷却装置の温度を定期的に記録されました。|
|ColdRoomTemperatures|コールド ルーム冷却装置の温度を定期的に記録|


## <a name="design-considerations"></a>設計に関する考慮事項

データベースの設計は主観的なものと、データベースをデザインの右端または正しくない方法はありません。 スキーマとこのデータベースのテーブルは、独自のデータベースを設計する方法に関するアイデアを表示します。

### <a name="schema-design"></a>スキーマのデザイン

データベース システムを理解およびデータベースの原則をデモンストレーションするやすいように、WideWorldImporters はスキーマの数が少ないを使用します。  

可能な限り、データベースは、一般的にたずねますまとめて結合の複雑さを最小限に抑える同じスキーマにテーブルを collocates です。

データベース スキーマがされましたコードによって生成されたメタデータ内のテーブルの別のデータベース WWI_Preparation 系列に基づきます。 これにより、WideWorldImporters は非常に高度なデザインの整合性、名前付け一貫性、および完全を期すためにします。 スキーマの生成方法の詳細については、ソース コードを参照してください: [wide world-インポーター/第一次世界大戦-データベースのスクリプト](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/wide-world-importers/sample-scripts)

### <a name="table-design"></a>テーブルのデザイン

- すべてのテーブルには、結合わかりやすくするための主キーを 1 つの列があります。
- すべてのスキーマ、テーブル、列、インデックス、および check 制約がある拡張オブジェクトまたは列の目的を識別するために使用できるプロパティの説明。 メモリ最適化テーブルは、拡張プロパティを現在サポートしていないために、この例外となるはします。
- 同じ左側コンポーネントを含む別の非クラスター化インデックスがある場合を除き、すべての外部キーが自動的にインデックスします。
- テーブルに自動番号付けは、シーケンスに基づいています。 これらのシーケンスは、リンク サーバーと ID 列よりも同様の環境全体で作業しやすくします。 メモリ最適化テーブルは、SQL Server 2016 でサポートしないために、ID 列を使用します。
- これらのテーブルの 1 つのシーケンス (TransactionID) を使用: CustomerTransactions、SupplierTransactions、および StockItemTransactions です。 これは、一連のテーブルが 1 つのシーケンスを持つ方法を示します。
- 一部の列では、適切な既定値があります。

### <a name="security-schemas"></a>セキュリティのスキーマ

セキュリティ、WideWorldImporters を外部アプリケーション データのスキーマに直接アクセスをすることはできません。 でのアクセスを特定するのには、WideWorldImporters は、データを保持しませんが、ビュー、ストアド プロシージャが含まれているセキュリティ アクセス スキーマを使用します。 外部アプリケーションでは、セキュリティ スキーマを使用して、表示が許可されているデータを取得します。  これにより、ユーザーのみで実行できますビューおよびストアド プロシージャ、セキュリティで保護されたアクセス スキーマ

たとえば、このサンプルには、Power BI ダッシュ ボードが含まれます。 外部アプリケーションを PowerBI スキーマに対する読み取り専用権限を持つユーザーとして、Power BI gateway からこれらの Power BI ダッシュ ボードにアクセスします。  読み取り専用のアクセス許可は、ユーザーには PowerBI スキーマに対する SELECT および EXECUTE 権限のみが必要です。 第一次世界大戦でデータベース管理者は、必要に応じて、これらのアクセス許可を割り当てます。

## <a name="stored-procedures"></a>ストアド プロシージャ

ストアド プロシージャは、スキーマで構成されます。 スキーマのほとんどは、構成またはサンプルの目的で使用されます。

`Website`スキーマには、Web フロント エンドで使用できるストアド プロシージャが含まれています。

`Reports`と`PowerBI`reporting services と power Bi 用のスキーマが意図したものです。 サンプルのすべての拡張機能はレポート目的でこれらのスキーマを使用することをお勧めします。

### <a name="website-schema"></a>Web サイトのスキーマ

これらは、Web フロント エンドなどのクライアント アプリケーションで使用されるプロシージャです。

|手順|用途|
|-----------------------------|---------------------|
|ActivateWebsiteLogon|使用すると (から`Application.People`) が、web サイトにアクセスします。|
|パスワードの変更|(外部の認証メカニズムを使用していないユーザー) 用のユーザーのパスワードを変更します。|
|InsertCustomerOrders|(注文明細行を含む) 1 つまたは複数の顧客注文の挿入を許可します。|
|InvoiceCustomerOrders|請求される注文の一覧を取得し、請求書を処理します。|
|RecordColdRoomTemperatures|リストを受け取り、センサー データ、テーブル値パラメーター (TVP) としてし、データの適用、`Warehouse.ColdRoomTemperatures`テンポラル テーブルです。|
|RecordVehicleTemperature|JSON 配列を受け取るし、それを使用して更新`Warehouse.VehicleTemperatures`です。|
|SearchForCustomers|名前または名前 (会社名またはユーザー名) の一部で顧客を検索します。|
|SearchForPeople|名前または名前の一部でユーザーを検索します。|
|SearchForStockItems|名前または名前またはマーケティングのコメントの一部で品目の在庫を検索します。|
|SearchForStockItemsByTags|タグを使用して在庫のアイテムを検索します。|
|SearchForSuppliers|名前または名前 (会社名またはユーザー名) の一部で suppliers を検索します。|

### <a name="integration-schema"></a>統合スキーマ

このスキーマ内のストアド プロシージャは、ETL プロセスによって使用されます。 必要な時間帯でさまざまなテーブルから必要なデータを取得する、 [ETL パッケージ](wide-world-importers-perform-etl.md)です。

### <a name="dataloadsimulation-schema"></a>DataLoadSimulation スキーマ

売り上げ高と購入を挿入するワークロードをシミュレートします。 主なストアド プロシージャは`PopulateDataToCurrentDate`、現在の日付までのサンプル データの挿入に使用されます。

|手順|用途|
|-----------------------------|---------------------|
|Configuration_ApplyDataLoadSimulationProcedures|再作成の手順は、必要なデータをロード シミュレーションします。 現在の日付までのデータを取り込むこれが必要です。|
|Configuration_RemoveDataLoadSimulationProcedures|データのシミュレーションが完了した後でもう一度、プロシージャを削除これとします。|
|DeactiveTemporalTablesBeforeDataLoad|すべてのテンポラル テーブルの一時的な性質を削除し、該当する場合、sys テンポラル テーブルを許可するよりも前の日付で適用されたされているかのように変更ができるようようにトリガーを適用します。|
|PopulateDataToCurrentDate|現在の日付までのデータを表示するために使用します。 最初のバックアップからデータベースを復元した後、その他の構成オプションの前に実行する必要があります。|
|ReactivateTemporalTablesAfterDataLoad|データの整合性のチェックを含む、テンポラル テーブルを再確立します。 (関連付けられたトリガーを削除します。)|


### <a name="application-schema"></a>アプリケーションのスキーマ

これらの手順は、サンプルの構成に使用されます。 これらのオプションを使用して、standard edition のバージョンのサンプルとも監査を追加して、フルテキスト インデックス作成を enterprise エディションの機能を適用します。

|手順|用途|
|-----------------------------|---------------------|
|AddRoleMemberIfNonexistant|ロールのメンバーがいない場合は、ロールにメンバーを追加します。|
|Configuration_ApplyAuditing|監査を追加します。 サーバー監査が standard edition のデータベースの適用します。enterprise edition の場合は、その他のデータベース監査が追加されます。|
|Configuration_ApplyColumnstoreIndexing|列ストア インデックスに適用される`Sales.OrderLines`と`Sales.InvoiceLines`し、適切に再作成します。|
|Configuration_ApplyFullTextIndexing|フルテキスト インデックスに適用される`Application.People`、 `Sales.Customers`、 `Purchasing.Suppliers`、および`Warehouse.StockItems`です。 置換`Website.SearchForPeople`、 `Website.SearchForSuppliers`、 `Website.SearchForCustomers`、 `Website.SearchForStockItems`、`Website.SearchForStockItemsByTags`がフルテキスト インデックス作成を使用する置換プロシージャです。|
|Configuration_ApplyPartitioning|適用するテーブルがパーティション分割`Sales.CustomerTransactions and `Purchasing.SupplierTransactions' と、インデックスの並べ替えに合うようにします。|
|Configuration_ApplyRowLevelSecurity|フィルターの顧客に販売して行レベルのセキュリティを適用 territory に関連するロール。|
|Configuration_ConfigureForEnterpriseEdition|列ストア インデックス、フルテキスト、メモリ内、polybase、およびパーティション分割を適用します。|
|Configuration_EnableInMemory|(Azure で動作していない) 場合は、メモリ最適化ファイル グループを追加、置換`Warehouse.ColdRoomTemperatures`、 `Warehouse.VehicleTemperatures` 、対応するメモリ内でのデータを移行し、再作成、 `Website.OrderIDList`、 `Website.OrderList`、 `Website.OrderLineList`、 `Website.SensorDataList` 、対応するメモリ最適化テーブル型を削除し、プロシージャを再作成`Website.InvoiceCustomerOrders`、 `Website.InsertCustomerOrders`、および`Website.RecordColdRoomTemperatures`これらのテーブル型を使用します。|
|Configuration_RemoveAuditing|監査の構成を削除します。|
|Configuration_RemoveRowLevelSecurity|(これは、関連付けられているテーブルの変更に必要です)、行レベルのセキュリティ構成を削除します。|
|CreateRoleIfNonExistant|存在しない場合は、データベース ロールを作成します。|


### <a name="sequences-schema"></a>シーケンス スキーマ

データベースのシーケンスを構成する手順。

|手順|用途|
|-----------------------------|---------------------|
|ReseedAllSequences|すべてのシーケンスの ReseedSequenceBeyondTableValue プロシージャを呼び出します。|
|ReseedSequenceBeyondTableValue|同じシーケンスを使用する任意のテーブルで値に加えて、次のシーケンス値の位置を変更するために使用します。 (など、DBCC CHECKIDENT のシーケンスが可能性のある複数のテーブルで、identity 列それと同等)。|
