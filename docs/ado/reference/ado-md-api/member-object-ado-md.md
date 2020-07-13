---
title: Member オブジェクト (ADO MD) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Member
helpviewer_keywords:
- Member object [ADO MD], members
ms.assetid: 3dedf755-0741-4c3f-8b4e-bff8ff8809c8
author: rothja
ms.author: jroth
ms.openlocfilehash: d4d512d651c8162124c935ffdb260c4abe4ecb14
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82753209"
---
# <a name="member-object-ado-md"></a>Member オブジェクト (ADO MD)
キューブ内のレベルのメンバー、レベルのメンバーの子、またはセルセットの軸に沿った位置のメンバーを表します。  
  
## <a name="remarks"></a>Remarks  
 メンバーのプロパティは、**メンバー**が使用されているコンテキストによって異なります。 [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)の[レベル](../../../ado/reference/ado-md-api/level-object-ado-md.md)の**メンバー**には、現在の**メンバー**から階層内の次の下位レベルにある**メンバー**を返す[Children](../../../ado/reference/ado-md-api/children-property-ado-md.md)プロパティがあります。 [位置](../../../ado/reference/ado-md-api/position-object-ado-md.md)の**メンバー**の場合、**子**コレクションは常に空です。 また、 [Type](../../../ado/reference/ado-md-api/type-property-ado-md.md)プロパティは、**レベル**の**メンバー**にのみ適用されます。  
  
 **Position**の**メンバー**には、[セルセット](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)を表示するときに便利な2つのプロパティがあります。 [Drilleddown](../../../ado/reference/ado-md-api/drilleddown-property-ado-md.md)および[parentsameasprev](../../../ado/reference/ado-md-api/parentsameasprev-property-ado-md.md)。 **レベル**の**メンバー**でこれらのプロパティにアクセスすると、エラーが発生します。  
  
 **レベル**の**メンバー**オブジェクトのコレクションとプロパティを使用して、次の操作を実行できます。  
  
-   [Name](../../../ado/reference/ado-md-api/name-property-ado-md.md)プロパティと[UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md)プロパティを使用して**メンバー**を識別します。  
  
-   [Caption](../../../ado/reference/ado-md-api/caption-property-ado-md.md)プロパティを使用して**メンバー**を表示するときに使用する文字列を返します。  
  
-   [Description](../../../ado/reference/ado-md-api/description-property-ado-md.md)プロパティを持つメジャーまたは数式**メンバー**を表す意味のある文字列を返します。  
  
-   [Type](../../../ado/reference/ado-md-api/type-property-ado-md.md)プロパティを使用して**メンバー**の性質を判断します。  
  
-   [Leveldepth](../../../ado/reference/ado-md-api/leveldepth-property-ado-md.md)プロパティと[leveldepth](../../../ado/reference/ado-md-api/levelname-property-ado-md.md)プロパティを使用して、**メンバー**の**レベル**に関する情報を取得します。  
  
-   [親](../../../ado/reference/ado-md-api/parent-property-ado-md.md)と[子](../../../ado/reference/ado-md-api/children-property-ado-md.md)のプロパティを使用して、[階層](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md)内の関連する**メンバー**を取得します。  
  
-   [Childcount](../../../ado/reference/ado-md-api/childcount-property-ado-md.md)プロパティを使用して**メンバー**の子をカウントします。  
  
-   標準の ADO[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)コレクションを使用して、 **Level**オブジェクトに関する追加情報を取得します。  
  
 [軸](../../../ado/reference/ado-md-api/axis-object-ado-md.md)に沿った**位置**の**メンバー**のコレクションとプロパティを使用して、次の操作を実行できます。  
  
-   [Name](../../../ado/reference/ado-md-api/name-property-ado-md.md)プロパティと[UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md)プロパティを使用して**メンバー**を識別します。  
  
-   [Caption](../../../ado/reference/ado-md-api/caption-property-ado-md.md)プロパティを使用して**メンバー**を表示するときに使用する文字列を返します。  
  
-   [Description](../../../ado/reference/ado-md-api/description-property-ado-md.md)プロパティを持つメジャーまたは数式**メンバー**を表す意味のある文字列を返します。  
  
-   [Leveldepth](../../../ado/reference/ado-md-api/leveldepth-property-ado-md.md)プロパティと[leveldepth](../../../ado/reference/ado-md-api/levelname-property-ado-md.md)プロパティを使用して、**メンバー**の**レベル**に関する情報を取得します。  
  
-   [Childcount](../../../ado/reference/ado-md-api/childcount-property-ado-md.md)プロパティを使用して**メンバー**の子をカウントします。  
  
-   この**メンバー**の直後にある**軸**に少なくとも1つの子があるかどうかを判断するには、 [drilの下](../../../ado/reference/ado-md-api/drilleddown-property-ado-md.md)のプロパティを使用します。  
  
-   この**メンバー**の親が直前の**メンバー**の親と同じであるかどうかを判断するには、 [parentsameasprev](../../../ado/reference/ado-md-api/parentsameasprev-property-ado-md.md)プロパティを使用します。  
  
-   標準の ADO[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)コレクションを使用して、 **Level**オブジェクトに関する追加情報を取得します。  
  
 **Properties**コレクションには、プロバイダーが提供するプロパティが含まれています。 次の表に、使用可能なプロパティを示します。 実際のプロパティリストは、プロバイダーの実装によって異なる場合があります。 使用できるプロパティの詳細な一覧については、プロバイダーのドキュメントを参照してください。  
  
|名前|説明|  
|----------|-----------------|  
|CatalogName|このキューブが所属するカタログの名前。|  
|ChildrenCardinality|メンバーが持つ子の数。|  
|CubeName|キューブの名前。|  
|説明|メンバーのわかりやすい説明。|  
|DimensionUniqueName|[ディメンション](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)の明確な名前です。|  
|HierarchyUniqueName|階層の明確な名前。|  
|LevelNumber|階層のレベルとルートとの間の距離。|  
|LevelUniqueName|レベルの明確な名前。|  
|MemberCaption|メンバーに関連付けられたラベルまたはキャプション。|  
|MemberGUID|メンバーの GUID。|  
|メンバー名|メンバーの名前。|  
|MemberOrdinal|メンバーの序数。|  
|MemberType|メンバーの種類。|  
|MemberUniqueName|メンバーの明確な名前。|  
|ParentCount|このメンバーが持つ親の数。|  
|ParentLevel|メンバーの親のレベル番号。|  
|ParentUniqueName|メンバーの親の明確な名前。|  
|SchemaName|このキューブが所属するスキーマの名前です。|  
  
 ここでは、次のトピックについて説明します。  
  
-   [プロパティ、メソッド、およびイベント](../../../ado/reference/ado-md-api/member-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [カタログの例 (VB)](../../../ado/reference/ado-md-api/catalog-example-vb.md)   
 [Members コレクション (ADO MD)](../../../ado/reference/ado-md-api/members-collection-ado-md.md)   
 [Properties コレクション (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
