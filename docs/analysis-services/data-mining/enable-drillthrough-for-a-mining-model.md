---
title: "マイニング モデルのドリルスルーを有効にする |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data mining [Analysis Services], how-to topics
- drillthrough [Analysis Services]
ms.assetid: 4fa44f60-ef9a-4b59-98c0-c0baf1195c8e
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e7e6ea500c7df8c57d7cec414ec31605c7d8991e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="enable-drillthrough-for-a-mining-model"></a>マイニング モデルのドリルスルーの有効化
  マイニング モデルのドリルスルーを有効にした場合は、モデルの参照時に、モデルの作成に使用されたケースに関する詳細情報を取得できます。 この情報を表示するには、必要な権限があり、構造が既に処理されている必要があります。  
  
 **権限** モデル データや構造データのドリルスルーを行うユーザーは、マイニング モデルまたはマイニング構造に対する [AllowDrillThrough](../../analysis-services/scripting/properties/allowdrillthrough-element-assl.md) 権限を持つロールのメンバーである必要があります。 ドリルスルー権限は、構造およびモデルで個別に設定されます。  
  
-   モデルのドリルスルー権限があれば、構造で権限が与えられていない場合でも、モデルからドリルスルーを行うことができます。  
  
-   構造のドリルスルー権限がある場合は、[StructureColumn (DMX)](../../dmx/structurecolumn-dmx.md) 関数を使用して、構造列をモデルからドリルスルー クエリに含めることもできます。 SELECT… \<構造 >。場合の構文。  
  
 **トレーニング ケースのキャッシュ** マイニング構造内のトレーニング ケースに関する情報が取得されることで、ドリルスルーが機能します。 この情報は、構造が処理されるときにキャッシュされます。 そのため、 <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> プロパティを **ClearAfterProcessing**に変更して、キャッシュされたデータをすべて消去した場合、ドリルスルーは機能しません。  
  
> [!NOTE]  
>  トレーニング ケースがキャッシュされていない場合、ケース データを表示するには、 <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> プロパティを **KeepTrainingCases** に変更してからモデルを再処理する必要があります。  
  
 詳細については、「 [ドリルスルー クエリ (データ マイニング)](../../analysis-services/data-mining/drillthrough-queries-data-mining.md)」をご覧ください。  
  
### <a name="to-enable-drillthrough-on-a-mining-model"></a>マイニング モデルのドリルスルーを有効にするには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]のデータ マイニング デザイナーの **[マイニング モデル]** タブで、ドリルスルーを有効にするマイニング モデルの名前を右クリックし、 **[プロパティ]**をクリックします。  
  
2.  **[プロパティ]** ウィンドウで **[AllowDrillthrough]**をクリックし、 **[True]**を選択します。  
  
3.  **[マイニング モデル]** タブでモデルを右クリックし、 **[モデルの処理]**をクリックします。  
  
### <a name="to-enable-caching-for-a-mining-structure"></a>マイニング構造のキャッシュを有効にするには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]のデータ マイニング デザイナーの **[マイニング構造]** タブで、マイニング構造の名前を右クリックします。  
  
2.  **[プロパティ]** ウィンドウを開きます。  
  
3.  **[プロパティ]** ウィンドウで、 **[CacheMode]** プロパティを探し、一覧から **[KeepTrainingCases]** を選択します。  
  
4.  **[データベース]** メニューの **[処理]**をクリックします。  
  
## <a name="see-also"></a>参照  
 [ドリルスルー クエリ &#40;データ マイニング&#41;](../../analysis-services/data-mining/drillthrough-queries-data-mining.md)  
  
  

