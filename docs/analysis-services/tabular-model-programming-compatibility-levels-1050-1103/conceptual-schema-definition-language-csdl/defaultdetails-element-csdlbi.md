---
title: "DefaultDetails 要素 (CSDLBI) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/07/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
ms.assetid: 05a08baa-23cc-4011-9c2e-f60a20bb87da
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 8010e9c0412b50c8d65a67c87c176bff02d1a887
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="defaultdetails-element-csdlbi"></a>DefaultDetails 要素 (CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]DefaultDetails 要素は、"既定のフィールド セット"、テーブルの列を定義するプロパティ参照のリストを表します。 各プロパティが参照できるのは、1 つのメジャーまたは 1 つの列だけです。  
  
## <a name="elements-and-attributes"></a>要素と属性  
 次の表に、DefaultDetails 要素を定義する要素と属性を示します。  
  
|[オブジェクト名]|必須かどうか|Description|  
|----------|-----------------|-----------------|  
|DefaultDetailsPosition|不可|コレクション内の存在と位置を示す正の整数。|  
  
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
 [レベルを 1050 から 1103 表形式オブジェクト モデルの互換性を理解します。](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)   
 [CSDLBI の概念](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/csdlbi-concepts.md)  
  
  
