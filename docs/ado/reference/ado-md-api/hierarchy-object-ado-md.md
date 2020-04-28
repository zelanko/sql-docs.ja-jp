---
title: Hierarchy オブジェクト (ADO MD) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Hierarchy
helpviewer_keywords:
- Hierarchy object [ADO MD]
ms.assetid: 034af340-ac79-494e-ba5e-2b57da1cb9de
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 35e02e4823d0a3abf245e1885b95176d6350d712
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67949693"
---
# <a name="hierarchy-object-ado-md"></a>Hierarchy オブジェクト (ADO MD)
[ディメンション](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)のメンバーを集計または "ロールアップ" できる1つの方法を表します。 ディメンションは、1つまたは複数の階層に沿って集計できます。  
  
## <a name="remarks"></a>Remarks  
 **Hierarchy**オブジェクトのコレクションとプロパティを使用して、次の操作を実行できます。  
  
-   [Name](../../../ado/reference/ado-md-api/name-property-ado-md.md)プロパティと[UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md)プロパティを使用して、**階層**を識別します。  
  
-   [Description](../../../ado/reference/ado-md-api/description-property-ado-md.md)プロパティを使用して**階層**を説明する意味のある文字列を返します。  
  
-   [レベルコレクションを](../../../ado/reference/ado-md-api/levels-collection-ado-md.md)持つ**階層**を構成する[Level](../../../ado/reference/ado-md-api/level-object-ado-md.md)オブジェクトを返します。  
  
-   標準の ADO[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)コレクションを使用して、 **Hierarchy**オブジェクトに関する追加情報を取得します。  
  
 **Properties**コレクションには、プロバイダーが提供するプロパティが含まれています。 次の表に、使用可能なプロパティを示します。 実際のプロパティリストは、プロバイダーの実装によって異なる場合があります。 使用できるプロパティの詳細な一覧については、プロバイダーのドキュメントを参照してください。  
  
|名前|説明|  
|----------|-----------------|  
|AllMember|階層内のロールアップの最上位レベルにあるメンバー。|  
|CatalogName|このキューブが所属するカタログの名前。|  
|CubeName|キューブの名前。|  
|DefaultMember|この階層の既定のメンバーの一意の名前。|  
|説明|階層についてのわかりやすい説明。|  
|DimensionType|この階層が属するディメンションの種類。|  
|DimensionUniqueName|ディメンションの明確な名前です。|  
|HierarchyCaption|階層に関連付けられたラベルまたはキャプション。|  
|HierarchyCardinality|階層内のメンバーの数。|  
|HierarchyGUID|階層の GUID。|  
|HierarchyName|階層の名前です。|  
|HierarchyUniqueName|階層の明確な名前。|  
|SchemaName|このキューブが所属するスキーマの名前です。|  
  
 ここでは、次のトピックについて説明します。  
  
-   [プロパティ、メソッド、およびイベント](../../../ado/reference/ado-md-api/hierarchy-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [CubeDef の例 (VBScript)](../../../ado/reference/ado-md-api/cubedef-example-vbscript.md)   
 [Dimension オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)   
 [Hierarchy コレクション (ADO MD)](../../../ado/reference/ado-md-api/hierarchies-collection-ado-md.md)   
 [Levels コレクション (ADO MD)](../../../ado/reference/ado-md-api/levels-collection-ado-md.md)   
 [Properties コレクション (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
