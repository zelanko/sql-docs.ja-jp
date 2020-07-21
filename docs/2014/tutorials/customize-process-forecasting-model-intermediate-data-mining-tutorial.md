---
title: 予測モデルのカスタマイズと処理 (中級者向けデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 4bd25e15-9d9e-4528-b7bc-ccb856643aec
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d2d0e73d1d9a4058ff63320552604b2bfa1bca8a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "63249402"
---
# <a name="customizing-and-processing-the-forecasting-model-intermediate-data-mining-tutorial"></a>予測モデルのカスタマイズと処理 (中級者向けデータ マイニング チュートリアル)
  [!INCLUDE[msCoName](../includes/msconame-md.md)] タイム シリーズ アルゴリズムには、モデルの作成方法と時間データの分析方法に影響するいくつかのパラメーターがあります。 これらのプロパティを変更すると、マイニング モデルでの予測の作成方法に大きく影響する場合があります。  
  
 このチュートリアルでは、次の作業を行ってモデルを変更します。  
  
1.  *PERIODICITY_HINT*パラメーターに新しい値を追加することで、モデルが期間を処理する方法をカスタマイズします。  
  
2.  Microsoft Time Series アルゴリズムの重要な 2 つのパラメーターについて理解します。FORECAST_METHOD では、予測に使用される方法を制御できます。PREDICTION_SMOOTHING では、長期予測と短期予測の組み合わせをカスタマイズできます。  
  
3.  必要に応じて、不足値を帰属させる方法を指定します。  
  
4.  すべての変更が完了したら、モデルを配置して処理します。  
  
## <a name="setting-time-series-parameters"></a>時系列のパラメーターの設定  
 **周期性のヒント**  
  
 *PERIODICITY_HINT*パラメーターは、データに表示されると予想される追加の期間に関する情報をアルゴリズムに提供します。 時系列モデルでは、既定でデータのパターンの検出が自動的に試行されますが、 予想される周期が既にわかっている場合は、周期性のヒントを指定することでモデルの精度を高めることができます。 ただし、適切でない周期性のヒントを指定すると精度が低下することがあるため、どの値を使用すればよいか確信がない場合は、既定値を使用することをお勧めします。  
  
 たとえば、このモデルで使用されるビューでは、1 か月ごとに [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] から売上データが集計されます。 したがって、このモデルで使用される各タイム スライスは 1 か月を表し、予測もすべて月単位で行われます。 1年に12か月があり、売上パターンが毎年繰り返されることが予想されるため、 *PERIODICITY_HINT*パラメーターをに`12`設定して、12個のタイムスライス (月) が1つの完全な販売サイクルを構成することを示します。  
  
 **予測方法**  
  
 *FORECAST_METHOD*パラメーターは、タイムシリーズアルゴリズムを短期または長期の予測用に最適化するかどうかを制御します。 既定では、 *FORECAST_METHOD*パラメーターは MIXED に設定されています。つまり、2つの異なるアルゴリズムがブレンドされ、短期予測と長期予測の両方に適した結果が得られるようになります。  
  
 ただし、使用するアルゴリズムが決まっている場合は、ARIMA または ARTXP に値を変更することができます。  
  
 **長期的な予測と短期的な予測の重み付け**  
  
 PREDICTION_SMOOTHING パラメーターを使用して、長期予測と短期予測の組み合わせ方法をカスタマイズすることもできます。 既定では、このパラメーターは 0.5 に設定されます。一般には、これが全体的な精度を確保するための最適なバランスです。  
  
#### <a name="to-change-the-algorithm-parameters"></a>アルゴリズム パラメーターを変更するには  
  
1.  [**マイニングモデル**] タブで、[**予測**] を右クリックし、[**アルゴリズムパラメーターの設定**] をクリックします。  
  
2.  `PERIODICITY_HINT` [**アルゴリズムパラメーター** ] ダイアログボックスの行で、[**値**] 列をクリックし`{12}`、「」と入力します (中かっこを含む)。  
  
     既定で、値 {1} も追加されます。  
  
3.  行で、[**値**] テキストボックスが空白であるか、に`MIXED`設定されていることを確認します。 `FORECAST_METHOD` 別の値が入力されている`MIXED`場合は、「」と入力してパラメーターを既定値に戻します。  
  
4.  **PREDICTION_SMOOTHING**の行で、[**値**] テキストボックスが空白であるか、または0.5 に設定されていることを確認します。 別の値を入力した場合は**Value** 、[値`0.5` ] をクリックして、パラメーターを既定値に戻します。  
  
    > [!NOTE]  
    >  PREDICTION_SMOOTHING パラメーターは、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Enterprise Edition でのみ使用できます。 したがって、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Standard Edition では PREDICTION_SMOOTHING パラメーターの値を表示または変更できません。 ただし、既定の動作では両方のアルゴリズムが使用され、同等の重み付けが行われます。  
  
5.  **[OK]** をクリックします。  
  
## <a name="handling-missing-data-optional"></a>不足データの処理 (オプション)  
 売上データに NULL で埋められたギャップ (途切れ) が含まれていたり、店舗からのレポートが期限に間に合わなかったために系列の終了時点で空のセルが残されたりすることがよくあります。 このような場合は、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] から次のエラーが表示されてモデルが処理されません。  
  
 "エラー (データマイニング): マイニングモデル、 \< \<モデル名> の系列系列名> で始まるタイムスタンプが同期されていません。 すべての時系列は同一の時点で終了する必要があります。また、データ消失点をそれぞれが任意に持つこともできません。 MISSING_VALUE_SUBSTITUTION パラメーターを Previous または数値定数に設定すると、可能な場所にデータ消失点が自動的に設定されます。"  
  
 このエラーを回避するには、次のいずれかの方法で、ギャップを埋めるための新しい値が [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] から自動的に提供されるように指定します。  
  
