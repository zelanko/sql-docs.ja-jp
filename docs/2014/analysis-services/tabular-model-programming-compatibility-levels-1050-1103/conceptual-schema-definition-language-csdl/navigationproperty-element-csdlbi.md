---
title: NavigationProperty 要素 (CSDLBI) |Microsoft Docs
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
ms.assetid: a36b4d3b-6a6c-489b-8a46-2e6b925b568f
caps.latest.revision: 9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 24fe0a9aab029226757cc84ef70e4e8da898e9c5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37287968"
---
# <a name="navigationproperty-element-csdlbi"></a>NavigationProperty 要素 (CSDLBI)
  NavigationProperty 要素は、CSDL Member の種類を拡張する複合型で、ビジネス インテリジェンス データ モデルでの移動をサポートします。  
  
> [!WARNING]  
>  この要素は報告用であり、変更または操作することはできません。  
  
## <a name="elements-and-attributes"></a>要素と属性  
 次の表に、NavigationProperty 要素を定義する要素と属性を示します。  
  
|名前|必須かどうか|説明|  
|----------|-----------------|-----------------|  
|CollectionCaption|いいえ|ナビゲーション プロパティのインスタンスのセットを参照するための複数形の名前。<br /><br /> この属性が省略されると、ベース メンバーの Caption 属性が使用されます。|  
  
## <a name="example"></a>例  
 **テーブル**  
  
 次の例では、テーブル モデルの Product SubCategory テーブルと Product テーブルの間のリンクを記述するナビゲーション プロパティを CSDLBI Version 1.1 で示します。  
  
```  
  
<NavigationProperty   
    Name="Product_Sub_Category_ProductSubcategoryKey"      
    Relationship="Sandbox.Product_Product_Sub_Category_Product_Sub_Category_ProductSubcategoryKey"  
     FromRole="Product_ProductSubcategoryKey"   
    ToRole="Product_Sub_Category_ProductSubcategoryKey">  
<bi:NavigationProperty   
     ReferenceName="Product Sub-Category_ProductSubcategoryKey" />  
</NavigationProperty>  
```  
  
## <a name="example"></a>例  
 **多次元**  
  
 次の例では、Contoso Operations キューブで 2 つのテーブル間のリレーションシップを記述するナビゲーション プロパティを CSDLBI Version 1.1 で示します。 このリレーションシップが、Bike Category テーブルと Product Subcategory テーブルを接続しています。  
  
```  
  
<NavigationProperty   
     Name="BikeSubcategory_ProductSubcategoryKey"   
     Relationship="Sandbox.Bike_BikeSubcategory_BikeSubcategory_ProductSubcategoryKey"   
     FromRole="Bike_ProductSubcategoryKey"   
     ToRole="BikeSubcategory_ProductSubcategoryKey">  
   <bi:NavigationProperty />  
</NavigationProperty>  
```  
  
## <a name="see-also"></a>参照  
 [テーブル オブジェクト モデルについて](../representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)  
  
  
