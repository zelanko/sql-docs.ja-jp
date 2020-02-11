---
title: Microsoft デシジョンツリーアルゴリズム |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- predictions [Analysis Services], discrete attributes
- predictions [Analysis Services], continuous attributes
- algorithms [data mining]
- discrete attributes [Analysis Services]
- classification algorithms [Analysis Services]
- discrete columns [Analysis Services]
- decision tree algorithms [Analysis Services]
- decision trees [Analysis Services]
- continuous columns
- regression algorithms [Analysis Services]
ms.assetid: 95ffe66f-c261-4dc5-ad57-14d2d73205ff
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7a9adfe74aef16e475d06eddfbe08852f7618518
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66084113"
---
# <a name="microsoft-decision-trees-algorithm"></a>Microsoft デシジョン ツリー アルゴリズム
  [!INCLUDE[msCoName](../../includes/msconame-md.md)]デシジョンツリーアルゴリズムは、不連続属性と連続属性の両方[!INCLUDE[msCoName](../../includes/msconame-md.md)]の予測モデリングで使用するためにによっ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]て提供される分類および回帰アルゴリズムです。  
  
 不連続属性の場合、予測はデータセットの入力列間のリレーションシップに基づいて行われます。 アルゴリズムでは、これらの列の値 (状態) を使用して、予測可能として指定した列の状態が予測されます。 具体的には、予測可能列に相関している入力列が識別されます。 たとえば、どのような顧客が自転車を購入する確率が高いかを予測するシナリオにおいて、若い顧客は 10 人のうち 9 人が自転車を購入するのに対し、中高年の顧客は 10 人のうち 2 人しか購入しない場合、アルゴリズムによって、年齢が自転車購入の適切な予測子であると推定されます。 デシジョン ツリーでは、特定の結果に対するこの傾向に基づいて予測が行われます。  
  
 連続属性の場合、アルゴリズムでは線型回帰を使用して、デシジョン ツリーの分割ポイントが判断されます。  
  
 複数の列が予測可能に設定されている場合、または予測可能に設定されている入れ子になったテーブルが入力データに含まれている場合は、予測可能列ごとに個別のデシジョン ツリーが作成されます。  
  
## <a name="example"></a>例  
 
  [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] 社のマーケティング部では、過去の顧客が製品を将来購入する可能性があるかどうかを示す特性を識別する必要があります。 
  [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] データベースには、過去の顧客に関する人口統計情報が格納されています。 マーケティング部は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] デシジョン ツリー アルゴリズムを使用してこの情報を分析することで、特定の顧客が製品を購入するかどうかを予測するモデルを作成できます。この予測は、人口統計や過去の購入パターンなど、顧客に関する既知の列の状態に基づいて行います。  
  
## <a name="how-the-algorithm-works"></a>アルゴリズムの動作  
 
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] デシジョン ツリー アルゴリズムでは、一連の分割をツリー内に作成することによって、データ マイニング モデルが作成されます。 これらの分割は *ノード*として表されます。 ノードは、入力列が予測可能列に密接に相関していることが認識されるたびに、アルゴリズムによってモデルに追加されます。 アルゴリズムで分割が決定される方法は、連続列と不連続列のどちらを予測するかによって異なります。  
  
 
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] デシジョン ツリー アルゴリズムの *機能の選択* を使用すると、最も役に立つ属性を選択できます。 機能の選択は、すべての [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データ マイニング アルゴリズムにおいて、パフォーマンスと分析の質を高めるために使用されています。 機能の選択は、重要でない属性によってプロセッサ時間が使用されるのを防ぐために重要です。 データ マイニング モデルの設計時に入力属性または予測可能属性を多用しすぎると、モデルの処理に非常に時間がかかったり、メモリが不足する場合があります。 ツリーを分割するかどうかの判断方法には、 *エントロピ* およびベイジアン ネットワーク*に関する業界標準の基準があります。* 重要な属性の選択、スコア計算、および順位付けの方法の詳細については、「[機能の選択 &#40;データ マイニング&#41;](feature-selection-data-mining.md)」を参照してください。  
  
 データマイニングモデルにおける一般的な問題として、モデルがトレーニングデータの小さな違いに敏感になることがあります。この場合は、*過剰適合*または*オーバートレーニング*と呼ばれます。 オーバーフィット モデルは、他のデータセットに一般化することができません。 特定のデータセットへのオーバーフィットを回避するため、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] デシジョン ツリー アルゴリズムでは、ツリーの拡大を制御する手法が使用されます。 
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] デシジョン ツリー アルゴリズムのしくみの詳細については、「 [Microsoft デシジョン ツリー アルゴリズム テクニカル リファレンス](microsoft-decision-trees-algorithm-technical-reference.md)」を参照してください。  
  
### <a name="predicting-discrete-columns"></a>不連続列の予測  
 不連続の予測可能列に対して [!INCLUDE[msCoName](../../includes/msconame-md.md)] デシジョン ツリー アルゴリズムがツリーを作成する方法は、ヒストグラムで示すことができます。 次の図は、予測可能列の "Bike Buyers" を入力列の "Age" と相関させてプロットしたヒストグラムを示しています。 このヒストグラムは、ある顧客が自転車を購入するかどうかは、その人の年齢からある程度判断できることを示しています。  
  
 ![Microsoft デシジョン ツリー アルゴリズムによるヒストグラム](../media/dt-histogram.gif "Microsoft デシジョン ツリー アルゴリズムによるヒストグラム")  
  
 
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] デシジョン ツリー アルゴリズムでは、図のような相関関係に基づいてモデルに新しいノードを作成します。  
  
 ![デシジョン ツリー ノード](../media/dt-tree.gif "デシジョン ツリー ノード")  
  
 アルゴリズムによって新しいノードがモデルに追加されるにつれて、ツリー構造が形成されていきます。 ツリーの最上部ノードには、顧客グループ全体の予測可能列の内訳が記述されます。 モデルが拡大する際、アルゴリズムではすべての列が考慮されます。  
  
