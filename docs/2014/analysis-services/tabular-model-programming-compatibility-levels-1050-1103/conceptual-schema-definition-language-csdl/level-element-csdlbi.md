---
title: レベルの要素 (CSDLBI) |Microsoft ドキュメント
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
ms.assetid: fdf75c47-77dc-4bdb-9931-8eca198fdb88
caps.latest.revision: 10
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: b63309bec7a37ef7953eb1a358ed317b366c4bee
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36085085"
---
# <a name="level-element-csdlbi"></a>Level 要素 (CSDLBI)
  Level 要素は、階層内の単一のレベルを定義する複合型です  
  
## <a name="elements-and-attributes"></a>要素と属性  
 次の表に、Level 要素を定義する要素と属性を示します。  
  
|名前|必須かどうか|説明|  
|----------|-----------------|-----------------|  
|Source|はい|プロパティ参照のコンテナー。|  
|PropertyRef|はい|インスタンス プロパティへの参照。 キャプション、名前、参照名などの他のレベル属性は、参照されるインスタンス プロパティから取得できます。 その場合は Level 要素でこれらを指定する必要はありません。|  
  
## <a name="remarks"></a>コメント  
 テーブル モデルでの階層の詳細については、「[Hierarchy 要素 &#40;CSDLBI&#41;](hierarchy-element-csdlbi.md)」を参照してください。  
  
## <a name="example"></a>例  
 **テーブル**  
  
 CSDLBI Version 1.1 における次の例では、AdventureWorks のテーブル モデル サンプルの階層における複数のレベルの定義を示します。  
  
```  
  
<bi:Hierarchy Name="Category">  
   <bi:Level Name="CategoryName">  
     <bi:Source>  
       <bi:PropertyRef Name="CategoryName" />  
     </bi:Source>  
   </bi:Level>  
   <bi:Level Name="ProductName">  
     <bi:Source>  
       <bi:PropertyRef Name="ProductName" />  
     </bi:Source>  
   </bi:Level>  
</bi:Hierarchy>  
```  
  
## <a name="example"></a>例  
 **多次元**  
  
 CSDLBI Version 1.1 における次の例は、Contoso Operations キューブからの複数のレベルを持つ階層を示します。  
  
```  
<bi:Hierarchy   
   Name="Product_Hierarchy"   
   Caption="Product Hierarchy"   
   ReferenceName="Product Hierarchy">  
     <bi:Documentation>  
        <bi:Summary>DESCRIPTION_ProductModelCateg_Hierarchies</bi:Summary>  
     </bi:Documentation>  
  
     <bi:Level Name="ProductLine">  
        <bi:Source>  
        <bi:PropertyRef Name="ProductLine" />  
        </bi:Source>  
     </bi:Level>  
  
     <bi:Level Name="ModelName">  
        <bi:Source>  
        <bi:PropertyRef Name="ModelName" />  
        </bi:Source>  
     </bi:Level>  
</bi:Hierarchy>  
```  
  
## <a name="see-also"></a>参照  
 [表形式オブジェクト モデルをについてください。](../representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)   
 [DAX の親子階層を扱う関数をについてください。](https://msdn.microsoft.com/library/gg492192(v=sql.120).aspx)   
 [構成、&#40;すべて&#41;属性階層のレベル](../../multidimensional-models/database-dimensions-configure-the-all-level-for-attribute-hierarchies.md)  
  
  