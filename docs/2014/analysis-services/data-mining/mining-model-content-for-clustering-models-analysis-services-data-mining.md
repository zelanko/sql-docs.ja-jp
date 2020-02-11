---
title: クラスターモデルのマイニングモデルコンテンツ (Analysis Services データマイニング) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- nearest neighbor [Data Mining]
- clustering [Data Mining]
- mining model content, clustering models
- clustering algorithms [Analysis Services]
ms.assetid: aed1b7d3-8f20-4eeb-b156-0229f942cefd
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a733b434e428f7486c235f4efc923adfa4b14949
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66083679"
---
# <a name="mining-model-content-for-clustering-models-analysis-services---data-mining"></a>クラスター モデルのマイニング モデル コンテンツ (Analysis Services - データ マイニング)
  このトピックでは、Microsoft クラスタリング アルゴリズムを使用するモデルに固有のマイニング モデル コンテンツについて説明します。 すべての種類のモデルのマイニング モデル コンテンツの一般的な説明については、「 [マイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](mining-model-content-analysis-services-data-mining.md)」 (マイニング モデル コンテンツ (Analysis Services - データ マイニング)) を参照してください。  
  
## <a name="understanding-the-structure-of-a-clustering-model"></a>クラスター モデルの構造について  
 クラスター モデルの構造は単純です。 モデルとそのメタデータを表す 1 つの親ノードが各モデルにあり、各親ノードにはクラスターのフラット リストがあります (NODE_TYPE = 5)。 この組織は次の図に表示されます。  
  
 ![クラスターのモデル コンテンツの構造](../media/modelcontentstructure-clust.gif "クラスターのモデル コンテンツの構造")  
  
 各子ノードは 1 つのクラスターを表し、そのクラスター内のケースの属性に関する詳細な統計を格納しています (クラスター内のケースの数や、クラスターを他のクラスターから区別する値の分布など)。  
  
> [!NOTE]  
>  クラスターのカウントや説明を取得するためにノードを反復処理する必要はありません。クラスターのカウントと一覧はモデルの親ノードにも含まれています。  
  
 親ノードには、すべてのトレーニング ケースの実際の分布を表す便利な統計も含まれています。 これらの統計は、入れ子になったテーブル列である NODE_DISTRIBUTION に含まれています。 たとえば次の表は、「 `TM_Clustering`基本的なデータ マイニング チュートリアル [」で作成したクラスター モデル (](../../tutorials/basic-data-mining-tutorial.md)) の顧客の人口統計の分布を表す NODE_DISTRIBUTION テーブルのいくつかの行を示しています。  
  
|ATTRIBUTE_NAME|ATRIBUTE_VALUE|サポート|PROBABILITY|VARIANCE|VALUE_TYPE|  
|---------------------|---------------------|-------------|-----------------|--------------|-----------------|  
|Age|Missing|0|0|0|1 (Missing: 不足)|  
|Age|44.9016152716593|12939|1 で保護されたプロセスとして起動されました|125.663453102554|3 (Continuous: 連続)|  
|性別|Missing|0|0|0|1 (Missing: 不足)|  
|性別|F|6350|0.490764355823479|0|4 (Discrete: 不連続)|  
|性別|M|6589|0.509235644176521|0|4 (Discrete: 不連続)|  
  
 これらの結果から、モデルの作成に 12939 個のケースが使用されたこと、男女の比率がほぼ半々であること、および平均年齢が 44 歳であることがわかります。 説明的な統計情報は、レポートされる属性が連続する数値データ型 (年齢など) か不連続値型 (性別など) かによって異なります。 統計的尺度の *平均* および *分散* は連続するデータ型に対して計算され、 *確率* および *サポート* は不連続のデータ型に対して計算されます。  
  
