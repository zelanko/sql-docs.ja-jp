---
title: WideWorldImporters OLTP データベース カタログ - SQL |Microsoft Docs
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.custom: ''
ms.date: 04/04/2018
ms.reviewer: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7e9d8fe2dba82e83594c73e442a2e52260900ba9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68091251"
---
# <a name="wideworldimporters-database-catalog"></a>WideWorldImporters データベース カタログ
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
WideWorldImporters データベースには、すべてのトランザクション情報と売り上げ高と購入の日次データだけでなく車両とコールドのルームのセンサー データが含まれています。

## <a name="schemas"></a>スキーマ

WideWorldImporters は、データを格納する、ユーザーが、データにアクセスする方法を定義するオブジェクトを提供するデータ ウェアハウスの開発との統合などのさまざまな目的のスキーマを使用します。

### <a name="data-schemas"></a>データ スキーマ

これらのスキーマには、データが含まれています。 テーブルの数は、その他のすべてのスキーマで必要なし、アプリケーション スキーマ内にあります。

|スキーマ|説明|
|-----------------------------|---------------------|
|アプリケーション|アプリケーション全体のユーザー、連絡先、およびパラメーター。 これも参照テーブルに複数のスキーマで使用されるデータが含まれています|
|Purchasing|在庫品目は、業者と仕入先に関する詳細から購入します。|  
|販売|在庫製品版の顧客、および顧客や販売人に関する情報を項目に販売します。 |  
|Warehouse|在庫品目の在庫とトランザクション。|  

### <a name="secure-access-schemas"></a>セキュリティで保護された access スキーマ

データ テーブルに直接アクセスを許可されていない外部のアプリケーションの場合、これらのスキーマが使用されます。 ビューと外部アプリケーションによって使用されるストアド プロシージャが含まれます。

|スキーマ|説明|
|-----------------------------|---------------------|
|[Web サイト]|会社の web サイトから、データベースへすべてのアクセスは、このスキーマでです。|
|レポート|Reporting Services レポートから、データベースへすべてのアクセスは、このスキーマでです。|
|PowerBI|エンタープライズ ゲートウェイ経由で Power BI ダッシュ ボードから、データベースへのすべてのアクセスは、このスキーマでです。|

なお、レポートと power Bi スキーマは、サンプル データベースの初期リリースでは使用されません。 ただし、これらのスキーマを使用してこのデータベースの上に構築されたすべての Reporting Services と Power BI のサンプルを推奨します。

### <a name="development-schemas"></a>スキーマの開発

特殊なスキーマ

|スキーマ|説明|
|-----------------------------|---------------------|
|統合|オブジェクトとデータ ウェアハウスの統合に必要な手順 (WideWorldImportersDW データベースには、データを移行など)。|
|シーケンス|アプリケーションのすべてのテーブルで使用される順序を保持します。|

## <a name="tables"></a>テーブル

データベース内のすべてのテーブルは、データ スキーマには。

### <a name="application-schema"></a>アプリケーションのスキーマ

パラメーターと共通の参照テーブル (その他の複数のスキーマに共通) と共にユーザー (ユーザーおよび連絡先) の詳細です。

|テーブル|説明|
|-----------------------------|---------------------|
|SystemParameters|システム全体の構成可能なパラメーターが含まれています。|
|ユーザー|ユーザー名、連絡先については、すべてのアプリケーションを使用して、お客様の組織において、Wide World Importers を処理するユーザーが含まれています。 これには、スタッフ、顧客、サプライヤー、およびその他すべての連絡先が含まれます。 システムまたは web サイトを使用するアクセス許可が付与されたユーザーにはについてには、ログインの詳細が含まれます。|
|市区町村|人々 にとって、お客様の組織の配送先住所、サプライヤーなどにピックアップ アドレス システムでは、格納されている多くのアドレスがあります。アドレスが格納されているときにこのテーブルの city への参照があります。 各都市の所在地もあります。|
|StateProvinces|市区町村には、州または郡の一部です。 このテーブルでは、州や都道府県など、境界を記述する空間データの詳細があります。|
|国|州または郡の国の一部であります。 このテーブルには、各国の境界を記述する空間データを含む、それらの詳細があります。|
|DeliveryMethods|品目の在庫 (例: トラック/van、post、pickup、媒体使用など) を配信するための選択肢|
|PaymentMethods|支払いを行うための選択肢 (など、現金、チェック、EFT など)。|
|TransactionTypes|顧客、仕入先、または (たとえば、請求書、貸方票など) の株価のトランザクションの種類|

