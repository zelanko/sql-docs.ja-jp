---
title: "Microsoft アソシエーション ルール ビューアーを使用したモデルの参照 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "アイテムセット [Analysis Services]"
  - "マイニング モデル [Analysis Services]、アソシエーション"
  - "マイニング モデル コンテンツ、表示"
  - "ルール [データ マイニング]"
  - "アソシエーション ルール ビューアー [Analysis Services]"
  - "マーケット バスケット分析 [Analysis Services]"
  - "アソシエーション [Analysis Services]"
  - "Microsoft アソシエーション ルール ビューアー"
  - "依存関係 [Analysis Services]"
ms.assetid: 538fc01b-8eb1-467a-9b66-3cd57cf7489f
caps.latest.revision: 39
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 39
---
# Microsoft アソシエーション ルール ビューアーを使用したモデルの参照
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の [!INCLUDE[msCoName](../../includes/msconame-md.md)] アソシエーション ルール ビューアーには、[!INCLUDE[msCoName](../../includes/msconame-md.md)] アソシエーション アルゴリズムを使用して作成されたマイニング モデルが表示されます。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] アソシエーション アルゴリズムは、マーケット バスケット分析に使用できるデータ マイニング モデルを作成するときに使用するアソシエーション アルゴリズムです。 このアルゴリズムの詳細については、「 [Microsoft Association Algorithm](../../analysis-services/data-mining/microsoft-association-algorithm.md)」を参照してください。  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] アソシエーション アルゴリズムを使用する主な理由は次のとおりです。  
  
-   トランザクション内で通常同時に検出されるアイテムについて説明するアイテムセットを検出する。  
  
-   既存のアイテムに基づいて、トランザクション内の他のアイテムの存在を予測するルールを発見する。  
  
> [!NOTE]  
>  モデルで使用された式と、検出されたパターンの詳細情報を表示するには、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 汎用コンテンツ ツリー ビューアーを使用します。 詳細については、「[Microsoft 汎用コンテンツ ツリー ビューアーを使用したモデルの参照](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)」または「[Microsoft 汎用コンテンツ ツリー ビューアー (データ マイニング)](../Topic/Microsoft%20Generic%20Content%20Tree%20Viewer%20\(Data%20Mining\).md)」を参照してください。  
  
 アソシエーション マイニング モデルの作成、調査、使用のチュートリアルについては、「[Lesson 3: Building a Market Basket Scenario (Intermediate Data Mining Tutorial)](../Topic/Lesson%203:%20Building%20a%20Market%20Basket%20Scenario%20\(Intermediate%20Data%20Mining%20Tutorial\).md)」(レッスン 3 : マーケット バスケット シナリオの作成 (中級者向けデータ マイニング チュートリアル)) を参照してください。  
  
##  <a name="BKMK_ViewerTabs"></a> ビューアーのタブ  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]でマイニング モデルを参照すると、そのモデルに適したビューアーを使用してデータ マイニング デザイナーの **[マイニング モデル ビューアー]** タブにモデルが表示されます。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] アソシエーション ルール ビューアーには、次のタブがあります。  
  
-   [アイテムセット](#BKMK_Itemsets)  
  
-   [ルール](#BKMK_Rules)  
  
-   [依存関係ネットワーク](#BKMK_Dependency)  
  
 各タブには **[長い名前を表示する]** チェック ボックスがあります。このチェック ボックスを使用して、ルールまたはアイテムセットでアイテムセットの元のテーブルを表示するか非表示にするかを切り替えることができます。  
  
###  <a name="BKMK_Itemsets"></a> アイテムセット  
 **[アイテムセット]** タブには、同時に検出されることが多いとモデルで判断されたアイテムセットの一覧が表示されます。 このタブには、 **[サポート]**、 **[サイズ]**、および **[アイテムセット]**列を持つグリッドが表示されます。 サポートの詳細については、「 [Microsoft Association Algorithm](../../analysis-services/data-mining/microsoft-association-algorithm.md)」を参照してください。 **[サイズ]** 列には、アイテムセット内のアイテム数が表示されます。 **[アイテムセット]** 列には、モデルで検出された実際のアイテムセットが表示されます。 **[表示]** の一覧を使用してアイテムセットの形式を指定できます。この一覧では、次のオプションを設定できます。  
  
-   **[属性の名前と値を表示]**  
  
-   **[属性値のみ表示]**  
  
-   **[属性名のみ表示]**  
  
 **[最小のサポート]** および **[最小のアイテムセットのサイズ]**を使用して、タブに表示されるアイテムセットの数をフィルター処理できます。 さらに、 **[アイテムセットのフィルター]** を使用し、残す必要のあるアイテムセットの特性を入力して、表示されるアイテムセットの数を制限できます。 たとえば、「Water Bottle = existing」と入力すると、アイテムセットを water bottle が含まれているもののみに限定できます。 **[アイテムセットのフィルター]** オプションでは、以前に使用したフィルターの一覧も表示されます。  
  
 列見出しをクリックすると、グリッド内の行を並べ替えることができます。  
  
 [トップに戻る](#BKMK_ViewerTabs)  
  
###  <a name="BKMK_Rules"></a> ルール  
 **[ルール]** タブには、アソシエーション アルゴリズムで発見されたルールが表示されます。 **[ルール]** タブには、 **[確率]**列、 **[重要度]**列、および **[ルール]**列で構成されたグリッドがあります。 確率は、ルールの結果が発生する可能性を示します。 重要度では、ルールの有用性が測定されます。 ルールが発生する確率が高くても、ルールの有用性自体は低い場合があります。 [重要度] 列は、これに対処しています。 たとえば、すべてのアイテムセットに特定の状態の属性が含まれている場合、確率が非常に高くても、状態を予測するルールはあまり意味がありません。 重要度が高いほど、ルールはより重要になります。  
  
 **[アイテムセット]** タブでのフィルター処理と同様に、 **[最小の確率]** と **[最小の重要度]** を使用してルールをフィルター処理できます。 **[ルールのフィルター]** を使用して、ルールに含まれている属性の状態に基づいてルールをフィルター処理することもできます。  
  
 列見出しをクリックすると、グリッド内の行を並べ替えることができます。  
  
 [トップに戻る](#BKMK_ViewerTabs)  
  
###  <a name="BKMK_Dependency"></a> 依存関係ネットワーク  
 **[依存関係ネットワーク]** タブには依存関係ネットワーク ビューアーがあります。 ビューアーの各ノードは、"state = WA" などのアイテムを表します。 ノード間の矢印は、アイテム間の関連を表します。 矢印の方向は、アルゴリズムが発見したルールに従ってアイテム間の関連を示します。 たとえば、ビューアーに A、B、C の 3 つのアイテムが含まれている場合、C は A と B から予測されます。ノード C を選択した場合は、A から C、B から C のように、ノード C に向かう 2 つの矢印が表示されます。  
  
 ビューアーの左側にあるスライダーは、ルールの確率に関連付けられたフィルターとして機能します。 スライダーを小さく設定すると、緊密なリンクのみが表示されます。  
  
 [トップに戻る](#BKMK_ViewerTabs)  
  
## 参照  
 [Microsoft アソシエーション アルゴリズム](../../analysis-services/data-mining/microsoft-association-algorithm.md)   
 [マイニング モデル ビューアーのタスクと操作方法](../../analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md)   
 [マイニング モデル ビューアーのタスクと操作方法](../../analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md)   
 [データ マイニング ツール](../../analysis-services/data-mining/data-mining-tools.md)   
 [データ マイニング モデル ビューアー](../../analysis-services/data-mining/data-mining-model-viewers.md)  
  
  