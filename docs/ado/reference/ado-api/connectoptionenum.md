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
ms.openlocfilehash: 819fb89d7f8c43e76ba9260a72fafa68084bf880
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67933443"
---
# <a name="connectoptionenum"></a>ConnectOptionEnum
接続の確立後に (同期的に)、またはそれ以前 (非同期) に[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクトの[Open](../../../ado/reference/ado-api/open-method-ado-connection.md)メソッドを返すかどうかを指定します。  
  
|常時|値|[説明]|  
|--------------|-----------|-----------------|  
|**adAsyncConnect**|16|接続を非同期的に開きます。 接続が使用可能かどうかを判断するには、 [Connectcomplete](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md)イベントを使用できます。|  
|**指定された Adの場合**|-1|既定。 接続を同期的に開きます。|  
  
## <a name="adowfc-equivalent"></a>同等の ADO/WFC  
 パッケージ: **com. ms. wfc. データ**  
  
|常時|  
|--------------|  
|AdoEnums ConnectOption|  
|AdoEnums ConnectOption.|  
  
## <a name="applies-to"></a>適用対象  
 [Open メソッド (ADO Connection)](../../../ado/reference/ado-api/open-method-ado-connection.md)
