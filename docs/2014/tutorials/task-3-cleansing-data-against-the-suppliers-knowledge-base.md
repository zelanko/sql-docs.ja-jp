---
title: 'タスク 3: Suppliers ナレッジ ベースに対してデータのクレンジング |Microsoft ドキュメント'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 647c924a-9b91-4294-8d96-e81416e4e90e
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: ca1a98045bd9f0ee9dfc52eafb274d5698195d68
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36073366"
---
# <a name="task-3-cleansing-data-against-the-suppliers-knowledge-base"></a>タスク 3: Suppliers ナレッジ ベースに対してデータをクレンジングする
  ここでは、コンピューター支援型のクレンジング プロセスを実行します。 DQS では、高度なアルゴリズムと、選択したナレッジ ベースに対してデータを分析し、クレンジングが行わに指定されたしきい値に基づく信頼レベルを使用します。 参照してください[クレンジング データを使用して DQS (内部) ナレッジ](http://msdn.microsoft.com/library/hh213061.aspx)詳細についてはします。  
  
1.  をクリックして**開始**コンピューター支援型クレンジング プロセスを開始します。  
  
     ![[クレンジング] ページ、クレンジング プロセスの](../../2014/tutorials/media/et-cleansingdataagainstthesupplierkb-01.jpg "[クレンジング] ページ、クレンジング プロセスの")  
  
2.  クレンジング プロセスが完了したら、確認**統計**で、**プロファイラー**タブです。[ソースの統計情報] には、処理されたレコードの数、適切なレコードとして検出されたレコードの数、DQS によって修正されたレコードの数、DQS によって提案された変更が存在するレコードの数、無効なレコードの数が表示されます。 右側のリスト ボックスには、クレンジング プロセスに含まれる各ドメインの、修正された値、提案された値、値の完全性 (データがどの程度存在するか) と正確性 (データがどの程度意図されたとおりに使用できるか) が表示されます。  
  
     ![クレンジングの結果](../../2014/tutorials/media/et-cleansingdataagainstthesupplierkb-02.jpg "クレンジングの結果")  
  
3.  をクリックして **[次へ]** に切り替えるには**管理と結果を表示する**ページ。  
  
## <a name="next-step"></a>次の手順  
 [タスク 4: 管理および結果を表示します。](../../2014/tutorials/task-4-manaing-and-viewing-results.md)  
  
  