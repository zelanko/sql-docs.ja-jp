---
title: "Microsoft クラスター ビューアーを使用してモデルを参照 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- clusters [Analysis Services]
- discrimination [Analysis Services]
- names [Analysis Services], clusters
- Microsoft Cluster Viewer
- mining model content, viewing
- comparing clusters
- viewing clusters
- displaying clusters
- data mining [Analysis Services], clusters
- Cluster Viewer [Analysis Services]
- mining models [Analysis Services], clusters
ms.assetid: 591fe30b-d88f-4a71-94d4-4a3907fc275d
caps.latest.revision: "42"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 78190bb150a0cb1df68722c0ed602c88f413be9a
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="browse-a-model-using-the-microsoft-cluster-viewer"></a>Microsoft クラスター ビューアーを使用したモデルの参照
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)][!INCLUDE[msCoName](../../includes/msconame-md.md)]クラスター ビューアーに[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]に組み込まれているマイニング モデルを表示、[!INCLUDE[msCoName](../../includes/msconame-md.md)]クラスタ リング アルゴリズムです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] クラスタリング アルゴリズムは、データの異常を特定したり予測を作成したりするときにデータを調べるための分割アルゴリズムです。 このアルゴリズムの詳細については、「 [Microsoft クラスタリング アルゴリズム](../../analysis-services/data-mining/microsoft-clustering-algorithm.md)」を参照してください。  
  
> [!NOTE]  
>  モデルで使用された式と、検出されたパターンの詳細情報を表示するには、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 汎用コンテンツ ツリー ビューアーを使用します。 詳細については、「[Microsoft 汎用コンテンツ ツリー ビューアーを使用したモデルの参照](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)」または「[Microsoft 汎用コンテンツ ツリー ビューアー (データ マイニング)](http://msdn.microsoft.com/library/751b4393-f6fd-48c1-bcef-bdca589ce34c)」を参照してください。  
  
##  <a name="BKMK_ViewerTabs"></a> ビューアーのタブ  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]でマイニング モデルを参照すると、そのモデルに適したビューアーを使用してデータ マイニング デザイナーの **[マイニング モデル ビューアー]** タブにモデルが表示されます。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] クラスター ビューアーには、クラスタリング マイニング モデルを調べるための次のタブがあります。  
  
-   [クラスター ダイアグラム](#BKMK_Diagram)  
  
-   [クラスターのプロファイル](#BKMK_Profile)  
  
-   [クラスターの特性](#BKMK_Characteristics)  
  
-   [クラスターの識別](#BKMK_Discrimination)  
  
###  <a name="BKMK_Diagram"></a> クラスター ダイアグラム  
 **クラスター ビューアーの** [クラスター ダイアグラム] [!INCLUDE[msCoName](../../includes/msconame-md.md)] タブには、マイニング モデル内のすべてのクラスターが表示されます。 クラスター間を結ぶ線の網掛けは、クラスターの類似性の強度を表します。 網掛けが薄いか存在しない場合は、クラスターがあまり似ていません。 線の網掛けが濃くなるほど、リンクの類似性も強くなります。 ビューアーに表示される線の数は、クラスターの右側のスライダーを使用して調整できます。 スライダーを小さく設定すると、緊密なリンクのみが表示されます。  
  
 既定では、網掛けはクラスターの母集団を表します。 **[シェーディング変数]** オプションと **[状態]** オプションを使用すると、網掛けによって、属性と状態のどの組み合わせを表すかを選択できます。 網掛けが濃いほど、対応する状態の属性分布は広くなります。 網掛けが薄くなるほど、分布は狭くなります。  
  
 クラスターの名前を変更するには、そのノードを右クリックして **[クラスター名の変更]**を選択します。 新しい名前はサーバーに保存されます。  
  
 ダイアグラムの表示部分をクリップボードにコピーするには、 **[グラフ ビューのコピー]**をクリックします。 ダイアグラム全体をコピーするには、 **[グラフ全体のコピー]**をクリックします。 **[拡大]** と **[縮小]**を使用してダイアグラムを拡大または縮小することも、 **[ウィンドウに合わせてダイアグラムの倍率を変更します]**を使用してダイアグラムを画面に合わせて調整することもできます。  
  
 [トップに戻る](#BKMK_ViewerTabs)  
  
###  <a name="BKMK_Profile"></a> クラスターのプロファイル  
 **[クラスターのプロファイル]** タブには、モデルのアルゴリズムによって作成されるクラスターの概要が表示されます。 このビューには、各クラスター内の属性の分布と共に各属性が表示されます。 各セルのヒントには分布統計が表示され、各列見出しのヒントにはクラスターの母集団が表示されます。 不連続属性は色分けされたバーとして表示され、連続属性は各クラスター内の平均偏差および標準偏差を表すダイヤモンド チャートとして表示されます。 **[ヒストグラム バー]** オプションでは、ヒストグラムに表示されるバーの数を制御します。 指定した数よりも多くのバーが存在する場合は、重要度が最も高いバーが保持され、残りのバーは灰色のバケットにまとめられます。  
  
 クラスターの既定の名前は、よりわかりやすい名前に変更できます。 クラスター名を変更するには、クラスターの列見出しを右クリックして、 **[クラスター名の変更]**を選択します。 **[列の非表示]**を選択すると、クラスターを非表示にすることもできます。  
  
 より広範かつ詳細なクラスターのビューをウィンドウで開くには、 **[状態]** 列のセルまたはビューアーのヒストグラムをダブルクリックします。  
  
 そのクラスターの属性を重要度順に並べ替えるには、列見出しをクリックします。 列をドラッグして、ビューアーでの順序を変更することもできます。  
  
 [トップに戻る](#BKMK_ViewerTabs)  
  
###  <a name="BKMK_Characteristics"></a> クラスターの特性  
 **[クラスターの特性]** タブを使用するには、 **[クラスター]** 一覧でクラスターを選択します。 クラスターを選択した後、そのクラスターを構成する特性を検証することができます。 クラスターに含まれている属性は **[変数]** 列に表示され、属性の状態は **[値]** 列に表示されます。 属性の状態は、それがクラスターに表示される確率によって表され、重要度の順に並んでいます。 確率は **[確率]** 列に表示されます。  
  
 [トップに戻る](#BKMK_ViewerTabs)  
  
###  <a name="BKMK_Discrimination"></a> クラスターの識別  
 **[クラスターの識別]** タブを使用すると、2 つのクラスター間で属性を比較できます。 **[クラスター 1]** と **[クラスター 2]** の一覧を使用して、比較するクラスターを選択します。 クラスター間の最も重要な差異がビューアーによって決定され、その差異に関連付けられた属性の状態が重要度順に表示されます。 属性の右側のバーには、どのクラスターがその状態で優先されているかが示され、その状態がクラスターを優先する度合いがバーのサイズによって表されます。  
  
 [トップに戻る](#BKMK_ViewerTabs)  
  
## <a name="see-also"></a>参照  
 [Microsoft クラスタリング アルゴリズム](../../analysis-services/data-mining/microsoft-clustering-algorithm.md)   
 [マイニング モデル ビューアーのタスクと操作方法](../../analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md)   
 [マイニング モデル ビューアーのタスクと操作方法](../../analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md)   
 [データ マイニング ツール](../../analysis-services/data-mining/data-mining-tools.md)   
 [データ マイニング モデル ビューアー](../../analysis-services/data-mining/data-mining-model-viewers.md)  
  
  
