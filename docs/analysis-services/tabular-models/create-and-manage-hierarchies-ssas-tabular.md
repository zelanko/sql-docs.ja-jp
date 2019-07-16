---
title: 作成し、Analysis Services 表形式モデルでの階層の管理 |Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5e785fe0e4a5f0030beceff7b9393932a29eaa52
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "68163029"
---
# <a name="create-and-manage-hierarchies"></a>作成し、階層の管理 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  階層の作成と管理はダイアグラム ビューのモデル デザイナーで行うことができます。 モデル デザイナーをダイアグラム ビューに表示するには、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で **[モデル]** メニューをクリックし、 **[モデル ビュー]** をポイントして、 **[ダイアグラム ビュー]** をクリックします。  
  
 この記事には、次のタスクが含まれています。  
  
-   [階層の作成](#bkmk_create)  
  
-   [階層の編集](#bkmk_edit)  
  
-   [階層の削除](#bkmk_delete)  
  
##  <a name="bkmk_create"></a> 階層を作成します。  
 列とテーブルのショートカット メニューを使用すると階層を作成できます。 階層を作成すると、選択した列を子レベルに持つ新しい親レベルが表示されます。  
  
#### <a name="to-create-a-hierarchy-from-the-context-menu"></a>ショートカット メニューから階層を作成するには  
  
1.  テーブル ウィンドウのモデル デザイナー (ダイアグラム ビュー) で、列を右クリックして **[階層の作成]** をクリックします。  
  
     複数の列を選択するには、列を 1 つずつクリックし、右クリックしてショートカット メニューを開き、 **[階層の作成]** をクリックします。  
  
     テーブル ウィンドウの下部に親階層レベルが作成され、選択した列が階層の下に子レベルとしてコピーされます。  
  
2.  階層の名前を入力します。  
  
 階層の親レベル、列をコピーするには、追加の列をドラッグできます。 子レベルを階層内の目的の場所にドロップします。  
  
> [!NOTE]  
>  1 つ以上の列と共に 1 つのメジャーを複数選択するか、または複数のテーブルから複数の列を選択した場合、ショートカット メニューの [階層の作成] コマンドは無効になります。  
  
##  <a name="bkmk_edit"></a> 階層を編集します。  
 階層名の変更、子レベルの名前の変更、子レベルの順序の変更、子レベルとしての列の追加、階層内の子レベルの削除、子レベルの基になる名前 (列名) の表示、階層の親レベルと同名の子レベルの非表示を行うことができます。  
  
#### <a name="to-change-the-name-of-a-hierarchy-or-child-level"></a>階層または子レベルの名前を変更するには  
  
1.  階層の親レベルまたは子レベルを右クリックし、 **[名前の変更]** をクリックします。  
  
2.  新しい名前を入力するか、既存の名前を編集します。  
  
#### <a name="to-change-the-order-of-a-child-level-in-a-hierarchy"></a>階層内の子レベルの順序を変更するには  
  
-   子レベルをクリックして、階層内の新しい場所にドラッグします。  
  
-   または、階層内の子レベルを右クリックし、[上へ移動] をクリックして一覧内を上へ移動するか、[下へ移動] をクリックして下へ移動します。  
  
-   または、子レベルをクリックして選択し、Alt キーを押しながら上方向キーを押して一覧内を上へ移動するか、Alt キーを押しながら下方向キーを押して下へ移動します。  
  
#### <a name="to-add-another-child-level-to-a-hierarchy"></a>階層に他の子レベルを追加するには  
  
-   列をクリックして、親レベルまたは階層内の特定の場所にドラッグします。 階層の子レベルとして列がコピーされます。  
  
-   または、列を右クリックして **[階層に追加]** をポイントし、階層をクリックします。  
  
> [!NOTE]  
>  非表示の列 (レポートで非表示の列) を子レベルとして階層に追加できます。 子レベルは非表示になりません。  
  
#### <a name="to-remove-a-child-level-from-a-hierarchy"></a>階層から子レベルを削除するには  
  
-   子レベルを右クリックし、 **[階層から削除]** をクリックします。  
  
-   または、子レベルをクリックして **Del**キーを押します。  
  
> [!NOTE]  
>  階層の子レベルの名前を変更すると、コピー元の列とは同じ名前を共有しなくなります。 コピー元の列を表示するには、 **[基になる列の名前の表示]** を使用します。  
  
#### <a name="to-show-a-source-name"></a>基になる列の名前を表示するには  
  
-   階層の子レベルを右クリックして、 **[基になる列の名前の表示]** をクリックします。 コピー元の列の名前が表示されます。  
  
##  <a name="bkmk_delete"></a> 階層の削除  
  
#### <a name="to-delete-a-hierarchy-and-remove-its-child-levels"></a>階層と子レベルを削除するには  
  
-   親階層レベルを右クリックして、[階層の削除] をクリックします。  
  
-   または、親階層レベルをクリックし、Del キーを押します。 これにより、すべての子レベルも削除されます。  
  
## <a name="see-also"></a>関連項目  
 [テーブル モデル デザイナー](../../analysis-services/tabular-models/tabular-model-designer-ssas.md)   
 [階層](../../analysis-services/tabular-models/hierarchies-ssas-tabular.md)   
 [メジャー](../../analysis-services/tabular-models/measures-ssas-tabular.md)  
  
  
