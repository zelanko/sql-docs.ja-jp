---
title: レッスン 2 のデータの作成機能が T-SQL 関数 (SQL Server Machine Learning) の使用 |Microsoft Docs
description: SQL Server に R を埋め込む方法を示すチュートリアルはストアド プロシージャと T-SQL 関数
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/19/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: f5427772ea438a198b1236a865e8cdbdd0b09d70
ms.sourcegitcommit: 3cd6068f3baf434a4a8074ba67223899e77a690b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/19/2018
ms.locfileid: "49462098"
---
# <a name="lesson-2-create-data-features-using-r-and-t-sql"></a>レッスン 2: R と T-SQL を使用してデータ機能を作成します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、SQL Server で R を使用する方法に関する SQL 開発者向けのチュートリアルの一部です。

この手順では、 [!INCLUDE[tsql](../../includes/tsql-md.md)] 関数を利用し、生データから機能を作成する方法について説明します。 その後、その関数をストアド プロシージャから呼び出し、機能の値を含むテーブルを作成します。

## <a name="about-feature-engineering"></a>特徴エンジニア リングについて

データ探索を何度か行うと、データからインサイトが収集されているので、 *機能エンジニアリング*に移ることができます。 生データから意味のある機能を作成するには、このプロセスは、分析モデルの作成で重要な手順です。

、このデータセットでは、距離の値は、報告されたメーター距離に基づいており、地理的距離や実際の距離を表すしないとは限りません。 そのため、ソースである NYC タクシー データセットの座標を利用し、乗車地点と降車地点の間の直接距離を計算する必要があります。 カスタム [関数で](https://en.wikipedia.org/wiki/Haversine_formula) Haversine 式 [!INCLUDE[tsql](../../includes/tsql-md.md)] を利用し、この計算を実行できます。

1 つ目のカスタム T-SQL 関数、 _fnCalculateDistance_を利用し、Haversine 式で距離を計算し、2 つ目のカスタム T-SQL 関数、 _fnEngineerFeatures_を利用し、すべての機能を含むテーブルを作成します。

プロセス全体は次のとおりです。

- 計算を実行する T-SQL 関数を作成します。

- 機能データを生成する関数を呼び出す

- 機能データをテーブルに保存します。

## <a name="calculate-trip-distance-using-fncalculatedistance"></a>FnCalculateDistance を使用して、乗車距離を計算します。

関数は、 _fnCalculateDistance_する必要がありますをダウンロードして登録されている[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]このチュートリアルの準備の一環として。 時間がかかるコードを確認します。
  
1. [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]で、 **[プログラミング]**、 **[関数]** 、 **[スカラー値関数]** の順に展開します。   

2. _fnCalculateDistance_を右クリックし、 **[変更]** を選択し、新しいクエリ ウィンドウで [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトを開きます。
  
    ```SQL
    CREATE FUNCTION [dbo].[fnCalculateDistance] (@Lat1 float, @Long1 float, @Lat2 float, @Long2 float)  
    -- User-defined function that calculates the direct distance between two geographical coordinates.  
    RETURNS float  
    AS  
    BEGIN  
      DECLARE @distance decimal(28, 10)  
      -- Convert to radians  
      SET @Lat1 = @Lat1 / 57.2958  
      SET @Long1 = @Long1 / 57.2958  
      SET @Lat2 = @Lat2 / 57.2958  
      SET @Long2 = @Long2 / 57.2958  
      -- Calculate distance  
      SET @distance = (SIN(@Lat1) * SIN(@Lat2)) + (COS(@Lat1) * COS(@Lat2) * COS(@Long2 - @Long1))  
      --Convert to miles  
      IF @distance <> 0  
      BEGIN  
        SET @distance = 3958.75 * ATAN(SQRT(1 - POWER(@distance, 2)) / @distance);  
      END  
      RETURN @distance  
    END
    GO
    ```
  
    - この関数はスカラー値関数であり、事前定義されている種類の単一データ値を返します。
  
    - 乗車場所と降車場所から取得した緯度値と経度値を入力値として受け取ります。 Haversine 式は場所をラジアンに変換し、その値を利用して 2 場所間の直接距離をマイルで計算します。

## <a name="generate-the-features-using-fnengineerfeatures"></a>使用して特徴を生成_fnEngineerFeatures_

計算値をモデルのトレーニングに使用できるテーブルを追加するには、別の関数を使用します_fnEngineerFeatures_します。 以前に作成した T-SQL 関数を呼び出し、新しい関数_fnCalculateDistance_乗車と降車場所間の直線距離を取得します。 

1. カスタム T-SQL 関数、 _fnEngineerFeatures_のコードを再確認します。この関数は、このチュートリアルの一環として自動的に作成されているはずです。
  
    ```SQL
    CREATE FUNCTION [dbo].[fnEngineerFeatures] (  
    @passenger_count int = 0,  
    @trip_distance float = 0,  
    @trip_time_in_secs int = 0,  
    @pickup_latitude float = 0,  
    @pickup_longitude float = 0,  
    @dropoff_latitude float = 0,  
    @dropoff_longitude float = 0)  
    RETURNS TABLE  
    AS
      RETURN
      (
      -- Add the SELECT statement with parameter references here
      SELECT
        @passenger_count AS passenger_count,
        @trip_distance AS trip_distance,
        @trip_time_in_secs AS trip_time_in_secs,
        [dbo].[fnCalculateDistance](@pickup_latitude, @pickup_longitude, @dropoff_latitude, @dropoff_longitude) AS direct_distance
  
      )
    GO
    ```

    + このテーブル値関数を入力として複数の列を受け取り、複数の機能列がテーブルに出力します。

    + この関数の目的は、モデルの構築に使用するための新機能を作成します。

2.  この関数が動作することを確認するために使用するメーター距離が 0 が乗車と降車の場所が異なっていた乗車の地理的距離を計算します。
  
    ```SQL
        SELECT tipped, fare_amount, passenger_count,(trip_time_in_secs/60) as TripMinutes,
        trip_distance, pickup_datetime, dropoff_datetime,
        dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) AS direct_distance
        FROM nyctaxi_sample
        WHERE pickup_longitude != dropoff_longitude and pickup_latitude != dropoff_latitude and trip_distance = 0
        ORDER BY trip_time_in_secs DESC
    ```
  
    ご覧のとおり、メーターによって報告された距離と地理的距離は常に一致しているわけではありません。 そのため、機能エンジニアリングが重要となります。 これらの機能の強化されたデータを使用して R を使用する機械学習モデルをトレーニングすることができます。

## <a name="next-lesson"></a>次のレッスン

[レッスン 3: トレーニングし、T-SQL を使用してモデルを保存](sqldev-train-and-save-a-model-using-t-sql.md)

## <a name="previous-lesson"></a>前のレッスン

[レッスン 1: の探索し、R とストアド プロシージャを使用してデータを視覚化します。](sqldev-explore-and-visualize-the-data.md)
