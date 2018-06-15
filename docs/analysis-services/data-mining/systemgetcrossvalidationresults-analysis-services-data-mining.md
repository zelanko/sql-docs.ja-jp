---
title: SystemGetCrossValidationResults (Analysis Services - データ マイニング) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2febed19e2bd481a8e442f115f9691e5abb6be4b
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34018619"
---
# <a name="systemgetcrossvalidationresults-analysis-services---data-mining"></a>SystemGetCrossValidationResults (Analysis Services - データ マイニング)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  指定した数の複数のセクションにマイニング構造をパーティション分割し、各パーティションに対してモデルをトレーニングして、各パーティションの精度の基準を返します。  
  
> [!NOTE]  
>  このストアド プロシージャを使用しても、クラスタリング モデルを相互検証したり、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] タイム シリーズ アルゴリズムや [!INCLUDE[msCoName](../../includes/msconame-md.md)] シーケンス クラスター アルゴリズムを使用して作成されたモデルを相互検証することはできません。 クラスタリング モデルを相互検証するには、 [SystemGetClusterCrossValidationResults &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/systemgetclustercrossvalidationresults-analysis-services-data-mining.md)という別のストアド プロシージャを使用できます。  
  
## <a name="syntax"></a>構文  
  
```  
  
SystemGetCrossValidationResults(  
<mining structure>  
[, <mining model list>]  
,<fold count>  
,<max cases>  
,<target attribute>  
[,<target state>]  
[,<target threshold>]  
[,<test list>])  
```  
  
## <a name="arguments"></a>引数  
 *マイニング構造 (mining structure)*  
 現在のデータベースのマイニング構造の名前。  
  
 (必須)  
  
 *マイニング モデルの一覧 (mining model list)*  
 検証するマイニング モデルのコンマ区切りの一覧。  
  
 識別子の名前で無効な文字がモデル名に含まれている場合、モデル名を角かっこで囲む必要があります。  
  
 マイニング モデルの一覧を指定しないと、指定した構造に関連付けられた、予測可能な属性を含むすべてのモデルに対して相互検証が実行されます。  
  
