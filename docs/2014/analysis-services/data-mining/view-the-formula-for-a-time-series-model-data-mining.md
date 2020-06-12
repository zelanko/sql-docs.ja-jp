---
title: タイムシリーズモデルの式の表示 (データマイニング) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], how-to topics
- ARTXP
- time series algorithms [Analysis Services]
- ARIMA
- time series [Analysis Services]
- Time Series Viewer [Analysis Services]
ms.assetid: 825ef719-2f44-4979-be01-5a81f54e1a53
author: minewiskan
ms.author: owend
ms.openlocfilehash: 27df4456d774f7c80f30fd4840c521ddf93c77a6
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84520218"
---
# <a name="view-the-formula-for-a-time-series-model-data-mining"></a>タイム シリーズ モデルの式の表示 (データ マイニング)
  [!INCLUDE[msCoName](../../includes/msconame-md.md)]タイムシリーズビューアーの inData マイニングデザイナーでは、タイムシリーズモデルで使用される回帰式の詳細を最も簡単に表示できます。  
  
 モデル コンテンツのクエリを実行することで、タイム シリーズ モデルの回帰式を抽出できます。 ただし、ARTXP または ARIMA の完全な式を表示するには、 [Microsoft タイムシリーズビューアー](browse-a-model-using-the-microsoft-time-series-viewer.md)の [**マイニング凡例**] を使用することをお勧めします。これにより、すべての定数が読み取り可能な形式で表示されます。  
  
 混合モデルを作成した場合は、ARIMA と ARTXP の分析が個別のツリーに作成され、モデルを表すルート ノードで結合されます。 ARIMA と ARTXP のツリーの構造は非常に異なります。 たとえば、ARTXP ツリーは実際にはデシジョン ツリーのようなツリー構造ですが、ARIMA ツリーは一連の移動平均を表します。 したがって、この 2 つの表現は、便宜上 1 つのモデルで提示されていますが、2 つの独立したモデルとして扱う必要があります。 式もまったく別のものであり、結合または比較することはできません。  
  
 [Microsoft 汎用コンテンツツリービューアー](../microsoft-generic-content-tree-viewer-data-mining.md)を使用して、タイムシリーズモデルを表示することもできます。 タイムシリーズモデルの内容の詳細については、「 [Analysis Services データマイニング&#41;&#40;タイムシリーズモデルのマイニングモデルコンテンツ](mining-model-content-for-time-series-models-analysis-services-data-mining.md)」を参照してください。  
  
### <a name="to-view-the-artxp-regression-formula-for-a-time-series-model"></a>タイム シリーズ モデルの ARTXP 回帰式を表示するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、表示するタイム シリーズ モデルを選択して、 **[参照]** をクリックします。  
  
     -- または --  
  
     [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、タイム シリーズ モデルを選択して、 **[マイニング モデル ビューアー]** タブをクリックします。  
  
2.  **[Model (モデル)]** タブをクリックします。  
  
3.  モデルに複数のツリーが含まれる場合は、 **[ツリー]** ボックスの一覧で 1 つのツリーを選択します。  
  
    > [!NOTE]  
    >  複数のデータ系列がある場合、モデルには必ず複数のツリーが含まれます。 ただし、 **タイム シリーズ ビューアー** では、 [Microsoft 汎用コンテンツ ツリー ビューアー](../microsoft-generic-content-tree-viewer-data-mining.md)ほど多くのツリーは表示されません。 これは、タイム シリーズ ビューアーが、データ系列ごとに ARIMA と ARTXP の情報を 1 つの表現にまとめるためです。  
  
4.  ツリーの任意のリーフ ノードをクリックします。  
  
     **[データ系列]** というラベルのノードは常にリーフ ノードであり、式を含むことができます。 **[(すべて)]** ノードに子ノードがない場合も、式を含むことができます。  
  
5.  **[マイニング凡例]** が表示されない場合は、ノードを右クリックし、 **[凡例の表示]** をクリックします。  
  
     ARTXP 式は、 **[マイニング凡例]** の前半に、 **[ツリー ノード式]** として表示されます。  
  
### <a name="to-view-the-arima-formula-for-a-time-series-model"></a>タイム シリーズ モデルの ARIMA 式を表示するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、表示するタイム シリーズ モデルを選択して、 **[参照]** をクリックします。  
  
     -- または --  
  
     [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、タイム シリーズ モデルを選択して、 **[マイニング モデル ビューアー]** タブをクリックします。  
  
2.  **[Model (モデル)]** タブをクリックします。  
  
3.  モデルに複数のツリーが含まれる場合は、 **[ツリー]** ボックスの一覧で 1 つのツリーを選択します。  
  
    > [!NOTE]  
    >  複数のデータ系列がある場合、モデルには必ず複数のツリーが含まれます。  
  
4.  ツリーの任意のノードをクリックします。  
  
     ARIMA 式は、 **[マイニング凡例]** の後半に、 **[ARIMA 式]** として表示されます。  
  
5.  **[マイニング凡例]** が表示されない場合は、ノードを右クリックし、 **[凡例の表示]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [マイニングモデルビューアーのタスクと操作方法](mining-model-viewer-tasks-and-how-tos.md)   
 [Microsoft タイムシリーズビューアーを使用したモデルの参照](browse-a-model-using-the-microsoft-time-series-viewer.md)   
 [Time Series Model Query Examples](time-series-model-query-examples.md)  
  
  
