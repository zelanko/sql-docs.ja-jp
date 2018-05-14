---
title: MemberRef 要素 (CSDLBI) |Microsoft ドキュメント
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 79b6f2684dabcb45cfddac626bc2a6aa140298f3
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="memberref-element-csdlbi"></a>MemberRef 要素 (CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  MemberRef 要素は、参照の対象であるプロパティの名前を示します。  
  
## <a name="elements-and-attributes"></a>要素と属性  
 次の表に、MemberRef 要素を定義する要素と属性を示します。  
  
|名前|必須かどうか|Description|  
|----------|-----------------|-----------------|  
|名前|可|MemberRef 要素に含まれるプロパティの名前。|  
  
## <a name="memberrefs-element"></a>MemberRefs 要素  
 MemberRefs は、それぞれのメンバーが MemberRef 要素に含まれるメンバーのコレクションを定義する複合型です。  
  
 次の表では、MemberRef の要素と属性を示します。  
  
|名前|必須かどうか|Description|  
|----------|-----------------|-----------------|  
|MemberRef|可|メンバー参照を表す文字列。|  
  
## <a name="example"></a>例  
 **表形式**  
  
 CSDLBI Version 1.1 における次の例では、Products テーブルを定義する AdventureWorks サンプル データ モデルの一部を示します。 MemberRef 要素が、モデルの既定のフィールド セットに含まれる各列に対して使用されています。  
  
```  
  
<bi:EntityType>  
   <bi:DefaultDetails>  
     <bi:MemberRef Name="Color" />  
     <bi:MemberRef Name="DealerPrice" />  
     <bi:MemberRef Name="Status" />  
   </bi:DefaultDetails>  
  
```  
  
## <a name="example"></a>例  
 **多次元**  
  
 CSDLBI Version 1.1 における次の例では、Bikes テーブルを定義する Contoso Operations キューブの一部を示します。 この例では MemberRef 要素が、レポートで既定のフィールド セットとして使用される列名を指定するために使用されています。また別の MemberRef 要素が、並べ替え順序を指定する列を参照するために使用されています。  
  
```  
  
<bi:DefaultDetails>  
   <bi:MemberRef Name="Color" />  
</bi:DefaultDetails>  
  
<bi:SortMembers>  
   <bi:MemberRef Name="Color" />  
</bi:SortMembers>  
  
```  
  
## <a name="see-also"></a>参照  
 [CSDL への BI 注釈のテクニカル リファレンス](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/technical-reference-for-bi-annotations-to-csdl.md)  
  
  
