---
title: 上位の要素 (CSDLBI) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: fdf75c47-77dc-4bdb-9931-8eca198fdb88
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8b932ac5fac719be29bda37f134f9beb06d1483f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48104782"
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
 [DAX の親子階層の機能の理解](https://msdn.microsoft.com/library/gg492192(v=sql.120).aspx)   
 [構成、&#40;すべて&#41;属性階層のレベル](../../multidimensional-models/database-dimensions-configure-the-all-level-for-attribute-hierarchies.md)  
  
  
