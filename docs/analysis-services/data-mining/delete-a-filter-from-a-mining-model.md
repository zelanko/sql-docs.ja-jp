---
title: マイニング モデルからのフィルターの削除 |Microsoft ドキュメント
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: fb3897d851c398b9703bf9514fc36cf30922727d
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="delete-a-filter-from-a-mining-model"></a>マイニング モデルからのフィルターの削除
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  マイニング モデルに対するフィルターを作成する場合は、データ ソース ビュー内のデータのサブセットに対するモデルを作成できます。 フィルターは、元のデータのサブセットでモデルの精度をテストするためにも役立ちます。  
  
 ただし、ケースの完全なセットを再度表示する場合は、フィルターを削除する必要があります。 この手順では、フィルターの条件を削除する方法や、フィルターを完全に削除する方法について説明します。  
  
### <a name="to-delete-a-condition-from-a-filter-on-a-mining-model"></a>マイニング モデルのフィルターから条件を削除するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]のソリューション エクスプローラーで、フィルターを適用するマイニング モデルが含まれているマイニング構造をクリックします。  
  
2.  **[マイニング モデル]** タブをクリックします。  
  
3.  モデルを選択し、右クリックしてショートカット メニューを開きます。  
  
     または  
  
     モデルを選択します。 **[マイニング モデル]** メニューの **[モデル フィルターの設定]** をクリックします。  
  
4.  **[モデル フィルター]** ダイアログ ボックスで、削除する条件が含まれているグリッドの行を右クリックします。  
  
5.  **[削除]** を選択します。  
  
### <a name="to-clear-the-filter-on-a-mining-model-in-the-filter-editor-dialog-box"></a>フィルター エディターのダイアログ ボックスからマイニング モデルのフィルターを消去するには  
  
-   **[フィルター エディター]** ダイアログ ボックスで、グリッドの任意の行を右クリックし、 **[すべて削除]** をクリックします。  
  
## <a name="working-with-model-filters-using-the-properties-window"></a>[プロパティ] ウィンドウを使用したモデル フィルターの操作  
 フィルター全体を削除する場合、フィルター エディターのダイアログ ボックスを開く必要はありません。 作成したフィルター条件は、マイニング モデルの **Filter** プロパティで使用できます。  
  
> [!NOTE]  
>  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]ではマイニング モデルのプロパティを表示できますが [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]ではできません。  
  
#### <a name="to-clear-the-filter-on-a-mining-model-in-solution-explorer"></a>ソリューション エクスプローラーでマイニング モデルのフィルターを消去するには  
  
1.  ソリューション エクスプローラーで、フィルターが含まれているマイニング モデルをクリックします。  
  
2.  **[プロパティ]** ウィンドウで、 **Filter** プロパティのフィルター テキストを右クリックし、 **[すべて選択]** をクリックします。  
  
3.  BackSpace キーまたは Del キーを押します。  
  
## <a name="see-also"></a>参照  
 [マイニング モデルからケース データにドリルスルーします。](../../analysis-services/data-mining/drill-through-to-case-data-from-a-mining-model.md)   
 [マイニング モデル タスクと操作方法](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)   
 [フィルターをマイニング モデルと #40 です。Analysis Services - データ マイニング & #41;](../../analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)  
  
  