> [!NOTE]  
>  クラスタリング モデルを相互検証するには、 [SystemGetClusterCrossValidationResults &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/systemgetclustercrossvalidationresults-analysis-services-data-mining.md)という別のストアド プロシージャを使用できます。  
  
 (省略可能)  
  
 *フォールド カウント (fold count)*  
 データセットを分割するパーティションの数を指定する整数。 最小値は、2 です。 フォールドの最大数は、 **maximum integer** とケース数のいずれか小さい方になります。  
  
 各パーティションには、 *ケースの最大数*/*フォールド カウント*とほぼ同じ数のケースが含まれます。  
  
 既定値はありません。  
  
> [!NOTE]  
>  フォールドの数は、相互検証の実行に必要な時間に大きく影響します。 選択する数が大きすぎると、クエリの実行時間が非常に長くなる可能性があります。また、場合によっては、サーバーが応答しなくなったり、タイムアウトする可能性があります。  
  
 (必須)  
  
 *ケースの最大数*  
 すべてのフォールドに対してテストできるケースの最大数を指定する整数。  
  
 値に 0 を指定すると、データ ソース内のすべてのケースが使用されます。  
  
 データセット内の実際のケース数より大きい値を指定すると、データ ソース内のすべてのケースが使用されます。  
  
 既定値はありません。  
  
 (必須)  
  
 *対象の属性 (target attribute)*  
 予測可能な属性の名前を表す文字列。 予測可能な属性には、マイニング モデルの列、入れ子になったテーブル列、または入れ子になったテーブル キー列を指定できます。  
  
> [!NOTE]  
>  対象となる属性の存在は、実行時にのみ検証されます。  
  
 (必須)  
  
 *対象の状態 (target state)*  
 予測する値を指定する数式。 対象の値を指定した場合、指定した値の基準だけが収集されます。  
  
 値を指定しなかった場合、または値が **null**の場合は、予測ごとに最も可能性の高い状態の基準が計算されます。  
  
 既定値は **null**です。  
  
 指定した値が指定した属性に対して無効な場合、または数式の種類が指定した属性に適切な型ではない場合は、検証中にエラーが発生します。  
  
 (省略可能)  
  
 *対象のしきい値 (target*  *threshold)*  
 0 より大きくかつ 1 より小さい**Double** 。 指定した対象の状態が正しいと見なすために取得する必要のある、最小の確率のスコアを示します。  
  
 確率がこの値以下の予測は、正しくないと見なされます。  
  
 値が指定されていない場合、または値が **null**の場合は、その確率のスコアに関係なく、最も可能性の高い状態が使用されます。  
  
 既定値は **null**です。  
  
> [!NOTE]  
>  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 設定した場合、エラーは発生しません*状態のしきい値*0.0 が、この値を使用することはありません。 実際、しきい値を 0.0 に設定すると、確率が 0% の予測が正しいと見なされます。  
  
 (省略可能)  
  
 *テスト リスト (test list)*  
 テスト オプションを指定する文字列。  
  
 **注** このパラメーターは将来使用するために予約されています。  
  
 (省略可能)  
  
## <a name="return-type"></a>戻り値の型  
 返される行セットには、各モデル内の各パーティションのスコアが含まれます。  
  
 次の表では、行セットの列について説明します。  
  
|列名|Description|  
|-----------------|-----------------|  
|ModelName|テストされたモデルの名前。|  
|AttributeName|予測可能列の名前。|  
|AttributeState|予測可能列で指定した対象の値。 この値が **null**の場合、最も可能性の高い予測が使用されます。<br /><br /> この列に値が含まれている場合は、その値に対してのみモデルの精度が評価されます。|  
|PartitionIndex|結果が適用されるパーティションを識別する、1 から始まるインデックス。|  
|PartitionSize|各パーティションに含まれていたケースの数を示す整数。|  
|テスト|実行されたテストのカテゴリ。 カテゴリおよび各カテゴリに含まれるテストの説明については、「 [相互検証レポートのメジャー](../../analysis-services/data-mining/measures-in-the-cross-validation-report.md)」を参照してください。|  
|[メジャー]|テストから返されたメジャーの名前。 各モデルのメジャーは、予測可能な値の型によって異なります。 各メジャーの定義については、「[相互検証 &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/cross-validation-analysis-services-data-mining.md)」を参照してください。<br /><br /> 予測可能な型ごとに返されるメジャーの一覧については、「[相互検証レポートのメジャー](../../analysis-services/data-mining/measures-in-the-cross-validation-report.md)」を参照してください。|  
|値|指定したテスト メジャーの値。|  
  
## <a name="remarks"></a>解説  
 データ セット全体の精度の基準を返すには、 [SystemGetAccuracyResults &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/systemgetaccuracyresults-analysis-services-data-mining.md)という別のストアド プロシージャを使用できます。  
  
 既にマイニング モデルをフォールドにパーティション分割している場合は、 [SystemGetAccuracyResults &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/systemgetaccuracyresults-analysis-services-data-mining.md)という別のストアド プロシージャを使用できます。  
  
## <a name="examples"></a>使用例  
 次の例では、相互検証を行うマイニング構造を 2 つのフォールドにパーティション分割し、マイニング構造 `[v Target Mail]`に関連付けられている 2 つのマイニング モデルをテストする方法を示します。  
  
 コードの 3 行目では、テストするマイニング モデルの一覧を指定します。 一覧を指定しない場合、構造に関連付けられているすべての非クラスタリング モデルが使用されます。 コードの 4 行目では、パーティションの数を指定します。 *max cases*に値が指定されていないため、マイニング構造のすべてのケースが使用され、パーティション間で均等に分散されます。  
  
 5 行目では予測可能な属性 Bike Buyer を指定し、6 行目では予測する値 1 ("はい、購入します") を指定します。  
  
 7 行目の NULL 値は、満たす必要がある最小の確率に関する制約がないことを示します。 したがって、精度の評価では、確率が 0 ではない最初の予測が使用されます。  
  
```  
CALL SystemGetCrossValidationResults(  
[v Target Mail],  
[Target Mail DT], [Target Mail NB],  
2,  
'Bike Buyer',  
1,  
NULL  
)  
```  
  
 サンプルの結果 :  
  
|ModelName|AttributeName|AttributeState|PartitionIndex|PartitionSize|テスト|[メジャー]|値|  
|---------------|-------------------|--------------------|--------------------|-------------------|----------|-------------|-----------|  
|Target Mail DT|Bike Buyer|1|1|500|分類|True Positive|144|  
|Target Mail DT|Bike Buyer|1|1|500|分類|False Positive|105|  
|Target Mail DT|Bike Buyer|1|1|500|分類|True Negative|186|  
|Target Mail DT|Bike Buyer|1|1|500|分類|False Negative|65|  
|Target Mail DT|Bike Buyer|1|1|500|Likelihood|ログ スコア|-0.619042807138345|  
|Target Mail DT|Bike Buyer|1|1|500|Likelihood|リフト|0.0740963734002671|  
|Target Mail DT|Bike Buyer|1|1|500|Likelihood|2 乗平均平方根誤差|0.346946279977653|  
|Target Mail DT|Bike Buyer|1|2|500|分類|True Positive|162|  
|Target Mail DT|Bike Buyer|1|2|500|分類|False Positive|86|  
|Target Mail DT|Bike Buyer|1|2|500|分類|True Negative|165|  
|Target Mail DT|Bike Buyer|1|2|500|分類|False Negative|87|  
|Target Mail DT|Bike Buyer|1|2|500|Likelihood|ログ スコア|-0.654117781086519|  
|Target Mail DT|Bike Buyer|1|2|500|Likelihood|リフト|0.038997399132084|  
|Target Mail DT|Bike Buyer|1|2|500|Likelihood|2 乗平均平方根誤差|0.342721344892651|  
  
## <a name="requirements"></a>必要条件  
 相互検証は、 [!INCLUDE[ssEnterprise](../../includes/ssenterprise-md.md)] 以降の [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]でのみ使用できます。  
  
## <a name="see-also"></a>参照  
 [SystemGetCrossValidationResults](../../analysis-services/data-mining/systemgetcrossvalidationresults-analysis-services-data-mining.md)   
 [SystemGetAccuracyResults &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/systemgetaccuracyresults-analysis-services-data-mining.md)   
 [SystemGetClusterCrossValidationResults &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/systemgetclustercrossvalidationresults-analysis-services-data-mining.md)   
 [SystemGetClusterAccuracyResults & #40 です。Analysis Services - データ マイニング & #41;](../../analysis-services/data-mining/systemgetclusteraccuracyresults-analysis-services-data-mining.md)  
  
  
