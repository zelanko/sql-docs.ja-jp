---
title: "Microsoft シーケンス クラスター アルゴリズム |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- clusters [Analysis Services]
- algorithms [data mining]
- sequence clustering algorithms [Analysis Services]
- sequence [Analysis Services]
ms.assetid: ae779a1f-0adb-4857-afbd-a15543dff299
caps.latest.revision: 49
author: Minewiskan
ms.author: owend
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 09d9c1909f093547dedd79823a06d9647f0bd6a8
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="microsoft-sequence-clustering-algorithm"></a>Microsoft シーケンス クラスター アルゴリズム
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] シーケンス クラスター アルゴリズムは、シーケンス分析とクラスタリングを組み合わせた独自のアルゴリズムです。 このアルゴリズムを使用すると、 *シーケンス*でリンク可能なイベントを含むデータを調べることができます。 このアルゴリズムは最も一般的なシーケンスを見つけ、クラスタリングを実行して類似したシーケンスを見つけます。 次の例では、機械学習用にデータを取り込むことができるシーケンスの種類を示し、一般的な問題やビジネス シナリオの理解を深めます。  
  
-   ユーザーによる Web サイト閲覧時に生成されるクリック ストリームまたはクリック パス  
  
-   ハード ディスク障害やサーバーのデッドロックなどの事象に先立つイベントを示すログ  
  
-   オンラインのショッピング カートで顧客が商品を買い物かごに追加する順序を示すトランザクション レコード  
  
-   サービスのキャンセルやその他の好ましくない結果を予測するために顧客または患者の操作を記録したレコード  
  
 このアルゴリズムは、多くの点で [!INCLUDE[msCoName](../../includes/msconame-md.md)] クラスター アルゴリズムに似ています。 ただし [!INCLUDE[msCoName](../../includes/msconame-md.md)] シーケンス クラスター アルゴリズムでは、類似する属性を含むケースのクラスターを検索する代わりに、シーケンス内の類似するパスを含むケースのクラスターを検索します。  
  
## <a name="example"></a>例  
 [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] の Web サイトでは、サイトのユーザーがどのページを閲覧するかについての情報と、これらのページの閲覧順序についての情報が収集されます。 顧客は、サイトにログインしてオンラインで注文することができます。 これにより、各顧客プロファイルに対するクリック情報が得られます。 このデータに対して [!INCLUDE[msCoName](../../includes/msconame-md.md)] シーケンス クラスター アルゴリズムを使用することによって、類似したクリックのパターンまたはシーケンスを持つ顧客のグループ (クラスター) を検出できます。 次に、これらのクラスターを使用して、顧客の Web サイト内での移動状況の分析、特定の製品の売上に最も密接に関連しているページの識別、次に閲覧される可能性が高いページの予測などが実行できます。  
  
## <a name="how-the-algorithm-works"></a>アルゴリズムの動作  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] シーケンス クラスター アルゴリズムは、クラスタリング技法と Markov 連鎖分析を組み合わせた複合アルゴリズムであり、クラスターとそのシーケンスを特定します。  [!INCLUDE[msCoName](../../includes/msconame-md.md)] シーケンス クラスター アルゴリズムの特徴の 1 つは、シーケンス データを使用することです。 このデータは通常、特定ユーザーによる一連の製品購入や Web でのクリックなど、データセット内の一連のイベントや状態間の遷移を表します。 クラスタリング用の入力として使用するのに適したシーケンスを判断するために、アルゴリズムはすべての遷移の確率を調べ、データセット内の有効なすべてのシーケンス間の差異または距離を測定します。 候補となるシーケンスの一覧がアルゴリズムによって作成された後、Expectation Maximization (EM) を使用してクラスタリング用の入力としてシーケンス情報を使用します。  
  
 実装の詳細については、「 [Microsoft シーケンス クラスタリング アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-sequence-clustering-algorithm-technical-reference.md)」を参照してください。  
  
## <a name="data-required-for-sequence-clustering-models"></a>シーケンス クラスター モデルに必要なデータ  
 シーケンス クラスター モデルのトレーニングに使用するデータを用意する際には、必要なデータ量やデータの使用方法など、このアルゴリズムにおける要件を把握しておいてください。  
  
 シーケンス クラスター モデルの要件は次のとおりです。  
  
