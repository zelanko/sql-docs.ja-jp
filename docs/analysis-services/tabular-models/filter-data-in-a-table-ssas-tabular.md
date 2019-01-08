---
title: Analysis Services 表形式モデル テーブルにデータをフィルター処理 |Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9b1fcdda5bd49f8056a6035ec10da8fb52f1c5d1
ms.sourcegitcommit: 8a64c59c5d84150659a015e54f8937673cab87a0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2018
ms.locfileid: "53072126"
---
# <a name="filter-data-in-a-table"></a>テーブル内のデータのフィルター処理 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  テーブルに読み込む行を制御するには、データをインポートする際にフィルターを適用します。 データをインポートした後、行を個別に削除することはできません。 ただし、カスタム フィルターを適用して行の表示方法を制御することは可能です。 フィルター条件を満たしていない行は非表示になります。 1 行以上の列を基準にしてフィルター処理を行うことができます。 フィルター処理は追加型です。つまり、新しいフィルターによる処理は、前のフィルター処理の結果に対して行われます。したがって、フィルターを適用するごとにデータのサブセットは減っていきます。  
  
> [!NOTE]  
>  フィルターのプレビュー ウィンドウでは、表示される異なる値の数が制限されます。 制限を超えた場合は、メッセージが表示されます。  
  
### <a name="to-filter-data-based-on-column-values"></a>列の値を基準にしてデータをフィルター処理するには  
  
1.  モデル デザイナーでテーブルを選択し、フィルター処理の基準にする列の見出しの矢印をクリックします。  
  
2.  [オートフィルター] メニューで次のいずれかの操作を行います。  
  
    -   列の値の一覧で、フィルター処理の基準にする 1 つ以上の値を選択するか、選択を解除し、 **[OK]** をクリックします。  
  
         値の数が極端に多い場合、個々のアイテムが一覧に表示されないことがあります。 その場合は、"アイテムが多すぎるため、表示できません" というメッセージが表示されます。  
  
    -   列の種類に応じて **[数値フィルター]** または **[テキスト フィルター]** をクリックし、比較演算子コマンド ( **[等しい]** など) のいずれかをクリックするか、 **[カスタム フィルター]** をクリックします。 **[カスタム フィルター]** ダイアログ ボックスで、フィルターを作成し、 **[OK]** をクリックします。  
  
### <a name="to-clear-a-filter-for-a-column"></a>列のフィルターをクリアするには  
  
1.  フィルターをクリアする列の見出しの矢印をクリックします。  
  
2.  クリックして**フィルターをクリア\<列名 >** します。  
  
### <a name="to-clear-all-filters-for-a-table"></a>テーブルのすべてのフィルターをクリアするには  
  
1.  モデル デザイナーで、フィルターをクリアするテーブルを選択します。  
  
2.  **[列]** メニューをクリックし、 **[すべてのフィルターをクリア]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [フィルターとのデータの並べ替え](http://msdn.microsoft.com/library/55ebd7a6-2458-4398-911f-fcfeb2413f1b)   
 [パースペクティブ](../../analysis-services/tabular-models/perspectives-ssas-tabular.md)   
 [Roles](../../analysis-services/tabular-models/roles-ssas-tabular.md)  
  
  
