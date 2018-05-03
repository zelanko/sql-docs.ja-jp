---
title: EntitySet 要素 (CSDLBI) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: d4703c9e-5594-472e-a85b-0f5bd0d73d6f
caps.latest.revision: 10
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 4e931f1756fc10028f0398c2e33e1f1b7a71aa1f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="entityset-element-csdlbi"></a>EntitySet 要素 (CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  EntitySet 要素は、CSDLBI データ モデル内の特定の種類のエンティティのコレクションを定義します。  
  
 EntitySet では、データ モデルに含まれる各エンティティ タイプを指定する必要があります。 これらのモデル エンティティに関する情報は、Entity 要素型の子エンティティをリストすることで指定します。 詳細については、「[EntityType 要素 &#40;CSDLBI&#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/entitytype-element-csdlbi.md)」を参照してください。  
  
 照合順序や言語などのプロパティは、個別のオブジェクトではなく、EntityContainer のレベルで定義されます。 ただし、モデル内の列およびテキスト属性は、キャプションまたは他の言語での翻訳を持つことができます。  
  
## <a name="elements-and-attributes"></a>要素と属性  
 次の表に、EntitySet を定義する要素と属性を示します。  
  
|属性名|必須かどうか|Description|  
|--------------------|-----------------|-----------------|  
|Caption|いいえ|エンティティ セットについてのわかりやすい説明。|  
|CollectionCaption|いいえ|エンティティの複数形の名前を表す文字列です。|  
|ReferenceName|いいえ|エンティティのマージされていない完全修飾名を含みます。 多次元モデルでは CubeDimension 名に対応します。|  
|[非表示]|いいえ|エンティティが非表示かどうかを示します。 既定ではエンティティは非表示ではありません。|  
  
## <a name="example"></a>例  
 **表形式**  
  
 CSDLBI Version 1.1 における次の例では、AdventureWorks のテーブル モデルで使用される Date テーブルと Geography テーブルの定義を示します。  
  
```  
  
<EntitySet   
   Name="Date"   
   EntityType="Sandbox. Date">  
<bi:EntitySet />  
</EntitySet>  
  
<EntitySet   
   Name="Geography"   
   EntityType="Sandbox.Geography">  
<bi:EntitySet />  
</EntitySet>  
```  
  
## <a name="example"></a>例  
 **多次元**  
  
 CSDLBI Version 1.1 における次の例では、Contoso Retail Operations キューブからの EntitySet 要素をいくつか示します。  
  
```  
  
<EntitySet Name="Outage" EntityType="Sandbox.Outage">  
       <bi:EntitySet />  
</EntitySet>  
  
<EntitySet Name="Store" EntityType="Sandbox.Store">  
     <bi:EntitySet />  
</EntitySet>  
```  
  
## <a name="see-also"></a>参照  
 [CSDL への BI 注釈のテクニカル リファレンス](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/technical-reference-for-bi-annotations-to-csdl.md)  
  
  
