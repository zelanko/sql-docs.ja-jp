---
title: データマイニングモデルを作成する |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining models, creating
- forecasting [data mining]
- mining models, creating
- clustering [data mining]
- association [data mining]
- data modeling [data mining]
- estimation
- classification [data mining]
ms.assetid: 804b7db3-1f6a-4f73-a81d-bbe02520d7c6
author: minewiskan
ms.author: owend
ms.openlocfilehash: cce03fab2757b366fbe67dc6c68cb3be1c075e3c
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84526462"
---
# <a name="creating-a-data-mining-model"></a>データ マイニング モデルの作成
  データモデリングは、*アルゴリズム*をデータに適用してパターンや傾向を構築するデータマイニングの手順です。 その後、それらのデータを使って追加の分析を行ったり、予測を立てたりすることができます。  
  
 Office 用データ マイニング アドインは、ウィザードによるデータ マイニングをサポートすることで、モデルの作成を簡素化しています。 ウィザードでは、データの分析、相関関係の特定、あらゆる変数の統計的有意性の計算、最適なモデルの自動選択が実行されます。  
  
 この機能は、およびによって提供されるデータマイニングツールと同様に、すべての機能を備えていますが、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ウィザードと使い慣れた Excel インターフェイスを組み合わせることにより、データマイニングの作成、変更、および使用が簡単になります。  
  
