---
title: WideWorldImporters データ - SQL サンプル データベースの生成 |Microsoft ドキュメント
ms.custom: ''
ms.date: 04/04/2018
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6ace1f771ef3a77a6f7db0072442affe181d7872
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2018
---
# <a name="wideworldimporters-data-generation"></a>WideWorldImporters データの生成
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
WideWorldImporters と WideWorldImportersDW データベースのリリース バージョンでは、2013、年 1 月 1 日まで、データベースが生成された日からのデータがあります。

これらのサンプル データベースを使用する場合より新しいサンプル データを含めることができます。

## <a name="data-generation-in-wideworldimporters"></a>WideWorldImporters でデータの生成

現在の日付までのサンプル データを生成します。

1. 実行していない場合は、WideWorldImporters データベースのクリーン バージョンをインストールします。 インストール手順については、次を参照してください。[インストールと構成](wide-world-importers-oltp-install-configure.md)です。
2. データベースで、次のステートメントを実行します。

    ```
        EXECUTE DataLoadSimulation.PopulateDataToCurrentDate
            @AverageNumberOfCustomerOrdersPerDay = 60,
            @SaturdayPercentageOfNormalWorkDay = 50,
            @SundayPercentageOfNormalWorkDay = 0,
            @IsSilentMode = 1,
            @AreDatesPrinted = 1;
    ```

    このステートメントは、現在の日付までのデータベースにサンプルの売上および注文書データを追加します。 日単位でデータの生成の進行状況を表示します。 データの生成は、データが必要なすべての年度の約 10 分かかります。 データ生成時に、ランダムな要素があるため、生成されたデータを実行間で違いの一部です。

    1 日の注文に対して生成されたデータの量を増減するには、パラメーターの値を変更する`@AverageNumberOfCustomerOrdersPerDay`です。 パラメーターを使用して`@SaturdayPercentageOfNormalWorkDay`と`@SundayPercentageOfNormalWorkDay`を週末の曜日に注文量を決定します。

## <a name="import-generated-data-in-wideworldimportersdw"></a>WideWorldImportersDW で生成されたインポートのデータ

WideWorldImportersDW OLAP データベースの現在の日付までのサンプル データをインポートするには。

1. 前のセクションの手順を使用して、WideWorldImporters OLTP データベースのデータ生成ロジックを実行します。
2. まだ行っていない、WideWorldImportersDW データベースのクリーン バージョンをインストールします。 インストール手順については、次を参照してください。[インストールと構成](wide-world-importers-oltp-install-configure.md)です。
3. データベースで、次のステートメントを実行することによって、OLAP データベースを再作成します。

    ```sql
    EXECUTE [Application].Configuration_ReseedETL
    ```

4. 実行、*毎日 ETL.ispac* OLAP データベースにデータをインポートする SQL Server Integration Services パッケージです。 ETL ジョブを実行する方法についてを参照してください。 [WideWorldImporters ETL ワークフロー](wide-world-importers-perform-etl.md)です。

## <a name="generate-data-in-wideworldimportersdw-for-performance-testing"></a>パフォーマンス テスト用 WideWorldImportersDW でデータを生成します。

WideWorldImportersDW は、パフォーマンス テスト用データのサイズを増やす任意にできます。 たとえば、クラスター化列ストア インデックスで使用するデータのサイズを増やすことできます。

課題の 1 つは、ダウンロードのサイズをダウンロードする簡単に、大規模なが SQL Server のパフォーマンス機能を示すために十分な大きさに保持します。 たとえば、列ストア インデックスの大きな利点で多数の行を操作する場合にのみ実行できます。 

使用することができます、`Application.Configuration_PopulateLargeSaleTable`プロシージャ内の行の数を増やす、`Fact.Sale`テーブル。 2012 年の 2013 年 1 月 1 日を開始する World Wide Importers の既存のデータとの衝突を回避するには、行が挿入されます。

### <a name="procedure-details"></a>プロシージャの詳細

#### <a name="name"></a>名前

    Application.Configuration_PopulateLargeSaleTable

#### <a name="parameters"></a>パラメーター

  `@EstimatedRowsFor2012` **bigint** (12000000 の既定値) の

#### <a name="result"></a>結果

約、必要な数の行が挿入され、 `Fact.Sale` 2012 年内のテーブルです。 手順 1 日あたり 50,000 行の数に制限します。 このような制限を変更できますが、制限を使用して、テーブルの偶発的な overinflations を回避できます。

プロシージャには、クラスター化列ストアが適用されていないインデックスを作成も適用されます。
