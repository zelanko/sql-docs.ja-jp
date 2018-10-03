---
title: StayInSync プロパティ |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset20::StayInSync
- Recordset20::put_StayInSync
- Recordset20::PutStayInSync
- Recordset20::get_StayInSync
- Recordset20::GetStayInSync
helpviewer_keywords:
- StayInSync property
ms.assetid: 502d69b5-dc9a-455d-b115-a03bd39a552b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 50cf569f6e0af5e753cca7fba030b8fc2caa4a86
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47805781"
---
# <a name="stayinsync-property"></a>StayInSync プロパティ
階層構造内に示します[レコード セット](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトかどうか、基になる子レコードへの参照 (、 *」の章*)、親の行の位置が変わったときに変更します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 設定または取得を**ブール**値。 既定値は **True**です。 場合**True**、章が更新されます親**レコード セット**場合、オブジェクトの変更行位置; **False**章は引き続き、前の章でデータを参照してください場合でも、親**Recordset**オブジェクトには、行の位置が変更されました。  
  
## <a name="remarks"></a>コメント  
 このプロパティでサポートされるものなど、階層レコード セットに適用されます、 [Microsoft Data Shaping Service for OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)、親に設定する必要がありますと**レコード セット**、子の前に**レコード セット**を取得します。 このプロパティは、階層レコード セットの移動を簡略化します。  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [StayInSync プロパティの例 (VB)](../../../ado/reference/ado-api/stayinsync-property-example-vb.md)   
 [Microsoft のデータ シェイプの OLE DB (ADO サービス プロバイダー) のサービス](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)
