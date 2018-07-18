---
title: EntitySet 要素 (CSDLBI) |Microsoft Docs
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
ms.assetid: d4703c9e-5594-472e-a85b-0f5bd0d73d6f
caps.latest.revision: 9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d8b1e7438714807260b4e317e9367ff77f9916df
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37314572"
---
# <a name="entityset-element-csdlbi"></a>EntitySet 要素 (CSDLBI)
  EntitySet 要素は、CSDLBI データ モデル内の特定の種類のエンティティのコレクションを定義します。  
  
 EntitySet では、データ モデルに含まれる各エンティティ タイプを指定する必要があります。 これらのモデル エンティティに関する情報は、Entity 要素型の子エンティティをリストすることで指定します。 詳細については、「[EntityType 要素 &#40;CSDLBI&#41;](entitytype-element-csdlbi.md)」を参照してください。  
  
 照合順序や言語などのプロパティは、個別のオブジェクトではなく、EntityContainer のレベルで定義されます。 ただし、モデル内の列およびテキスト属性は、キャプションまたは他の言語での翻訳を持つことができます。  
  
## <a name="elements-and-attributes"></a>要素と属性  
 次の表に、EntitySet を定義する要素と属性を示します。  
  
|属性名|必須かどうか|説明|  
|--------------------|-----------------|-----------------|  
|[キャプション]|いいえ|エンティティ セットについてのわかりやすい説明。|  
|CollectionCaption|いいえ|エンティティの複数形の名前を表す文字列です。|  
|ReferenceName|いいえ|エンティティのマージされていない完全修飾名を含みます。 多次元モデルでは CubeDimension 名に対応します。|  
|[非表示]|いいえ|エンティティが非表示かどうかを示します。 既定ではエンティティは非表示ではありません。|  
  
## <a name="example"></a>例  
 **テーブル**  
  
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
 [CSDL への BI 注釈のテクニカル リファレンス](technical-reference-for-bi-annotations-to-csdl.md)  
  
  
