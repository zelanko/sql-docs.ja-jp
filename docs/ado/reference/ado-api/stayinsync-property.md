---
description: StayInSync プロパティ
title: StayInSync Property |Microsoft Docs
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 7bd35cbd24dadef9d6a9468f65bc85f95169d0cb
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88441884"
---
# <a name="stayinsync-property"></a>StayInSync プロパティ
親の行位置が変更されたときに、基になる子レコード (つまり、*チャプター*) への参照が変更されるかどうかを階層[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトで示します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 **ブール**値を設定または返します。 既定値は **True** です。 **True**の場合、親の**Recordset**オブジェクトが行の位置を変更すると、チャプターが更新されます。**False**の場合、親の**Recordset**オブジェクトが行の位置を変更した場合でも、チャプターは前の章のデータを参照し続けます。  
  
## <a name="remarks"></a>解説  
 このプロパティは、 [OLE DB 用の Microsoft データ整形サービス](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)によってサポートされるレコードセットなどの階層的なレコードセットに適用されます。子**レコード**セットを取得する前に、親**レコード**セットに設定する必要があります。 このプロパティは、階層的なレコードセットの移動を簡略化します。  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [StayInSync プロパティの例 (VB)](../../../ado/reference/ado-api/stayinsync-property-example-vb.md)   
 [OLE DB 用の Microsoft データ整形サービス (ADO サービスプロバイダー)](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)
