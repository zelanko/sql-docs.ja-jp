---
title: "マイニング モデルのコピーの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/20/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "コピーのマイニング モデル [Analysis Services]"
  - "作成するマイニング モデル [Analysis Services]"
  - "マイニング モデル [Analysis Services], 操作方法に関するトピック"
  - "マイニング モデルのコピー"
ms.assetid: 7975bb02-f188-49a0-b7de-5b9b216254ad
caps.latest.revision: 12
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 12
---
# マイニング モデルのコピーの作成
  マイニング モデルのコピーの作成は、同じデータに基づいて複数のマイニング モデルをすばやく作成する場合に便利です。 モデルをコピーした後で、パラメーターを変更したり、フィルターを追加したりすることで、新しいコピーを編集できます。  
  
 たとえば、購入記録のテーブルにリンクされた Customers テーブルがある場合、コピーを作成して、年齢や地域などの属性でフィルター選択した顧客の統計区分ごとに別々のマイニング モデルを生成できます。  
  
 モデルのコンテンツ (グラフィカル表示やモデル パターンなど) をクリップボードにコピーして他のプログラムで使用する方法については、「[マイニング モデルの表示のコピー](../../analysis-services/data-mining/copy-a-view-of-a-mining-model.md)」を参照してください。  
  
### 関連マイニング モデルを作成するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] のソリューション エクスプローラーで、マイニング モデルを含むマイニング構造をクリックします。  
  
2.  **[マイニング モデル]** タブをクリックします。  
  
3.  モデルを選択し、右クリックしてショートカット メニューを開きます。  
  
     または  
  
     モデルを選択します。 **[マイニング モデル]** メニューの **[新しいマイニング モデル]** をクリックします。  
  
4.  新しいマイニング モデルの名前を入力し、アルゴリズムを選択します。 [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### コピーされたマイニング モデルのフィルターを編集するには  
  
1.  マイニング モデルを選択します。  
  
2.  **[プロパティ]** ウィンドウで **[フィルター]** プロパティのテキスト ボックスをクリックし、作成ボタン (**[...]**) をクリックします。  
  
3.  フィルター条件を変更します。  
  
     フィルター エディターのダイアログ ボックスの使用方法の詳細については、「[マイニング モデルへのフィルターの適用](../../analysis-services/data-mining/apply-a-filter-to-a-mining-model.md)」を参照してください。  
  
4.  必要に応じて、**[プロパティ]** ウィンドウの **[AlgorithmParameters]** ボックスで **[アルゴリズム パラメーターの設定]** をクリックし、アルゴリズム パラメーターを変更します。  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## 参照  
 [マイニング モデルのフィルター (Analysis Services - データ マイニング)](../../analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)   
 [マイニング モデル タスクと操作方法](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)   
 [マイニング モデルからのフィルターの削除](../../analysis-services/data-mining/delete-a-filter-from-a-mining-model.md)  
  
  