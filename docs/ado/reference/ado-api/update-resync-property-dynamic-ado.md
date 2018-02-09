---
title: "再同期のプロパティ-動的 (ADO) の更新 |Microsoft ドキュメント"
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
helpviewer_keywords:
- Update Resync property [ADO]
ms.assetid: 8a3bb608-66d7-4128-a3ef-84cb0556de0d
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d6084a0075508c8a9a3658b4a8c694957409376c
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="update-resync-property-dynamic-ado"></a>再同期のプロパティ-動的 (ADO) の更新します。
指定するかどうか、 [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)メソッドは暗黙的な続けている[再同期](../../../ado/reference/ado-api/resync-method.md)メソッド操作と、そのその操作のスコープです。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 1 つ以上を取得または設定、 [ADCPROP_UPDATERESYNC_ENUM](../../../ado/reference/ado-api/adcprop-updateresync-enum.md)値。  
  
## <a name="remarks"></a>解説  
 既に残りの値の組み合わせを表す adResyncAll を除き、ADCPROP_UPDATERESYNC_ENUM の値を組み合わせることができます。  
  
 定数**adResyncConflicts**基になる値として、再同期の値を格納しますが、保留中の変更をオーバーライドしません。  
  
 **再同期を更新**に動的なプロパティが追加、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)コレクションときに、 [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)プロパティに設定**adUseClient**です。  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
