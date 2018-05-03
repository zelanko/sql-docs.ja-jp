---
title: メンバー オブジェクト (ADO MD) |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Member
helpviewer_keywords:
- Member object [ADO MD], members
ms.assetid: 3dedf755-0741-4c3f-8b4e-bff8ff8809c8
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9650c6c34d426004f30e22ce7b265bf26bfec77c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="member-object-ado-md"></a>メンバー オブジェクト (ADO MD)
キューブでは、レベルのメンバー、レベルのメンバーまたはセル セットの軸に沿った位置のメンバーの子を表します。  
  
## <a name="remarks"></a>解説  
 プロパティ、**メンバー**が使用されているコンテキストによって異なります。 A**メンバー**の[レベル](../../../ado/reference/ado-md-api/level-object-ado-md.md)で、 [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)が、[子](../../../ado/reference/ado-md-api/children-property-ado-md.md)プロパティを返す、**メンバー**上現在の階層内の次の下位レベル**メンバー**です。 **メンバー**の[位置](../../../ado/reference/ado-md-api/position-object-ado-md.md)、**子**コレクションは常に空です。 また、[型](../../../ado/reference/ado-md-api/type-property-ado-md.md)プロパティにのみ適用されます**メンバー**の**レベル**です。  
  
 A**メンバー**の**位置**は表示するときに、便利な 2 つのプロパティを持つ、[セルセット](../../../ado/reference/ado-md-api/cellset-object-ado-md.md): [DrilledDown](../../../ado/reference/ado-md-api/drilleddown-property-ado-md.md)と[ParentSameAsPrev](../../../ado/reference/ado-md-api/parentsameasprev-property-ado-md.md)です。 これらのプロパティにアクセスした場合、エラーが発生、**メンバー**の**レベル**です。  
  
 コレクションのプロパティと、**メンバー**のオブジェクト、**レベル**次を行うことができます。  
  
-   識別、**メンバー**で、[名前](../../../ado/reference/ado-md-api/name-property-ado-md.md)と[UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md)プロパティです。  
  
-   表示するときに使用する文字列を返す、**メンバー**で、[キャプション](../../../ado/reference/ado-md-api/caption-property-ado-md.md)プロパティです。  
  
-   メジャーまたは式を記述する意味のある文字列を返す**メンバー**で、[説明](../../../ado/reference/ado-md-api/description-property-ado-md.md)プロパティです。  
  
-   種類を特定、**メンバー**で、[型](../../../ado/reference/ado-md-api/type-property-ado-md.md)プロパティです。  
  
-   に関する情報を取得、**レベル**の**メンバー**で、 [LevelDepth](../../../ado/reference/ado-md-api/leveldepth-property-ado-md.md)と[LevelName](../../../ado/reference/ado-md-api/levelname-property-ado-md.md)プロパティです。  
  
-   取得関連**メンバー**で、[階層](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md)で、[親](../../../ado/reference/ado-md-api/parent-property-ado-md.md)と[子](../../../ado/reference/ado-md-api/children-property-ado-md.md)プロパティです。  
  
-   子の数、**メンバー**で、 [ChildCount](../../../ado/reference/ado-md-api/childcount-property-ado-md.md)プロパティです。  
  
-   標準の ADO を使用して[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)に関する追加情報を取得するコレクション、**レベル**オブジェクト。  
  
 コレクションのプロパティと、**メンバー**の**位置**に沿って、[軸](../../../ado/reference/ado-md-api/axis-object-ado-md.md)次を行うことができます。  
  
-   識別、**メンバー**で、[名前](../../../ado/reference/ado-md-api/name-property-ado-md.md)と[UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md)プロパティです。  
  
-   表示するときに使用する文字列を返す、**メンバー**で、[キャプション](../../../ado/reference/ado-md-api/caption-property-ado-md.md)プロパティです。  
  
-   メジャーまたは式を記述する意味のある文字列を返す**メンバー**で、[説明](../../../ado/reference/ado-md-api/description-property-ado-md.md)プロパティです。  
  
-   に関する情報を取得、**レベル**の**メンバー**で、 [LevelDepth](../../../ado/reference/ado-md-api/leveldepth-property-ado-md.md)と[LevelName](../../../ado/reference/ado-md-api/levelname-property-ado-md.md)プロパティです。  
  
-   子の数、**メンバー**で、 [ChildCount](../../../ado/reference/ado-md-api/childcount-property-ado-md.md)プロパティです。  
  
-   使用して、 [DrilledDown](../../../ado/reference/ado-md-api/drilleddown-property-ado-md.md)上には、少なくとも 1 つの子があるかどうかを判断するプロパティ、**軸**この直後**メンバー**です。  
  
-   使用して、 [ParentSameAsPrev](../../../ado/reference/ado-md-api/parentsameasprev-property-ado-md.md)を決定するプロパティかどうかの親で**メンバー**は、直前の親と同じ**メンバー**です。  
  
-   標準の ADO を使用して[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)に関する追加情報を取得するコレクション、**レベル**オブジェクト。  
  
 **プロパティ**コレクションには、プロバイダーが指定したプロパティが含まれています。 次の表は、利用可能なプロパティを一覧表示します。 実際のプロパティの一覧は、プロバイダーの実装によって異なる場合があります。 使用可能なプロパティの完全な一覧については、プロバイダーのドキュメントを参照してください。  
  
|名前|Description|  
|----------|-----------------|  
|CatalogName|このキューブに所属するカタログの名前。|  
|ChildrenCardinality|メンバーが持つ子の数。|  
|CubeName|キューブの名前。|  
|Description|メンバーの説明文です。|  
|DimensionUniqueName|明確な名前、[ディメンション](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)です。|  
|HierarchyUniqueName|階層の明確な名前。|  
|LevelNumber|レベルと階層のルートの距離。|  
|LevelUniqueName|レベルの明確な名前。|  
|MemberCaption|メンバーに関連付けられたラベルまたはキャプション。|  
|MemberGUID|メンバーの GUID。|  
|MemberName|メンバーの名前。|  
|MemberOrdinal|メンバーの序数。|  
|MemberType|メンバーの種類。|  
|MemberUniqueName|メンバーの明確な名前。|  
|ParentCount|このメンバーは、親の数の数。|  
|ParentLevel|メンバーの親のレベル数。|  
|ParentUniqueName|メンバーの親の明確な名前。|  
|SchemaName|このキューブが属しているスキーマの名前。|  
  
 このセクションには、次のトピックが含まれています。  
  
-   [プロパティ、メソッド、およびイベント](../../../ado/reference/ado-md-api/member-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [カタログの例 (VB)](../../../ado/reference/ado-md-api/catalog-example-vb.md)   
 [メンバーのコレクション (ADO MD)](../../../ado/reference/ado-md-api/members-collection-ado-md.md)   
 [Properties コレクション (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
