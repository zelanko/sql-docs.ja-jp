---
title: WideWorldImporters OLAP データベース - SQL Server の使用 |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.custom: ''
ms.date: 04/04/2018
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: c386ab66a0084ec2da0508d7ae30f96e75031783
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "33032569"
---
# <a name="wideworldimportersdw-use-of-sql-server-features-and-capabilities"></a>SQL Server の機能と機能の使用を WideWorldImportersDW
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
WideWorldImportersDW については、データ ウェアハウスと分析に適している SQL Server の主な機能の多くを紹介しています。 SQL Server の機能と機能、および WideWorldImportersDW での使用方法の説明の一覧を次に示します。

## <a name="polybase"></a>PolyBase

[SQL Server (2016 以降) に適用されます]

PolyBase を使用すると、人口統計を理解している都市可能性がありますの売上のさらに拡張するための関心のあるに関するパブリック データ セットで WideWorldImportersDW の売上情報を結合します。

サンプル データベースでの PolyBase の使用を有効にするがインストールされているかどうかを確認し、データベースで次のストアド プロシージャを実行します。

    EXEC [Application].[Configuration_ApplyPolybase]

これは、外部テーブルを作成`dbo.CityPopulationStatistics`を Azure blob ストレージでホストされている、米国での市区町村の人口データを含むパブリック データ セットを参照します。 構成プロセスを理解するストアド プロシージャ内のコードを確認することをお勧めしています。 Azure blob ストレージにデータをホストし、一般的なパブリック アクセスから保護する場合は、追加の構成手順を実行する必要があります。 次のクエリは、その外部のデータ セットからデータを返します。

    SELECT CityID, StateProvinceCode, CityName, YearNumber, LatestRecordedPopulation FROM dbo.CityPopulationStatistics;

さらに拡張するための関心のあるどの都市があります。 詳細については、次のクエリが都市の増加率で検索し、大幅な増加は、上位 100 の最大規模の都市を返しますと場所、Wide World importers 社には販売存在することはありません。 クエリでは、リモート テーブルの間の結合`dbo.CityPopulationStatistics`とローカル テーブル`Dimension.City`、およびフィルターをローカル テーブルに関連する`Fact.Sales`です。

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

(フル バージョンのサンプル)

クラスター化列ストア インデックス (CCI) は、ストレージの使用量を削減し、クエリのパフォーマンスを向上させるすべてのファクト テーブルで使用されます。 CCI を使用するとは、ファクト テーブルの場合、基本の記憶域は、列の圧縮を使用します。

非クラスター化インデックスは、上、クラスター化列ストア インデックスに主キーと外部キー制約を容易にするために使用されます。 これらの制約は、注意の豊富なから追加された - ETL プロセスの整合性を強制する制約があります WideWorldImporters データベースからのデータのソースします。 主キーと外部キー制約、およびその関連インデックスを削除すると、ファクト テーブルのストレージの使用量が削減できます。

**データのサイズ**

サンプル データベースには、ダウンロードして、サンプルをインストールするが簡単に、データのサイズが制限されています。 ただし、列ストア インデックスの実際のパフォーマンスの利点を表示するには、大きなデータ セットを使用するとします。

サイズを増やすには、次のステートメントを実行することができます、`Fact.Sales`サンプル データの別の 12 の 100万行を挿入することによってテーブル。 これらの行がすべて挿入、2012 年の ETL プロセスに干渉がないようにします。

    EXECUTE [Application].[Configuration_PopulateLargeSaleTable]

このステートメントを実行するには約 5 分になります。 12 100万以上の行を挿入するには、このストアド プロシージャのパラメーターとして挿入する行の必要な数を渡します。

および列ストアを使用せずに、クエリのパフォーマンスを比較するには、削除したり、クラスター化列ストア インデックスを再作成することができます。

インデックスを削除します。

    DROP INDEX [CCX_Fact_Order] ON [Fact].[Order]

再作成します。

    CREATE CLUSTERED COLUMNSTORE INDEX [CCX_Fact_Order] ON [Fact].[Order]

## <a name="partitioning"></a>[パーティション分割]

(フル バージョンのサンプル)

データ ウェアハウスにデータのサイズは非常に大きくなることができます。 そのためお勧めをパーティション分割を使用して、データベース内の大きなテーブルのストレージを管理します。

すべてのファクト テーブルのサイズは、年でパーティション分割されます。 唯一の例外は`Fact.Stock Holdings`日付に基づくが、ない場合、制限付きでデータ サイズが、他のファクト テーブルで比較します。

すべてのパーティション分割されたテーブルに使用されるパーティション関数は`PF_Date`、使用されているパーティション スキームが`PS_Date`です。

## <a name="in-memory-oltp"></a>インメモリ OLTP

(フル バージョンのサンプル)

WideWorldImportersDW は、SCHEMA_ONLY メモリ最適化テーブルをステージング テーブルを使用します。 すべて`Integration.` * `_Staging`テーブルは、SCHEMA_ONLY メモリ最適化テーブル。

SCHEMA_ONLY テーブルの利点は記録されず、ディスク アクセスは必要ありません。 これにより、ETL プロセスのパフォーマンスが向上します。 これらのテーブルがログオンしていないのでエラーが発生した場合、内容は失われます。 ただし、ETL プロセスは、障害が発生した場合にだけで再起動するようには、データ ソースが引き続き使用できます。
