---
title: "テーブル (SSAS テーブル) 内のデータを並べ替える |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5fa6ad56-bf68-4aac-a226-52556173b7e2
caps.latest.revision: "10"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 6cfced262d6b178712da538e9b678ac46357bc1a
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="sort-data-in-a-table-ssas-tabular"></a>テーブル内のデータの並べ替え (SSAS テーブル)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]テキスト (A ~ Z、Z A から) と 1 つまたは複数の列で (小さい最大または降順に) 番号ごとにデータを並べ替えることができます。  
  
### <a name="to-sort-the-data-in-a-table-based-on-a-text-column"></a>テキスト列を基準にテーブル データを並べ替えるには  
  
1.  モデル デザイナーで、英数字データの列を選択するか、列内で一定範囲のセルを選択するか、英数字データが含まれるテーブル列内でセルをアクティブにしたうえで、フィルターとして使用する列のヘッダーにある矢印をクリックします。  
  
2.  [オートフィルター] メニューで次のいずれかの操作を行います。  
  
    -   英数字の昇順で並べ替えるには、 **[昇順で並べ替え]**をクリックします。  
  
    -   英数字の降順で並べ替えるには、 **[降順で並べ替え]**をクリックします。  
  
    > [!NOTE]  
    >  他のアプリケーションからインポートされたデータの場合、データの先頭にスペースが挿入されていることがあります。 データを正しく並べ替えるには、先頭のスペースを削除する必要があります。  
  
### <a name="to-sort-the-data-in-a-table-based-on-a-numeric-column"></a>数値列を基準にテーブル データを並べ替えるには  
  
1.  モデル デザイナーで、英数字データの列を選択するか、列内で一定範囲のセルを選択するか、英数字データが含まれるテーブル列内でセルをアクティブにしたうえで、フィルターとして使用する列のヘッダーにある矢印をクリックします。  
  
2.  [オートフィルター] メニューで次のいずれかの操作を行います。  
  
    -   小さい数値から順に並べ替えるには、 **[小さい順に並べ替え]**をクリックします。  
  
    -   大きい数値から順に並べ替えるには、 **[大きい順に並べ替え]**をクリックします。  
  
    > [!NOTE]  
    >  期待した結果が得られない場合、列の数値が数値ではなくテキストとして格納されている可能性があります。 たとえば、何らかの会計システムからインポートされた負の数値や、先頭にアポストロフィ (') が入力されている数値は、テキストとして格納されます。  
  
## <a name="see-also"></a>参照  
 [データのフィルター処理と並べ替え (SSAS テーブル)](http://msdn.microsoft.com/library/55ebd7a6-2458-4398-911f-fcfeb2413f1b)   
 [パースペクティブ (SSAS テーブル)](../../analysis-services/tabular-models/perspectives-ssas-tabular.md)   
 [ロール (SSAS テーブル)](../../analysis-services/tabular-models/roles-ssas-tabular.md)  
  
  