### <a name="predicting-continuous-columns"></a>連続列の予測  
 
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] デシジョン ツリー アルゴリズムが連続する予測可能列に基づいてツリーを作成するとき、各ノードには回帰式が含まれます。 分割は、回帰式内の非線形性のポイントで発生します。 たとえば、次の図について検討します。  
  
 ![非線形性を表す複数の回帰線](../media/regression-tree1.gif "非線形性を表す複数の回帰線")  
  
 この図には、1 本の線または 2 本の接続された線を使用してモデル化できるデータが含まれています。 ただし、1 本の線ではデータを的確に表すことができません。 代わりに 2 本の線を使用すると、モデルはデータをさらに的確に表すことができます。 2 本の線が交差するポイントは非線形性のポイントで、これはデシジョン ツリー モデルのノードが分割されるポイントになります。 たとえば、前のグラフで非線形性のポイントに対応しているノードは、次の図で表すことができます。 2 つの式は、2 本の線の回帰式を表します。  
  
 ![非線形性のポイントを表す式](../media/regression-tree2.gif "非線形性のポイントを表す式")  
  
## <a name="data-required-for-decision-tree-models"></a>デシジョン ツリー モデルに必要なデータ  
 デシジョン ツリー モデルで使用するデータを用意する際には、必要なデータ量やデータの使用方法など、このアルゴリズムにおける要件を把握しておいてください。  
  
 デシジョン ツリー モデルの要件は次のとおりです。  
  
-   **1 つのキー列**各モデルには、各レコードを一意に識別する数値列またはテキスト列が1つ含まれている必要があります。 複合キーは使用できません。  
  
-   **予測可能列**少なくとも1つの予測可能列が必要です。 1 つのモデルに対し、複数の予測可能属性を含めることができます。また、数値型と不連続型の予測可能属性を混在させることもできます。 ただし、予測可能属性の数を増やすと、処理時間が長くなる可能性があります。  
  
-   **入力列**入力列が必要です。これは不連続でも連続でもかまいません。 入力属性の数を増やすと、処理時間に影響します。  
  
 デシジョン モデルでサポートされるコンテンツの種類とデータ型の詳細については、「 [Microsoft デシジョン ツリー アルゴリズム テクニカル リファレンス](microsoft-decision-trees-algorithm-technical-reference.md)」の「必要条件」を参照してください。  
  
## <a name="viewing-a-decision-trees-model"></a>デシジョン ツリー モデルの表示  
 モデルを参照するには、 **Microsoft ツリー ビューアー**を使用します。 モデルで複数のツリーが生成される場合、そのいずれかを選択すると、予測可能属性ごとのケースの分類がビューアーに表示されます。 また、依存関係ネットワーク ビューアーを使用すると、複数ツリー間の相互関係を表示できます。 詳細については、 [「Microsoft ツリー ビューアーを使用したモデルの参照」](browse-a-model-using-the-microsoft-tree-viewer.md)を参照してください。  
  
 ツリー内の特定の分岐 (ノード) の詳細を調べる場合は、 [Microsoft 汎用コンテンツ ツリー ビューアー](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)でモデルを参照することもできます。 モデルに保存される内容には、各ノードのすべての値の分布、ツリーの各レベルにおける確率、および連続属性用の回帰式が含まれます。 詳細については、「 [デシジョン ツリー モデルのマイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](mining-model-content-for-decision-tree-models-analysis-services-data-mining.md)」を参照してください。  
  
## <a name="creating-predictions"></a>予測の作成  
 モデルの処理後、結果がパターンと統計のセットとして保存されます。これを使用して、関係を調査したり予測を実行したりできます。  
  
 デシジョン ツリー モデルで使用するクエリの例については、「 [デシジョン ツリー モデルのクエリ例](decision-trees-model-query-examples.md)」を参照してください。  
  
 マイニング モデルに対するクエリの作成方法については、「 [データ マイニング クエリ](data-mining-queries.md)」を参照してください。  
  
## <a name="remarks"></a>解説  
  
-   Predictive Model Markup Language (PMML) を使用したマイニング モデルの作成がサポートされています。  
  
-   ドリルスルーがサポートされています。  
  
-   OLAP マイニング モデルの使用およびデータ マイニング ディメンションの作成がサポートされています。  
  
## <a name="see-also"></a>参照  
 [データマイニングアルゴリズム &#40;Analysis Services-データマイニング&#41;](data-mining-algorithms-analysis-services-data-mining.md)   
 [Microsoft デシジョンツリーアルゴリズムテクニカルリファレンス](microsoft-decision-trees-algorithm-technical-reference.md)   
 [デシジョンツリーモデルのクエリ例](decision-trees-model-query-examples.md)   
 [デシジョンツリーモデルのマイニングモデルコンテンツ &#40;Analysis Services データマイニング&#41;](mining-model-content-for-decision-tree-models-analysis-services-data-mining.md)  
  
  
