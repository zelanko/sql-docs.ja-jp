---
title: "SystemGetClusterAccuracyResults (Analysis Services - データ マイニング) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- stored procedures [Analysis Services], data mining
- SystemGetClusterAccuracyResults
- cross-validation [data mining]
ms.assetid: e1701738-50d5-46b4-b406-f1e800545abb
caps.latest.revision: 18
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 8e31548023acfa5ef3c202b978d7be3c46d788a0
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="systemgetclusteraccuracyresults-analysis-services---data-mining"></a>SystemGetClusterAccuracyResults (Analysis Services - データ マイニング)
  マイニング構造と関連するクラスター モデルに対するクロス検証の精度基準を返します。  
  
 このストアド プロシージャは、データセット全体の基準を 1 つのパーティションとして返します。 データセットをクロスセクションにパーティション分割し、各パーティションのメトリックを取得するには、 [SystemGetClusterCrossValidationResults &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/systemgetclustercrossvalidationresults-analysis-services-data-mining.md)を使用します。  
  
> [!NOTE]  
>  このストアド プロシージャは、クラスター モデルに対してのみ使用できます。 非クラスター モデルの場合は、 [SystemGetAccuracyResults &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/systemgetaccuracyresults-analysis-services-data-mining.md)を使用します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SystemGetClusterAccuracyResults(  
<mining structure>   
[,<mining model list>]  
,<data set>  
,<test list>])  
```  
  
## <a name="arguments"></a>引数  
 *マイニング構造 (mining structure)*  
 現在のデータベースのマイニング構造の名前。  
  
 (必須)  
  
 *マイニング モデルの一覧 (mining model list)*  
 検証するモデルのコンマ区切りの一覧。  
  
 既定値は **null**です。つまり、適用可能なモデルがすべて使用されます。 既定値を使用すると、非クラスター モデルは処理の対象一覧から自動的に除外されます。  
  
 (オプション)  
  
 *データ セット (data set)*  
 テストに使用される、マイニング構造のパーティションを示す整数値。 この値は、次の値の合計を表すビットマスクから派生しています。この場合、いずれの値も省略可能です。  
  
|||  
|-|-|  
|トレーニング ケース|0x0001|  
|テスト ケース|0x0002|  
|モデル フィルター|0x0004|  
  
 指定可能な値の一覧については、このトピックの「解説」を参照してください。  
  
 (必須)  
  
 *テスト リスト (test list)*  
 テスト オプションを指定する文字列。 このパラメーターは将来使用するために予約されています。  
  
 (オプション)  
  
## <a name="return-type"></a>戻り値の型  
 テーブルには、個別のパーティションのスコアと、すべてのモデルの集計が含まれます。  
  
 次の表は、 **SystemGetClusterAccuracyResults**によって返される列の一覧です。 ストアド プロシージャによって返される情報を解釈する方法の詳細については、「 [相互検証レポートのメジャー](../../analysis-services/data-mining/measures-in-the-cross-validation-report.md)」をご覧ください。  
  
|列名|Description|  
|-----------------|-----------------|  
|ModelName|テストされたモデルの名前。 **All** は、結果がすべてのモデルの集計であることを示します。|  
|AttributeName|クラスター モデルには適用されません。|  
|AttributeState|クラスター モデルには適用されません。|  
|PartitionIndex|パーティションを示す番号。<br /><br /> このストアド プロシージャでは、番号は常に 0 になります。|  
|PartitionCases|テスト済みのケースの数を示す整数。|  
|テスト|実行されたテストの種類。|  
|[メジャー]|テストから返されたメジャーの名前。 各モデルのメジャーは、モデルの種類と、予測可能な値の型によって異なります。<br /><br /> 予測可能な型ごとに返されるメジャーの一覧については、「[相互検証レポートのメジャー](../../analysis-services/data-mining/measures-in-the-cross-validation-report.md)」をご覧ください。<br /><br /> 各メジャーの定義については、「[相互検証 &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/cross-validation-analysis-services-data-mining.md)」をご覧ください。|  
|値|クラスターのケースの確率値を示す確率スコア。|  
  
## <a name="remarks"></a>解説  
 次の表は、クロス検証に使用されるマイニング構造のデータを指定するために使用できる値の例を示しています。 クロス検証にテスト ケースを使用する場合、マイニング構造には、既にテスト データセットが含まれている必要があります。 マイニング構造の作成時にテスト データセットを定義する方法の詳細については、「 [トレーニング データ セットとテスト データ セット](../../analysis-services/data-mining/training-and-testing-data-sets.md)」をご覧ください。  
  
|整数値|Description|  
|-------------------|-----------------|  
|1|トレーニング ケースのみが使用されます。|  
|2|テスト ケースのみが使用されます。|  
|3|トレーニング ケースとテスト ケースの両方が使用されます。|  
|4|無効な組み合わせです。|  
|5|トレーニング ケースのみが使用され、モデル フィルターが適用されます。|  
|6|テスト ケースのみが使用され、モデル フィルターが適用されます。|  
|7|トレーニング ケースとテスト ケースの両方が使用され、モデル フィルターが適用されます。|  
  
 クロス検証を使用するシナリオの詳細については、「[テストおよび検証 &#40;データ マイニング&#41;](../../analysis-services/data-mining/testing-and-validation-data-mining.md)」をご覧ください。  
  
## <a name="examples"></a>使用例  
 この例では、vTargetMail マイニング構造に関連付けられている 2 つのクラスター モデル `Cluster 1` と `Cluster 2`の精度のメジャーを返します。 4 行目のコードは、結果が、各モデルに関連付けられている可能性のあるフィルターを使用せず、テスト ケースのみに基づいていることを示します。  
  
```  
CALL SystemGetClusterAccuracyResults (  
[vTargetMail],  
[Cluster 1], [Cluster 2],  
2  
)  
```  
  
 サンプルの結果 :  
  
|ModelName|AttributeName|AttributeState|PartitionIndex|PartitionSize|テスト|[メジャー]|値|  
|---------------|-------------------|--------------------|--------------------|-------------------|----------|-------------|-----------|  
|クラスター 1|||0|5545|クラスター|ケースの確率値|0.796514342249313|  
|Cluster 2|||0|5545|クラスター|ケースの確率値|0.732122471228572|  
  
## <a name="requirements"></a>必要条件  
 クロス検証は、 [!INCLUDE[ssEnterprise](../../includes/ssenterprise-md.md)] 以降の [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]でのみ使用できます。  
  
## <a name="see-also"></a>参照  
 [SystemGetCrossValidationResults &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/systemgetcrossvalidationresults-analysis-services-data-mining.md)   
 [SystemGetAccuracyResults & #40 です。Analysis Services - データ マイニング &#41;](../../analysis-services/data-mining/systemgetaccuracyresults-analysis-services-data-mining.md)   
 [SystemGetClusterCrossValidationResults & #40 です。Analysis Services - データ マイニング &#41;](../../analysis-services/data-mining/systemgetclustercrossvalidationresults-analysis-services-data-mining.md)   
 [SystemClusterGetAccuracyResults](../../analysis-services/data-mining/systemgetclusteraccuracyresults-analysis-services-data-mining.md)  
  
  

