---
title: ディメンションに属性を追加 |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- adding attributes
- automatic attribute creation
- attributes [Analysis Services], creating
- attributes [Analysis Services], adding
- manual attribute creation [Analysis Services]
ms.assetid: 25826ba1-2b38-4b34-bd3a-7eba116093ae
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 7b3f94d20f7f39efffd435793bf3dff808e115df
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36178570"
---
# <a name="add-an--attribute-to-a-dimension"></a>ディメンションへの属性の追加
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、自動または手動で、属性をディメンションに追加できます。  
  
 属性を自動的に作成するには、 **のディメンション デザイナーの** [ディメンション構造] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]タブで、属性にマッピングする列を選択し、その列を **[データ ソース ビュー]** ペインから **[属性]** ペインにドラッグします。 これにより、列にマッピングされる属性が作成され、列の名前と同じ名前が属性に割り当てられます。 その名前を使用している属性が既に存在する場合は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では序数サフィックスを追加して、最初の重複する名前を "1" から始めます。  
  
 属性を手動で作成するには、 **[属性]** ペインをグリッド ビューに設定します。 グリッドの最後の行の 名前 列、 **\<新しい属性 >** 項目。 新しい属性の名前を入力します。 これにより、列にマッピングされない、すべてのプロパティが既定に設定されている属性が作成されます。 新しい属性の **KeyColumns** プロパティを構成して、 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] の **[プロパティ]** ウィンドウでマッピングを設定できます。  
  
 詳細については、「 [新しい属性の自動定義](attribute-properties-define-a-new-attribute-automatically.md)」、「 [新しい属性の手動による定義](../define-a-new-attribute-manually.md)」、「 [名前列への属性のバインド](attribute-properties-bind-an-attribute-to-a-name-column.md)」、「 [属性の KeyColumns プロパティの変更](attribute-properties-modify-the-keycolumn-property.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [ディメンションの属性のプロパティの参照](dimension-attribute-properties-reference.md)  
  
  