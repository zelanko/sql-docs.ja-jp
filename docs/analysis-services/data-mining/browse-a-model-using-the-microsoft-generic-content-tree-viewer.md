---
title: "Microsoft 汎用コンテンツ ツリー ビューアーを使用したモデルの参照 | Microsoft Docs"
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
  - "マイニング モデル コンテンツ、表示"
ms.assetid: 4a5f7c51-c704-4214-b05d-21cf735e6d96
caps.latest.revision: 23
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 23
---
# Microsoft 汎用コンテンツ ツリー ビューアーを使用したモデルの参照
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] 汎用マイニング モデル コンテンツ ビューアーは、マイニング アルゴリズムによって発見されたパターンについての詳細情報を提供します。また、分析処理中に生成されたさまざまな統計情報へのアクセスも提供します。 情報の量と種類は、使用されたアルゴリズムによって異なりますが、次のカテゴリを含んでいます。  
  
-   データのセグメントとその特性  
  
-   各グループまたはデータセット全体に関する説明的な統計情報  
  
-   ツリー内の分岐または子ノードの数  
  
-   クラスターまたはデータセット全体に対する、分散や平均などの計算  
  
 この情報を表示すると、分析結果を理解しやすくなります。 モデルを調整および再トレーニングする方法を特定することもできます。 また、別のアルゴリズムを使用して再トレーニングすることもできます。  
  
## マイニング モデル コンテンツの表示  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 汎用コンテンツ ビューアーは、列、ルール、プロパティ、属性、ノードなど、マイニング モデルの*コンテンツ スキーマ行セット*のコンテンツを表示します。 コンテンツ スキーマ行セットは、データ マイニング モデルのコンテンツに関する詳細情報を表すための汎用フレームワークです。  
  
 この詳細情報は、モデル内のパターン、クラスター、またはツリーを表す HTML テーブルにノードとして格納されています。 各ノードをクリックして展開し、数値属性の数式や個別の値数などの詳細を表示できます。 ノード間の親子リレーションシップを調べることもできます。  
  
 マイニング モデルのコンテンツに使用されている用語の一般的な意味については、「[マイニング モデル コンテンツ (Analysis Services - データ マイニング)](../../analysis-services/data-mining/mining-model-content-analysis-services-data-mining.md)」を参照してください。 このトピックには、特定の種類のモデルのマイニング モデルのコンテンツに関する情報へのリンクも含まれています。 それぞれの種類のマイニング モデルにはアルゴリズムに固有の情報とデータ内で見つかったパターンが含まれるため、各モデルの種類を十分に理解するために各モデルの種類のテクニカル リファレンス トピックを参照することをお勧めします。  
  
## マイニング モデルのコンテンツのクエリ  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 汎用コンテンツ ツリー ビューアーで表示される情報は、マイニング モデルにクエリを実行することによっても取得できます。 マイニング モデル コンテンツに対するクエリは、データ マイニング拡張機能 (DMX) ステートメントを使用して作成できます。 たとえば、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] でコンテンツ クエリを実行するには、次の DMX ステートメントを実行します。  
  
```  
SELECT * FROM [<mining model name>].CONTENT  
```  
  
 詳細については、「[データ マイニング クエリ](../../analysis-services/data-mining/data-mining-queries.md)」を参照してください。  
  
## 参照  
 [Microsoft 汎用コンテンツ ツリー ビューアー (データ マイニング)](../Topic/Microsoft%20Generic%20Content%20Tree%20Viewer%20\(Data%20Mining\).md)   
 [データ マイニング アルゴリズム (Analysis Services - データ マイニング)](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)  
  
  