---
title: "ADO MD オブジェクト |Microsoft ドキュメント"
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
helpviewer_keywords:
- ADO MD, objects
- objects [ADO MD]
ms.assetid: 2a32e873-3282-4520-a7ed-89493f1da80e
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9967930e6ee7ff1310a1ea331fb972f93d902f88
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="ado-md-objects"></a>ADO MD オブジェクト
|||  
|-|-|  
|[軸](../../../ado/reference/ado-md-api/axis-object-ado-md.md)|1 つまたは複数のディメンションの選択したメンバーを含むセル セットのフィルター軸または位置指定を表します。|  
|[Catalog](../../../ado/reference/ado-md-api/catalog-object-ado-md.md)|多次元データ プロバイダー (MDP) に固有のマルチ ディメンション スキーマ情報 (つまり、キューブと基になるディメンション、階層、レベル、およびメンバー) が含まれています。|  
|[セル](../../../ado/reference/ado-md-api/cell-object-ado-md.md)|セル セットに含まれる軸座標の交差部分にデータを表します。|  
|[セル セット](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)|多次元クエリの結果を表します。 これは、キューブまたはその他のセルセットから選択したセルのコレクションです。|  
|[CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)|関連するディメンションのセットを含んでいる、マルチ ディメンション スキーマからキューブを表します。|  
|[ディメンション](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)|1 つまたは複数のメンバーの階層を含む、多次元キューブのディメンションの 1 つを表します。|  
|[階層](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md)|ディメンションのメンバーを集計または「ロール アップされます」の 1 つの方法を表します ディメンションは、1 つまたは複数の階層に従って集計できます。|  
|[レベル](../../../ado/reference/ado-md-api/level-object-ado-md.md)|それぞれが、階層内で同じランクを持つメンバーのセットが含まれています。|  
|[メンバー](../../../ado/reference/ado-md-api/member-object-ado-md.md)|キューブでは、レベルのメンバー、レベルのメンバーまたはセル セットの軸に沿った位置のメンバーの子を表します。|  
|[[位置]](../../../ado/reference/ado-md-api/position-object-ado-md.md)|軸に沿ったポイントを定義するさまざまなディメンションの 1 つまたは複数のメンバーのセットを表します。|  
  
 また、**カタログ**ADO にオブジェクトが接続されている**接続**オブジェクト、標準の ADO ライブラリに含まれています。  
  
|オブジェクト|Description|  
|------------|-----------------|  
|[接続](../../../ado/reference/ado-api/connection-object-ado.md)|データ ソースへの接続を開くを表します。|  
  
 これらのオブジェクト間のリレーションシップの図解は、 [ADO MD オブジェクト モデル](../../../ado/reference/ado-md-api/ado-md-object-model.md)です。  
  
 ADO MD オブジェクトの多くは、対応するコレクションに含まれることができます。 たとえば、 [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)オブジェクトに格納できる、 [CubeDefs](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md)のコレクション、**カタログ**です。 詳細については、次を参照してください。 [ADO MD コレクション](../../../ado/reference/ado-md-api/ado-md-collections.md)です。  
  
## <a name="see-also"></a>参照  
 [ADO MD API リファレンス](../../../ado/reference/ado-md-api/ado-md-api-reference.md)   
 [ADO MD コードの例](../../../ado/reference/ado-md-api/ado-md-code-examples.md)   
 [ADO MD コレクション](../../../ado/reference/ado-md-api/ado-md-collections.md)   
 [ADO MD 列挙定数](../../../ado/reference/ado-md-api/ado-md-enumerated-constants.md)   
 [ADO MD メソッド](../../../ado/reference/ado-md-api/ado-md-methods.md)   
 [ADO MD オブジェクト モデル](../../../ado/reference/ado-md-api/ado-md-object-model.md)   
 [ADO MD のプロパティ](../../../ado/reference/ado-md-api/ado-md-properties.md)