-   平均値を使用する。 平均は、同じデータ系列のすべての有効値を使用して計算されます。  
  
-   前の値を使用する。 複数の不足セルに前の値を割り当てることは可能ですが、開始値を埋めることはできません。  
  
-   指定した定数値を使用する。  
  
#### <a name="to-specify-that-gaps-be-filled-by-averaging-values"></a>値の平均を計算してギャップを埋めるように指定するには  
  
1.  [**マイニングモデル**] タブで、[**予測**] 列を右クリックし、[**アルゴリズムパラメーターの設定**] をクリックします。  
  
2.  [**アルゴリズムパラメーター** ] ダイアログボックスの [ **MISSING_VALUE_SUBSTITUTION** ] 行で、[**値**] 列をクリック`Mean`し、「」と入力します。  
  
## <a name="build-the-model"></a>モデルを構築する  
 モデルを使用するには、サーバーにモデルを配置し、アルゴリズムを使用してトレーニング データを実行することでそのモデルを処理する必要があります。  
  
#### <a name="to-process-the-forecasting-model"></a>予測モデルを処理するには  
  
1.  の [**マイニングモデル**] メニュー [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]で、[**マイニング構造とすべてのモデルの処理**] を選択します。  
  
2.  プロジェクトをビルドして配置するかどうかを確認する警告が表示されたら、[**はい]** をクリックします。  
  
3.  [**マイニング構造の処理-予測**] ダイアログボックスで、[**実行**] をクリックします。  
  
     [**処理の進行状況**] ダイアログボックスが開き、モデルの処理に関する情報が表示されます。 モデルの処理には、時間がかかることがあります。  
  
4.  処理が完了したら、[**閉じる**] をクリックして [**処理の進行状況**] ダイアログボックスを閉じます。  
  
5.  もう一度 [**閉じる**] をクリックして、[**マイニング構造の処理-予測**] ダイアログボックスを閉じます。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [予測モデル &#40;中級者向けデータマイニングチュートリアル&#41;](../../2014/tutorials/exploring-the-forecasting-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>参照  
 [Microsoft タイムシリーズアルゴリズムテクニカルリファレンス](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)   
 [Microsoft タイムシリーズアルゴリズム](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)   
 [処理の要件および注意事項 &#40;データ マイニング&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
  
