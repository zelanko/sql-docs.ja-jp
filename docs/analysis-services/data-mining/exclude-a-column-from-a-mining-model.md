---
title: "マイニング モデルからの列の除外 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "マイニング モデルの列の除外"
  - "マイニング モデル [Analysis Services], 列"
  - "列 [データ マイニング], 除外"
ms.assetid: 404fe5fe-3ba2-4b9b-8780-0d02343d467f
caps.latest.revision: 29
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 29
---
# マイニング モデルからの列の除外
  新しいマイニング モデルを作成するとき、基となるマイニング構造に存在するすべての列を使用しないことがあります。 たとえば、顧客名列をドリルスルー用に追加し、モデリングには使用しない場合があります。 または、列の複数のコピーをそれぞれ異なる分離で作成して、各モデルで 1 つのコピーのみ使用し、残りは無視する場合があります。 複数の異なるモデルで入力列を選択的に追加して、追加した変数が出力列に与える影響を確認することもできます。  
  
 列の組み合わせごとに新しいマイニング構造を作成する必要はありません。代わりに、特定のモデルで使用されていないことを示すフラグを列に設定できます。  
  
### マイニング モデルから列を除外するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] のデータ マイニング デザイナーの **[マイニング モデル]** タブにある適切なマイニング モデルで、除外する列に対応するセルを選択します。  
  
2.  ドロップダウン リスト ボックスから **[無視]** を選択します。  
  
## 参照  
 [マイニング モデル タスクと操作方法](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)  
  
  