---
description: ADO MD オブジェクト
title: ADO MD オブジェクト |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- ADO MD, objects
- objects [ADO MD]
ms.assetid: 2a32e873-3282-4520-a7ed-89493f1da80e
author: rothja
ms.author: jroth
ms.openlocfilehash: 54e7eae0aaab754dbc57f1001263ea20c0bd8999
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88441354"
---
# <a name="ado-md-objects"></a>ADO MD オブジェクト

|Object|説明|  
|-|-|  
|[軸](../../../ado/reference/ado-md-api/axis-object-ado-md.md)|1つ以上のディメンションの選択されたメンバーを含むセルセットの位置指定軸またはフィルター軸を表します。|  
|[カタログ](../../../ado/reference/ado-md-api/catalog-object-ado-md.md)|多次元データプロバイダー (.MDP) に固有の多次元スキーマ情報 (つまり、キューブおよび基になるディメンション、階層、レベル、およびメンバー) が含まれています。|  
|[Cell (セル)](../../../ado/reference/ado-md-api/cell-object-ado-md.md)|セルセットに含まれる軸の座標の交差部分にあるデータを表します。|  
|[セルセット](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)|多次元クエリの結果を表します。 これは、キューブまたは他のセルセットから選択されたセルのコレクションです。|  
|[CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)|多次元スキーマから、関連するディメンションのセットを含むキューブを表します。|  
|[ディメンション](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)|メンバーの1つ以上の階層を含む多次元キューブのディメンションの1つを表します。|  
|[Hierarchy](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md)|ディメンションのメンバーを集計または "ロールアップ" できる1つの方法を表します。 ディメンションは、1つまたは複数の階層に沿って集計できます。|  
|[Level](../../../ado/reference/ado-md-api/level-object-ado-md.md)|にはメンバーのセットが含まれており、各メンバーは階層内で同じランクを持ちます。|  
|[メンバー](../../../ado/reference/ado-md-api/member-object-ado-md.md)|キューブ内のレベルのメンバー、レベルのメンバーの子、またはセルセットの軸に沿った位置のメンバーを表します。|  
|[Position](../../../ado/reference/ado-md-api/position-object-ado-md.md)|軸に沿って点を定義する、異なる次元の1つ以上のメンバーのセットを表します。|  
  
 また、 **カタログ** オブジェクトは、標準の ado ライブラリに含まれる ado **Connection** オブジェクトに接続されています。  
  
|Object|説明|  
|------------|-----------------|  
|[接続](../../../ado/reference/ado-api/connection-object-ado.md)|データ ソースへの開いた接続を表します。|  
  
 これらのオブジェクト間のリレーションシップは、 [ADO MD オブジェクトモデル](../../../ado/reference/ado-md-api/ado-md-object-model.md)で示されています。  
  
 多くの ADO MD オブジェクトを対応するコレクションに含めることができます。 たとえば、 [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)オブジェクトは、**カタログ**の[cubedefs](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md)コレクションに含めることができます。 詳細については、「 [ADO MD コレクション](../../../ado/reference/ado-md-api/ado-md-collections.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [ADO MD API リファレンス](../../../ado/reference/ado-md-api/ado-md-api-reference.md)   
 [ADO MD コード例](../../../ado/reference/ado-md-api/ado-md-code-examples.md)   
 [ADO MD コレクション](../../../ado/reference/ado-md-api/ado-md-collections.md)   
 [ADO MD 列挙定数](../../../ado/reference/ado-md-api/ado-md-enumerated-constants.md)   
 [ADO MD メソッド](../../../ado/reference/ado-md-api/ado-md-methods.md)   
 [ADO MD オブジェクトモデル](../../../ado/reference/ado-md-api/ado-md-object-model.md)   
 [ADO MD のプロパティ](../../../ado/reference/ado-md-api/ado-md-properties.md)
