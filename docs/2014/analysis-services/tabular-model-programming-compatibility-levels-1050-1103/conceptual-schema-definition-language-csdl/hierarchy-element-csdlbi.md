---
title: Hierarchy 要素 (CSDLBI) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: 9debb638-1b28-401b-9499-8f63943863e9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 34ef944610a9e3b52fec600b3da5e1f9b06790bf
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48129252"
---
# <a name="hierarchy-element-csdlbi"></a>Hierarchy 要素 (CSDLBI)
  Hierarchy 要素はテーブル内のフィールドの論理的なコンテナーであり、相互にリンクして階層を形成できます。 Hierarchy 要素は CSDL Member 要素から派生し、ビジネス インテリジェンス データ モデルで作成される階層をサポートするように拡張されています。  
  
## <a name="elements-and-attributes"></a>要素と属性  
 次の表に、Hierarchy 要素を定義する要素と属性を示します。  
  
|名前|必須かどうか|説明|  
|----------|-----------------|-----------------|  
|ドキュメント|いいえ|階層の説明。|  
|Level|はい|階層内で使用される列を定義する 1 つまたは複数の Level 要素。<br /><br /> 「[Level 要素 &#40;CSDLBI&#41;](level-element-csdlbi.md)」を参照してください。|  
  
## <a name="remarks"></a>コメント  
 テーブル モデルでは、同じテーブル内の列間の親子関係を指定することにより階層を作成します。 詳細については、「[階層 (SSAS テーブル)](../../tabular-models/hierarchies-ssas-tabular.md)」を参照してください。  
  
## <a name="example"></a>例  
 **テーブル**  
  
 CSDLBI Version 1.1 における次の例では、Products テーブルに追加された AdventureWorks サンプル モデルの階層を示します。  
  
```  
  
<bi:Hierarchy Name="Categoryy">  
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
  
 CSDLBI Version 1.1 における次の例では、Contoso Retail Operations キューブからの階層を示します。  
  
```  
  
<bi:Hierarchy Name="Product_Hierarchy" Caption="Product Hierarchy" ReferenceName="Product Hierarchy">  
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
  
  
