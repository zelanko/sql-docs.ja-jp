---
title: Microsoft アソシエーション ルール ビューアーを使用してモデルを参照 |Microsoft ドキュメント
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d5a10bbf085f47bea372c9721220ef64cbd1af1d
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="browse-a-model-using-the-microsoft-association-rules-viewer"></a>Microsoft アソシエーション ルール ビューアーを使用したモデルの参照
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の [!INCLUDE[msCoName](../../includes/msconame-md.md)] アソシエーション ルール ビューアーには、[!INCLUDE[msCoName](../../includes/msconame-md.md)] アソシエーション アルゴリズムを使用して作成されたマイニング モデルが表示されます。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] アソシエーション アルゴリズムは、マーケット バスケット分析に使用できるデータ マイニング モデルを作成するときに使用するアソシエーション アルゴリズムです。 このアルゴリズムの詳細については、「 [Microsoft Association Algorithm](../../analysis-services/data-mining/microsoft-association-algorithm.md)」を参照してください。  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] アソシエーション アルゴリズムを使用する主な理由は次のとおりです。  
  
-   トランザクション内で通常同時に検出されるアイテムについて説明するアイテムセットを検出する。  
  
-   既存のアイテムに基づいて、トランザクション内の他のアイテムの存在を予測するルールを発見する。  
  
> [!NOTE]  
>  モデルで使用された式と、検出されたパターンの詳細情報を表示するには、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 汎用コンテンツ ツリー ビューアーを使用します。 詳細については、「[Microsoft 汎用コンテンツ ツリー ビューアーを使用したモデルの参照](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)」または「[Microsoft 汎用コンテンツ ツリー ビューアー (データ マイニング)](http://msdn.microsoft.com/library/751b4393-f6fd-48c1-bcef-bdca589ce34c)」を参照してください。  
  
 アソシエーション マイニング モデルの作成、調査、使用のチュートリアルについては、「[Lesson 3: Building a Market Basket Scenario (Intermediate Data Mining Tutorial)](http://msdn.microsoft.com/library/651eef38-772e-4d97-af51-075b1b27fc5a)」(レッスン 3 : マーケット バスケット シナリオの作成 (中級者向けデータ マイニング チュートリアル)) を参照してください。  
  
##  <a name="BKMK_ViewerTabs"></a> ビューアーのタブ  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]でマイニング モデルを参照すると、そのモデルに適したビューアーを使用してデータ マイニング デザイナーの **[マイニング モデル ビューアー]** タブにモデルが表示されます。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] アソシエーション ルール ビューアーには、次のタブがあります。  
  
-   [アイテムセット](#BKMK_Itemsets)  
  
-   [ルール](#BKMK_Rules)  
  
-   [依存関係ネットワーク](#BKMK_Dependency)  
  
 各タブには **[長い名前を表示する]** チェック ボックスがあります。このチェック ボックスを使用して、ルールまたはアイテムセットでアイテムセットの元のテーブルを表示するか非表示にするかを切り替えることができます。  
  
###  <a name="BKMK_Itemsets"></a> アイテムセット  
 **[アイテムセット]** タブには、同時に検出されることが多いとモデルで判断されたアイテムセットの一覧が表示されます。 このタブには、 **[サポート]**、 **[サイズ]**、および **[アイテムセット]** 列を持つグリッドが表示されます。 サポートの詳細については、「 [Microsoft Association Algorithm](../../analysis-services/data-mining/microsoft-association-algorithm.md)」を参照してください。 **[サイズ]** 列には、アイテムセット内のアイテム数が表示されます。 **[アイテムセット]** 列には、モデルで検出された実際のアイテムセットが表示されます。 **[表示]** の一覧を使用してアイテムセットの形式を指定できます。この一覧では、次のオプションを設定できます。  
  
-   **[属性の名前と値を表示]**  
  
-   **[属性値のみ表示]**  
  
-   **[属性名のみ表示]**  
  
 **[最小のサポート]** および **[最小のアイテムセットのサイズ]** を使用して、タブに表示されるアイテムセットの数をフィルター処理できます。 さらに、 **[アイテムセットのフィルター]** を使用し、残す必要のあるアイテムセットの特性を入力して、表示されるアイテムセットの数を制限できます。 たとえば、「Water Bottle = existing」と入力すると、アイテムセットを water bottle が含まれているもののみに限定できます。 **[アイテムセットのフィルター]** オプションでは、以前に使用したフィルターの一覧も表示されます。  
  
 列見出しをクリックすると、グリッド内の行を並べ替えることができます。  
  
 [トップに戻る](#BKMK_ViewerTabs)  
  
###  <a name="BKMK_Rules"></a> ルール  
 **[ルール]** タブには、アソシエーション アルゴリズムで発見されたルールが表示されます。 **[ルール]** タブには、 **[確率]** 列、 **[重要度]** 列、および **[ルール]** 列で構成されたグリッドがあります。 確率は、ルールの結果が発生する可能性を示します。 重要度では、ルールの有用性が測定されます。 ルールが発生する確率が高くても、ルールの有用性自体は低い場合があります。 [重要度] 列は、これに対処しています。 たとえば、すべてのアイテムセットに特定の状態の属性が含まれている場合、確率が非常に高くても、状態を予測するルールはあまり意味がありません。 重要度が高いほど、ルールはより重要になります。  
  
 **[アイテムセット]** タブでのフィルター処理と同様に、 **[最小の確率]** と **[最小の重要度]** を使用してルールをフィルター処理できます。**[ルールのフィルター]** を使用して、ルールに含まれている属性の状態に基づいてルールをフィルター処理することもできます。  
  
 列見出しをクリックすると、グリッド内の行を並べ替えることができます。  
  
 [トップに戻る](#BKMK_ViewerTabs)  
  
###  <a name="BKMK_Dependency"></a> 依存関係ネットワーク  
 **[依存関係ネットワーク]** タブには依存関係ネットワーク ビューアーがあります。 ビューアーの各ノードは、"state = WA" などのアイテムを表します。 ノード間の矢印は、アイテム間の関連を表します。 矢印の方向は、アルゴリズムが発見したルールに従ってアイテム間の関連を示します。 たとえば、ビューアーに A、B、C の 3 つのアイテムが含まれている場合、C は A と B から予測されます。ノード C を選択した場合は、A から C、B から C のように、ノード C に向かう 2 つの矢印が表示されます。  
  
 ビューアーの左側にあるスライダーは、ルールの確率に関連付けられたフィルターとして機能します。 スライダーを小さく設定すると、緊密なリンクのみが表示されます。  
  
 [トップに戻る](#BKMK_ViewerTabs)  
  
## <a name="see-also"></a>参照  
 [Microsoft アソシエーション アルゴリズム](../../analysis-services/data-mining/microsoft-association-algorithm.md)   
 [マイニング モデル ビューアーのタスクと操作方法](../../analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md)   
 [マイニング モデル ビューアーのタスクと操作方法](../../analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md)   
 [データ マイニング ツール](../../analysis-services/data-mining/data-mining-tools.md)   
 [データ マイニング モデル ビューアー](../../analysis-services/data-mining/data-mining-model-viewers.md)  
  
  
