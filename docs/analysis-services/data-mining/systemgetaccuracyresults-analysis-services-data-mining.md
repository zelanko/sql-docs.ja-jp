---
title: "SystemGetAccuracyResults (Analysis Services - データ マイニング) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- stored procedures [Analysis Services], data mining
- SystemGetAccuracyResults
- cross-validation [data mining]
ms.assetid: 54ff584c-c6ce-4c31-9515-0a645719bd1a
caps.latest.revision: "26"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 183fbed8a59f4f6288b321b47d30895e4a7c7394
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="systemgetaccuracyresults-analysis-services---data-mining"></a>SystemGetAccuracyResults (Analysis Services - データ マイニング)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]マイニング構造とクラスタ リング モデルを除く、すべての関連モデルのクロス検証の精度の基準を返します。  
  
 このストアド プロシージャは、データセット全体の基準を 1 つのパーティションとして返します。 データセットをクロスセクションにパーティション分割し、各パーティションのメトリックを取得するには、 [SystemGetCrossValidationResults (Analysis Services - データ マイニング)](../../analysis-services/data-mining/systemgetcrossvalidationresults-analysis-services-data-mining.md)を使用します。  
  
> [!NOTE]  
>  このストアド プロシージャは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] タイム シリーズ アルゴリズムや [!INCLUDE[msCoName](../../includes/msconame-md.md)] シーケンス クラスター アルゴリズムを使用して作成されたモデルではサポートされていません。 また、クラスター モデルの場合は、別のストアド プロシージャ [SystemGetClusterAccuracyResults (Analysis Services - データ マイニング)](../../analysis-services/data-mining/systemgetclusteraccuracyresults-analysis-services-data-mining.md)を使用します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SystemGetAccuracyResults(<mining structure>,   
[,<mining model list>]  
,<data set>  
,<target attribute>  
[,<target state>]  
[,<target threshold>]  
[,<test list>])  
```  
  
## <a name="arguments"></a>引数  
 *マイニング構造 (mining structure)*  
 現在のデータベースのマイニング構造の名前。  
  
 (必須)  
  
 *model list*  
 検証するモデルのコンマ区切りの一覧。  
  
 既定値は **null**です。 つまり、適用可能なモデルがすべて使用されます。 既定値を使用すると、クラスター モデルは処理の対象一覧から自動的に除外されます。  
  
 (オプション)  
  
 *データ セット (data set)*  
 テストにマイニング構造のパーティションを使用しているかを示す整数値。 この値は、次の値の合計を表すビットマスクから派生しています。この場合、いずれの値も省略可能です。  
  
|||  
|-|-|  
|トレーニング ケース|0x0001|  
|テスト ケース|0x0002|  
|モデル フィルター|0x0004|  
  
 指定可能な値の一覧については、このトピックの「解説」を参照してください。  
  
 (必須)  
  
 *target attribute*  
 予測可能なオブジェクトの名前を表す文字列。 予測可能なオブジェクトには、マイニング モデルの列、入れ子になったテーブル列、または入れ子になったテーブル キー列を指定できます。  
  
 (必須)  
  
 *target state*  
 予測する特定の値を表す文字列。  
  
 値を指定した場合、その特定の状態の基準が収集されます。  
  
 値を指定しなかった場合、または Null を指定した場合は、予測ごとに最も可能性の高い状態の基準が計算されます。  
  
 既定値は **null**です。  
  
 (オプション)  
  
 *target threshold*  
 予測値が正確であると見なされる最小確率を示す 0.0 ～ 1 の範囲の数値。  
  
 既定値は **null**です。これは、すべての予測が正しいと見なされることを意味します。  
  
 (オプション)  
  
 *テスト リスト (test list)*  
 テスト オプションを指定する文字列。 このパラメーターは将来使用するために予約されています。  
  
 (オプション)  
  
## <a name="return-type"></a>戻り値の型  
 返される行セットには、各パーティションのスコアと、すべてのモデルの集計が含まれます。  
  
 次の表は、 **GetValidationResults**によって返される列の一覧です。  
  
|列名|Description|  
|-----------------|-----------------|  
|モデル|テストされたモデルの名前。 **All** は、結果がすべてのモデルの集計であることを示します。|  
|AttributeName|予測可能列の名前。|  
|AttributeState|予測可能列の対象の値。<br /><br /> この列に値が含まれる場合、指定した状態の基準だけが収集されます。<br /><br /> この値が指定されていない場合や Null の場合は、予測ごとに最も可能性の高い状態の基準が計算されます。|  
|PartitionIndex|結果が適用されるパーティションを表します。<br /><br /> このプロシージャでは、常に 0 になります。|  
|PartitionCases|基づいた、ケースのセット内の行の数を示す整数、 *\<データ セット >*パラメーター。|  
|テスト|実行されたテストの種類。|  
|[メジャー]|テストから返されたメジャーの名前。 各モデルのメジャーは、モデルの種類と、予測可能な値の型によって異なります。<br /><br /> 予測可能な型ごとに返されるメジャーの一覧については、「[相互検証レポートのメジャー](../../analysis-services/data-mining/measures-in-the-cross-validation-report.md)」をご覧ください。<br /><br /> 各メジャーの定義については、「[相互検証 &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/cross-validation-analysis-services-data-mining.md)」をご覧ください。|  
|値|指定したメジャーの値。|  
  
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
 この例では、 `v Target Mail DT`マイニング構造に関連付けられている 1 つのデシジョン ツリー モデル `vTargetMail` の精度のメジャーを返します。 4 行目のコードは、結果が、テスト ケースに基づいていて、モデルごとにそのモデル固有のフィルターでフィルター処理されていることを示します。  `[Bike Buyer]` は、予測される列を指定し、その次の行の 1 は、モデルが特定の値 1 ("はい、購入します") に対してのみ評価されることを示します。  
  
 コードの最後の行では、状態のしきい値が 0.5 であることを指定します。 つまり、確率が 50% を超える予測は、精度を計算する際に "良い" 予測であると見なされます。  
  
```  
CALL SystemGetAccuracyResults (  
[vTargetMail],  
[vTargetMail DT],  
6,  
'Bike Buyer',  
1,  
0.5  
)  
```  
  
 サンプルの結果 :  
  
|ModelName|AttributeName|AttributeState|PartitionIndex|PartitionSize|テスト|[メジャー]|値|  
|---------------|-------------------|--------------------|--------------------|-------------------|----------|-------------|-----------|  
|v Target Mail DT|Bike Buyer|1|0|1638|分類|True Positive|605|  
|v Target Mail DT|Bike Buyer|1|0|1638|分類|False Positive|177|  
|v Target Mail DT|Bike Buyer|1|0|1638|分類|True Negative|501|  
|v Target Mail DT|Bike Buyer|1|0|1638|分類|False Negative|355|  
|v Target Mail DT|Bike Buyer|1|0|1638|Likelihood|ログ スコア|-0.598454638753028|  
|v Target Mail DT|Bike Buyer|1|0|1638|Likelihood|リフト|0.0936717116894395|  
|v Target Mail DT|Bike Buyer|1|0|1638|Likelihood|2 乗平均平方根誤差|0.361630800104946|  
  
## <a name="requirements"></a>必要条件  
 相互検証は、 [!INCLUDE[ssEnterprise](../../includes/ssenterprise-md.md)] 以降の [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]でのみ使用できます。  
  
## <a name="see-also"></a>参照  
 [SystemGetCrossValidationResults (Analysis Services - データ マイニング)](../../analysis-services/data-mining/systemgetcrossvalidationresults-analysis-services-data-mining.md)   
 [SystemGetAccuracyResults](../../analysis-services/data-mining/systemgetaccuracyresults-analysis-services-data-mining.md)   
 [SystemGetClusterCrossValidationResults &#40;です。Analysis Services - データ マイニング &#41;](../../analysis-services/data-mining/systemgetclustercrossvalidationresults-analysis-services-data-mining.md)   
 [SystemGetClusterAccuracyResults &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/systemgetclusteraccuracyresults-analysis-services-data-mining.md)  
  
  
