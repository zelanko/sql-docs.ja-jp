---
title: ディメンションに属性を追加 |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d175c8731c3c808d33e1f9fa7f70a01a15ddbed3
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="attribute-properties---add-an--attribute-to-a-dimension"></a>属性のプロパティ - のディメンションに属性を追加
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、自動または手動で、属性をディメンションに追加できます。  
  
 属性を自動的に作成するには、 **のディメンション デザイナーの** [ディメンション構造] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]タブで、属性にマッピングする列を選択し、その列を **[データ ソース ビュー]** ペインから **[属性]** ペインにドラッグします。 これにより、列にマッピングされる属性が作成され、列の名前と同じ名前が属性に割り当てられます。 その名前を使用している属性が既に存在する場合は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では序数サフィックスを追加して、最初の重複する名前を "1" から始めます。  
  
 属性を手動で作成するには、**[属性]** ペインをグリッド ビューに設定します。 グリッドの最後の行の 名前 列、 **\<新しい属性 >** 項目。 新しい属性の名前を入力します。 これにより、列にマッピングされない、すべてのプロパティが既定に設定されている属性が作成されます。 新しい属性の **KeyColumns** プロパティを構成して、 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] の **[プロパティ]** ウィンドウでマッピングを設定できます。  
  
 詳細については、「 [新しい属性の自動定義](../../analysis-services/multidimensional-models/attribute-properties-define-a-new-attribute-automatically.md)」、「 [名前列への属性のバインド](../../analysis-services/multidimensional-models/attribute-properties-bind-an-attribute-to-a-name-column.md)」、「 [属性の KeyColumns プロパティの変更](../../analysis-services/multidimensional-models/attribute-properties-modify-the-keycolumn-property.md)では、自動または手動で、属性をディメンションに追加できます。  
  
## <a name="see-also"></a>参照  
 [ディメンションの属性のプロパティの参照](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md)  
  
  
