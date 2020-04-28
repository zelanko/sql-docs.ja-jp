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
ms.openlocfilehash: 4a872ee5f4af49d9fbe97621a5d2549fd9472202
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67931241"
---
# <a name="resyncenum"></a>ResyncEnum
再[同期](../../../ado/reference/ado-api/resync-method.md)の呼び出しによって基になる値を上書きするかどうかを指定します。  
  
|Constant|値|説明|  
|--------------|-----------|-----------------|  
|**adResyncAllValues**|2|既定値。 データを上書きします。保留中の更新は取り消されます。|  
|**adResyncUnderlyingValues**|1|はデータを上書きしません。保留中の更新は取り消されません。|  
  
## <a name="adowfc-equivalent"></a>同等の ADO/WFC  
 パッケージ: **com. ms. wfc. データ**  
  
|Constant|  
|--------------|  
|AdoEnums. ALLVALUES|  
|AdoEnums. UNDERLYINGVALUES|  
  
## <a name="applies-to"></a>適用対象  
 [Resync メソッド](../../../ado/reference/ado-api/resync-method.md)
