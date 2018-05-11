---
title: 新しい属性を自動的に定義 |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e6191af998108de112a81ab3a5b4edbaa7a49d18
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="attribute-properties---define-a-new-attribute-automatically"></a>属性のプロパティ -、自動的に新しい属性の定義
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  ディメンション デザイナーでは、ドラッグ アンド ドロップ編集を使用して、ディメンションに新しい属性を作成することができます。  
  
### <a name="to-create-a-new-attribute-automatically"></a>新しい属性を自動的に作成するには  
  
1.  ディメンション デザイナーで、属性を作成するディメンションを開きます。  
  
2.  **[ディメンション構造]** タブの **[データ ソース ビュー]** ペインで、属性をバインドするテーブルの列を選択し、その列を **[属性]** ペインにドラッグします。  
  
     [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によって、バインド先の列と同じ名前の新しい属性が作成されます。 同じ列を使用する複数の属性がある場合は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] により、属性名に番号が追加されます。  
  
## <a name="see-also"></a>参照  
 [多次元モデル内のディメンション](../../analysis-services/multidimensional-models/dimensions-in-multidimensional-models.md)   
 [ディメンションの属性のプロパティの参照](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md)  
  
  
