---
title: "テーブル内のデータのフィルター処理 (SSAS テーブル) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.asvs.bidtoolset.notallitemsshowing.f1"
  - "sql13.asvs.bidtoolset.autofiltermenu.f1"
  - "sql13.asvs.bidtoolset.customfilterdb.f1"
ms.assetid: 3223059d-f525-4835-bf88-ebc195d9dbdc
caps.latest.revision: 13
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 13
---
# テーブル内のデータのフィルター処理 (SSAS テーブル)
  テーブルに読み込む行を制御するには、データをインポートする際にフィルターを適用します。 データをインポートした後、行を個別に削除することはできません。 ただし、カスタム フィルターを適用して行の表示方法を制御することは可能です。 フィルター条件を満たしていない行は非表示になります。 1 行以上の列を基準にしてフィルター処理を行うことができます。 フィルター処理は追加型です。つまり、新しいフィルターによる処理は、前のフィルター処理の結果に対して行われます。したがって、フィルターを適用するごとにデータのサブセットは減っていきます。  
  
> [!NOTE]  
>  フィルターのプレビュー ウィンドウでは、表示される異なる値の数が制限されます。 制限を超えた場合は、メッセージが表示されます。  
  
### 列の値を基準にしてデータをフィルター処理するには  
  
1.  モデル デザイナーでテーブルを選択し、フィルター処理の基準にする列の見出しの矢印をクリックします。  
  
2.  [オートフィルター] メニューで次のいずれかの操作を行います。  
  
    -   列の値の一覧で、フィルター処理の基準にする 1 つ以上の値を選択するか、選択を解除し、 **[OK]**をクリックします。  
  
         値の数が極端に多い場合、個々のアイテムが一覧に表示されないことがあります。 その場合は、"アイテムが多すぎるため、表示できません" というメッセージが表示されます。  
  
    -   列の種類に応じて **[数値フィルター]** または **[テキスト フィルター]** をクリックし、比較演算子コマンド (**[等しい]** など) のいずれかをクリックするか、**[カスタム フィルター]** をクリックします。 **[カスタム フィルター]** ダイアログ ボックスで、フィルターを作成し、 **[OK]**をクリックします。  
  
### 列のフィルターをクリアするには  
  
1.  フィルターをクリアする列の見出しの矢印をクリックします。  
  
2.  **[\<列名> のフィルターをクリア]** をクリックします。  
  
### テーブルのすべてのフィルターをクリアするには  
  
1.  モデル デザイナーで、フィルターをクリアするテーブルを選択します。  
  
2.  **[列]** メニューをクリックし、 **[すべてのフィルターをクリア]**をクリックします。  
  
## 参照  
 [データのフィルター処理と並べ替え (SSAS テーブル)](../Topic/Filter%20and%20Sort%20Data%20\(SSAS%20Tabular\).md)   
 [パースペクティブ (SSAS テーブル)](../../analysis-services/tabular-models/perspectives-ssas-tabular.md)   
 [ロール (SSAS テーブル)](../../analysis-services/tabular-models/roles-ssas-tabular.md)  
  
  