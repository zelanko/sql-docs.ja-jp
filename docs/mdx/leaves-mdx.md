---
title: "リーフ (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- LEAVES
dev_langs:
- kbMDX
helpviewer_keywords:
- Leaves function
ms.assetid: 09f908aa-1b2d-4af9-8c8d-c023915241b2
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 0c6201939c5bfb6f5ad61c009aac5a7e4740af63
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="leaves-mdx"></a>Leaves (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  すべての属性から構成されるセットを返します。必要に応じて特定のディメンションに属している属性のみを返すこともできます。 返すセット内の各属性 x について、x が粒度属性であるか、直接または間接的に粒度属性に関連付けられている属性である場合、粒度はスライスに影響することなく属性 x に対して設定されます。 **まま**関数が SCOPE ステートメント内または代入の左辺で使用するために設計されています。  
  
## <a name="syntax"></a>構文  
  
```  
  
Leaves( [ Dimension_expression ] )  
```  
  
## <a name="arguments"></a>引数  
 *Dimension_Expression*  
 ディメンションを返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 リーフ メンバーとは、すべての属性階層の最下位レベルのクロス結合によって形成される組です。 計算されるメンバーは除外されます。  
  
-   ディメンション名が指定されている場合、**まま**関数を指定されたディメンションのキー属性のリーフ メンバーを含むセットを返します。  
  
-   ディメンションが複数のメジャー グループに関連付けられている場合、現在のスコープにあるメジャーのディメンションが使用されます。  
  
-   ディメンション名が指定されていない場合は、キューブ全体のリーフ メンバーで構成されるセットを返します。  
  
    > [!NOTE]  
    >  ディメンション式が階層に解決され、その階層の一意名がディメンションの一意名と同じになる場合 (キューブ ディメンション プロパティ HierarchyUniqueNameStyle = ExcludeDimensionName であり、階層名 = ディメンション名の場合) は、ディメンションが使用されます。  
  
    > [!IMPORTANT]  
    >  現在のスコープのメジャー グループに対する粒度が異なる属性が 1 つでもあると、エラーが生成されます。  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  

