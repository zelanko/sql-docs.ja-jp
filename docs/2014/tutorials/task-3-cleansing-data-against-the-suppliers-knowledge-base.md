---
title: 'タスク 3: サプライヤーのナレッジベースに対してデータをクレンジングする |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 647c924a-9b91-4294-8d96-e81416e4e90e
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: b13e3d30ac0afce5293cc0e104aa2b291112647f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "78177282"
---
# <a name="task-3-cleansing-data-against-the-suppliers-knowledge-base"></a>タスク 3: Suppliers ナレッジ ベースに対してデータをクレンジングする
  ここでは、コンピューター支援型のクレンジング プロセスを実行します。 DQS は、指定されたしきい値に基づいて高度なアルゴリズムと信頼レベルを使用して、選択したナレッジベースに対してデータを分析し、クレンジングします。 詳細については、「 [DQS (内部) ナレッジを使用したデータのクレンジング](https://msdn.microsoft.com/library/hh213061.aspx)」を参照してください。

1.  [**開始**] をクリックして、コンピューター支援型のクレンジングプロセスを開始します。

     ![クレンジング プロセスの [クレンジング] ページ](../../2014/tutorials/media/et-cleansingdataagainstthesupplierkb-01.jpg "クレンジング プロセスの [クレンジング] ページ")

2.  クレンジングプロセスが完了したら、[**プロファイラー** ] タブで**統計**を確認します。ソースの統計情報には、処理されたレコードの数、正しいことが検出されたレコードの数、dqs によって修正されたレコードの数、DQS によって提案された変更を含むレコードの数、および無効なレコードの数が示されます。 右側のリスト ボックスには、クレンジング プロセスに含まれる各ドメインの、修正された値、提案された値、値の完全性 (データがどの程度存在するか) と正確性 (データがどの程度意図されたとおりに使用できるか) が表示されます。

     ![クレンジングの結果](../../2014/tutorials/media/et-cleansingdataagainstthesupplierkb-02.jpg "クレンジングの結果")

3.  [**次へ**] をクリックし**て、[管理と結果の表示**] ページに切り替えます。

## <a name="next-step"></a>次の手順
 [タスク 4: 結果を管理および表示する](../../2014/tutorials/task-4-manaing-and-viewing-results.md)


