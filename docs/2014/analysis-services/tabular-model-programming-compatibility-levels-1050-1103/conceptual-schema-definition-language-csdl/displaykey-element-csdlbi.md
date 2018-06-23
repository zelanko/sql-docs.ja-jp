---
title: DisplayKey 要素 (CSDLBI) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 7d881278-1e77-42e1-8cfc-f1bbd9ec2340
caps.latest.revision: 11
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 907bb04d59225180fad91b63971d578181c6663d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36084176"
---
# <a name="displaykey-element-csdlbi"></a>DisplayKey 要素 (CSDLBI)
  DisplayKey 要素には、全体として厳密な識別子を構成する次の要素の一覧が含まれます。 DisplayKey は EntityType 要素の子としてのみ存在します。 列またはロール エンドを参照できます。  
  
## <a name="elements-and-attributes"></a>要素と属性  
 次の表に DisplayKey 要素の属性を示します。  
  
|名前|必須かどうか|説明|  
|----------|-----------------|-----------------|  
|IsDisplayKey|いいえ|True または False |  
  
## <a name="remarks"></a>コメント  
 この要素はレポート用です。 この属性を適用する要素は、実際のテーブル キーである必要はなく、キーとして提示する要素でかまいません。 ただし、DisplayKey に対して使用する列は一意の値を含む必要があります。  
  
## <a name="example"></a>例  
 **テーブル**  
  
 CSDLBI Version 1.1 における次の例では、テーブルに対して DisplayKey と指定された AdventureWorks サンプル データ モデルの列を示します。  
  
```  
<sample in progress>  
```  
  
## <a name="example"></a>例  
 **多次元**  
  
 CSDLBI Version 1.1 における次の例は、Contoso Operations キューブの表現から抜粋したものです。 このモデルでは、Color 列が Bikes テーブルの表示キーとしてマークされています。  
  
```  
  
<EntityType   
    Name="Bike">  
.. .. ..  
<Property   
    Name="Color"   
    Type="String"   
    MaxLength="Max"   
    Unicode="true"   
    FixedLength="false">  
<bi:Property   
    ContextualNameRule="Context"   
    Alignment="Left" Units="counts"   
    SortDirection="Descending"   
    IsRightToLeft="true"   
    DefaultAggregateFunction="Max" />  
</Property>  
.. .. ..  
<bi:EntityType>  
   <bi:DisplayKey>  
      <bi:MemberRef Name="Color" />  
   </bi:DisplayKey>>  
.. .. ..  
</bi:EntityType>  
</EntityType>  
```  
  
## <a name="see-also"></a>参照  
 [表形式オブジェクト モデルをについてください。](../representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)   
 [CSDLBI の概念](../csdlbi-concepts.md)  
  
  