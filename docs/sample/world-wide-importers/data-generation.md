---
title: "データ生成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/30/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.prod: sql-non-specified
ms.technology:
- " database-engine "
ms.topic: article
ms.assetid: f387273b-8b5f-4687-b033-09499ea2d68f
caps.latest.revision: 4
author: BarbKess
ms.author: barbkess
manager: jhubbard
robots: noindex,nofollow
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: c17ad40220d46ab6e19054818ce2abfdce7251f4
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="wideworldimporters-data-generation"></a>WideWorldImporters データの生成
WideWorldImporters と WideWorldImportersDW データベースのリリース バージョンには、年 1 月 1 日の 2013、最大 1 日に、これらのデータベースが生成されたデータが含まれています。

サンプル データベースが、後で、デモや図の目的で使用されている場合は、データベースに最新のサンプル データを含めると役に立つ場合があります。

## <a name="data-generation-in-wideworldimporters"></a>WideWorldImporters でデータの生成

現在の日付までのサンプル データを生成するには、次の手順を実行します。

1. まだいない場合は、WideWorldImporters データベースのクリーン バージョンをインストールします。 インストール手順については、 **WideWorldImporters インストールと構成**です。
2. データベースで、次のステートメントを実行します。

```
    EXECUTE DataLoadSimulation.PopulateDataToCurrentDate
        @AverageNumberOfCustomerOrdersPerDay = 60,
        @SaturdayPercentageOfNormalWorkDay = 50,
        @SundayPercentageOfNormalWorkDay = 0,
        @IsSilentMode = 1,
        @AreDatesPrinted = 1;
```

このステートメントは、現在の日付まで、データベース内のサンプルの売上および注文書データを追加します。 データの進行状況は生成によって日が出力されます。 かかります rougly データが必要なすべての年を 10 分です。 データ生成時に、ランダムな要素があるため、実行間で生成されたデータにいくつか違いがあることに注意してください。

パラメーターの値を変更する、1 日の注文の観点から生成されたデータの量を増減する`@AverageNumberOfCustomerOrdersPerDay`です。 パラメーター`@SaturdayPercentageOfNormalWorkDay`と`@SundayPercentageOfNormalWorkDay`週末の曜日に注文量を決定するために使用します。

## <a name="importing-generated-data-in-wideworldimportersdw"></a>WideWorldImportersDW で生成されたデータをインポートします。

OLAP データベース WideWorldImportersDW 内の現在の日付までのサンプル データをインポートするには、次の手順を実行します。

1. 上記の手順を使用して、WideWorldImporters OLTP データベースにデータ生成ロジックを実行します。
2. まだいない場合は、WideWorldImportersDW データベースのクリーン バージョンをインストールします。 インストール手順については、 **WideWorldImporters インストールと構成**です。
3. データベースで、次のステートメントを実行することによって、OLAP データベースを再作成します。

```
    EXECUTE [Application].Configuration_ReseedETL
```

4. SSIS パッケージを実行**毎日 ETL.ispac** OLAP データベースにデータをインポートします。 ETL ジョブを実行する方法については、次を参照してください。 **WideWorldImporters ETL ワークフロー**です。

## <a name="generating-data-in-wideworldimportersdw-for-performance-testing"></a>パフォーマンス テスト用 WideWorldImportersDW でデータを生成します。

WideWorldImportersDW 任意パフォーマンス テスト、たとえばクラスター化列ストアにするために、データのサイズを増やし機能が備わっています。

サイズを小さく、ダウンロードの十分な配布が、SQL Server のパフォーマンス機能を示すことができる十分な大きさにする World Wide Importers のようにサンプルを送るときの課題の 1 つです。 1 つの領域が、これは、特定の課題は、列ストア インデックスを使用する場合。 大きな利点は、多数の行を使用する場合にのみ付属します。 

プロシージャ`Application.Configuration_PopulateLargeSaleTable`内の行の数が大幅に増加するために使用する、`Fact.Sale`テーブル。 2013 年 1 月 1 日で始まる既存の World Wide Importers データとの衝突を回避する 2012 年間、行が挿入されることに注意してください。

### <a name="procedure-details"></a>プロシージャの詳細

#### <a name="name"></a>名前 : 

    Application.Configuration_PopulateLargeSaleTable

#### <a name="parameters"></a>パラメーター:

  `@EstimatedRowsFor2012`**bigint** (12000000 の既定値) の

#### <a name="result"></a>結果:

約、必要な数の行が挿入され、 `Fact.Sale` 2012 年内のテーブルです。 プロシージャ 50000 1 日あたりの行の数に制限します。 これにより、変更する可能性がありますを誤って overinflations テーブルを回避するのにはあります。

さらに、プロシージャは既に適用されていない場合のようにクラスター化列ストア インデックスの作成を適用します。

