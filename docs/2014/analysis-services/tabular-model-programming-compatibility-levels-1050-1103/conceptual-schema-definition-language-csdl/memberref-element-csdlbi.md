---
title: MemberRef 要素 (CSDLBI) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: 399aaa34-896c-48e7-aacb-18564f31b568
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bb0912afd99c7a4859ca4750a3ba1b66fdecd5f5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48205719"
---
# <a name="memberref-element-csdlbi"></a>MemberRef 要素 (CSDLBI)
  MemberRef 要素は、参照の対象であるプロパティの名前を示します。  
  
## <a name="elements-and-attributes"></a>要素と属性  
 次の表に、MemberRef 要素を定義する要素と属性を示します。  
  
|名前|必須かどうか|説明|  
|----------|-----------------|-----------------|  
|名前|はい|MemberRef 要素に含まれるプロパティの名前。|  
  
## <a name="memberrefs-element"></a>MemberRefs 要素  
 MemberRefs は、それぞれのメンバーが MemberRef 要素に含まれるメンバーのコレクションを定義する複合型です。  
  
 次の表では、MemberRef の要素と属性を示します。  
  
|名前|必須かどうか|説明|  
|----------|-----------------|-----------------|  
|MemberRef|はい|メンバー参照を表す文字列。|  
  
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
 [CSDL への BI 注釈のテクニカル リファレンス](technical-reference-for-bi-annotations-to-csdl.md)  
  
  
