---
title: ディメンション オブジェクト (ADO MD) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Dimension
helpviewer_keywords:
- Dimension object [ADO MD]
ms.assetid: 66adbbd2-23a3-4c19-a91b-84c31309aa1b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 332701caacd2eb4a813e8ec09ff66aa4dc4bf828
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63225785"
---
# <a name="dimension-object-ado-md"></a>Dimension オブジェクト (ADO MD)
1 つまたは複数のメンバーの階層を含む多次元キューブのディメンションの 1 つを表します。  
  
## <a name="remarks"></a>コメント  
 コレクションのプロパティと、**ディメンション**オブジェクトを次を行うことができます。  
  
-   識別、**ディメンション**で、[名前](../../../ado/reference/ado-md-api/name-property-ado-md.md)と[UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md)プロパティ。  
  
-   説明するわかりやすい文字列を返す、**ディメンション**で、[説明](../../../ado/reference/ado-md-api/description-property-ado-md.md)プロパティ。  
  
-   返す、[階層](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md)を構成するオブジェクト、**ディメンション**で、[階層](../../../ado/reference/ado-md-api/hierarchies-collection-ado-md.md)コレクション。  
  
-   標準の ADO を使用して[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)コレクションに関する追加情報を取得、**ディメンション**オブジェクト。  
  
 **プロパティ**コレクションには、プロバイダーが指定したプロパティが含まれています。 次の表は、使用可能な可能性があるプロパティを一覧表示します。 実際のプロパティの一覧は、プロバイダーの実装によって異なる場合があります。 使用可能なプロパティの詳細な一覧については、プロバイダーのドキュメントを参照してください。  
  
|名前|説明|  
|----------|-----------------|  
|CatalogName|このキューブが所属するカタログの名前。|  
|CubeName|キューブの名前。|  
|DefaultHierarchy|既定の階層の一意の名前。|  
|説明|キューブのわかりやすい説明。|  
|DimensionCaption|ラベルまたはキャプションをディメンションに関連付けられています。|  
|DimensionCardinality|ディメンションのメンバーの数。|  
|DimensionGUID|ディメンションの GUID です。|  
|DimensionName|ディメンションの名前。|  
|DimensionOrdinal|キューブを形成するディメンションのグループ内の次元の序数。|  
|DimensionType|ディメンションの種類。|  
|DimensionUniqueName|ディメンションの明確な名前。|  
|SchemaName|このキューブが所属するスキーマの名前。|  
  
 このセクションには、次のトピックが含まれています。  
  
-   [プロパティ、メソッド、およびイベント](../../../ado/reference/ado-md-api/dimension-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [CubeDef の例 (VBScript)](../../../ado/reference/ado-md-api/cubedef-example-vbscript.md)   
 [CubeDef オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)   
 [Dimensions コレクション (ADO MD)](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md)   
 [Hierarchies コレクション (ADO MD)](../../../ado/reference/ado-md-api/hierarchies-collection-ado-md.md)   
 [Properties コレクション (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
