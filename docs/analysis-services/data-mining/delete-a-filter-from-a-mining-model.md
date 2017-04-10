---
title: "マイニング モデルからのフィルターの削除 | Microsoft Docs"
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
  - "フィルター [Analysis Services]"
ms.assetid: 91220b21-adbc-49a9-b200-8bf0a724eff1
caps.latest.revision: 13
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 13
---
# マイニング モデルからのフィルターの削除
  マイニング モデルに対するフィルターを作成する場合は、データ ソース ビュー内のデータのサブセットに対するモデルを作成できます。 フィルターは、元のデータのサブセットでモデルの精度をテストするためにも役立ちます。  
  
 ただし、ケースの完全なセットを再度表示する場合は、フィルターを削除する必要があります。 この手順では、フィルターの条件を削除する方法や、フィルターを完全に削除する方法について説明します。  
  
### マイニング モデルのフィルターから条件を削除するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]のソリューション エクスプローラーで、フィルターを適用するマイニング モデルが含まれているマイニング構造をクリックします。  
  
2.  **[マイニング モデル]** タブをクリックします。  
  
3.  モデルを選択し、右クリックしてショートカット メニューを開きます。  
  
     または  
  
     モデルを選択します。 **[マイニング モデル]** メニューの **[モデル フィルターの設定]**をクリックします。  
  
4.  **[モデル フィルター]** ダイアログ ボックスで、削除する条件が含まれているグリッドの行を右クリックします。  
  
5.  [**削除**] を選択します。  
  
### フィルター エディターのダイアログ ボックスからマイニング モデルのフィルターを消去するには  
  
-   **[フィルター エディター]** ダイアログ ボックスで、グリッドの任意の行を右クリックし、**[すべて削除]** をクリックします。  
  
## [プロパティ] ウィンドウを使用したモデル フィルターの操作  
 フィルター全体を削除する場合、フィルター エディターのダイアログ ボックスを開く必要はありません。 作成したフィルター条件は、マイニング モデルの **Filter** プロパティで使用できます。  
  
> [!NOTE]  
>  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] ではマイニング モデルのプロパティを表示できますが [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ではできません。  
  
#### ソリューション エクスプローラーでマイニング モデルのフィルターを消去するには  
  
1.  ソリューション エクスプローラーで、フィルターが含まれているマイニング モデルをクリックします。  
  
2.  **[プロパティ]** ウィンドウで、**Filter** プロパティのフィルター テキストを右クリックし、**[すべて選択]** をクリックします。  
  
3.  BackSpace キーまたは Del キーを押します。  
  
## 参照  
 [マイニング モデルからケース データへのドリルスルー](../../analysis-services/data-mining/drill-through-to-case-data-from-a-mining-model.md)   
 [マイニング モデル タスクと操作方法](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)   
 [マイニング モデルのフィルター &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)  
  
  