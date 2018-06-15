---
title: SystemGetClusterCrossValidationResults (Analysis Services - データ マイニング) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ce11f7cb54d40336633d09a5d6601f0366c6bf55
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34018879"
---
# <a name="systemgetclustercrossvalidationresults-analysis-services---data-mining"></a>SystemGetClusterCrossValidationResults (Analysis Services - データ マイニング)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  指定した数の複数のセクションにマイニング構造をパーティション分割し、各パーティションに対してモデルをトレーニングして、各パーティションの精度の基準を返します。  
  
 **注** このストアド プロシージャは、少なくとも 1 つのクラスター モデルが含まれているマイニング構造でのみ使用できます。 非クラスター モデルをクロス検証するには、 [SystemGetCrossValidationResults (Analysis Services - データ マイニング)](../../analysis-services/data-mining/systemgetcrossvalidationresults-analysis-services-data-mining.md)を使用する必要があります。  
  
## <a name="syntax"></a>構文  
  
```  
  
SystemGetClusterCrossValidationResults(  
<structure name>,   
[,<mining model list>]  
,<fold count>}  
,<max cases>  
<test list>])  
```  
  
## <a name="arguments"></a>引数  
 *マイニング構造 (mining structure)*  
 現在のデータベースのマイニング構造の名前。  
  
 (必須)  
  
 *マイニング モデルの一覧 (mining model list)*  
 検証するマイニング モデルのコンマ区切りの一覧。  
  
 マイニング モデルの一覧を指定しないと、指定した構造に関連付けられたすべてのクラスター モデルに対してクロス検証が実行されます。  
  
> [!NOTE]  
>  クラスター モデルではないモデルをクロス検証するには、 [SystemGetCrossValidationResults (Analysis Services - データ マイニング)](../../analysis-services/data-mining/systemgetcrossvalidationresults-analysis-services-data-mining.md)を使用する必要があります。  
  
 (省略可能)  
  
 *フォールド カウント (fold count)*  
 データセットを分割するパーティションの数を指定する整数。 最小値は、2 です。 フォールドの最大数は、 **maximum integer** とケース数のいずれか小さい方になります。  
  
 各パーティションには、 *ケースの最大数*/*フォールド カウント*とほぼ同じ数のケースが含まれます。  
  
 既定値はありません。  
  
> [!NOTE]  
>  フォールドの数は、クロス検証の実行に必要な時間に大きく影響します。 選択する数が大きすぎると、クエリの実行時間が非常に長くなる可能性があります。また、場合によっては、サーバーが応答しなくなったり、タイムアウトする可能性があります。  
  
 (必須)  
  
 *ケースの最大数*  
 テストできるケースの最大数を指定する整数。  
  
 値に 0 を指定すると、データ ソース内のすべてのケースが使用されます。  
  
 データセット内の実際のケース数より大きい数字を指定すると、データ ソース内のすべてのケースが使用されます。  
  
 (必須)  
  
 *テスト リスト (test list)*  
 テスト オプションを指定する文字列。  
  
 **注** このパラメーターは将来使用するために予約されています。  
  
 (省略可能)  
  
## <a name="return-type"></a>戻り値の型  
 戻り値の型のテーブルには、個別のパーティションのスコアと、すべてのモデルの集計が含まれます。  
  
 次の表は、返される列を示しています。  
  
|列名|Description|  
|-----------------|-----------------|  
|ModelName|テストされたモデルの名前。|  
|AttributeName|予測可能列の名前。 クラスター モデルでは、常に **null**になります。|  
|AttributeState|予測可能列で指定した対象の値。 クラスター モデルでは、常に **null.**|  
|PartitionIndex|結果が適用されるパーティションを識別する、1 から始まるインデックス。|  
|PartitionSize|各パーティションに含まれていたケースの数を示す整数。|  
|テスト|実行されたテストの種類。|  
|[メジャー]|テストから返されたメジャーの名前。 各モデルのメジャーは、予測可能な値の型によって異なります。 各メジャーの定義については、「[相互検証 &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/cross-validation-analysis-services-data-mining.md)」を参照してください。<br /><br /> 予測可能な型ごとに返されるメジャーの一覧については、「[相互検証レポートのメジャー](../../analysis-services/data-mining/measures-in-the-cross-validation-report.md)」を参照してください。|  
|値|指定したテスト メジャーの値。|  
  
## <a name="remarks"></a>解説  
 データ セット全体の精度の基準を返すには、 [SystemGetClusterAccuracyResults (Analysis Services - データ マイニング)](../../analysis-services/data-mining/systemgetclusteraccuracyresults-analysis-services-data-mining.md)を使用する必要があります。  
  
 また、既にマイニング モデルをフォールドにパーティション分割している場合は、 [SystemGetClusterAccuracyResults (Analysis Services - データ マイニング)](../../analysis-services/data-mining/systemgetclusteraccuracyresults-analysis-services-data-mining.md)を使用する必要があります。  
  
## <a name="examples"></a>使用例  
 次の例では、マイニング構造を 3 つのフォールドにパーティション分割し、マイニング構造に関連付けられている 2 つのクラスター モデルをテストする方法を示します。  
  
 コードの 3 行目では、テストする特定のマイニング モデルの一覧を指定します。 一覧を指定しない場合、構造に関連付けられているすべてのクラスター モデルが使用されます。  
  
 コードの 4 行目ではフォールドの数を指定し、5 行目では使用するケースの最大数を指定しています。  
  
 これらはクラスター モデルであるため、予測可能な属性または値を指定する必要はありません。  
  
```  
CALL SystemGetClusterCrossValidationResults(  
[v Target Mail],  
[Cluster 1], [Cluster 2],  
3,  
10000  
)  
```  
  
 サンプルの結果 :  
  
|ModelName|AttributeName|AttributeState|PartitionIndex|PartitionSize|テスト|[メジャー]|値|  
|---------------|-------------------|--------------------|--------------------|-------------------|----------|-------------|-----------|  
|クラスター 1|||1|3025|クラスター|ケースの確率値|0.930524511864121|  
|クラスター 1|||2|3025|クラスター|ケースの確率値|0.919184178430778|  
|クラスター 1|||3|3024|クラスター|ケースの確率値|0.929651120490248|  
|Cluster 2|||1|1289|クラスター|ケースの確率値|0.922789726933607|  
|Cluster 2|||2|1288|クラスター|ケースの確率値|0.934865535691068|  
|Cluster 2|||3|1288|クラスター|ケースの確率値|0.924724595688798|  
  
## <a name="requirements"></a>必要条件  
 クロス検証は、 [!INCLUDE[ssEnterprise](../../includes/ssenterprise-md.md)] 以降の [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]でのみ使用できます。  
  
## <a name="see-also"></a>参照  
 [SystemGetCrossValidationResults &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/systemgetcrossvalidationresults-analysis-services-data-mining.md)   
 [SystemGetAccuracyResults &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/systemgetaccuracyresults-analysis-services-data-mining.md)   
 [SystemGetClusterCrossValidationResults](../../analysis-services/data-mining/systemgetclustercrossvalidationresults-analysis-services-data-mining.md)   
 [SystemGetClusterAccuracyResults & #40 です。Analysis Services - データ マイニング & #41;](../../analysis-services/data-mining/systemgetclusteraccuracyresults-analysis-services-data-mining.md)  
  
  
