---
title: WideWorldImporters データ - SQL サンプル データベースの生成 |Microsoft Docs
ms.custom: ''
ms.date: 04/04/2018
ms.reviewer: ''
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 38ba117051ad10d788c2357dfb70d36c2b5e50d1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68091268"
---
# <a name="wideworldimporters-data-generation"></a>WideWorldImporters データ生成
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
、2013 年 1 月 1日最大のデータベースが生成された 1 日からのデータは、WideWorldImporters と WideWorldImportersDW データベースのリリース バージョンであります。

これらのサンプル データベースを使用する場合は、最新のサンプル データが含まれます。

## <a name="data-generation-in-wideworldimporters"></a>WideWorldImporters でデータの生成

現在の日付までのサンプル データを生成するには。

1. これを完了していない場合は、WideWorldImporters データベースのクリーン バージョンをインストールします。 インストール手順については、次を参照してください。[インストールと構成](wide-world-importers-oltp-install-configure.md)します。
2. データベースでは、次のステートメントを実行します。

    ```
        EXECUTE DataLoadSimulation.PopulateDataToCurrentDate
            @AverageNumberOfCustomerOrdersPerDay = 60,
            @SaturdayPercentageOfNormalWorkDay = 50,
            @SundayPercentageOfNormalWorkDay = 0,
            @IsSilentMode = 1,
            @AreDatesPrinted = 1;
    ```

    このステートメントは、サンプルの売上および注文データを現在の日付まで、データベースに追加します。 日別に、データ生成の進行状況を表示します。 データの生成は、データが必要なすべての年の約 10 分かかります。 データ生成、ランダムな要素のための実行の間に生成されるデータにいくつか違いがあります。

    1 日の注文に対して生成されたデータの量を増減するには、パラメーターの値を変更する`@AverageNumberOfCustomerOrdersPerDay`します。 パラメーターを使用して`@SaturdayPercentageOfNormalWorkDay`と`@SundayPercentageOfNormalWorkDay`週末の曜日の注文の量を確認します。

## <a name="import-generated-data-in-wideworldimportersdw"></a>WideWorldImportersDW で生成されるインポート データ

WideWorldImportersDW OLAP データベースの現在の日付までのサンプル データをインポートするには。

1. 前のセクションで手順を使用して、WideWorldImporters OLTP データベースのデータの生成ロジックを実行します。
2. 場合は、まだ完了していない、WideWorldImportersDW のデータベースのクリーン バージョンをインストールします。 インストール手順については、次を参照してください。[インストールと構成](wide-world-importers-oltp-install-configure.md)します。
3. データベースで、次のステートメントを実行することによって OLAP データベースを再作成します。

    ```sql
    EXECUTE [Application].Configuration_ReseedETL
    ```

4. 実行、*毎日 ETL.ispac* OLAP データベースにデータをインポートする SQL Server Integration Services パッケージ。 ETL ジョブを実行する方法についてを参照してください。 [WideWorldImporters ETL ワークフロー](wide-world-importers-perform-etl.md)します。

## <a name="generate-data-in-wideworldimportersdw-for-performance-testing"></a>WideWorldImportersDW でパフォーマンスをテストするためのデータを生成します。

WideWorldImportersDW は、パフォーマンスをテストするためのデータのサイズを増やす任意にできます。 たとえば、クラスター化列ストア インデックスで使用するデータのサイズを増やすことできます。

ダウンロードする簡単に、大規模なが、SQL Server のパフォーマンス機能を紹介するのに十分な大きさのダウンロードのサイズを保つの課題の 1 つです。 たとえば、列ストア インデックスの大きな利点がでより多くの行を使用する場合にのみ実行できます。 

使用することができます、`Application.Configuration_PopulateLargeSaleTable`プロシージャ内の行の数を増やす、`Fact.Sale`テーブル。 2013 年 1 月 1 日を開始する World Wide Importers の既存のデータとの衝突を回避するために、2012 年の行が挿入されます。

### <a name="procedure-details"></a>プロシージャの詳細

#### <a name="name"></a>名前

    Application.Configuration_PopulateLargeSaleTable

#### <a name="parameters"></a>パラメーター

  `@EstimatedRowsFor2012` **bigint** (12000000 の既定値) の使用

#### <a name="result"></a>結果

行の約必要な数の挿入、 `Fact.Sale` 2012 年のテーブル。 手順 1 日あたり 50,000 行の数に制限しています。 このような制限を変更できますが、制限を使用して、テーブルの偶発的な overinflations を回避できます。

プロシージャには、クラスター化列ストアが適用されていない場合のインデックス作成も適用されます。
