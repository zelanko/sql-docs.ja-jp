---
title: 'タスク 3: Suppliers ナレッジ ベースに対してデータのクレンジング |Microsoft Docs'
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
ms.topic: conceptual
ms.assetid: 647c924a-9b91-4294-8d96-e81416e4e90e
caps.latest.revision: 6
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 7b375399adc201e3b67018101b8be6fbe26eb9ba
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37210352"
---
# <a name="task-3-cleansing-data-against-the-suppliers-knowledge-base"></a>タスク 3: Suppliers ナレッジ ベースに対してデータをクレンジングする
  ここでは、コンピューター支援型のクレンジング プロセスを実行します。 DQS では、高度なアルゴリズムと選択されたナレッジ ベースに対してデータを分析し、クレンジングが行われます指定されたしきい値に基づく信頼レベルを使用します。 参照してください[クレンジング データを使用して DQS (内部) ナレッジ](http://msdn.microsoft.com/library/hh213061.aspx)の詳細。  
  
1.  クリックして**開始**コンピューター支援型のクレンジング プロセスを開始します。  
  
     ![[クレンジング] ページ、クレンジング プロセスの](../../2014/tutorials/media/et-cleansingdataagainstthesupplierkb-01.jpg "[クレンジング] ページのクレンジング プロセス")  
  
2.  クレンジング プロセスが完了したら、確認**統計**で、 **Profiler**タブ。[ソースの統計情報] には、処理されたレコードの数、適切なレコードとして検出されたレコードの数、DQS によって修正されたレコードの数、DQS によって提案された変更が存在するレコードの数、無効なレコードの数が表示されます。 右側のリスト ボックスには、クレンジング プロセスに含まれる各ドメインの、修正された値、提案された値、値の完全性 (データがどの程度存在するか) と正確性 (データがどの程度意図されたとおりに使用できるか) が表示されます。  
  
     ![クレンジングの結果](../../2014/tutorials/media/et-cleansingdataagainstthesupplierkb-02.jpg "クレンジングの結果")  
  
3.  をクリックして**次**に切り替える**管理し、結果を表示する**ページ。  
  
## <a name="next-step"></a>次の手順  
 [タスク 4: 管理および結果の表示](../../2014/tutorials/task-4-manaing-and-viewing-results.md)  
  
  
