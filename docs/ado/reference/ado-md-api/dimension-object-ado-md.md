---
title: Dimension オブジェクト (ADO MD) |Microsoft Docs
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
ms.openlocfilehash: f7a13ad87d56f5e7855070d8fe577bb408d6ce9e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67938539"
---
# <a name="dimension-object-ado-md"></a>Dimension オブジェクト (ADO MD)
メンバーの1つ以上の階層を含む多次元キューブのディメンションの1つを表します。  
  
## <a name="remarks"></a>Remarks  
 **ディメンション**オブジェクトのコレクションとプロパティを使用して、次の操作を実行できます。  
  
-   [Name](../../../ado/reference/ado-md-api/name-property-ado-md.md)プロパティと[UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md)プロパティを使用して、**ディメンション**を識別します。  
  
-   [Description](../../../ado/reference/ado-md-api/description-property-ado-md.md)プロパティを使用して、**ディメンション**を説明する意味のある文字列を返します。  
  
-   Hierarchy[コレクションを使用して](../../../ado/reference/ado-md-api/hierarchies-collection-ado-md.md)、**ディメンション**を構成する[階層](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md)オブジェクトを返します。  
  
-   標準の ADO[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)コレクションを使用して、**ディメンション**オブジェクトに関する追加情報を取得します。  
  
 **Properties**コレクションには、プロバイダーが提供するプロパティが含まれています。 次の表に、使用可能なプロパティを示します。 実際のプロパティリストは、プロバイダーの実装によって異なる場合があります。 使用できるプロパティの詳細な一覧については、プロバイダーのドキュメントを参照してください。  
  
|名前|説明|  
|----------|-----------------|  
|CatalogName|このキューブが所属するカタログの名前。|  
|CubeName|キューブの名前。|  
|DefaultHierarchy|既定の階層の一意の名前。|  
|説明|キューブについてのわかりやすい説明。|  
|DimensionCaption|ディメンションに関連付けられているラベルまたはキャプション。|  
|DimensionCardinality|ディメンション内のメンバーの数。|  
|DimensionGUID|ディメンションの GUID。|  
|DimensionName|ディメンションの名前。|  
|DimensionOrdinal|キューブを形成するディメンションのグループ間のディメンションの序数です。|  
|DimensionType|ディメンションの種類。|  
|DimensionUniqueName|ディメンションの明確な名前です。|  
|SchemaName|このキューブが所属するスキーマの名前です。|  
  
 ここでは、次のトピックについて説明します。  
  
-   [プロパティ、メソッド、およびイベント](../../../ado/reference/ado-md-api/dimension-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [CubeDef の例 (VBScript)](../../../ado/reference/ado-md-api/cubedef-example-vbscript.md)   
 [CubeDef オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)   
 [Dimensions コレクション (ADO MD)](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md)   
 [Hierarchy コレクション (ADO MD)](../../../ado/reference/ado-md-api/hierarchies-collection-ado-md.md)   
 [Properties コレクション (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
