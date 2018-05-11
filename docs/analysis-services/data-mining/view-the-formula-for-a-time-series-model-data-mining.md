---
title: タイム シリーズの式の表示モデル (データ マイニング) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 92281a0c8cd570d14c605e5cfc0b173905971a19
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="view-the-formula-for-a-time-series-model-data-mining"></a>タイム シリーズ モデルの式の表示 (データ マイニング)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ マイニングを使用してタイム シリーズ モデルを作成した場合、モデルの回帰式を確認する最も簡単な方法は、すべての定数を読み取り可能な形式で表示する **Microsoft タイム シリーズ ビューアー** の [マイニング凡例](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-time-series-viewer.md)を使用する方法です。  
  
### <a name="to-view-the-artxp-regression-formula-for-a-time-series-model"></a>タイム シリーズ モデルの ARTXP 回帰式を表示するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、表示するタイム シリーズ モデルを選択して、 **[参照]** をクリックします。  
  
     -- または --  
  
     [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、タイム シリーズ モデルを選択して、 **[マイニング モデル ビューアー]** タブをクリックします。  
  
2.  **[モデル]** タブをクリックします。  
  
3.  モデルに複数のツリーが含まれる場合は、 **[ツリー]** ボックスの一覧で 1 つのツリーを選択します。  
  
    > [!NOTE]  
    >  複数のデータ系列がある場合、モデルには必ず複数のツリーが含まれます。 ただし、 **タイム シリーズ ビューアー** では、 [Microsoft 汎用コンテンツ ツリー ビューアー](http://msdn.microsoft.com/library/751b4393-f6fd-48c1-bcef-bdca589ce34c)ほど多くのツリーは表示されません。 これは、タイム シリーズ ビューアーが、データ系列ごとに ARIMA と ARTXP の情報を 1 つの表現にまとめるためです。  
  
4.  ツリーの任意のリーフ ノードをクリックします。  
  
     **[データ系列]** というラベルのノードは常にリーフ ノードであり、式を含むことができます。 **[(すべて)]** ノードに子ノードがない場合も、式を含むことができます。  
  
5.  **[マイニング凡例]** が表示されない場合は、ノードを右クリックし、 **[凡例の表示]** をクリックします。  
  
     ARTXP 式は、 **[マイニング凡例]** の前半に、 **[ツリー ノード式]** として表示されます。  
  
     ![タイム シリーズ式の凡例に表示](../../analysis-services/data-mining/media/ssdm-timeserieslegend.png "凡例でタイム シリーズ式の表示")  
  
### <a name="to-view-the-arima-formula-for-a-time-series-model"></a>タイム シリーズ モデルの ARIMA 式を表示するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、表示するタイム シリーズ モデルを選択して、 **[参照]** をクリックします。  
  
     -- または --  
  
     [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、タイム シリーズ モデルを選択して、 **[マイニング モデル ビューアー]** タブをクリックします。  
  
2.  **[モデル]** タブをクリックします。  
  
3.  モデルに複数のツリーが含まれる場合は、 **[ツリー]** ボックスの一覧で 1 つのツリーを選択します。  
  
    > [!NOTE]  
    >  複数のデータ系列がある場合、モデルには必ず複数のツリーが含まれます。  
  
4.  ツリーの任意のノードをクリックします。  
  
     ARIMA 式は、 **[マイニング凡例]** の後半に、 **[ARIMA 式]** として表示されます。  
  
5.  **[マイニング凡例]** が表示されない場合は、ノードを右クリックし、 **[凡例の表示]** をクリックします。  
  
### <a name="to-get-the-coefficients-and-terms-for-the-equation"></a>式の係数と項を取得するには  
  
1.  モデル コンテンツに **コンテンツ クエリ** を作成することで、タイム シリーズ モデルの回帰式の項と係数を取得することもできます。  
  
     詳細については、「 [タイム シリーズ モデルのクエリ例](../../analysis-services/data-mining/time-series-model-query-examples.md)」を参照してください。  
  
2.  [Microsoft 汎用コンテンツ ツリー ビューアー](http://msdn.microsoft.com/library/751b4393-f6fd-48c1-bcef-bdca589ce34c)を使用することで、タイム シリーズ モデルを参照して項や係数を探すこともできます。  
  
     詳細については、「[タイム シリーズ モデルのマイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/mining-model-content-for-time-series-models-analysis-services-data-mining.md)」を参照してください。  
  
    > [!NOTE]  
    >  ARIMA モデルと ARTXP モデルの両方を使用する混在モデルのコンテンツを参照すると、2 つのモデルは別のツリーにあり、モデルを表すルート ノードで結合されています。 ARIMA モデルと ARTXP モデルは便宜上 1 つのビューアーで表示されますが、式と同様に構造はまったく異なり、結合も比較もできません。 ARTXP ツリーはデシジョン ツリーにより近く、ARIMA ツリーは一連の移動平均を表します。  
  
## <a name="see-also"></a>参照  
 [マイニング モデル ビューアーのタスクと操作方法](../../analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md)   
 [Microsoft タイム シリーズ ビューアーを使用してモデルを参照します。](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-time-series-viewer.md)  
  
  
