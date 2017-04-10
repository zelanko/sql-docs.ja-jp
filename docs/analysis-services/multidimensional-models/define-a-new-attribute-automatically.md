---
title: "新しい属性の自動定義 | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
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
  - "属性の自動作成"
  - "属性 [Analysis Services], 作成"
ms.assetid: 208a050a-5e2f-470c-b645-8d835e123db7
caps.latest.revision: 34
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# 新しい属性の自動定義
  ディメンション デザイナーでは、ドラッグ アンド ドロップ編集を使用して、ディメンションに新しい属性を作成することができます。  
  
### 新しい属性を自動的に作成するには  
  
1.  ディメンション デザイナーで、属性を作成するディメンションを開きます。  
  
2.  **[ディメンション構造]** タブの **[データ ソース ビュー]** ペインで、属性をバインドするテーブルの列を選択し、その列を **[属性]** ペインにドラッグします。  
  
     [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] バインド先の列と同じ名前の新しい属性が作成されます。 同じ列を使用する複数の属性がある場合は、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] により、属性名に番号が追加されます。  
  
## 参照  
 [多次元モデル内のディメンション](../../analysis-services/multidimensional-models/dimensions-in-multidimensional-models.md)   
 [ディメンションの属性のプロパティの参照](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md)  
  
  