## <a name="advanced-data-mining"></a>詳細設定 (データ マイニング)  
 詳細設定ウィザードでは、のデータマイニングアルゴリズムの1つを使用して、Excel に格納されているデータに基づいて新しいデータマイニングモデルを作成でき [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ます。  
  
### <a name="create-mining-structure"></a>マイニング構造の作成  
 マイニング構造の作成ウィザードを使用すると、新しいデータ マイニング構造を構築し、複数のマイニング モデルの基礎として使用できます。 このウィザードには、テスト セットとして使用するデータの一部を確保するオプションが用意されているので、一貫したテスト標準に従って同じデータを使用するすべてのモデルを評価できます。  
  
 [SQL Server データマイニングアドイン &#40;マイニング構造の作成&#41;](create-mining-structure-sql-server-data-mining-add-ins.md)  
  
### <a name="add-model-to-structure"></a>構造へのモデルの追加  
 構造へのモデルの追加ウィザードを使用すると、既存のデータ マイニング構造を選択して、その構造に使用する新しいデータ マイニング モデルを作成できます。 複数のマイニング モデルを構造に追加し、パラメーターを変更するか、別のデータ マイニング アルゴリズムを選択して、出力をカスタマイズできます。  
  
 [Excel 用データマイニングアドイン &#40;構造へのモデルの追加&#41;](add-model-to-structure-data-mining-add-ins-for-excel.md)  
  
## <a name="analyze-key-influencers-analyze"></a>主要な影響元の分析 (分析)  
 目的の列または出力値を選択すると、アルゴリズムがすべての入力データを分析して、対象に最大の影響を与えている要因を特定します。 必要に応じて、2 つの値を比較するレポートを作成できます。これにより、影響元がどのように変化するかを確認できます。  
  
 **主要影響**元の分析ツールでは、Microsoft の単純 Bayes アルゴリズムが使用されます。  
  
 [Excel 用のテーブル分析ツール &#40;主要な影響元の分析&#41;](analyze-key-influencers-table-analysis-tools-for-excel.md)  
  
## <a name="associate-data-mining"></a>アソシエーション (データ マイニング)  
 **関連付け**ウィザードでは、マーケットバスケット分析などで、複数のトランザクションに出現する項目間の関連付けを検出するアソシエーションモデルを構築します。  
  
 [関連付けウィザード &#40;Excel 用データマイニングクライアント&#41;](associate-wizard-data-mining-client-for-excel.md)  
  
## <a name="classify-data-mining"></a>分類 (データ マイニング)  
 **分類**ウィザードでは、ターゲットの結果に寄与する要因を分析する分類モデルを構築します。 このウィザードでは、デシジョン ツリー、Naïve Bayes、ニューラル ネットワークを含む複数のアルゴリズムを使用できます。  
  
 [分類ウィザード &#40;Excel 用データマイニングアドイン&#41;](classify-wizard-data-mining-add-ins-for-excel.md)  
  
## <a name="cluster-data-mining"></a>クラスター (データ マイニング)  
 **クラスター**ウィザードは、類似した特性を共有する行グループを検出するクラスターモデルを構築します。 クラスタリング (*セグメンテーション*と呼ばれることもあります) は、新しいデータのパターンとグループ化について理解する際に非常に役立つ教師なし学習手法です。  
  
 Microsoft クラスタリング アルゴリズムは、K-Means および Expectation Maximization (EM) クラスタリング両方について、複数の種類をサポートします。  
  
 [クラスターウィザードでは、Excel 用データマイニングアドイン &#40;&#41;](cluster-wizard-data-mining-add-ins-for-excel.md)ます。  
  
## <a name="detect-categories-analyze"></a>カテゴリの検出 (分析)  
 **カテゴリの検出**ツールを使用すると、データセットを追加し、クラスタリングを適用してデータのグループを検索できます。 類似点を見つけて、さらに分析するグループを作成する場合に便利です。  
  
 **カテゴリの検出**ツールは、Microsoft クラスタリングアルゴリズムを使用します。  
  
 [Excel 用のテーブル分析ツール &#40;のカテゴリの検出&#41;](detect-categories-table-analysis-tools-for-excel.md)  
  
## <a name="estimate-data-mining"></a>推定 (データ マイニング)  
 推定ウィザードを使用すると、データのパターンを抽出し、そのパターンを基に、連続する数値、日付、または時刻の値を予測する推定モデルを構築できます。 [!INCLUDE[msCoName](../includes/msconame-md.md)] のデシジョン ツリー アルゴリズムが使用されます。  
  
 [推定ウィザード &#40;Excel 用データマイニングアドイン&#41;](estimate-wizard-data-mining-add-ins-for-excel.md)  
  
## <a name="fill-from-example-analyze"></a>自動推論 (分析)  
 **Fill From サンプル**ツールを使用すると、欠損値を埋め込むことができます。 不足値の例をいくつか指定すると、このツールはテーブル内のすべてのデータに基づいてパターンを作成し、データのパターンに基づいて新しい値を推奨します。  
  
 **Fill From サンプル**ツールは、Microsoft ロジスティック回帰アルゴリズムを使用します。  
  
 [例 &#40;Excel 用のテーブル分析ツール&#41;](fill-from-example-table-analysis-tools-for-excel.md)  
  
## <a name="forecast-analyze"></a>予測 (分析)  
 **予測**ツールは、時間の経過と共に変化するデータを取得し、将来の値を予測します。  
  
 **予測**ツールでは、Microsoft タイムシリーズアルゴリズムが使用されます。  
  
 [Excel 用のテーブル分析ツールの予測 &#40;&#41;](forecast-table-analysis-tools-for-excel.md)  
  
## <a name="forecast-data-mining"></a>予測 (データ マイニング)  
 **予測**ウィザードでは、一連のセルのパターンを検出し、追加の値を予測する予測モデルを作成します。  
  
 [予測ウィザード &#40;Excel 用データマイニングアドイン&#41;](forecast-wizard-data-mining-add-ins-for-excel.md)  
  
## <a name="highlight-exceptions-analyze"></a>例外の強調表示 (分析)  
 **例外の強調表示**ツールは、データのテーブル内のパターンを分析し、パターンに合わない行と値を見つけます。 ユーザーは、これらの値を確認し、修正してモデルを再実行することも、後で処理するためにこれらの値にフラグを設定することもできます。  
  
 **例外の強調表示**ツールは、Microsoft クラスタリングアルゴリズムを使用します。  
  
 [Excel 用のテーブル分析ツール &#40;例外を強調表示&#41;](highlight-exceptions-table-analysis-tools-for-excel.md)  
  
## <a name="prediction-calculator-analyze"></a>予測計算ツール (分析)  
 このツールは、目標の結果の達成につながる要因を分析し、これらのパターンから派生した基準に基づいて新しい入力の結果を予測するモデルを作成します。また、新しい入力を簡単にスコアするために役立つ対話形式の意思決定ワークシートを生成します。 ユーザーは、オフラインで使用できるスコアリング ワークシートの印刷バージョンを作成することもできます。  
  
 **予測計算**ツールでは、Microsoft ロジスティック回帰アルゴリズムが使用されます。  
  
 [予測計算 &#40;Excel 用のテーブル分析ツール&#41;](prediction-calculator-table-analysis-tools-for-excel.md)  
  
## <a name="scenario-goal-seek-analyze"></a>シナリオ: ゴール シーク (分析)  
 **ゴールシーク**ツールでは、ターゲット値を指定します。このツールは、そのターゲットを満たすために変更する必要がある基になる要因を識別します。 たとえば、電話対応満足度を 20% 向上させる必要がある場合、その目標を達成するために変更する必要のある要因を予測するようモデルに要求できます。  
  
 **ゴールシーク**ツールは、Microsoft ロジスティック回帰アルゴリズムを使用します。  
  
 details  
  
 [ゴールシークシナリオ &#40;Excel 用のテーブル分析ツール&#41;](goal-seek-scenario-table-analysis-tools-for-excel.md)  
  
## <a name="scenario-what-if-scenario-analyze"></a>シナリオ: What-If シナリオ(分析)  
 **What-if 分析**ツールは、**ゴールシーク**ツールを補完します。 このツールで変更する必要のある値を入力すると、モデルはその変更が目標の結果を達成するために十分であるかどうかを予測します。 たとえば、電話オペレーターを 1 人追加することによって顧客満足度が 1 ポイント向上するかどうかを推測するようモデルに要求できます。  
  
 **What-if**ツールは、Microsoft ロジスティック回帰アルゴリズムを使用します。  
  
 [What-if シナリオ &#40;Excel 用のテーブル分析ツール&#41;](what-if-scenario-table-analysis-tools-for-excel.md)  
  
## <a name="shopping-basket-analysis-analyze"></a>買い物かご分析 (分析)  
 **買い物かご分析**ツールでは、同時に購入される頻度の高い製品のグループを作成して、クロスセルやアップセルで使用できるパターンを特定します。 また、意思決定の際に役立つ、関連する製品バンドルの価格とコストに基づくレポートを生成します。  
  
 このツールは、頻繁に同時発生するイベント、診断につながる要因、またはその他の考えられる原因と結果のセットを特定するために使用することもできます。  
  
 **買い物かご分析**ツールでは、Microsoft アソシエーションアルゴリズムが使用されます。  
  
 [買い物かご分析 &#40;テーブル AnalysisTools for Excel&#41;](shopping-basket-analysis-table-analysistools-for-excel.md)  
  
## <a name="see-also"></a>参照  
 [データの探索とクリーンアップ](exploring-and-cleaning-data.md)   
 [Excel 用データマイニングアドインのモデルを検証し、モデルを使用して予測 &#40;する&#41;](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md)   
 [Excel 用データマイニングアドイン &#40;のマイニングモデルの配置とスケーリング&#41;](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md)  
  
  
