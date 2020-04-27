---
title: Naive Bayes Model | の参照Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: f9160b48-3beb-439c-9694-f084e1afa625
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 65b8bb26a72903644b5985d69efc8adb362fe412
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66088478"
---
# <a name="browsing-a-naive-bayes-model"></a>Naive Bayes モデルの参照
  **参照**を使用して単純な Bayes モデルを開くと、4つの異なるペインを含む対話型ビューアーにモデルが表示されます。 ビューアーを使用して、相関関係を調査し、モデルと基になるデータに関する情報を取得します。  
  
-   [依存関係ネットワーク](#bkmk_DepNet)  
  
-   [属性のプロファイル](#bkmk_AttProf)  
  
-   [属性の特性](#bkmk_AttChar)  
  
-   [属性の識別](#bkmk_AttDisc)  
  
##  <a name="explore-the-model"></a><a name="BKMK_Tabs"></a>モデルの調査  
 ビューアーの目的は、[!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes モデルで検出された入力属性と出力属性 (入力と従属変数) の相互作用を調査することです。  
  
 単純な Bayes ビューアーを試してみる場合は、[データマイニング] リボンの [ [Excel 用データマイニングアドインの &#40;データマイニングアドイン]&#41;](classify-wizard-data-mining-add-ins-for-excel.md)ウィザードを使用して、[**詳細設定**] オプションをクリックし、単純な Bayes アルゴリズムを使用するようにアルゴリズムを変更します。  
  
 これらの例では、サンプルブックのソースデータを使用して、**年収**の列を、**非常に低い**から**非常に高い**5 つの収入グループにグループ化しています。 その後、Naïve Bayes モデルを使って、各収入カテゴリと相関関係を持つ要因を分析しました。  
  
###  <a name="dependency-network"></a><a name="bkmk_DepNet"></a>依存関係ネットワーク  
 最初に使用するウィンドウは、**依存関係ネットワーク**です。 どの入力が選択した結果と密接に関連しているかがひとめでわかります。  
  
 ![Naive Bayes ビューアーに表示された依存関係ネットワーク](media/dm13-nb.gif "Naive Bayes ビューアーに表示された依存関係ネットワーク")  
  
##### <a name="explore-the-dependency-network"></a>依存関係ネットワークの調査  
  
1.  最初に、目標の結果 (**年収**) をクリックします。これは、グラフのノードとして表されます。  
  
     目標の変数を囲む強調表示されたノードは、この結果と統計的に相関関係のあるノードです。 関係の特性を理解するには、ビューアーの下部にある凡例を使用します。  
  
2.  ビューアーの左側にあるスライダーをクリックして下へドラッグします。  
  
     このコントロールは、依存関係の強さに基づいて、独立変数をフィルター処理します。 スライダーをドラッグして下げると、関係が最も強いリンクだけがグラフに表示されます。  
  
3.  グラフをフィルター処理した後、[**グラフビューのコピー**] ボタンをクリックします。 Excel でワークシートを選択し、Ctrl キーを押しながら V キーを押します。  
  
     これで、選択したビューが、フィルターと強調表示も含めて、コピーされます。  
  
 [トップに戻る](#BKMK_Tabs)  
  
###  <a name="attribute-profiles"></a><a name="bkmk_AttProf"></a> 属性のプロファイル  
 [**属性プロファイル**ウィンドウには、他のすべての変数が個々の結果にどのように関連しているかが視覚的に示されます。  
  
##### <a name="explore-the-profiles"></a>プロファイルの調査  
  
1.  結果を簡単に比較できるように、いくつかの値を非表示にするには、列見出しを別の列にドラッグします。  
  
     ![Naive Bayes ビューアーに表示された属性のプロファイル](media/dm13-nb-attprof.gif "Naive Bayes ビューアーに表示された属性のプロファイル")  
  
2.  任意のセルをクリックすると、[**マイニング凡例**] の値の分布が表示されます。  
  
     異なる結果に関連付けられた属性は異なる表示になるため、地域別の収入の分布など、興味のある相関関係をすばやく見つけることができます。  
  
3.  このビューの基になるデータを取得するには、[ **Excel にコピー**] をクリックします。 個々の属性と結果との相関関係を示す新しいテーブルがワークシートに生成されます。 この Excel テーブルでは、簡単に列の非表示やフィルター処理ができます。  
  
 [トップに戻る](#BKMK_Tabs)  
  
###  <a name="attribute-characteristics"></a><a name="bkmk_AttChar"></a>属性の特性  
 **属性特性**ビューは、特定の結果変数および関与する要因の詳細な調査に役立ちます。  
  
 ![Naive Bayes ビューアーに表示された属性の特性](media/dm13-nb-viewer.gif "Naive Bayes ビューアーに表示された属性の特性")  
  
##### <a name="explore-the-attribute-characteristics"></a>属性の特性の調査  
  
1.  [**値**] をクリックし、**値**から項目を選択します。  
  
     目標の結果を選択すると、グラフが更新されて、その結果との関連性が最も強い要素が重要度順に表示されます。  
  
     [ [&#40;テーブル分析ツール]&#41;](analyze-key-influencers-table-analysis-tools-for-excel.md)オプションを使用してモデルを作成する場合は、複数の予測可能な属性を持つモデルを作成できます。 ただし、データ マイニング アドインのその他のウィザードはすべて、予測可能な属性が 1 つに制限されています。  
  
2.  新しいワークシートにテーブルを作成するには、[ **Excel にコピー** ] をクリックします。これにより、選択したターゲットの結果に関連するすべての属性のスコアが一覧表示されます。  
  
 [トップに戻る](#BKMK_Tabs)  
  
###  <a name="attribute-discrimination"></a><a name="bkmk_AttDisc"></a>属性の識別  
 **属性の識別**ビューは、2つの結果、または1つの結果と他のすべての結果を比較するのに役立ちます。  
  
 ![Naive Bayes ビューアーに表示された属性の識別](media/dm13-nb-attdisc.gif "Naive Bayes ビューアーに表示された属性の識別")  
  
##### <a name="explore-attribute-discrimination"></a>属性の識別の調査  
  
1.  比較する結果を選択するには、[**値 1** ] と [**値 2**] のコントロールを使用します。  
  
     たとえば、このモデルでは、低所得グループにいくつかの興味深い属性があったので、最初のドロップダウンリストで最も低い収入グループを選択し、2番目のドロップダウンリストで [**その他のすべての状態**] を選択しました。  
  
     属性は、重要度順に並べ替えられます (重要度はトレーニング データに基づいて計算)。 したがって、職業が最も密接に収入との相関関係がある要因です (少なくともこの対象グループの場合)。  
  
     正確な数値を表示するには、色分けされたバーをクリックし、[**マイニング凡例**] を表示します。  
  
2.  低収入は、ヨーロッパ地域とも相関関係があります。  
  
     Naïve Bayes モデルではドリルダウンはサポートされていません。ただし、この結果グループに関連付けられたケースを調査する場合は、クエリを使用できます。 この種類のモデルに対するクエリの詳細については、「 [Naive Bayes model のクエリ例](data-mining/naive-bayes-model-query-examples.md)」を参照してください。  
  
 [トップに戻る](#BKMK_Tabs)  
  
## <a name="see-also"></a>参照  
 [Excel &#40;SQL Server データマイニングアドインのモデルの参照&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  
