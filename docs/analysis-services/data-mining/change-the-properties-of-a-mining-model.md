---
title: "マイニング モデルのプロパティの変更 | Microsoft Docs"
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
  - "マイニング モデル [Analysis Services]、プロパティ"
  - "プロパティ [データ マイニング]"
ms.assetid: aefaeb7f-d174-48d1-a188-0987a3b1196b
caps.latest.revision: 38
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 38
---
# マイニング モデルのプロパティの変更
  マイニング モデルのプロパティには、モデル全体に適用されるものと個別の列に適用されるものがあります。 モデル全体に適用されるプロパティの例は、ケース データをクエリで使用可能にする必要があるかどうかを指定する **Drillthrough** プロパティと、**Description** プロパティです。 列に適用されるプロパティには、モデル内で列のデータが使用される方法を制御する **Usage** および **ModelingFlags** があります。  
  
 次のモデル プロパティには、式の作成または複雑なモデル プロパティの構成に使用できる高度なエディターがあります。 プロパティには次の機能があります。  
  
-   **Filter** プロパティ: [[データセット フィルター] または [モデル フィルター] ダイアログ ボックス](../Topic/Data%20Set%20Filter%20or%20Model%20Filter%20Dialog%20Box.md)を開きます。  
  
-   **AlgorithmParameters** プロパティ: [[アルゴリズム パラメーター] ダイアログ ボックス &#40;[マイニング モデル] ビュー&#41;](../Topic/Algorithm%20Parameters%20Dialog%20Box%20\(Mining%20Models%20View\).md) を開きます。  
  
 マイニング モデルのプロパティを設定する方法については、「[マイニング モデル列](../../analysis-services/data-mining/mining-model-columns.md)」を参照してください。  
  
### マイニング モデルのプロパティを変更するには  
  
1.  データ マイニング デザイナーの **[マイニング モデル]** タブで、マイニング モデル名を含む列ヘッダーか、マイニング アルゴリズム名を含むグリッドの行のいずれかを右クリックし、**[プロパティ]** を選択します。  
  
2.  画面の右側の **[プロパティ]** ウィンドウで、変更するプロパティに対応する値を強調表示し、新しい値を入力します。  
  
     新しい値は、デザイナーで別の要素を選択したときに有効になります。  
  
### マイニング モデル列のプロパティを変更するには  
  
1.  データ マイニング デザイナーの **[マイニング モデル]** タブで、マイニング構造列とマイニング モデルが交差するグリッド内のセルを右クリックし、**[プロパティ]** を選択します。  
  
2.  画面の右側の **[プロパティ]** ウィンドウで、変更するプロパティに対応する値を強調表示し、新しい値を入力します。  
  
    > [!NOTE]  
    >  列の使用法が **Ignore** に設定されている場合、その列の **[プロパティ]** ウィンドウは空白になります。  
  
     新しい値は、デザイナーで別の要素を選択したときに有効になります。  
  
## 参照  
 [マイニング モデル タスクと操作方法](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)  
  
  