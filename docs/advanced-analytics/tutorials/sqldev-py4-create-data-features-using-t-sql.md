---
title: "手順 4: T-SQL を使用してデータ機能を作成する | Microsoft Docs"
ms.custom: 
ms.date: 10/17/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: 
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: tutorial
applies_to:
- SQL Server 2017
dev_langs:
- Python
- TSQL
ms.assetid: 
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.openlocfilehash: 3adcfd4a53da9f0e61c7ae62d1367cff48194782
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2018
---
# <a name="step-4-create-data-features-using-t-sql"></a>手順 4: T-SQL を使用してデータ機能を作成する
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

データ探索後から、データをある程度の知見を収集および上に移動する準備が整いました*機能のエンジニア リング*です。 生データから機能を作成するには、このプロセスは、高度な分析のモデリングの重要なステップを指定できます。

この記事では、チュートリアルのパート[SQL 開発者のためのデータベースでの Python analytics](sqldev-in-database-python-for-sql-developers.md)です。 

この手順では、 [!INCLUDE[tsql](../../includes/tsql-md.md)] 関数を利用し、生データから機能を作成する方法について説明します。 その後、その関数をストアド プロシージャから呼び出し、機能の値を含むテーブルを作成します。

## <a name="define-the-function"></a>関数を定義する

元のデータで報告されている距離の値は報告されたメーター距離に基づき、必ずしも地理的距離や走行距離を表しません。 そのため、ソースである NYC タクシー データセットの座標を利用し、乗車地点と降車地点の間の直接距離を計算する必要があります。 カスタム [関数で](https://en.wikipedia.org/wiki/Haversine_formula) Haversine 式 [!INCLUDE[tsql](../../includes/tsql-md.md)] を利用し、この計算を実行できます。

1 つ目のカスタム T-SQL 関数、 _fnCalculateDistance_を利用し、Haversine 式で距離を計算し、2 つ目のカスタム T-SQL 関数、 _fnEngineerFeatures_を利用し、すべての機能を含むテーブルを作成します。

### <a name="calculate-trip-distance-using-fncalculatedistance"></a>FnCalculateDistance を使用してのトリップ距離を計算します。

1.  このチュートリアルの準備の一環として関数 _fnCalculateDistance_ がダウンロードされ、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に登録されているはずです。 コードを確認してみましょう。
  
    [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]で、 **[プログラミング]**、 **[関数]** 、 **[スカラー値関数]**の順に展開します。
    _fnCalculateDistance_を右クリックし、 **[変更]** を選択し、新しいクエリ ウィンドウで [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトを開きます。
  
    ```SQL
    CREATE FUNCTION [dbo].[fnCalculateDistance] (@Lat1 float, @Long1 float, @Lat2 float, @Long2 float)
    -- User-defined function that calculates the direct distance between two geographical coordinates
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
**Notes:**

- この関数はスカラー値関数であり、事前定義されている種類の単一データ値を返します。
- 乗車場所と降車場所から取得した緯度値と経度値を入力値として受け取ります。 Haversine 式は場所をラジアンに変換し、その値を利用して 2 場所間の直接距離をマイルで計算します。

計算された値をモデルのトレーニングに利用できるテーブルに追加するには、別の関数、 _fnEngineerFeatures_を利用します。

### <a name="save-the-features-using-fnengineerfeatures"></a>使用して機能を保存_fnEngineerFeatures_

1.  カスタム T-SQL 関数、 _fnEngineerFeatures_のコードを再確認します。この関数は、このチュートリアルの一環として自動的に作成されているはずです。
  
    この関数はテーブル値関数であり、複数の列を入力値として受け取り、複数の機能列を含むテーブルを出力します。  この関数の目的は、モデルの構築に利用する機能セットを作成することです。 関数 _fnEngineerFeatures_ は先に作成した T-SQL 関数 _fnCalculateDistance_を呼び出し、乗車場所と降車場所の間の直接距離を取得します。
  
    ```
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
  
2. この関数が動作することを確認するために、それを利用し、メーター距離が 0 であったが、乗車場所と降車場所が異なっていた乗車の地理的距離を計算できます。
  
    ```
        SELECT tipped, fare_amount, passenger_count,(trip_time_in_secs/60) as TripMinutes,
        trip_distance, pickup_datetime, dropoff_datetime,
        dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) AS direct_distance
        FROM nyctaxi_sample
        WHERE pickup_longitude != dropoff_longitude and pickup_latitude != dropoff_latitude and trip_distance = 0
        ORDER BY trip_time_in_secs DESC
    ```
  
    ご覧のとおり、メーターによって報告された距離と地理的距離は常に一致しているわけではありません。 これは、特徴エンジニア リングが重要な理由です。

次の手順では、これらのデータの機能を使用して作成および Python を使用する機械学習モデルをトレーニングする方法を学習します。

## <a name="next-step"></a>次の手順

[手順 5: トレーニングおよび T-SQL を使用して、Python モデルを保存](sqldev-py5-train-and-save-a-model-using-t-sql.md)

## <a name="previous-step"></a>前の手順

[手順 3: データの探索と視覚化](sqldev-py3-explore-and-visualize-the-data.md)


