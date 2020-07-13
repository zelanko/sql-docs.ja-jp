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
author: rothja
ms.author: jroth
ms.openlocfilehash: fa372f05a80290e907298a0969d9eb9f14355f90
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82762603"
---
# <a name="connectoptionenum"></a>ConnectOptionEnum
接続の確立後に (同期的に)、またはそれ以前 (非同期) に[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクトの[Open](../../../ado/reference/ado-api/open-method-ado-connection.md)メソッドを返すかどうかを指定します。  
  
|定数|[値]|説明|  
|--------------|-----------|-----------------|  
|**adAsyncConnect**|16|接続を非同期的に開きます。 接続が使用可能かどうかを判断するには、 [Connectcomplete](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md)イベントを使用できます。|  
|**指定された Adの場合**|-1|既定値。 接続を同期的に開きます。|  
  
## <a name="adowfc-equivalent"></a>同等の ADO/WFC  
 パッケージ: **com. ms. wfc. データ**  
  
|定数|  
|--------------|  
|AdoEnums ConnectOption|  
|AdoEnums ConnectOption.|  
  
## <a name="applies-to"></a>適用対象  
 [Open メソッド (ADO Connection)](../../../ado/reference/ado-api/open-method-ado-connection.md)
