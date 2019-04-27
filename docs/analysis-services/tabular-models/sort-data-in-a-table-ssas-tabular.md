---
title: Analysis Services 表形式モデル テーブルにデータを並べ替える |Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4ab79de3551f1ef4613bb3c6f14b44ca660e2dfc
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62472092"
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
  
  
