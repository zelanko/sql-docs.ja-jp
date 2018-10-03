---
title: DefaultDetails 要素 (CSDLBI) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: 05a08baa-23cc-4011-9c2e-f60a20bb87da
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fa1fcc05363cf356d5895c0d5e6f62c037f45fb2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48120862"
---
# <a name="defaultdetails-element-csdlbi"></a>DefaultDetails 要素 (CSDLBI)
  DefaultDetails 要素は、テーブルの列の「既定のフィールド セット」を一緒に定義するプロパティ参照のリストを表します。 各プロパティが参照できるのは、1 つのメジャーまたは 1 つの列だけです。  
  
## <a name="elements-and-attributes"></a>要素と属性  
 次の表に、DefaultDetails 要素を定義する要素と属性を示します。  
  
|名前|必須かどうか|説明|  
|----------|-----------------|-----------------|  
|DefaultDetailsPosition|いいえ|コレクション内の存在と位置を示す正の整数。|  
  
## <a name="example"></a>例  
 **テーブル**  
  
 CSDLBI Version 1.1 における次の例は、AdventureWorks サンプル データ モデルから抜粋したものです。 Employee テーブル (タイトル) には既定の列セットが 1 つ存在します。 しかし 3 つの列が、Product テーブルに対する既定のフィールド セットとして定義されています。  
  
```  
  
<EntityType   
    Name="DimEmployee">  
....  
   <bi:DefaultDetails>  
      <bi:MemberRef Name="Title" />  
   </bi:DefaultDetails>  
.....  
<EntityType   
    Name="Products">  
.....  
   <bi:DefaultDetails>  
      <bi:MemberRef Name="Color" />  
      <bi:MemberRef Name="DealerPrice" />  
      <bi:MemberRef Name="Status" />  
   </bi:DefaultDetails>  
  
```  
  
## <a name="example"></a>例  
 **多次元**  
  
 CSDLBI Version 1.1 における次の例は、Contoso Operations キューブの Bike テーブルの定義から抜粋したものです。 この注釈は、他の表示列が指定されていなくても Color 列が表示されることを示しています。  
  
```  
  
<EntityType Name="Bike">  
   <Key>  
   <PropertyRef Name="RowNumber" />  
   </Key>  
....  
<bi:EntityType>  
   <bi:DisplayKey>  
      <bi:MemberRef Name="Color" />  
   </bi:DisplayKey>  
   <bi:DefaultDetails>  
      <bi:MemberRef Name="Color" />  
   </bi:DefaultDetails>  
   <bi:SortMembers>  
      <bi:MemberRef Name="Color" />  
   </bi:SortMembers>  
....  
</bi:EntityType>  
</EntityType>  
```  
  
## <a name="see-also"></a>参照  
 [表形式オブジェクト モデルをについてください。](../representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)   
 [CSDLBI の概念](../csdlbi-concepts.md)  
  
  
