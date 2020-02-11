---
title: マイニングモデルのドリルスルーを有効にする |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], how-to topics
- drillthrough [Analysis Services]
ms.assetid: 4fa44f60-ef9a-4b59-98c0-c0baf1195c8e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 06ce3967bf9258e9b8f6cd4a28cb28a29a1e0588
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66084543"
---
# <a name="enable-drillthrough-for-a-mining-model"></a>マイニング モデルのドリルスルーの有効化
  マイニング モデルのドリルスルーを有効にした場合は、モデルの参照時に、モデルの作成に使用されたケースに関する詳細情報を取得できます。 この情報を表示するには、必要な権限があり、構造が既に処理されている必要があります。  
  
 **アクセス許可**ユーザーがモデルデータまたは構造データにドリルスルーするには、マイニングモデルまたはマイニング構造に対する[Allowdrillthrough スルー](https://docs.microsoft.com/bi-reference/assl/properties/allowdrillthrough-element-assl)権限を持つロールのメンバーである必要があります。 ドリルスルー権限は、構造およびモデルで個別に設定されます。  
  
-   モデルのドリルスルー権限があれば、構造で権限が与えられていない場合でも、モデルからドリルスルーを行うことができます。  
  
-   構造のドリルスルー権限がある場合は、[StructureColumn &#40;DMX&#41;](/sql/dmx/structurecolumn-dmx) 関数を使用して、構造列をモデルからドリルスルー クエリに含めることもできます。 また、[選択...] を使用して、構造内のトレーニングケースとテストケースに対してクエリを実行することもできます。構造\<体> から。CASE 構文。  
  
 **トレーニングケースのキャッシュ**ドリルスルーは、マイニング構造内のトレーニングケースに関する情報を取得することによって機能します。 この情報は、構造が処理されるときにキャッシュされます。 そのため、<xref:Microsoft.AnalysisServices.MiningStructureCacheMode> プロパティを `ClearAfterProcessing` に変更して、キャッシュされたデータをすべて消去した場合、ドリルスルーは機能しません。  
  
> [!NOTE]  
>  トレーニング ケースがキャッシュされていない場合、ケース データを表示するには、 <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> プロパティを **KeepTrainingCases** に変更してからモデルを再処理する必要があります。  
  
 詳細については、「 [ドリルスルー クエリ (データ マイニング)](drillthrough-queries-data-mining.md)」をご覧ください。  
  
### <a name="to-enable-drillthrough-on-a-mining-model"></a>マイニング モデルのドリルスルーを有効にするには  
  
1.  
  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]のデータ マイニング デザイナーの **[マイニング モデル]** タブで、ドリルスルーを有効にするマイニング モデルの名前を右クリックし、 **[プロパティ]** をクリックします。  
  
2.  
  **[プロパティ]** ウィンドウで **[AllowDrillthrough]** をクリックし、 **[True]** を選択します。  
  
3.  
  **[マイニング モデル]** タブでモデルを右クリックし、 **[モデルの処理]** をクリックします。  
  
### <a name="to-enable-caching-for-a-mining-structure"></a>マイニング構造のキャッシュを有効にするには  
  
1.  
  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]のデータ マイニング デザイナーの **[マイニング構造]** タブで、マイニング構造の名前を右クリックします。  
  
2.  
  **[プロパティ]** ウィンドウを開きます。  
  
3.  
  **[プロパティ]** ウィンドウで、 **[CacheMode]** プロパティを探し、一覧から **[KeepTrainingCases]** を選択します。  
  
4.  
  **[データベース]** メニューの **[処理]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [データマイニング &#40;のドリルスルークエリ&#41;](drillthrough-queries-data-mining.md)  
  
  
