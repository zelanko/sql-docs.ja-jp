---
title: テーブル内のデータを並べ替える |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 5fa6ad56-bf68-4aac-a226-52556173b7e2
caps.latest.revision: 10
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 910ccebc68fc68acf8b7c57a949871b473eb1689
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sort-data-in-a-table"></a>テーブル内のデータの並べ替え 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  データは、1 つ以上の列のテキスト (A から Z、または Z から A) または数値 (小さい数値から大きい数値、または大きい数値から小さい数値) の順で並べ替えることができます。  
  
### <a name="to-sort-the-data-in-a-table-based-on-a-text-column"></a>テキスト列を基準にテーブル データを並べ替えるには  
  
1.  モデル デザイナーで、英数字データの列を選択するか、列内で一定範囲のセルを選択するか、英数字データが含まれるテーブル列内でセルをアクティブにしたうえで、フィルターとして使用する列のヘッダーにある矢印をクリックします。  
  
2.  [オートフィルター] メニューで次のいずれかの操作を行います。  
  
    -   英数字の昇順で並べ替えるには、 **[昇順で並べ替え]** をクリックします。  
  
    -   英数字の降順で並べ替えるには、 **[降順で並べ替え]** をクリックします。  
  
    > [!NOTE]  
    >  他のアプリケーションからインポートされたデータの場合、データの先頭にスペースが挿入されていることがあります。 データを正しく並べ替えるには、先頭のスペースを削除する必要があります。  
  
### <a name="to-sort-the-data-in-a-table-based-on-a-numeric-column"></a>数値列を基準にテーブル データを並べ替えるには  
  
1.  モデル デザイナーで、英数字データの列を選択するか、列内で一定範囲のセルを選択するか、英数字データが含まれるテーブル列内でセルをアクティブにしたうえで、フィルターとして使用する列のヘッダーにある矢印をクリックします。  
  
2.  [オートフィルター] メニューで次のいずれかの操作を行います。  
  
    -   小さい数値から順に並べ替えるには、 **[小さい順に並べ替え]** をクリックします。  
  
    -   大きい数値から順に並べ替えるには、 **[大きい順に並べ替え]** をクリックします。  
  
    > [!NOTE]  
    >  期待した結果が得られない場合、列の数値が数値ではなくテキストとして格納されている可能性があります。 たとえば、何らかの会計システムからインポートされた負の数値や、先頭にアポストロフィ (') が入力されている数値は、テキストとして格納されます。  
  
## <a name="see-also"></a>参照  
 [フィルターとのデータの並べ替え](http://msdn.microsoft.com/library/55ebd7a6-2458-4398-911f-fcfeb2413f1b)   
 [パースペクティブ](../../analysis-services/tabular-models/perspectives-ssas-tabular.md)   
 [Roles](../../analysis-services/tabular-models/roles-ssas-tabular.md)  
  
  