### <a name="purchasing-schema"></a>スキーマの購入

在庫品目の購入および仕入先の詳細情報。

|テーブル|説明|
|-----------------------------|---------------------|
|Suppliers|Suppliers (組織) の主要なエンティティ テーブル|
|SupplierCategories|カテゴリの業者 (novelties、パッケージ化など、clothing toys など。)|
|SupplierTransactions|供給業者に関連する (請求書支払い) であるすべての財務トランザクション|
|次の使用|供給業者の注文書の詳細|
|PurchaseOrderLines|発注書を業者から詳細行|

 
### <a name="sales-schema"></a>販売スキーマ

顧客、営業担当者、および在庫品目の売上の詳細情報。

|テーブル|説明|
|-----------------------------|---------------------|
|Customers|顧客 (組織または個人) のメイン エンティティ テーブル|
|CustomerCategories|(つまり装飾的なストア、スーパー マーケットなど) のお客様のカテゴリ|
|BuyingGroups|お客様の組織が厳密に大きい購買力グループの一部にすることができます。|
|CustomerTransactions|顧客に関連する (請求書支払い) であるすべての財務トランザクション|
|SpecialDeals|特別な価格設定です。 固定価格を含めるをドル、割引率の割引率します。|
|Orders|顧客の注文の詳細|
|OrderLines|顧客の注文からの詳細行|
|請求書|顧客の請求書の詳細|
|InvoiceLines|顧客の請求書から詳細行|

### <a name="warehouse-schema"></a>ウェアハウスのスキーマ

品目の在庫、holdings およびトランザクションの詳細です。

