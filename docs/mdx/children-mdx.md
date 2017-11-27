---
title: "子 (MDX) |Microsoft ドキュメント"
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
- CHILDREN
dev_langs:
- kbMDX
helpviewer_keywords:
- Children function
ms.assetid: ce2c3069-914c-44a3-8a4c-5cbd4fb71e4c
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 4d55ca99aade56ae6cf5b1e01402877c924b78d8
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="children-mdx"></a>Children (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  指定されたメンバーの子のセットを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Member_Expression.Children  
```  
  
## <a name="arguments"></a>引数  
 *メンバー式*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 **子**関数は、指定したメンバーの子を含む自然順序のセットを返します。 指定されているメンバーに子メンバーがない場合、この関数は空のセットを返します。  
  
## <a name="example"></a>例  
 次の例では、Geography ディメンション内の Geography 階層の United States メンバーの子が返されます。  
  
```  
SELECT [Geography].[Geography].[Country].&[United States].Children ON 0  
FROM [Adventure Works]  
```  
  
 次の例は、すべてのメンバーを返します、**メジャー**ディメンションで列の軸が含まれますすべての計算されるメンバー、およびすべての子のセット、`[Product].[Model Name]`属性階層からの行軸、 **Adventure Works**キューブ。  
  
```  
SELECT  
    Measures.AllMembers ON COLUMNS,  
    [Product].[Model Name].Children ON ROWS  
FROM  
    [Adventure Works]  
  
```  
  
|リリース|履歴|  
|-------------|-------------|  
|[!INCLUDE[ssBOL2005_R03](../includes/ssbol2005-r03-md.md)]|**変更内容:**<br /> わかりやすくするための向上に構文および引数を更新します。<br /><br /> -更新された例を追加しました。|  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  

