---
title: テーブル内のデータのフィルター処理 (SSAS テーブル) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.customfilterdb.f1
- sql12.asvs.bidtoolset.autofiltermenu.f1
- sql12.asvs.bidtoolset.notallitemsshowing.f1
ms.assetid: 3223059d-f525-4835-bf88-ebc195d9dbdc
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 869185e56db9a4ffb07282d3ce51ced191a6bac8
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66067129"
---
# <a name="filter-data-in-a-table-ssas-tabular"></a>テーブル内のデータのフィルター処理 (SSAS テーブル)
  テーブルに読み込む行を制御するには、データをインポートする際にフィルターを適用します。 データをインポートした後、行を個別に削除することはできません。 ただし、カスタム フィルターを適用して行の表示方法を制御することは可能です。 フィルター条件を満たしていない行は非表示になります。 1 行以上の列を基準にしてフィルター処理を行うことができます。 フィルター処理は追加型です。つまり、新しいフィルターによる処理は、前のフィルター処理の結果に対して行われます。したがって、フィルターを適用するごとにデータのサブセットは減っていきます。  
  
> [!NOTE]  
>  フィルターのプレビュー ウィンドウでは、表示される異なる値の数が制限されます。 制限を超えた場合は、メッセージが表示されます。  
  
### <a name="to-filter-data-based-on-column-values"></a>列の値を基準にしてデータをフィルター処理するには  
  
1.  モデル デザイナーでテーブルを選択し、フィルター処理の基準にする列の見出しの矢印をクリックします。  
  
2.  [オートフィルター] メニューで次のいずれかの操作を行います。  
  
    -   列の値の一覧で、フィルター処理の条件として1つ以上の値を選択または選択解除し、[ **OK]** をクリックします。  
  
         値の数が極端に多い場合、個々のアイテムが一覧に表示されないことがあります。 その場合は、"アイテムが多すぎるため、表示できません" というメッセージが表示されます。  
  
    -   [**数値フィルター** ] または [**テキストフィルター** ] (列の種類によって異なります) をクリックし、比較演算子コマンドのいずれかクリック ( **Equals**など) を選択するか、[**カスタムフィルター**] をクリックします。 **[カスタム フィルター]** ダイアログ ボックスで、フィルターを作成し、 **[OK]** をクリックします。  
  
### <a name="to-clear-a-filter-for-a-column"></a>列のフィルターをクリアするには  
  
1.  フィルターをクリアする列の見出しの矢印をクリックします。  
  
2.  [**列名の\<>からフィルターをクリア] を**クリックします。  
  
### <a name="to-clear-all-filters-for-a-table"></a>テーブルのすべてのフィルターをクリアするには  
  
1.  モデル デザイナーで、フィルターをクリアするテーブルを選択します。  
  
2.  **[列]** メニューをクリックし、 **[すべてのフィルターをクリア]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [SSAS 表形式&#41;&#40;データのフィルター処理と並べ替え](../filter-and-sort-data-ssas-tabular.md)   
 [SSAS テーブル&#41;&#40;パースペクティブ](perspectives-ssas-tabular.md)   
 [ロール (SSAS テーブル)](roles-ssas-tabular.md)  
  
  