> [!NOTE]  
>  分散は、クラスターの全分散を表します。 分散の値が小さい場合は、その列のほとんどの値が平均にきわめて近いことになります。 標準偏差を得るには、分散の平方根を計算します。  
  
 各属性の `Missing` という値の型は、その属性のデータがなかったケースの数を示します。 Missing のデータが重要になる場合もあります。このデータが計算に与える影響は、データ型によって異なります。 詳細については、「 [不足値 &#40;Analysis Services - データ マイニング&#41;](missing-values-analysis-services-data-mining.md)であらかじめ定義されているフラグに加えて他のモデリング フラグがある場合もあります。  
  
## <a name="model-content-for-a-clustering-model"></a>クラスター モデルのモデル コンテンツ  
 ここでは、マイニング モデル コンテンツの列のうち、クラスター モデルに関連する列についてのみ詳細と例を紹介します。  
  
 スキーマ行セットの汎用の列 (MODEL_CATALOG や MODEL_NAME など) の詳細については、「 [マイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](mining-model-content-analysis-services-data-mining.md)」を参照してください。  
  
 MODEL_CATALOG  
 モデルが格納されているデータベースの名前。  
  
 MODEL_NAME  
 モデルの名前。  
  
 ATTRIBUTE_NAME  
 クラスター モデルでは、予測可能な属性がないため常に空白になります。  
  
 NODE_NAME  
 常に NODE_UNIQUE_NAME と同じです。  
  
 NODE_UNIQUE_NAME  
 モデル内のノードの一意の識別子。 この値は変更できません。  
  
 NODE_TYPE  
 クラスター モデルでは次のノード型が出力されます。  
  
|ノード ID とノード名|[説明]|  
|----------------------|-----------------|  
|1 (モデル)|モデルのルート ノードです。|  
|5 (クラスター)|クラスター内のケースの数および特性と、クラスター内の値を説明する統計が含まれます。|  
  
 NODE_CAPTION  
 表示名。 モデルを作成すると、NODE_UNIQUE_NAME の値が自動的にキャプションとして使用されます。 ただし、NODE_CAPTION の値を変更してクラスターの表示名を更新することもできます。この値は、プログラムで変更することも、ビューアーを使用して変更することもできます。  
  
> [!NOTE]  
>  モデルを再処理すると、すべての名前変更が新しい値で上書きされます。 モデル内の名前を固定したり、クラスター メンバーシップの変更をモデルの異なるバージョンの間で追跡したりすることはできません。  
  
 CHILDREN_CARDINALITY  
 ノードの子の推定数。  
  
 **親ノード**モデル内のクラスターの数を示します。  
  
 **クラスターノード**常に0です。  
  
 PARENT_UNIQUE_NAME  
 ノードの親の一意な名前です。  
  
 **親ノード**常に NULL  
  
 **クラスターノード**通常は000です。  
  
 NODE_DESCRIPTION  
 ノードの説明です。  
  
 **親ノード**常に **(すべて)**。  
  
 **クラスターノード**クラスターを他のクラスターと区別するプライマリ属性のコンマ区切りのリスト。  
  
 NODE_RULE  
 クラスター モデルでは使用されません。  
  
 MARGINAL_RULE  
 クラスター モデルでは使用されません。  
  
 NODE_PROBABILITY  
 このノードに関連付けられている確率。 **親ノード**常に1です。  
  
 **クラスターノード**確率は、属性の複合確率を表し、クラスターモデルの作成に使用されるアルゴリズムに応じて調整を行います。  
  
 MARGINAL_PROBABILITY  
 親ノードからノードに到達する確率です。 クラスター モデルでは常に NODE_PROBABILITY と同じです。  
  
 NODE_DISTRIBUTION  
 ノードの確率ヒストグラムが含まれているテーブル。  
  
 **親ノード**このトピックの概要を参照してください。  
  
 **クラスターノード**このクラスターに含まれているケースの属性と値の分布を表します。  
  
 NODE_SUPPORT  
 このノードをサポートするケースの数。 **親ノード**モデル全体のトレーニングケースの数を示します。  
  
 **クラスターノード**クラスターのサイズをケースの数として示します。  
  
 **メモ**モデルで K を使用する場合は、各ケースを1つのクラスターにのみ所属させることができます。 モデルで EM クラスタリングが使用されている場合は、各ケースが異なるクラスターに所属することができ、所属するクラスターごとに重み付きの距離が割り当てられます。 したがって、EM モデルの場合は、個々のクラスターのサポートの合計がモデル全体のサポートより大きくなります。  
  
 MSOLAP_MODEL_COLUMN  
 クラスター モデルでは使用されません。  
  
 MSOLAP_NODE_SCORE  
 ノードに関連付けられたスコアが表示されます。  
  
 **親ノード**クラスターモデルのベイジアン Information 条件 (BIC) スコア。  
  
 **クラスターノード**常に0です。  
  
 MSOLAP_NODE_SHORT_CAPTION  
 表示目的で使用されるラベル。 変更することはできません。  
  
 **親ノード**モデルの種類: クラスターモデル  
  
 **クラスターノード**クラスターの名前。 (Cluster 1 など)。  
  
## <a name="remarks"></a>解説  
 
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] には、クラスター モデルを作成するための方法が複数用意されています。 使用しているモデルがどの方法で作成されたかわからない場合は、モデルのメタデータを取得します。モデルのメタデータは、ADOMD クライアントや AMO を使用してプログラムで取得することも、データ マイニング スキーマ行セットに対してクエリを実行して取得することもできます。 詳細については、「 [マイニング モデルの作成に使用されたパラメーターのクエリ](query-the-parameters-used-to-create-a-mining-model.md)」を参照してください。  
  
> [!NOTE]  
>  使用するクラスタリング手法やパラメーターが違っても、モデルの構造とコンテンツは変わりません。  
  
## <a name="see-also"></a>参照  
 [マイニングモデルコンテンツ &#40;Analysis Services-データマイニング&#41;](mining-model-content-analysis-services-data-mining.md)   
 [データマイニングモデルビューアー](data-mining-model-viewers.md)   
 [Microsoft クラスタリングアルゴリズム](microsoft-clustering-algorithm.md)   
 [データ マイニング クエリ](data-mining-queries.md)  
  
  
