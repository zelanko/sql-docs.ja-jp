---
title: Analysis Services 表形式モデルでリレーションシップを作成 |Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7e9ee96a04aa6b023be51f8e1e8d913e26a7e2a8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "68207739"
---
# <a name="create-a-relationship"></a>リレーションシップを作成します。 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  データ ソース内のテーブルに既存のリレーションシップがない場合、または新しいテーブルを追加する場合は、モデル デザイナーのツールを使用して新しいリレーションシップを作成できます。 表形式モデルでリレーションシップを使用する方法については、次を参照してください。[リレーションシップ](../../analysis-services/tabular-models/relationships-ssas-tabular.md)します。  
  
## <a name="create-a-relationship-between-two-tables"></a>2 つのテーブル間のリレーションシップの作成  
  
#### <a name="to-create-a-relationship-between-two-tables-in-diagram-view-click-and-drag"></a>ダイアグラム ビューで 2 つのテーブル間のリレーションシップを作成するには (クリックしてドラッグ)  
  
1.  [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]で、 **[モデル]** メニューをクリックし、 **[モデル ビュー]** をポイントし、 **[ダイアグラム ビュー]** をクリックします。  
  
2.  テーブル内の列をクリックして、(マウスのボタンを押しながら) 関連する参照テーブル内の関連する参照列までカーソルをドラッグして、ボタンを離します。 リレーションシップは自動的に正しい順序で作成されます。  
  
#### <a name="to-create-a-relationship-between-two-tables-in-diagram-view-right-click"></a>ダイアグラム ビューで 2 つのテーブル間のリレーションシップを作成するには (右クリック)  
  
1.  [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]で、 **[モデル]** メニューをクリックし、 **[モデル ビュー]** をポイントし、 **[ダイアグラム ビュー]** をクリックします。  
  
2.  テーブルの見出しまたは列を右クリックして、 **[リレーションシップの作成]** をクリックします。  
  
3.  **[リレーションシップの作成]** ダイアログ ボックスの **[テーブル]** の下矢印をクリックし、一覧からテーブルを選択します。  
  
     このテーブルは、"一対多" リレーションシップの "多" の側に当たります。  
  
4.  **[列]** で、 **[関連する参照列]** に関連するデータを含む列を選択します。 列を右クリックしてリレーションシップを作成した場合は、列が自動的に選択されます。  
  
5.  **[関連する参照テーブル]** で、 **[テーブル]** で選択したテーブルに関連するデータの列を少なくとも 1 つ含むテーブルを選択します。  
  
     このテーブルは、"一対多" リレーションシップの "一" の側に当たります。つまり、選択した列には重複する値がないことを意味します。 間違った順序 (多対一ではなく一対多) でリレーションシップを作成しようとすると、 **[関連する参照列]** フィールドの横にアイコンが表示されます。 順序を逆にして有効なリレーションシップを作成してください。  
  
6.  **[関連する参照列]** で、 **[列]** で選択した列の値と一致する一意の値を含む列を選択します。  
  
7.  **[作成]** をクリックします。  
  
#### <a name="to-create-a-relationship-between-two-tables-in-data-view"></a>データ ビューで 2 つのテーブル間のリレーションシップを作成するには  
  
1.  [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]で、 **[テーブル]** メニューをクリックし、 **[リレーションシップの作成]** をクリックします。  
  
2.  **[リレーションシップの作成]** ダイアログ ボックスの **[テーブル]** の下矢印をクリックし、一覧からテーブルを選択します。  
  
     このテーブルは、"一対多" リレーションシップの "多" の側に当たります。  
  
3.  **[列]** で、 **[関連する参照列]** に関連するデータを含む列を選択します。  
  
4.  **[関連する参照テーブル]** で、 **[テーブル]** で選択したテーブルに関連するデータの列を少なくとも 1 つ含むテーブルを選択します。  
  
     このテーブルは、"一対多" リレーションシップの "一" の側に当たります。つまり、選択した列には重複する値がないことを意味します。 間違った順序 (多対一ではなく一対多) でリレーションシップを作成しようとすると、 **[関連する参照列]** フィールドの横にアイコンが表示されます。 順序を逆にして有効なリレーションシップを作成してください。  
  
5.  **[関連する参照列]** で、 **[列]** で選択した列の値と一致する一意の値を含む列を選択します。  
  
6.  **[作成]** をクリックします。  
  
## <a name="see-also"></a>関連項目  
 [リレーションシップを削除します。](../../analysis-services/tabular-models/delete-relationships-ssas-tabular.md)   
 [リレーションシップ](../../analysis-services/tabular-models/relationships-ssas-tabular.md)  
  
  
