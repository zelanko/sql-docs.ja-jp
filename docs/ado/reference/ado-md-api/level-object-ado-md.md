---
title: レベルのオブジェクト (ADO MD) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Level
helpviewer_keywords:
- Level object [ADO MD]
ms.assetid: 37815869-ed30-45fd-9aea-0a986c1b305c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 27e789c4eb34ed275d6f18f62325287febb73422
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47734560"
---
# <a name="level-object-ado-md"></a>Level オブジェクト (ADO MD)
それぞれが階層内で同じランクを持つメンバーのセットが含まれています。  
  
## <a name="remarks"></a>コメント  
 コレクションのプロパティと、**レベル**オブジェクトを次を行うことができます。  
  
-   識別、**レベル**で、[名前](../../../ado/reference/ado-md-api/name-property-ado-md.md)と[UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md)プロパティ。  
  
-   表示するときに使用する文字列を返す、**レベル**で、[キャプション](../../../ado/reference/ado-md-api/caption-property-ado-md.md)プロパティ。  
  
-   説明するわかりやすい文字列を返す、**レベル**で、[説明](../../../ado/reference/ado-md-api/description-property-ado-md.md)プロパティ。  
  
-   返す、[メンバー](../../../ado/reference/ado-md-api/member-object-ado-md.md)を構成するオブジェクト、**レベル**で、[メンバー](../../../ado/reference/ado-md-api/members-collection-ado-md.md)コレクション。  
  
-   ルートからレベルの数を返す、**レベル**で、[深さ](../../../ado/reference/ado-md-api/depth-property-ado-md.md)プロパティ。  
  
-   標準の ADO を使用して[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)コレクションに関する追加情報を取得、**レベル**オブジェクト。  
  
 **プロパティ**コレクションには、プロバイダーが指定したプロパティが含まれています。 次の表は、使用可能な可能性があるプロパティを一覧表示します。 実際のプロパティの一覧は、プロバイダーの実装によって異なる場合があります。 使用可能なプロパティの詳細な一覧については、プロバイダーのドキュメントを参照してください。  
  
|名前|説明|  
|----------|-----------------|  
|CatalogName|このキューブが所属するカタログの名前。|  
|CubeName|キューブの名前。|  
|説明|レベルのわかりやすい説明。|  
|DimensionUniqueName|明確な名前、[ディメンション](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)します。|  
|HierarchyUniqueName|階層の明確な名前。|  
|LevelCaption|ラベルまたはキャプション、レベルに関連付けられています。|  
|LevelCardinality|レベル内のメンバーの数。|  
|LevelGUID|レベルの GUID です。|  
|LevelName|レベルの名前。|  
|LevelNumber|レベルと階層のルート間の距離。|  
|LevelType|レベルの型。|  
|LevelUniqueName|明確なレベルの名前。|  
|SchemaName|このキューブが所属するスキーマの名前。|  
  
 このセクションには、次のトピックが含まれています。  
  
-   [プロパティ、メソッド、およびイベント](../../../ado/reference/ado-md-api/level-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [CubeDef の例 (VBScript)](../../../ado/reference/ado-md-api/cubedef-example-vbscript.md)   
 [Hierarchy オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md)   
 [Levels コレクション (ADO MD)](../../../ado/reference/ado-md-api/levels-collection-ado-md.md)   
 [Members コレクション (ADO MD)](../../../ado/reference/ado-md-api/members-collection-ado-md.md)   
 [Properties コレクション (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
