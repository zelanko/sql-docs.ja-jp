---
title: ResyncEnum |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ResyncEnum
helpviewer_keywords:
- ResyncEnum enumeration [ADO]
ms.assetid: d3df2c90-e570-4c40-a79a-25b3448a009c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: aaf396e8969d490933e26652e18c0c070e030785
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63060971"
---
# <a name="resyncenum"></a>ResyncEnum
呼び出して、基になる値を上書きするかどうかを示す[再同期](../../../ado/reference/ado-api/resync-method.md)します。  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|**adResyncAllValues**|2|既定値です。 データは上書きされ、保留中の更新は取り消されます。|  
|**adResyncUnderlyingValues**|1|データは上書きされず、保留中の更新は取り消されません。|  
  
## <a name="adowfc-equivalent"></a>ADO と WFC と同等  
 パッケージ: **com.ms.wfc.data**  
  
|定数|  
|--------------|  
|AdoEnums.Resync.ALLVALUES|  
|AdoEnums.Resync.UNDERLYINGVALUES|  
  
## <a name="applies-to"></a>適用対象  
 [Resync メソッド](../../../ado/reference/ado-api/resync-method.md)
