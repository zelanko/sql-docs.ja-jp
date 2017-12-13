---
title: "MemberRef 要素 (CSDLBI) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
ms.assetid: 399aaa34-896c-48e7-aacb-18564f31b568
caps.latest.revision: "5"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 924e945003026241f29f532ffd64393ec4623414
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="memberref-element-csdlbi"></a>MemberRef 要素 (CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]MemberRef 要素は、参照の対象となっているプロパティの名前を識別します。  
  
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
 **テーブル**  
  
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
  
  
