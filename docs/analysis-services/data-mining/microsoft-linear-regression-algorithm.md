---
title: "Microsoft 線形回帰アルゴリズム | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "アルゴリズム [データ マイニング]"
  - "線形回帰アルゴリズム [Analysis Services]"
  - "線形回帰 [Analysis Services]"
  - "回帰アルゴリズム [Analysis Services]"
ms.assetid: 50a4abb8-c0b0-4380-ba5e-c49b305b9d22
caps.latest.revision: 23
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 23
---
# Microsoft 線形回帰アルゴリズム
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] 線形回帰アルゴリズムは、[!INCLUDE[msCoName](../../includes/msconame-md.md)] デシジョン ツリー アルゴリズムの一種であり、従属変数と独立変数の間の線形の関係を計算し、その関係を予測に使用するのに役立ちます。  
  
 この関係は、一連のデータを最もよく表す直線の式の形になります。 たとえば、次の図の直線は、データの最適な線形表現です。  
  
 ![データ セットをモデル化した直線](../../analysis-services/data-mining/media/linear-regression.png "データ セットをモデル化した直線")  
  
 図の各データ ポイントには、回帰直線からの距離に関する誤差があります。 回帰式の係数 a および b により、回帰直線の角度と位置が調整されます。 すべてのデータ ポイントに関する誤差の合計が最小になるまで、a および b を調整して、回帰式を取得できます。  
  
 複数の変数を使用するその他の種類の回帰や、線形でない回帰の方法もあります。 線形回帰は、何らかの基になっている要因の変更に対する反応をモデル化するための、便利でよく知られた方法です。  
  
## 例  
 線形回帰を使用して、2 つの連続した列の関係を調べることができます。 たとえば、線形回帰を使用して、製造データまたは売上データから傾向線を計算することができます。 また、線形回帰をより複雑なデータ マイニング モデルの開発の前段階として使用し、データ列間の関係を評価することもできます。  
  
 データ マイニング ツールを必要としない線形回帰の計算方法は多数ありますが、このタスクに [!INCLUDE[msCoName](../../includes/msconame-md.md)] 線形回帰アルゴリズムを使用することの利点は、変数間の考えられるすべての関係が自動的に計算され、テストされるということです。 最小二乗法の解決などの計算方法を選択する必要はありません。 ただし、線形回帰では、結果に影響を与える要因が複数存在するシナリオで、関係が過剰に簡素化される場合があります。  
  
## アルゴリズムの動作  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 線形回帰アルゴリズムは、[!INCLUDE[msCoName](../../includes/msconame-md.md)] デシジョン ツリー アルゴリズムの一種です。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 線形回帰アルゴリズムを選択すると、[!INCLUDE[msCoName](../../includes/msconame-md.md)] デシジョン ツリー アルゴリズムの特殊なケースが、アルゴリズムの動作を制約して特定の入力データ型を要求するパラメーターを使用して起動されます。 さらに、標準のデシジョン ツリー モデルではデータが小さなサブセットまたはツリーに反復的に分割されるのに対し、線形回帰モデルではデータセット全体が最初のパスでの関係の計算に使用されます。  
  
## 線形回帰モデルに必要なデータ  
 線形回帰モデルで使用するデータを用意する際には、特定のアルゴリズムの要件を把握しておいてください。 これには、必要なデータ量やデータの使用方法が含まれます。 このモデルの種類の要件は次のとおりです。  
  
-   **単一キー列** : それぞれのモデルには、各レコードを一意に識別する数値列またはテキスト列が 1 つ含まれている必要があります。 複合キーは使用できません。  
  
-   **予測可能列** 少なくとも 1 つの予測可能列が必要です。 1 つのモデルに対し、複数の予測可能属性を含めることができます。ただし、予測可能属性は連続する数値データ型である必要があります。 データのネイティブ ストレージが数値であっても、datetime データ型を予測可能属性として使用することはできません。  
  
-   **入力列** 入力列は連続する数値データを含み、適切なデータ型が割り当てられている必要があります。  
  
 詳細については、「[Microsoft 線形回帰アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-linear-regression-algorithm-technical-reference.md)」の「必要条件」を参照してください。  
  
## 線形回帰モデルの表示  
 モデルを参照するには、**Microsoft ツリー ビューアー**を使用します。 線形回帰モデルのツリー構造は非常に単純であり、回帰式に関するすべての情報が単一のノードに含まれています。 詳細については、[「Microsoft ツリー ビューアーを使用したモデルの参照」](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-tree-viewer.md) を参照してください。  
  
 式の詳細を調べる場合は、[Microsoft 汎用コンテンツ ツリー ビューアー](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)で係数およびその他の詳細を参照することもできます。  
  
 線形回帰モデルの場合、モデル コンテンツには、メタデータ、回帰式、および入力値の分布に関する統計が含まれます。 詳細については、「[回帰モデルのマイニング モデル コンテンツ (Analysis Services - データ マイニング)](../../analysis-services/data-mining/mining-model-content-for-linear-regression-models-analysis-services-data-mining.md)」を参照してください。  
  
## 予測の作成  
 モデルの処理後、結果が統計のセットとして線形回帰式と共に保存されます。これを使用して、将来の傾向を計算することができます。 線形回帰モデルで使用するクエリの例については、「[線形回帰モデルのクエリ例](../../analysis-services/data-mining/linear-regression-model-query-examples.md)」を参照してください。  
  
 マイニング モデルに対するクエリの作成方法については、「[データ マイニング クエリ](../../analysis-services/data-mining/data-mining-queries.md)」を参照してください。  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 線形回帰アルゴリズムを選択して線形回帰モデルを作成することに加えて、予測可能属性が連続する数値データ型である場合は、回帰を含むデシジョン ツリー モデルを作成することができます。 この場合、アルゴリズムが適切な分離ポイントを見つけたときにデータは分割されますが、データの一部の領域では、代わりに回帰式が作成されます。 デシジョン ツリー モデル内の回帰ツリーの詳細については、「[デシジョン ツリー モデルのマイニング モデル コンテンツ (Analysis Services - データ マイニング)](../../analysis-services/data-mining/mining-model-content-for-decision-tree-models-analysis-services-data-mining.md)」を参照してください。  
  
## 解説  
  
-   Predictive Model Markup Language (PMML) を使用したマイニング モデルの作成はサポートされていません。  
  
-   データ マイニング ディメンションの作成はサポートされていません。  
  
-   ドリルスルーがサポートされています。  
  
-   OLAP マイニング モデルの使用がサポートされています。  
  
## 参照  
 [データ マイニング アルゴリズム (Analysis Services - データ マイニング)](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Microsoft 線形回帰アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-linear-regression-algorithm-technical-reference.md)   
 [線形回帰モデルのクエリ例](../../analysis-services/data-mining/linear-regression-model-query-examples.md)   
 [線形回帰モデルのマイニング モデル コンテンツ (Analysis Services - データ マイニング)](../../analysis-services/data-mining/mining-model-content-for-linear-regression-models-analysis-services-data-mining.md)  
  
  