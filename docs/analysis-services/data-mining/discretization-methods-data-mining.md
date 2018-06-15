---
title: 分離メソッド (データ マイニング) |Microsoft ドキュメント
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 610108ce4edb6e3beb5c13398d0a79eca200bdba
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34016979"
---
# <a name="discretization-methods-data-mining"></a>分離メソッド (データ マイニング)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] でデータ マイニング モデルを作成するための一部のアルゴリズムでは、正常に機能するために特定の種類のコンテンツが必要です。 たとえば、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes アルゴリズムでは、連続列を入力として使用したり、連続する値を予測したりすることはできません。 また、一部の列に含まれている値が多すぎるため、データ マイニング モデルの作成元となるデータ内の対象パターンをアルゴリズムで容易に識別できない場合があります。  
  
 このような場合、アルゴリズムを使用してマイニング モデルを生成できるように、列内のデータを分離できます。 *分離* とは、値をバケットに分割して、限定された数の可能な状態を生成するプロセスです。 バケット自体は、順序付きの不連続の値として処理されます。 数値と文字列の両方の列を分離できます。  
  
 データを分離するためのいくつかのメソッドがあります。 データ マイニング ソリューションでリレーショナル データを使用する場合は、 <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> property プロパティの値を設定して、データのグループ化に使用するバケットの数を制御できます。 既定のバケット数は 5 です。  
  
 データ マイニング ソリューションでオンライン分析処理 (OLAP) キューブのデータを使用する場合、データ マイニング アルゴリズムでは生成するバケットの数が次の式を使用して自動的に計算されます。ここで、n は列のデータの個別の値の数です。  
  
 `Number of Buckets = sqrt(n)`  
  
 たくない場合[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]バケットの数を計算する際、<xref:Microsoft.AnalysisServices.DimensionAttribute.DiscretizationBucketCount%2A>プロパティを手動でバケットの数を指定します。  
  
 次の表では、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]でデータを分離するときに使用できるメソッドについて説明します。  
  
|分離メソッド|Description|  
|---------------------------|-----------------|  
|**AUTOMATIC**|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によって、使用する分離メソッドが決定されます。|  
|**CLUSTERS**|このアルゴリズムは、トレーニング データをサンプリングして多数のランダム ポイントに初期化し、Expectation Maximization (EM) クラスター化アルゴリズムを使用して Microsoft クラスタリング アルゴリズムを何度か繰り返し実行することによって、データをグループに分割します。 **CLUSTERS** メソッドは、どのような分布曲線にも使用できるので便利です。 ただし、その他の分離メソッドよりも処理時間は長くなります。<br /><br /> このメソッドは数値列でのみ使用できます。|  
|**EQUAL_AREAS**|このアルゴリズムは、同数の値が含まれているグループにデータを分割します。 このメソッドは正規分布曲線に最適ですが、連続データの小さなグループに多数の値が含まれている分布の場合は適切に機能しません。 たとえば、品目の半数のコストが 0 である場合、データの半数は曲線の 1 点の下に位置します。 このような分布の場合、このメソッドはデータを分割するときに、複数の領域に均等に分離しようとします。 これにより、データが不適切に表示されます。|  
  
## <a name="remarks"></a>解説  
  
-   **EQUAL_AREAS** メソッドを使用すると、文字列を分離できます。  
  
-   **CLUSTERS** メソッドでは、ランダム サンプルとして 1,000 個のレコードを使用してデータの分離が行われます。 アルゴリズムでデータをサンプリングしない場合は、 **EQUAL_AREAS** メソッドを使用します。  
  
  
  
## <a name="see-also"></a>参照  
 [コンテンツの種類 (&) #40 です。 データ マイニング (&) #41;](../../analysis-services/data-mining/content-types-data-mining.md)   
 [コンテンツの種類 (&) #40";"DMX"&"#41;](../../dmx/content-types-dmx.md)   
 [データ マイニング アルゴリズム &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [マイニング構造と #40 です。Analysis Services - データ マイニング & #41;](../../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)   
 [データ型 (&) #40";"データ マイニング"&"#41;](../../analysis-services/data-mining/data-types-data-mining.md)   
 [マイニング構造列](../../analysis-services/data-mining/mining-structure-columns.md)   
 [列の分布 (データ マイニング)](../../analysis-services/data-mining/column-distributions-data-mining.md)  
  
  
