---
title: キーの列 ダイアログ ボックス (Analysis Services - 多次元データ) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql.asvs.dimensiondesigner.dbv.dataitemCollection.f1
helpviewer_keywords:
- DataItem Collection dialog box
ms.assetid: 585f27f2-d5eb-4516-b29a-2084010b7d51
caps.latest.revision: 19
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 1bdfbda7088df7953df18ee796f6e41057eb090b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36175626"
---
# <a name="key-columns-dialog-box-analysis-services---multidimensional-data"></a>[キー列] ダイアログ ボックス (Analysis Services - 多次元データ)
  属性の **KeyColumns** プロパティを変更するには、**[キー列]** ダイアログ ボックスを使用します。 詳細については、「 [属性の KeyColumn プロパティの変更](multidimensional-models/attribute-properties-modify-the-keycolumn-property.md)」を参照してください。  
  
 **キー列 ダイアログ ボックスを表示するには**  
  
-   [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] または [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、属性を選択し、 **[プロパティ]** ウィンドウで、その属性の**KeyColumns**プロパティに関連付けられた省略記号ボタン ( **[...]** ) をクリックします。  
  
## <a name="options"></a>および  
 **ソース テーブル**  
 選択するキー列を含む、基になるテーブルを選択します。 基になるテーブルは、データ ソース ビュー内のすべてのテーブルの一覧から選択できます。  
  
 **使用可能な列**  
 キー列として使用する列を選択します。 指定した **[基になるテーブル]** 内の列の一覧から、まだキー列として選択されていない列を選択できます。  
  
 選択した列を **[キー列]** の一覧に追加するには、**[>]** ボタンをクリックします。  
  
 **[キー列]**  
 選択したキー列の順序を定義します。 キー列の順序は、適切な複合キーを定義する際に重要です。 キー列の一覧の順序を設定または変更するには、列を選択し、**[上へ]** または **[下へ]** ボタンをクリックします。  
  
 **[キー列]** の一覧から列を削除するには、列を選択し、**[\<]** ボタンをクリックします。  
  
 **[上へ]**  
 **[キー列]** で選択した列を 1 つ上の位置に移動する場合にクリックします。  
  
> [!NOTE]  
>  このオプションは、一覧に複数の列が含まれ、列が選択されている場合のみ有効です。  
  
 **[下へ]**  
 **[キー列]** で選択した列を 1 つ下の位置に移動する場合にクリックします。  
  
> [!NOTE]  
>  このオプションは、一覧に複数の列が含まれ、列が選択されている場合のみ有効です。  
  
 **>**  
 新しい列を **[キー列]** の一覧に表示される列の末尾に追加する場合にクリックします。  
  
 **<**  
 選択した列を **[キー列]** の一覧に表示される列から削除する場合にクリックします。  
  
## <a name="see-also"></a>参照  
 [Analysis Services のデザイナーおよびダイアログ ボックス&#40;多次元データ&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  