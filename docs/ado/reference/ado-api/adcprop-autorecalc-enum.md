---
title: ADCPROP_AUTORECALC_ENUM |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADCPROP_AUTORECALC_ENUM
helpviewer_keywords:
- ADCPROP_AUTORECALC_ENUM [ADO]
ms.assetid: ded4f087-87b9-4efa-8026-bde53d3e9e8a
author: rothja
ms.author: jroth
ms.openlocfilehash: 7b00d507a2ddbe596311e16d51a302f4b0dc0dc5
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82760718"
---
# <a name="adcprop_autorecalc_enum"></a>ADCPROP_AUTORECALC_ENUM
[MSDataShape](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)プロバイダーが階層レコードセットの集計列と計算列を再計算するタイミングを指定します。  
  
 これらの定数は、 **MSDataShape**プロバイダーと**レコードセット**の "**自動**再計算" 動的プロパティでのみ使用されます。動的プロパティは[ADO 動的プロパティインデックス](../../../ado/reference/ado-api/ado-dynamic-property-index.md)で参照され、OLE DB ドキュメントについては、 [Microsoft Cursor service for OLE DB](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md)または[microsoft データ整形サービス](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)に記載されています。  
  
|定数|[値]|説明|  
|--------------|-----------|-----------------|  
|**adRecalcAlways**|1|既定値。 計算列が依存している値が**MSDataShape**プロバイダーによって決定されるたびに再計算されます。|  
|**adRecalcUpFront**|0|は、最初に階層**レコードセット**を作成するときにのみ計算されます。|  
  
## <a name="adowfc-equivalent"></a>同等の ADO/WFC  
 これらの定数には、対応する ADO/WFC がありません。
