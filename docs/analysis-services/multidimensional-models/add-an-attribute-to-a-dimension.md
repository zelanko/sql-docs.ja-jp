---
title: "ディメンションへの属性の追加 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "属性の追加"
  - "属性の自動作成"
  - "属性 [Analysis Services], 作成"
  - "属性 [Analysis Services], 追加"
  - "手動による属性の作成 [Analysis Services]"
ms.assetid: 25826ba1-2b38-4b34-bd3a-7eba116093ae
caps.latest.revision: 32
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# ディメンションへの属性の追加
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、自動または手動で、属性をディメンションに追加できます。  
  
 属性を自動的に作成するには、[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] のディメンション デザイナーの **[ディメンション構造]** タブで、属性にマッピングする列を選択し、その列を **[データ ソース ビュー]** ペインから **[属性]** ペインにドラッグします。 これにより、列にマッピングされる属性が作成され、列の名前と同じ名前が属性に割り当てられます。 その名前を使用している属性が既に存在する場合は、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では序数サフィックスを追加して、最初の重複する名前を "1" から始めます。  
  
 属性を手動で作成するには、**[属性]** ペインをグリッド ビューに設定します。 グリッドの最後の行の名前列で、**\<新しい属性>** をクリックします。 新しい属性の名前を入力します。 これにより、列にマッピングされない、すべてのプロパティが既定に設定されている属性が作成されます。 新しい属性の **KeyColumns** プロパティを構成して、[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] の **[プロパティ]** ウィンドウでマッピングを設定できます。  
  
 詳細については、「[新しい属性の自動定義](../../analysis-services/multidimensional-models/define-a-new-attribute-automatically.md)」、「[新しい属性の手動による定義](../Topic/Define%20a%20New%20Attribute%20Manually.md)」、「[名前列への属性のバインド](../../analysis-services/multidimensional-models/bind-an-attribute-to-a-name-column.md)」、「[属性の KeyColumns プロパティの変更](../../analysis-services/multidimensional-models/modify-the-keycolumn-property-of-an-attribute.md)」を参照してください。  
  
## 参照  
 [ディメンションの属性のプロパティの参照](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md)  
  
  