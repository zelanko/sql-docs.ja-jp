---
title: Microsoft シーケンス クラスター ビューアーを使用してモデルを参照 |Microsoft ドキュメント
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: cce1203b73f5a1685634c4b50f6e5941bed3eb98
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34016789"
---
# <a name="browse-a-model-using-the-microsoft-sequence-cluster-viewer"></a>Microsoft シーケンス クラスター ビューアーを使用したモデルの参照
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] シーケンス クラスター ビューアーには、[!INCLUDE[msCoName](../../includes/msconame-md.md)] シーケンス クラスター アルゴリズムを使用して作成されたマイニング モデルが表示されます。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] シーケンス クラスター アルゴリズムは、パス ( *シーケンス*) をたどることによってリンクできるイベントが含まれているデータを探索するためのシーケンス分析アルゴリズムです。 このアルゴリズムの詳細については、 [「Microsoft シーケンス クラスター アルゴリズム」](../../analysis-services/data-mining/microsoft-sequence-clustering-algorithm.md)を参照してください。  
  
> [!NOTE]  
>  モデルで使用された式と、検出されたパターンの詳細情報を表示するには、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 汎用コンテンツ ツリー ビューアーを使用します。 詳細については、「[Microsoft 汎用コンテンツ ツリー ビューアーを使用したモデルの参照](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)」または「[Microsoft 汎用コンテンツ ツリー ビューアー (データ マイニング)](http://msdn.microsoft.com/library/751b4393-f6fd-48c1-bcef-bdca589ce34c)」を参照してください。  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] シーケンス クラスター ビューアーには、[!INCLUDE[msCoName](../../includes/msconame-md.md)] クラスター ビューアーに似た機能とオプションが用意されています。 詳細については、「 [Microsoft クラスター ビューアーを使用したモデルの参照](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)」を参照してください。  
  
##  <a name="BKMK_ViewerTabs"></a> ビューアーのタブ  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]でマイニング モデルを参照すると、そのモデルに適したビューアーを使用してデータ マイニング デザイナーの **[マイニング モデル ビューアー]** タブにモデルが表示されます。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] シーケンス クラスター ビューアーには、シーケンス クラスター マイニング モデルを調べるための次のタブがあります。  
  
-   [クラスター ダイアグラム](#BKMK_Diagram)  
  
-   [クラスターのプロファイル](#BKMK_Profile)  
  
-   [クラスターの特性](#BKMK_Characteristics)  
  
-   [クラスターの識別](#BKMK_Discrimination)  
  
-   [状態遷移](#BKMK_Transitions)  
  
###  <a name="BKMK_Diagram"></a> クラスター ダイアグラム  
 **シーケンス クラスター ビューアーの** [クラスター ダイアグラム] [!INCLUDE[msCoName](../../includes/msconame-md.md)] タブには、マイニング モデルに含まれているすべてのクラスターが表示されます。 クラスター間を結ぶ線の網掛けは、クラスターの類似性の強度を表します。 網掛けが薄いか存在しない場合は、クラスターがあまり似ていません。 線の網掛けが濃くなるほど、リンクの類似性も強くなります。 ビューアーに表示される線の数は、クラスターの右側のスライダーを使用して調整できます。 スライダーを小さく設定すると、緊密なリンクのみが表示されます。  
  
 既定では、網掛けはクラスターの母集団を表します。 **[シェーディング変数]** オプションと **[状態]** オプションを使用すると、網掛けによって、属性と状態のどの組み合わせを表すかを選択できます。 網掛けが濃いほど、対応する状態の属性分布は広くなります。 網掛けが薄くなるほど、分布は狭くなります。  
  
 クラスターの名前を変更するには、そのノードを右クリックして **[クラスター名の変更]** を選択します。 新しい名前はサーバーに保存されます。  
  
 ダイアグラムの表示部分をクリップボードにコピーするには、 **[グラフ ビューのコピー]** をクリックします。 ダイアグラム全体をコピーするには、 **[グラフ全体のコピー]** をクリックします。 **[拡大]** と **[縮小]** を使用してダイアグラムを拡大または縮小することも、 **[ウィンドウに合わせてダイアグラムの倍率を変更します]** を使用してダイアグラムを画面に合わせて調整することもできます。  
  
 [トップに戻る](#BKMK_ViewerTabs)  
  
###  <a name="BKMK_Profile"></a> クラスターのプロファイル  
 **[クラスターのプロファイル]** タブには、モデルのアルゴリズムによって作成されるクラスターの概要が表示されます。 グリッド内の **[母集団]** 列に続く各列は、モデルによって発見されたクラスターを表します。 \<属性 > <attribute>.samples 行は、クラスター内に存在するデータのさまざまなシーケンスを表す、\<属性 > 行は、クラスターに含まれるすべてのアイテムとその全体的な分布について説明します。  
  
 **[ヒストグラム バー]** オプションでは、ヒストグラムに表示されるバーの数を制御します。 指定した数よりも多くのバーが存在する場合は、重要度が最も高いバーが保持され、残りのバーは灰色のバケットにまとめられます。  
  
 クラスターの既定の名前は、よりわかりやすい名前に変更できます。 クラスター名を変更するには、クラスターの列見出しを右クリックして、 **[クラスター名の変更]** を選択します。 **[列の非表示]** を選択するとクラスターを非表示にでき、列をドラッグしてビューアー内の順序を変更することもできます。  
  
 より広範かつ詳細なクラスターのビューをウィンドウで開くには、 **[状態]** 列のセルまたはビューアーのヒストグラムをダブルクリックします。  
  
 [トップに戻る](#BKMK_ViewerTabs)  
  
###  <a name="BKMK_Characteristics"></a> クラスターの特性  
 **[クラスターの特性]** タブを使用するには、 **[クラスター]** 一覧でクラスターを選択します。 クラスターを選択した後、そのクラスターを構成する特性を検証することができます。 クラスターに含まれている属性は **[変数]** 列に表示され、属性の状態は **[値]** 列に表示されます。 属性の状態は、それがクラスターに表示される確率によって表され、重要度の順に並んでいます。 確率は **[確率]** 列に表示されます。  
  
 [トップに戻る](#BKMK_ViewerTabs)  
  
###  <a name="BKMK_Discrimination"></a> クラスターの識別  
 **[クラスターの識別]** タブを使用すると、2 つのクラスター間で属性を比較して、シーケンス内のアイテムによってクラスター間の優先順位がどのように付けられるかを調べることができます。 **[クラスター 1]** と **[クラスター 2]** の一覧を使用して、比較するクラスターを選択します。 クラスター間の最も重要な差異がビューアーによって決定され、その差異に関連付けられた属性の状態が重要度順に表示されます。 属性の右側のバーには、どのクラスターがその状態で優先されているかが示され、その状態がクラスターを優先する度合いがバーのサイズによって表されます。  
  
 [トップに戻る](#BKMK_ViewerTabs)  
  
###  <a name="BKMK_Transitions"></a> 状態遷移  
 **[状態遷移]** タブでクラスターを選択すると、選択したクラスターのシーケンス状態間の遷移を参照できます。 ビューアーの各ノードは、シーケンス列の状態を表します。 矢印は、2 つの状態間の遷移とその遷移に関連付けられた確率を表します。 遷移が元のノードに戻る場合は、矢印を元のノードに向けることもできます。  
  
 点から始まる矢印は、そのノードがシーケンスの始点である確率を表します。 NULL に向かう枠は、そのノードがシーケンスの終点である確率を表します。  
  
 タブの左側にあるスライダーを使用すると、ノードの枠にフィルターをかけることができます。  
  
 [トップに戻る](#BKMK_ViewerTabs)  
  
## <a name="see-also"></a>参照  
 [マイニング モデル ビューアーのタスクと操作方法](../../analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md)   
 [マイニング モデル ビューアーのタスクと操作方法](../../analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md)   
 [Microsoft シーケンス クラスタ リング アルゴリズム](../../analysis-services/data-mining/microsoft-sequence-clustering-algorithm.md)   
 [データ マイニング ツール](../../analysis-services/data-mining/data-mining-tools.md)   
 [データ マイニング モデル ビューアー](../../analysis-services/data-mining/data-mining-model-viewers.md)   
 [Microsoft クラスター ビューアーを使用してモデルを参照します。](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)  
  
  
