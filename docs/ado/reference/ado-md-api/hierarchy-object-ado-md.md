---
title: Hierarchy オブジェクト (ADO MD) |Microsoft ドキュメント
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
- Hierarchy
helpviewer_keywords:
- Hierarchy object [ADO MD]
ms.assetid: 034af340-ac79-494e-ba5e-2b57da1cb9de
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1904398172f9a7b1eaad57e3c4cda11a00fad22e
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="hierarchy-object-ado-md"></a>Hierarchy オブジェクト (ADO MD)
1 つの方法を表すのメンバー、[ディメンション](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)集約または「ロール アップされます」。 ディメンションは、1 つまたは複数の階層に従って集計できます。  
  
## <a name="remarks"></a>解説  
 コレクションのプロパティと、**階層**オブジェクトを次を行うことができます。  
  
-   識別、**階層**で、[名前](../../../ado/reference/ado-md-api/name-property-ado-md.md)と[UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md)プロパティです。  
  
-   説明するわかりやすい文字列を返す、**階層**で、[説明](../../../ado/reference/ado-md-api/description-property-ado-md.md)プロパティです。  
  
-   返す、[レベル](../../../ado/reference/ado-md-api/level-object-ado-md.md)を構成するオブジェクト、**階層**で、[レベル](../../../ado/reference/ado-md-api/levels-collection-ado-md.md)コレクション。  
  
-   標準の ADO を使用して[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)に関する追加情報を取得するコレクション、**階層**オブジェクト。  
  
 **プロパティ**コレクションには、プロバイダーが指定したプロパティが含まれています。 次の表は、利用可能なプロパティを一覧表示します。 実際のプロパティの一覧は、プロバイダーの実装によって異なる場合があります。 使用可能なプロパティの完全な一覧については、プロバイダーのドキュメントを参照してください。  
  
|名前|Description|  
|----------|-----------------|  
|AllMember|階層でプログラムのロールアップの最高レベルにあるメンバー。|  
|CatalogName|このキューブに所属するカタログの名前。|  
|CubeName|キューブの名前。|  
|DefaultMember|この階層の既定のメンバーの一意の名前。|  
|Description|階層のわかりやすい説明。|  
|DimensionType|この階層が所属するディメンションの種類。|  
|DimensionUniqueName|ディメンションの明確な名前。|  
|HierarchyCaption|階層に関連付けられたラベルまたはキャプション。|  
|HierarchyCardinality|階層内のメンバーの数。|  
|HierarchyGUID|階層の GUID です。|  
|HierarchyName|階層の名前です。|  
|HierarchyUniqueName|階層の明確な名前。|  
|SchemaName|このキューブが属しているスキーマの名前。|  
  
 このセクションには、次のトピックが含まれています。  
  
-   [プロパティ、メソッド、およびイベント](../../../ado/reference/ado-md-api/hierarchy-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [CubeDef 例 (VBScript)](../../../ado/reference/ado-md-api/cubedef-example-vbscript.md)   
 [ディメンション オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)   
 [Hierarchies コレクション (ADO MD)](../../../ado/reference/ado-md-api/hierarchies-collection-ado-md.md)   
 [Levels コレクション (ADO MD)](../../../ado/reference/ado-md-api/levels-collection-ado-md.md)   
 [Properties コレクション (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
