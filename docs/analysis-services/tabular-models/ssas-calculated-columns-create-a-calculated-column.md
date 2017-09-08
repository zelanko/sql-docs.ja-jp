---
title: "計算列を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 04/10/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.as.daxref.CreataCalculatedColumn.f1
ms.assetid: 59440510-2d76-41dc-9b55-edc15259f9da
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 512b3ae1512c48d1d502d763505ee0609fd90608
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="create-a-calculated-column"></a>計算列の作成
  計算列では、モデルに新しいデータを追加することができます。 列に値を貼り付けまたはインポートする代わりに、列の行レベルの値を定義する DAX 数式を作成します。 計算列の各行の値は、有効な数式を作成して Enter キーを押したときに、計算および代入されます。 計算列は、他のデータ列と同じように、レポートまたは分析のアプリケーションに追加できます。 このトピックでは、モデル デザイナーの DAX 数式バーを使用して新しい計算列を作成する方法について説明します。  
  
#### <a name="to-create-a-new-calculated-column"></a>新しい計算列を作成するには  
  
1.  モデル デザイナーのデータ ビューで、計算列を追加するテーブルを選択し、 **[列]** メニューをクリックしてから **[列の追加]**をクリックします。  
  
     右端の空白の列に対して**[列の追加]** が強調表示され、カーソルが数式バーに移動します。  
  
     2 つの既存の列の間に新しい列を作成するには、既存の列をクリックしてから **[列の挿入]**をクリックします。  
  
2.  数式バーで次のいずれかの操作を行います。  
  
    -   等号を入力し、続いて数式を入力します。  
  
    -   等号に続けて DAX 関数、その後に関数に必要な引数やパラメーターを入力します。  
  
    -   関数ボタン (**[fx]**) をクリックし、 **[関数の挿入]** ダイアログ ボックスでカテゴリおよび関数を選択してから、 **[OK]**をクリックします。 数式バーで、関数に必要な残りの引数とパラメーターを入力します。  
  
3.  Enter キーを押して数式を確定します。  
  
     列全体に数式が設定され、行ごとに値が計算されます。  
  
> [!TIP]  
>  DAX 数式のオートコンプリート機能は、関数が入れ子になっている既存の数式の途中で使用できます。 挿入ポイントの直前のテキストが、ドロップダウン リストに値を表示するために使用されます。挿入ポイントより後ろのすべてのテキストは変更されません。  
  
## <a name="see-also"></a>参照  
 [計算列](../../analysis-services/tabular-models/ssas-calculated-columns.md)   
 [メジャー](../../analysis-services/tabular-models/measures-ssas-tabular.md)  
  
  
