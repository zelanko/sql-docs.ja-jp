---
title: "Unorder (MDX) |Microsoft ドキュメント"
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
- UNORDER
dev_langs:
- kbMDX
helpviewer_keywords:
- Unorder function
ms.assetid: a805df2a-6320-45bc-989f-90e85faf027f
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 9b5ed088bc1dd8203e7bdcb13d763dccb75eb49a
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="unorder-mdx"></a>Unorder (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  指定されたセットから適用済みの順序設定を解除します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Unorder(Set_Expression)   
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
## <a name="remarks"></a>解説  
 **Unorder**関数では、セットに含まれる、他の関数またはステートメントでなどの組に適用された順序設定を削除、[順序](../mdx/order-mdx.md)関数。 によって返されるセット内の組の順序、 **Unorder**関数が不定になります。  
  
 **Unorder**関数へのヒントとして使用されます[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]のクエリ最適化のセットを処理します。 使用してセット内の組の順序が計算処理またはクエリにとって重要ではない場合、 **Unorder**関数は、このような場合、パフォーマンスが向上を提供できます。 たとえば、 [NonEmpty (MDX)](../mdx/nonempty-mdx.md)関数パフォーマンスが向上この関数に指定されたセットが場合と順序付けられた場合[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]の順序を保持する必要がで[!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)]、クエリ プロセッサなど多くの関数では、この関数を自動的に実行しようとしました。**合計**と**集計**です。 使用して、パフォーマンスが向上**Unorder**数百万の組から成る大きなセットである可能性があります。  
  
## <a name="example"></a>例  
 次の擬似コードでは、この関数の構文例を示しています。  
  
```  
NonEmpty (UnOrder (<set_expression>))  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  

