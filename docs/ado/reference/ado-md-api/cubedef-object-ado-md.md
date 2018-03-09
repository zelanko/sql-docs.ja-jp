---
title: "CubeDef オブジェクト (ADO MD) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- CubeDef
helpviewer_keywords:
- CubeDef object [ADO MD]
ms.assetid: feb2581c-fc41-471c-bb69-29f8a55fda70
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ea97010f67e571ddf9ddfb1dcc1cf36e38769710
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="cubedef-object-ado-md"></a>CubeDef オブジェクト (ADO MD)
関連するディメンションのセットを含んでいる、マルチ ディメンション スキーマからキューブを表します。  
  
## <a name="remarks"></a>解説  
 コレクションのプロパティと、 **CubeDef**オブジェクトを次を行うことができます。  
  
-   識別、 **CubeDef**で、[名前](../../../ado/reference/ado-md-api/name-property-ado-md.md)プロパティです。  
  
-   使用してキューブを表す文字列を返す、[説明](../../../ado/reference/ado-md-api/description-property-ado-md.md)プロパティです。  
  
-   使用してキューブを構成するディメンションを返す、[ディメンション](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md)コレクション。  
  
-   に関する追加情報を取得、 **CubeDef**標準 ado[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)コレクション。  
  
 **プロパティ**コレクションには、プロバイダーが指定したプロパティが含まれています。 次の表は、利用可能なプロパティを一覧表示します。 実際のプロパティの一覧は、プロバイダーの実装によって異なる場合があります。 使用可能なプロパティの完全な一覧については、プロバイダーのドキュメントを参照してください。  
  
|名前|Description|  
|----------|-----------------|  
|CatalogName|このキューブに所属するカタログの名前。|  
|CreatedOn|キューブの作成日時。|  
|CubeGUID|キューブの GUID です。|  
|CubeName|キューブの名前。|  
|CubeType|キューブの種類。|  
|DataUpdatedBy|最後のデータ更新を実行するユーザーのユーザー ID。|  
|Description|キューブのわかりやすい説明。|  
|LastSchemaUpdate|スキーマの最終更新日時。|  
|SchemaName|このキューブが属しているスキーマの名前。|  
|SchemaUpdatedBy|スキーマの最終更新を実行するユーザーのユーザー ID。|  
  
 このセクションには、次のトピックが含まれています。  
  
-   [プロパティ、メソッド、およびイベント](../../../ado/reference/ado-md-api/cubedef-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [CubeDef 例 (VBScript)](../../../ado/reference/ado-md-api/cubedef-example-vbscript.md)   
 [カタログ オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/catalog-object-ado-md.md)   
 [CubeDefs コレクション (ADO MD)](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md)   
 [Dimensions コレクション (ADO MD)](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md)   
 [Properties コレクション (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