|テーブル|説明|
|-----------------------------|---------------------|
|StockItems|品目の在庫の主なエンティティ テーブル|
|StockItemHoldings|品目の在庫の非テンポラルの列です。 これらは頻繁に更新される列です。|
|StockGroups|(例: novelties、玩具、活用 novelties など) の株価の項目を分類するためのグループ|
|StockItemStockGroups|ストック アイテムはストックが (多対多) にグループ|
|色|品目の在庫が色を持つことができます (省略可能)|
|PackageTypes|在庫品目の方法をパッケージ化することができます (例: ボックス、窪みがパック、パレット、kg など。|
|StockItemTransactions|すべてのストック アイテム (受信、販売、損金処理) のすべての動きをカバーするトランザクション|
|VehicleTemperatures|車両の冷却の温度を定期的に記録されました。|
|ColdRoomTemperatures|コールド ルーム冷却の温度を定期的に記録|


## <a name="design-considerations"></a>設計に関する考慮事項

データベースの設計は主観的であり、データベースを設計する方法を正解や間違いはありません。 スキーマと、このデータベースのテーブルは、独自のデータベースを設計する方法に関するアイデアを表示します。

### <a name="schema-design"></a>スキーマの設計

簡単に、データベース システムを理解して、データベースの原則を説明できるように、WideWorldImporters はスキーマの数が少ないを使用します。  

可能な限り、データベースには、結合の複雑さを最小限に抑えるのと同じスキーマにクエリが通常のテーブルが併置したりします。

データベース スキーマが、別のデータベース WWI_Preparation 内の一連のメタデータ テーブルに基づいて、コード生成されました。 これにより、WideWorldImporters は非常に高度なデザインの整合性、名前付け一貫性、および完全性を実現します。 スキーマの生成方法の詳細については、ソース コードを参照してください: [wide-world-importers/wwi-database-scripts](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/wide-world-importers/sample-scripts)

### <a name="table-design"></a>テーブルのデザイン

- すべてのテーブルには、結合をわかりやすくするための主キーを 1 つの列があります。
- 拡張オブジェクトまたは列の目的を識別するために使用できるプロパティの説明には、すべてのスキーマ、テーブル、列、インデックス、および check 制約があります。 メモリ最適化テーブルでは、拡張プロパティを現在サポートしていないために、この例外です。
- 同じ左側コンポーネント別の非クラスター化インデックスがある場合を除き、すべての外部キーが自動的にインデックスします。
- テーブルの自動番号付けは、シーケンスに基づいています。 これらのシーケンスは、リンク サーバー、および ID 列よりも同様の環境全体で作業しやすくします。 メモリ最適化テーブルでは、SQL Server 2016 でサポートしていないために、ID 列を使用します。
- これらのテーブルに 1 つのシーケンス (TransactionID) が使用されます。CustomerTransactions、SupplierTransactions、および StockItemTransactions です。 これは、一連のテーブルが 1 つのシーケンスを必要する方法について説明します。
- 一部の列は、適切な既定値を指定します。

### <a name="security-schemas"></a>セキュリティ スキーマ

セキュリティ、WideWorldImporters に外部のアプリケーション データのスキーマに直接アクセスは許可されません。 でアクセスを特定するのには、WideWorldImporters には、データを保持しませんが、ビュー、ストアド プロシージャが含まれているセキュリティ アクセス スキーマが使用されます。 外部のアプリケーションでは、セキュリティ スキーマを使用して、表示が許可されているデータを取得します。  これにより、ユーザーのみで実行できますビューとストアド プロシージャ、セキュリティで保護されたアクセス スキーマ

たとえば、このサンプルには、Power BI ダッシュ ボードが含まれます。 外部アプリケーションは、PowerBI スキーマに対する読み取り専用のアクセス許可を持つユーザーとして、Power BI Gateway からこれらの Power BI ダッシュ ボードにアクセスします。  読み取り専用のアクセス許可については、ユーザーには PowerBI スキーマに対する SELECT および EXECUTE のアクセス許可のみが必要です。 WWI でのデータベース管理者は、必要に応じて、これらのアクセス許可を割り当てます。

## <a name="stored-procedures"></a>ストアド プロシージャ

ストアド プロシージャは、スキーマで編成されます。 スキーマのほとんどは、構成またはサンプルの目的で使用されます。

`Website`スキーマには、Web フロント エンドで使用できるストアド プロシージャが含まれています。

`Reports`と`PowerBI`スキーマは、reporting services と power Bi のためのものです。 サンプルのすべての拡張機能はレポート用にこれらのスキーマを使用することをお勧めします。

### <a name="website-schema"></a>Web サイトのスキーマ

これらは、Web フロント エンドなどのクライアント アプリケーションによって使用されるプロシージャです。

|手順|目的|
|-----------------------------|---------------------|
|ActivateWebsiteLogon|使用すると (から`Application.People`) が、web サイトにアクセスします。|
|パスワードの変更|(外部の認証メカニズムを使用していないユーザー) 用のユーザーのパスワードを変更します。|
|InsertCustomerOrders|(注文明細行を含む) 1 つまたは複数の顧客注文を挿入できます。|
|InvoiceCustomerOrders|請求される注文の一覧を受け取り、請求書を処理します。|
|RecordColdRoomTemperatures|テーブル値パラメーター (TVP) として、センサー データのリストを受け取り、データに適用、`Warehouse.ColdRoomTemperatures`テンポラル テーブル。|
|RecordVehicleTemperature|JSON 配列を受け取り、それを使用して更新する`Warehouse.VehicleTemperatures`します。|
|SearchForCustomers|名前または名前 (会社名またはユーザー名) の一部で顧客を検索します。|
|SearchForPeople|名前または名前の一部で人を検索します。|
|SearchForStockItems|名前または名前またはマーケティングのコメントの一部で株式の項目を検索します。|
|SearchForStockItemsByTags|タグを使用して株式の項目を検索します。|
|SearchForSuppliers|名前または名前 (会社名またはユーザー名) の一部で仕入先を検索します。|

### <a name="integration-schema"></a>統合スキーマ

このスキーマでストアド プロシージャは、ETL プロセスによって使用されます。 必要な期間のさまざまなテーブルから必要なデータを取得する、 [ETL パッケージ](wide-world-importers-perform-etl.md)します。

### <a name="dataloadsimulation-schema"></a>DataLoadSimulation スキーマ

売り上げ高と購入を挿入するワークロードをシミュレートします。 主なストアド プロシージャは`PopulateDataToCurrentDate`を使用して、現在の日付までのサンプル データを挿入します。

|手順|目的|
|-----------------------------|---------------------|
|Configuration_ApplyDataLoadSimulationProcedures|プロシージャが再作成されるために必要なデータのロード シミュレーション。 これは、現在の日付データを取り込むことの必要です。|
|Configuration_RemoveDataLoadSimulationProcedures|データのシミュレーションが完了した後でもう一度、プロシージャを削除これとします。|
|DeactivateTemporalTablesBeforeDataLoad|すべてのテンポラル テーブルの一時的な性質を削除し、該当する場合、sys テンポラル テーブルよりも前の日付で適用されたされているように変更を実行できるようにトリガーを適用します。|
|PopulateDataToCurrentDate|現在の日付までのデータを取り込むために使用します。 初回のバックアップからデータベースを復元した後はその他の構成オプションの前に実行する必要があります。|
|ReactivateTemporalTablesAfterDataLoad|データの整合性のチェックを含む、テンポラル テーブルを再確立します。 (関連付けられたトリガーを削除します)。|


### <a name="application-schema"></a>アプリケーションのスキーマ

これらの手順は、サンプルの構成に使用されます。 これらのオプションを使用して、standard edition のバージョンのサンプルとも監査を追加して、フルテキスト インデックス作成を enterprise edition の機能を適用します。

|手順|目的|
|-----------------------------|---------------------|
|AddRoleMemberIfNonexistant|ロールのメンバーがいない場合は、メンバーをロールに追加します。|
|Configuration_ApplyAuditing|監査を追加します。 Standard edition のデータベースのサーバー監査が適用されます。その他のデータベースの監査は、enterprise edition 用追加されます。|
|Configuration_ApplyColumnstoreIndexing|列ストア インデックスに適用される`Sales.OrderLines`と`Sales.InvoiceLines`と適切に再作成します。|
|Configuration_ApplyFullTextIndexing|フルテキスト インデックスに適用される`Application.People`、 `Sales.Customers`、 `Purchasing.Suppliers`、および`Warehouse.StockItems`します。 置換`Website.SearchForPeople`、 `Website.SearchForSuppliers`、 `Website.SearchForCustomers`、 `Website.SearchForStockItems`、`Website.SearchForStockItemsByTags`フルテキスト インデックス作成を使用して、交換手順とします。|
|Configuration_ApplyPartitioning|適用するテーブルのパーティション分割`Sales.CustomerTransactions`と`Purchasing.SupplierTransactions`に合うようにインデックスを再配置するとします。|
|Configuration_ApplyRowLevelSecurity|フィルターの顧客に販売で行レベルのセキュリティを適用 territory に関連するロール。|
|Configuration_ConfigureForEnterpriseEdition|列ストア インデックス、フルテキスト、メモリ内、polybase、およびパーティション分割を適用します。|
|Configuration_EnableInMemory|(Azure では機能していない) 場合は、メモリ最適化ファイル グループを追加、置換`Warehouse.ColdRoomTemperatures`、 `Warehouse.VehicleTemperatures` 、対応するメモリ内でのデータを移行、再作成、 `Website.OrderIDList`、 `Website.OrderList`、 `Website.OrderLineList`、`Website.SensorDataList`テーブルでの型対応するメモリが最適化された、削除操作を行うと、プロシージャが再作成される`Website.InvoiceCustomerOrders`、 `Website.InsertCustomerOrders`、および`Website.RecordColdRoomTemperatures`これらのテーブル型を使用します。|
|Configuration_RemoveAuditing|監査の構成を削除します。|
|Configuration_RemoveRowLevelSecurity|(これは、関連付けられているテーブルへの変更の必要)、行レベルのセキュリティ構成を削除します。|
|CreateRoleIfNonExistant|存在しない場合は、データベース ロールを作成します。|


### <a name="sequences-schema"></a>シーケンス スキーマ

データベースで、シーケンスを構成する手順。

|手順|目的|
|-----------------------------|---------------------|
|ReseedAllSequences|すべてのシーケンスの ReseedSequenceBeyondTableValue プロシージャを呼び出します。|
|ReseedSequenceBeyondTableValue|同じシーケンスを使用する任意のテーブルで、値を上回る次のシーケンス値の位置を変更するために使用します。 (など、DBCC CHECKIDENT のシーケンスが、可能性のある複数のテーブルの identity 列と同じ)。|
