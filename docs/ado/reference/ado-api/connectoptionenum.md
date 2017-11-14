---
title: "ConnectOptionEnum |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
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
- ConnectOptionEnum
helpviewer_keywords:
- ConnectOptionEnum enumeration [ADO]
ms.assetid: bff07eeb-dee3-4e4e-9b2d-d56061ea744d
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 582f85d3ce45071cd283f05f5d595e10b5d1614c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="connectoptionenum"></a>ConnectOptionEnum
指定するかどうか、[開く](../../../ado/reference/ado-api/open-method-ado-connection.md)のメソッド、[接続](../../../ado/reference/ado-api/connection-object-ado.md)(同期的に)、接続が確立された後、またはオブジェクトを返す必要があります (非同期)。  
  
|定数|値|Description|  
|--------------|-----------|-----------------|  
|**adAsyncConnect**|16|非同期的に、接続を開きます。 [ConnectComplete](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md)イベントを使用して、接続が利用可能な場合を決定することがあります。|  
|**adConnectUnspecified**|-1|既定値です。 同期的に、接続を開きます。|  
  
## <a name="adowfc-equivalent"></a>該当するショートカットは ADO/WFC  
 パッケージ: **com.ms.wfc.data**  
  
|定数|  
|--------------|  
|AdoEnums.ConnectOption.ASYNCCONNECT|  
|AdoEnums.ConnectOption.CONNECTUNSPECIFIED|  
  
## <a name="applies-to"></a>適用対象  
 [Open メソッド (ADO 接続)](../../../ado/reference/ado-api/open-method-ado-connection.md)

