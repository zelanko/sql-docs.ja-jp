---
title: Level オブジェクト (ADO MD) |Microsoft Docs
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
author: rothja
ms.author: jroth
ms.openlocfilehash: e1ee7ad05f05d2eb77d7d705200c52ddf3f01146
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82753846"
---
# <a name="level-object-ado-md"></a>Level オブジェクト (ADO MD)
にはメンバーのセットが含まれており、各メンバーは階層内で同じランクを持ちます。  
  
## <a name="remarks"></a>Remarks  
 **Level**オブジェクトのコレクションとプロパティを使用して、次の操作を実行できます。  
  
-   [Name](../../../ado/reference/ado-md-api/name-property-ado-md.md)プロパティと[UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md)プロパティを使用して、**レベル**を識別します。  
  
-   [キャプション](../../../ado/reference/ado-md-api/caption-property-ado-md.md)プロパティを使用して**レベル**を表示するときに使用する文字列を返します。  
  
-   [Description](../../../ado/reference/ado-md-api/description-property-ado-md.md)プロパティを使用して、**レベル**を説明する意味のある文字列を返します。  
  
-   [メンバー](../../../ado/reference/ado-md-api/members-collection-ado-md.md)コレクションを使用して、**レベル**を構成する[メンバー](../../../ado/reference/ado-md-api/member-object-ado-md.md)オブジェクトを返します。  
  
-   [Depth](../../../ado/reference/ado-md-api/depth-property-ado-md.md)プロパティを使用して、**レベル**のルートからレベル数を返します。  
  
-   標準の ADO[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)コレクションを使用して、 **Level**オブジェクトに関する追加情報を取得します。  
  
 **Properties**コレクションには、プロバイダーが提供するプロパティが含まれています。 次の表に、使用可能なプロパティを示します。 実際のプロパティリストは、プロバイダーの実装によって異なる場合があります。 使用できるプロパティの詳細な一覧については、プロバイダーのドキュメントを参照してください。  
  
|名前|説明|  
|----------|-----------------|  
|CatalogName|このキューブが所属するカタログの名前。|  
|CubeName|キューブの名前。|  
|説明|レベルのわかりやすい説明。|  
|DimensionUniqueName|[ディメンション](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)の明確な名前です。|  
|HierarchyUniqueName|階層の明確な名前。|  
|LevelCaption|レベルに関連付けられているラベルまたはキャプション。|  
|LevelCardinality|レベル内のメンバーの数。|  
|LevelGUID|レベルの GUID。|  
|LevelName|レベルの名前。|  
|LevelNumber|階層のレベルとルートとの間の距離。|  
|LevelType|レベルの種類。|  
|LevelUniqueName|レベルの明確な名前。|  
|SchemaName|このキューブが所属するスキーマの名前です。|  
  
 ここでは、次のトピックについて説明します。  
  
-   [プロパティ、メソッド、およびイベント](../../../ado/reference/ado-md-api/level-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [CubeDef の例 (VBScript)](../../../ado/reference/ado-md-api/cubedef-example-vbscript.md)   
 [Hierarchy オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md)   
 [Levels コレクション (ADO MD)](../../../ado/reference/ado-md-api/levels-collection-ado-md.md)   
 [Members コレクション (ADO MD)](../../../ado/reference/ado-md-api/members-collection-ado-md.md)   
 [Properties コレクション (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
