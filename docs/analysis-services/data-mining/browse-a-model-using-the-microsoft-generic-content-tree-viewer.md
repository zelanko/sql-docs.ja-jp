---
title: "Microsoft 汎用コンテンツ ツリー ビューアーを使用してモデルを参照 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mining model content, viewing
ms.assetid: 4a5f7c51-c704-4214-b05d-21cf735e6d96
caps.latest.revision: 23
author: Minewiskan
ms.author: owend
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: dcb5c01581dd9d42e7504dc00f514544479b27fc
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="browse-a-model-using-the-microsoft-generic-content-tree-viewer"></a>Microsoft 汎用コンテンツ ツリー ビューアーを使用したモデルの参照
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] 汎用マイニング モデル コンテンツ ビューアーは、マイニング アルゴリズムによって発見されたパターンについての詳細情報を提供します。また、分析処理中に生成されたさまざまな統計情報へのアクセスも提供します。 情報の量と種類は、使用されたアルゴリズムによって異なりますが、次のカテゴリを含んでいます。  
  
-   データのセグメントとその特性  
  
-   各グループまたはデータセット全体に関する説明的な統計情報  
  
-   ツリー内の分岐または子ノードの数  
  
-   クラスターまたはデータセット全体に対する、分散や平均などの計算  
  
 この情報を表示すると、分析結果を理解しやすくなります。 モデルを調整および再トレーニングする方法を特定することもできます。 また、別のアルゴリズムを使用して再トレーニングすることもできます。  
  
## <a name="viewing-mining-model-content"></a>マイニング モデル コンテンツの表示  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 汎用コンテンツ ビューアーは、列、ルール、プロパティ、属性、ノードなど、マイニング モデルの *コンテンツ スキーマ行セット* のコンテンツを表示します。 コンテンツ スキーマ行セットは、データ マイニング モデルのコンテンツに関する詳細情報を表すための汎用フレームワークです。  
  
 この詳細情報は、モデル内のパターン、クラスター、またはツリーを表す HTML テーブルにノードとして格納されています。 各ノードをクリックして展開し、数値属性の数式や個別の値数などの詳細を表示できます。 ノード間の親子リレーションシップを調べることもできます。  
  
 マイニング モデルのコンテンツに使用されている用語の一般的な意味については、「[マイニング モデル コンテンツ (Analysis Services - データ マイニング)](../../analysis-services/data-mining/mining-model-content-analysis-services-data-mining.md)」を参照してください。 このトピックには、特定の種類のモデルのマイニング モデルのコンテンツに関する情報へのリンクも含まれています。 それぞれの種類のマイニング モデルにはアルゴリズムに固有の情報とデータ内で見つかったパターンが含まれるため、各モデルの種類を十分に理解するために各モデルの種類のテクニカル リファレンス トピックを参照することをお勧めします。  
  
## <a name="querying-mining-model-content"></a>マイニング モデルのコンテンツのクエリ  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 汎用コンテンツ ツリー ビューアーで表示される情報は、マイニング モデルにクエリを実行することによっても取得できます。 マイニング モデル コンテンツに対するクエリは、データ マイニング拡張機能 (DMX) ステートメントを使用して作成できます。 たとえば、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でコンテンツ クエリを実行するには、次の DMX ステートメントを実行します。  
  
```  
SELECT * FROM [<mining model name>].CONTENT  
```  
  
 詳細については、「 [データ マイニング クエリ](../../analysis-services/data-mining/data-mining-queries.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Microsoft 汎用コンテンツ ツリー ビューアー &#40;データ マイニング&#41;](http://msdn.microsoft.com/library/751b4393-f6fd-48c1-bcef-bdca589ce34c)   
 [データ マイニング アルゴリズム &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)  
  
  
