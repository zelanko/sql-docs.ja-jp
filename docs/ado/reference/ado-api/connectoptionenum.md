---
title: ConnectOptionEnum |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ConnectOptionEnum
helpviewer_keywords:
- ConnectOptionEnum enumeration [ADO]
ms.assetid: bff07eeb-dee3-4e4e-9b2d-d56061ea744d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f9df3fd695e9bf281133dabf436e5e8b5de7e0b1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47646620"
---
# <a name="connectoptionenum"></a>ConnectOptionEnum
指定するかどうか、[オープン](../../../ado/reference/ado-api/open-method-ado-connection.md)のメソッド、[接続](../../../ado/reference/ado-api/connection-object-ado.md)(同期的に) 接続が確立された後、またはオブジェクトを返す必要があります (非同期)。  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|**adAsyncConnect**|16|非同期的に接続を開きます。 [ConnectComplete](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md)イベントを使用して、接続が使用可能な場合があります。|  
|**adConnectUnspecified**|-1|既定値です。 同期的に接続を開きます。|  
  
## <a name="adowfc-equivalent"></a>ADO と WFC と同等  
 パッケージ: **com.ms.wfc.data**  
  
|定数|  
|--------------|  
|AdoEnums.ConnectOption.ASYNCCONNECT|  
|AdoEnums.ConnectOption.CONNECTUNSPECIFIED|  
  
## <a name="applies-to"></a>適用対象  
 [Open メソッド (ADO Connection)](../../../ado/reference/ado-api/open-method-ado-connection.md)