-   **1 つのキー列** シーケンス クラスター モデルでは、レコードを識別するキーが必要です。  
  
-   **1 つのシーケンス列** このモデルでは、シーケンス データ用に、シーケンス ID 列を含む入れ子になったテーブルが必要です。 シーケンス ID には、任意の並べ替え可能なデータ型を使用できます。 たとえば、この列でシーケンス内のイベントを識別できる限り、Web ページ識別子、整数、またはテキスト文字列を使用できます。 各シーケンスが持てるシーケンス ID は 1 つのみ、また、各モデルが持てるシーケンスの種類は 1 種類のみです。  
  
-   **省略可能な非シーケンス属性** このアルゴリズムでは、シーケンス化に無関係な他の属性を追加することができます。 これらの属性には、入れ子になった列を含めることができます。  
  
 たとえば、前に挙げた [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] の Web サイトの例でシーケンス クラスター モデルを使用する場合、注文情報をケース テーブルとして、注文ごとの特定の顧客に関する人口統計情報を非シーケンス属性として、顧客がサイトを閲覧したり買い物かごに商品を入れたりしたシーケンスを含む入れ子になったテーブルをシーケンス情報として、それぞれ含めることができます。  
  
 シーケンス クラスター モデルでサポートされるコンテンツの種類とデータ型の詳細については、「 [Microsoft シーケンス クラスタリング アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-sequence-clustering-algorithm-technical-reference.md)」の「必要条件」を参照してください。  
  
## <a name="viewing-a-sequence-clustering-model"></a>シーケンス クラスター モデルの表示  
 このアルゴリズムが作成するマイニング モデルには、データ内の最も一般的なシーケンスの説明が含まれています。 モデルを参照するには、 **Microsoft シーケンス クラスター ビューアー**を使用します。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] でシーケンス クラスター モデルを表示すると、複数の遷移を含むクラスターが表示されます。 関連する統計情報も表示できます。 詳細については、「 [Microsoft シーケンス クラスター ビューアーを使用したモデルの参照](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)」を参照してください。  
  
 さらに詳細を知るには、 [Microsoft 汎用コンテンツ ツリー ビューアー](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)でモデルを参照してください。 モデルに保存される内容には、各ノードのすべての値の分布、各クラスターの確率、および遷移に関する詳細が含まれます。 詳細については、「[シーケンス クラスター モデルのマイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/mining-model-content-for-sequence-clustering-models.md)」を参照してください。  
  
## <a name="creating-predictions"></a>予測の作成  
 モデルのトレーニング後、結果がパターンのセットとして保存されます。 データ内の最も一般的なシーケンスの説明を使用して、新しいシーケンスの次に来る可能性の高いステップを予測できます。 ただし、アルゴリズムには他の列が含まれるため、結果として得られるモデルを使用して、シーケンス化されたデータとシーケンシャルではない入力との間の関係を識別できます。 たとえば、モデルに人口統計データを追加すると、特定の顧客グループに対する予測を実行できます。 さまざまな数の予測を返したり、説明的な統計情報を返したりするように、予測クエリをカスタマイズできます。  
  
 データ マイニング モデルに対するクエリの作成方法については、「 [データ マイニング クエリ](../../analysis-services/data-mining/data-mining-queries.md)」を参照してください。 シーケンス クラスター モデルでクエリを使用する方法の例については、「 [シーケンス クラスター モデルのクエリの例](../../analysis-services/data-mining/sequence-clustering-model-query-examples.md)」を参照してください。  
  
## <a name="remarks"></a>解説  
  
-   Predictive Model Markup Language (PMML) を使用したマイニング モデルの作成はサポートされていません。  
  
-   ドリルスルーがサポートされています。  
  
-   OLAP マイニング モデルの使用およびデータ マイニング ディメンションの作成がサポートされています。  
  
## <a name="see-also"></a>参照  
 [データ マイニング アルゴリズム &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Microsoft シーケンス クラスタ リング アルゴリズム テクニカル リファレンス](../../analysis-services/data-mining/microsoft-sequence-clustering-algorithm-technical-reference.md)   
 [シーケンス クラスター モデルのクエリ例](../../analysis-services/data-mining/sequence-clustering-model-query-examples.md)   
 [Microsoft シーケンス クラスター ビューアーを使用したモデルの参照](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)  
  
  

