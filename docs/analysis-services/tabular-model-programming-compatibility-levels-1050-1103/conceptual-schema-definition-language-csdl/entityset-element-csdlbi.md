---
title: EntitySet 要素 (CSDLBI) |Microsoft ドキュメント
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5a900dba9a1e78c3dc77648eaf3a5dd1f5b2802b
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34041806"
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
  
  
