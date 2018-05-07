---
title: DrillupMember (MDX) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DRILLUPMEMBER
dev_langs:
- kbMDX
helpviewer_keywords:
- DrillupMember function
ms.assetid: debcd966-ea4e-4ecf-8600-0a4d346d03f8
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 6bfb3843e351ca6b2fe76c92fb8e1e50f090acfc
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="drillupmember-mdx"></a>DrillupMember (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  指定されたセットのメンバーのうち、2 番目に指定されたセットに含まれるメンバーの子孫ではないものを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
DrillupMember(Set_Expression1, Set_Expression2)   
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression1*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *Set_Expression2*  
 セットを返す有効な多次元式 (MDX) です。  
  
## <a name="remarks"></a>解説  
 **DrillupMember**関数が 2 番目のセット内のメンバーの子孫である最初のセットで指定されたメンバーに基づくメンバーのセットを返します。 1 番目のセットの次元は任意ですが、2 番目には 1 次元のセットを指定する必要があります。 1 番目のセット内の元のメンバー間の順序はそのまま保持されます。 この関数は、1 番目のセット内のメンバーのうち、2 番目のセット内のメンバーの直接の子孫でもあるメンバーだけで構成されるセットを作成します。 1 番目のセット内のメンバーの直接の先祖が 2 番目のセット内に存在しない場合、この関数から返されるセットには 1 番目のセット内のメンバーが格納されます。 1 番目のセット内の子孫のうち、2 番目のセット内の先祖メンバーより前にあるメンバーも含められます。  
  
 1 番目のセットには、メンバーではなく組を含めることもできます。 組のドリル ダウンは、OLE DB の拡張機能であり、メンバーではなく組のセットを返します。  
  
> [!IMPORTANT]  
>  メンバーのドリルアップは、直後に子または子孫が続く場合のみ行われます。 セット内のメンバーの順序は重要の両方、ドリル ダウン\*と Drillup\*系関数。 使用を検討して、 **Hierarchize**適切に最初のセットのメンバーの順序付けする関数。  
  
## <a name="example"></a>例  
 次の 3 つの例は、2 番目のセットを除いて同一です。 最初の例では、2 番目のセットは United States です。 その結果、Colorado は結果セットから除外されます。 これは United States の子孫です。  
  
```  
SELECT DrillUpMember (   
  { [Geography].[Geography].[Country].[Canada]   
   ,[Geography].[Geography].[Country].[United States]   
   ,[Geography].[Geography].[State-Province].[Colorado]   
   ,[Geography].[Geography].[State-Province].[Alberta]   
   ,[Geography].[Geography].[State-Province].[Brunswick]    
 }   
 , {[Geography].[Geography].[Country].[United States]}   
 ) ON 0   
FROM [Adventure Works]  
```  
  
 例 2 は、メンバーの順序の重要性を示しています。 **DrillupMember**のみ 1 番目のセット内の子孫の直前に置かれるこれらのメンバー ドリル アップ、それをドリル アップしません、Canada メンバーです。 Canada は、United States および Colorado によって、Canada の子孫から分離されています。 Canada が Alberta のすぐ上になるようにメンバーの順序を変更する場合、Alberta と Brunswick の両方が行セットから除外されます。  
  
```  
SELECT DrillUpMember (   
 {  [Geography].[Geography].[Country].[Canada]   
   ,[Geography].[Geography].[Country].[United States]   
   ,[Geography].[Geography].[State-Province].[Colorado]   
   ,[Geography].[Geography].[State-Province].[Alberta]   
   ,[Geography].[Geography].[State-Province].[Brunswick]    
 }   
 , {[Geography].[Geography].[Country].[Canada]}   
 )   
ON 0   
FROM [Adventure Works]  
```  
  
 3 つの例に示す方法の使用**Hierarchize** Canada メンバーに対するメンバーの順序、およびドリル アップの影響を軽減することができます。  
  
```  
SELECT DrillUpMember (   
 Hierarchize   
  (   
   { [Geography].[Geography].[Country].[Canada]   
    ,[Geography].[Geography].[Country].[United States]   
    ,[Geography].[Geography].[State-Province].[Colorado]   
    ,[Geography].[Geography].[State-Province].[Alberta]   
    ,[Geography].[Geography].[State-Province].[Brunswick]    
   }   
  ), {[Geography].[Geography].[Country].[Canada]}   
 )   
ON 0   
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
