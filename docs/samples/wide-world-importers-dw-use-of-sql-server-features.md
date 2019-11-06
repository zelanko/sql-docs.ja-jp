---
title: WideWorldImporters OLAP データベース - SQL Server の使用 |Microsoft Docs
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.custom: ''
ms.date: 08/04/2018
ms.reviewer: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
monikerRange: '>=sql-server-2016||>=sql-server-linux-2017||=azure-sqldw-latest||>=aps-pdw-2016||=sqlallproducts-allversions||=azuresqldb-mi-current'
ms.openlocfilehash: 313f85c5d5ec3590e231bdac4a746318c927a33a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68104225"
---
# <a name="wideworldimportersdw-use-of-sql-server-features-and-capabilities"></a>SQL Server の機能と機能の WideWorldImportersDW の使用
[!INCLUDE[appliesto-ss-xxxx-asdw-pdw-md](../includes/appliesto-ss-xxxx-asdw-pdw-md.md)]
データ ウェアハウスと分析に適している SQL Server の主な機能の多くを紹介することは、WideWorldImportersDW は設計されています。 次に SQL Server の機能と機能、および WideWorldImportersDW での使用方法の説明の一覧を示します。

## <a name="polybase"></a>PolyBase

[SQL Server (2016 以降) に適用されます]

PolyBase を使用して、売上のさらに拡張するための役立つことがある都市を理解するには、人口統計データについてのパブリック データ セットで WideWorldImportersDW の売上情報を結合します。

PolyBase を使用してをサンプル データベースを有効にするがインストールされているかどうかを確認し、データベースで次のストアド プロシージャを実行します。

    EXEC [Application].[Configuration_ApplyPolyBase]

これは外部テーブルを作成`dbo.CityPopulationStatistics`Azure blob ストレージでホストされている米国の都市の人口データを含むパブリック データ セットを参照します。 構成プロセスを理解するストアド プロシージャでコードを確認することが推奨されます。 Azure blob storage にデータをホストし、汎用パブリック アクセスから保護する場合は、追加の構成手順を実行する必要があります。 次のクエリでは、その外部データ セットからデータを返します。

    SELECT CityID, StateProvinceCode, CityName, YearNumber, LatestRecordedPopulation FROM dbo.CityPopulationStatistics;

さらに拡張するための関心のあるどの都市があります。 詳細については、次のクエリが都市の成長率で検索し、大幅な増加は、上位 100 件の最大規模の都市を返します場所、Wide World importers 社には販売の存在はありません。 クエリは、リモートのテーブル間の結合`dbo.CityPopulationStatistics`とローカル テーブル`Dimension.City`、およびローカル テーブルに関連するフィルター`Fact.Sales`します。

    WITH PotentialCities
    AS
    (
        SELECT cps.CityName,
               cps.StateProvinceCode,
               MAX(cps.LatestRecordedPopulation) AS PopulationIn2016,
               (MAX(cps.LatestRecordedPopulation) - MIN(cps.LatestRecordedPopulation)) * 100.0
                   / MIN(cps.LatestRecordedPopulation) AS GrowthRate
        FROM dbo.CityPopulationStatistics AS cps
        WHERE cps.LatestRecordedPopulation IS NOT NULL
        AND cps.LatestRecordedPopulation <> 0
        GROUP BY cps.CityName, cps.StateProvinceCode
    ),
    InterestingCities
    AS
    (
        SELECT DISTINCT pc.CityName,
                        pc.StateProvinceCode,
                        pc.PopulationIn2016,
                        FLOOR(pc.GrowthRate) AS GrowthRate
        FROM PotentialCities AS pc
        INNER JOIN Dimension.City AS c
        ON pc.CityName = c.City
        WHERE GrowthRate > 2.0
        AND NOT EXISTS (SELECT 1 FROM Fact.Sale AS s WHERE s.[City Key] = c.[City Key])
    )
    SELECT TOP(100) CityName, StateProvinceCode, PopulationIn2016, GrowthRate
    FROM InterestingCities
    ORDER BY PopulationIn2016 DESC;

## <a name="clustered-columnstore-indexes"></a>クラスター化列ストア インデックス

(完全なバージョンのサンプル)

クラスター化列ストア インデックス (CCI) は、ストレージのフット プリントを削減し、クエリのパフォーマンスを向上させるすべてのファクト テーブルで使用されます。 CCI を使用するとは、ファクト テーブルの基本の記憶域は、列の圧縮を使用します。

非クラスター化インデックスは、主キーと外部キー制約を容易にするためにクラスター化列ストア インデックスに加えて使用されます。 これらの制約は、豊富な注意が必要ですから追加された - ETL プロセスの整合性を強制する制約があります WideWorldImporters データベースからデータのソースします。 主キーと外部キー制約、およびサポートのインデックスを削除すると、ファクト テーブルのストレージ フット プリントが低くなります。

**データ サイズ**

サンプル データベースをダウンロードして、サンプルをインストールするは簡単にし、データのサイズが制限されています。 ただし、列ストア インデックスの実際のパフォーマンスの利点を表示するには、大きなデータ セットを使用するとします。

サイズを増やすには、次のステートメントを実行することができます、`Fact.Sales`別の 12 の 100万行のサンプル データを挿入することでテーブル。 これらの行はすべて挿入 2012 年の ETL プロセスに干渉がないようにします。

    EXECUTE [Application].[Configuration_PopulateLargeSaleTable]

このステートメントを実行するまでに約 5 分になります。 1,200万件を超える行を挿入するには、このストアド プロシージャにパラメーターとして挿入する行の必要な数を渡します。

列ストアなしのクエリのパフォーマンスを比較するには、削除したり、クラスター化列ストア インデックスを再作成できます。

インデックスを削除します。

    DROP INDEX [CCX_Fact_Order] ON [Fact].[Order]

再作成します。

    CREATE CLUSTERED COLUMNSTORE INDEX [CCX_Fact_Order] ON [Fact].[Order]

## <a name="partitioning"></a>[パーティション分割]

(完全なバージョンのサンプル)

Data Warehouse でのデータのサイズは非常に大きくなることができます。 そのために、パーティション分割を使用して、データベース内の大きなテーブルのストレージを管理するベスト プラクティスを勧めします。

年では、すべての大規模なファクト テーブルがパーティション分割します。 唯一の例外は`Fact.Stock Holdings`日付に基づくが、ない場合が制限されたデータのサイズは、その他のファクト テーブルと比較します。

すべてのパーティション テーブルに使用されるパーティション関数は`PF_Date`、使用されているパーティション スキームが`PS_Date`します。

## <a name="in-memory-oltp"></a>インメモリ OLTP

(完全なバージョンのサンプル)

WideWorldImportersDW は、ステージング テーブルを SCHEMA_ONLY メモリ最適化テーブルを使用します。 すべて`Integration.` * `_Staging`テーブルは、SCHEMA_ONLY メモリ最適化テーブル。

SCHEMA_ONLY テーブルの利点は記録されず、また、ディスク アクセスを必要としないことです。 これにより、ETL プロセスのパフォーマンスが向上します。 これらのテーブルがログインしていないため、障害が発生した場合は、その内容は失われます。 ただし、データ ソースが引き続き使用できますが、ETL プロセスは、障害が発生した場合に単に再起動させるようにします。
