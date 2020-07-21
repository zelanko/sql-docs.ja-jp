---
title: マイニングモデルからフィルターを削除する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- filters [Analysis Services]
ms.assetid: 91220b21-adbc-49a9-b200-8bf0a724eff1
author: minewiskan
ms.author: owend
ms.openlocfilehash: 12dec570bb4ef4a499c5f141d62b15467212d2ae
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84522598"
---
# <a name="delete-a-filter-from-a-mining-model"></a>マイニング モデルからのフィルターの削除
  マイニング モデルに対するフィルターを作成する場合は、データ ソース ビュー内のデータのサブセットに対するモデルを作成できます。 フィルターは、元のデータのサブセットでモデルの精度をテストするためにも役立ちます。  
  
 ただし、ケースの完全なセットを再度表示する場合は、フィルターを削除する必要があります。 この手順では、フィルターの条件を削除する方法や、フィルターを完全に削除する方法について説明します。  
  
### <a name="to-delete-a-condition-from-a-filter-on-a-mining-model"></a>マイニング モデルのフィルターから条件を削除するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]のソリューション エクスプローラーで、フィルターを適用するマイニング モデルが含まれているマイニング構造をクリックします。  
  
2.  **[マイニング モデル]** タブをクリックします。  
  
3.  モデルを選択し、右クリックしてショートカット メニューを開きます。  
  
     \- または -  
  
     モデルを選択します。 **[マイニング モデル]** メニューの **[モデル フィルターの設定]** をクリックします。  
  
4.  **[モデル フィルター]** ダイアログ ボックスで、削除する条件が含まれているグリッドの行を右クリックします。  
  
5.  **[削除]** を選択します。  
  
### <a name="to-clear-the-filter-on-a-mining-model-in-the-filter-editor-dialog-box"></a>フィルター エディターのダイアログ ボックスからマイニング モデルのフィルターを消去するには  
  
-   **[フィルター エディター]** ダイアログ ボックスで、グリッドの任意の行を右クリックし、 **[すべて削除]** をクリックします。  
  
## <a name="working-with-model-filters-using-the-properties-window"></a>[プロパティ] ウィンドウを使用したモデル フィルターの操作  
 フィルター全体を削除する場合、フィルター エディターのダイアログ ボックスを開く必要はありません。 作成したフィルター条件は、マイニング モデルの `Filter` プロパティで使用できます。  
  
> [!NOTE]  
>  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]ではマイニング モデルのプロパティを表示できますが [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]ではできません。  
  
#### <a name="to-clear-the-filter-on-a-mining-model-in-solution-explorer"></a>ソリューション エクスプローラーでマイニング モデルのフィルターを消去するには  
  
1.  ソリューション エクスプローラーで、フィルターが含まれているマイニング モデルをクリックします。  
  
2.  [**プロパティ**] ウィンドウで、プロパティのフィルターテキストを右クリック `Filter` し、[**すべて選択]** をクリックします。  
  
3.  BackSpace キーまたは Del キーを押します。  
  
## <a name="see-also"></a>参照  
 [マイニングモデルからケースデータへのドリルスルー](drill-through-to-case-data-from-a-mining-model.md)   
 [マイニングモデルタスクと操作方法](mining-model-tasks-and-how-tos.md)   
 [マイニング モデルのフィルター &#40;Analysis Services - データ マイニング&#41;](mining-models-analysis-services-data-mining.md)  
  
  
