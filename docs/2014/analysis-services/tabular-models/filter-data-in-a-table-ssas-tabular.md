---
title: テーブル (SSAS テーブル) 内のデータをフィルター処理 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.customfilterdb.f1
- sql12.asvs.bidtoolset.autofiltermenu.f1
- sql12.asvs.bidtoolset.notallitemsshowing.f1
ms.assetid: 3223059d-f525-4835-bf88-ebc195d9dbdc
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d33148543677c58a353253a86bbdf99f1c892326
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48079702"
---
# <a name="filter-data-in-a-table-ssas-tabular"></a>テーブル内のデータのフィルター処理 (SSAS テーブル)
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
 [フィルター処理し、データの並べ替え&#40;SSAS 表形式&#41;](../filter-and-sort-data-ssas-tabular.md)   
 [パースペクティブ&#40;SSAS 表形式&#41;](perspectives-ssas-tabular.md)   
 [ロール&#40;SSAS 表形式&#41;](roles-ssas-tabular.md)  
  
  
