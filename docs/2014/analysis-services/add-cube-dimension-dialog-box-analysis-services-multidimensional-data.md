---
title: キューブ ディメンション ダイアログ ボックス (Analysis Services - 多次元データ) を追加 |Microsoft ドキュメント
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
- sql12.asvs.cubeeditor.addcubedimensiondialog.f1
helpviewer_keywords:
- Add Cube Dimension dialog box
ms.assetid: 625a3b1f-183b-445f-9bb7-96945c324767
caps.latest.revision: 23
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: ff89f880df12126f173f1f5ad47d1841e532262d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36178571"
---
# <a name="add-cube-dimension-dialog-box-analysis-services---multidimensional-data"></a>[キューブ ディメンションの追加] ダイアログ ボックス (Analysis Services - 多次元データ)
  **の** [キューブ ディメンションの追加] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ダイアログ ボックスを使用すると、キューブにデータベース ディメンションへの参照を追加できます。 **[キューブ ディメンションの追加]** ダイアログ ボックスは、次のいずれかの操作で表示できます。  
  
-   キューブ デザイナーの **[キューブ構造]** または **[ディメンションの使用法]** タブにある **[ツール バー]** ペインで、 **[キューブ ディメンションの追加]** をクリックします。  
  
-   キューブ デザイナーの **[キューブ構造]** タブにある **[ディメンション]** ペインを右クリックして、ショートカット メニューの **[キューブ ディメンションの追加]** をクリックします。  
  
-   キューブ デザイナーの **[ディメンションの使用法]** タブにある **[グリッド]** ペインを右クリックして、ショートカット メニューの **[キューブ ディメンションの追加]** をクリックします。  
  
> [!NOTE]  
>  各キューブ ディメンションには、メジャー グループに対するリレーションシップを 1 つのみ設定できます。 しかし、データ ソース ビューで、キューブ ディメンションの基となるデータベース ディメンションが複数のリレーションシップによりメジャー グループに関連付けられている場合、複数のキューブ ディメンションを作成してキューブに追加できます。 このようなディメンションを多様ディメンションと呼び、一般的には時間ディメンションに使用されます。  
  
## <a name="options"></a>および  
 **ディメンションを選択します。**  
 選択したキューブに追加されるキューブ ディメンションの基となる、既存のデータベース ディメンションを選択します。 同じデータベース ディメンションから、複数のキューブ ディメンションを定義できます。  
  
> [!NOTE]  
>  同じデータベース ディメンションに基づく複数のキューブ ディメンションがキューブに追加される場合、追加されるキューブ ディメンションは多様ディメンションと呼ばれます。  
  
## <a name="see-also"></a>参照  
 [Analysis Services のデザイナーおよびダイアログ ボックス&#40;多次元データ&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  