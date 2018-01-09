---
title: "SELECT FROM&lt;モデル&gt;です。ケース (DMX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SELECT
- CASES
- FROM
dev_langs: DMX
helpviewer_keywords:
- SELECT FROM <model>.CASES statement
- drillthrough [DMX]
ms.assetid: d58acb47-aaa6-40b7-b8c4-6a6700fbc1dd
caps.latest.revision: "55"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: b40b75f21b77e6dd17cf426be3ea70fe05ac0757
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="select-from-ltmodelgtcases-dmx"></a>SELECT FROM&lt;モデル&gt;です。ケース (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  ドリルスルーをサポートし、モデルのトレーニングに使用されたケースを返します。 マイニング構造とマイニング モデルについてドリルスルーを有効にした場合、ユーザーが適切な権限を持っているときは、モデルに含まれていない構造列も返すことができます。  
  
 ドリルスルーがマイニング モデルで使用可能でない場合、このステートメントは失敗します。  
  
> [!NOTE]  
>  データ マイニング拡張機能 (DMX) では、ドリルスルーはモデルの作成時にのみ可能です。 使用して、既存のモデルにドリルスルーを追加することができます[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]が、表示したり、ケースをクエリする前に、モデルが再処理する必要があります。  
  
 ドリルスルーを有効にする方法の詳細については、次を参照してください。[マイニング モデルの作成 &#40;DMX&#41;](../dmx/create-mining-model-dmx.md)、 [SELECT INTO &#40;DMX&#41;](../dmx/select-into-dmx.md)、および[ALTER MINING STRUCTURE &#40;DMX&#41;](../dmx/alter-mining-structure-dmx.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
SELECT [FLATTENED] [TOP <n>] <expression list> FROM <model>.CASES  
[WHERE <condition expression>][ORDER BY <expression> [DESC|ASC]]  
```  
  
## <a name="arguments"></a>引数  
 *n*  
 省略可。 返す行数を指定する整数値です。  
  
 *式の一覧*  
 式のコンマ区切りのリストです。 式には、列識別子、ユーザー定義関数、UDF、VBA 関数などを含めることができます。  
  
 マイニング モデルに含まれていない構造列を含めるには、関数 `StructureColumn('<structure column name>')` を使用します。  
  
 *model*  
 モデル識別子です。  
  
 *条件式*  
 列のリストから返される値を制限する条件です。  
  
 *式 (expression)*  
 省略可。 スカラー値を返す式。  
  
## <a name="remarks"></a>解説  
 マイニング モデルとマイニング構造の両方についてドリルスルーを有効にした場合、そのモデルと構造に対するドリルスルー権限を持つロールのメンバー ユーザーが、マイニング モデルに含まれていないマイニング構造の列にアクセスできるようになります。 したがって、機密データまたは個人情報を保護する必要がありますを構築、個人情報をマスクし、付与、するデータ ソース ビュー **AllowDrillthrough**必要がある場合にのみ、マイニング構造に対する権限。  
  
 [Lag &#40;DMX&#41;](../dmx/lag-dmx.md)を返したりフィルター各ケースと初期時間の間のタイム ラグ タイム シリーズ モデルで関数を使用できます。  
  
 使用して、 [IsInNode & # #40; DMX &#41;](../dmx/isinnode-dmx.md)で機能、**場所**句には、スキーマ行セットの NODE_UNIQUE_NAME 列によって指定されているノードに関連付けられているケースのみが返されます。  
  
## <a name="examples"></a>使用例  
 次の例は、マイニング構造に基づく Targeted Mailing に基づいて、[!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]データベースとその関連マイニング モデルです。 詳細については、次を参照してください。 [Basic Data Mining Tutorial](http://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c)です。  
  
### <a name="example-1-drillthrough-to-model-cases-and-structure-columns"></a>例 1 : モデル ケースと構造列にドリルスルーする  
 次の例は、Targeted Mailing モデルのテストに使用されたすべてのケースの列を返します。 モデルの基となるマイニング構造に、提示されたテスト データセットが含まれていない場合、このクエリはケースを返しません。 必要な列のみを返す式のリストを使用できます。  
  
```  
SELECT * FROM [TM Decision Tree].Cases  
WHERE IsTestCase();  
```  
  
### <a name="example-2-drillthrough-to-training-cases-in-a-specific-node"></a>例 2 : 特定のノードのトレーニング ケースにドリルスルーする  
 次の例は、Cluster 2 のトレーニングに使用されたケースのみを返します。 Cluster 2 のノードの NODE_UNIQUE_NAME 列の値は '002' です。 この例では、構造列を 1 つ、[Customer Key]、マイニング モデルの一部ではなかったと別名も返されます`CustomerID`列にします。 構造列の名前は文字列値として渡されるので、角かっこではなく引用符で囲む必要があります。  
  
```  
SELECT StructureColumn('Customer Key') AS CustomerID, *   
FROM [TM_Clustering].Cases  
WHERE IsTrainingCase()  
AND IsInNode('002')  
```  
  
 構造列を返すには、マイニング モデルとマイニング構造の両方についてドリルスルー権限を有効にする必要があります。  
  
> [!NOTE]  
>  すべての種類のマイニング モデルでドリルスルーがサポートされるわけではありません。 ドリルスルーをサポートするモデルについては、次を参照してください。[ドリルスルー クエリ (&) #40 です。 データ マイニング &#41;](../analysis-services/data-mining/drillthrough-queries-data-mining.md)です。  
  
## <a name="see-also"></a>参照  
 [選択 &#40;DMX&#41;](../dmx/select-dmx.md)   
 [データ マイニング拡張機能 &#40;DMX&#41;データ定義ステートメント](../dmx/dmx-statements-data-definition.md)   
 [データ マイニング拡張機能 &#40;DMX&#41;データ操作ステートメント](../dmx/dmx-statements-data-manipulation.md)   
 [データ マイニング拡張機能 &#40;DMX&#41; ステートメント リファレンス](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
