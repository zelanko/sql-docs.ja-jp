---
title: テーブル (SSAS テーブル) 内のデータを並べ替える |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 5fa6ad56-bf68-4aac-a226-52556173b7e2
caps.latest.revision: 9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0038e15b9fceef897e117a3f2bb9d2f895cf234e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37287948"
---
# <a name="sort-data-in-a-table-ssas-tabular"></a>テーブル内のデータの並べ替え (SSAS テーブル)
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
 [フィルター処理し、データの並べ替え&#40;SSAS 表形式&#41;](../filter-and-sort-data-ssas-tabular.md)   
 [パースペクティブ&#40;SSAS 表形式&#41;](perspectives-ssas-tabular.md)   
 [ロール&#40;SSAS 表形式&#41;](roles-ssas-tabular.md)  
  
  
