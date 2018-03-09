---
title: "ResyncEnum |Microsoft ドキュメント"
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
f1_keywords:
- ResyncEnum
helpviewer_keywords:
- ResyncEnum enumeration [ADO]
ms.assetid: d3df2c90-e570-4c40-a79a-25b3448a009c
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4aecc0ca8d53aa4eb1986b55c178943a3acf752f
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="resyncenum"></a>ResyncEnum
呼び出しによって基になる値を上書きするかどうかを示す[再同期](../../../ado/reference/ado-api/resync-method.md)です。  
  
|定数|[値]|Description|  
|--------------|-----------|-----------------|  
|**adResyncAllValues**|2|既定値です。 データは上書きされ、保留中の更新が取り消されます。|  
|**adResyncUnderlyingValues**|1|データは上書きされず、保留中の更新は取り消されません。|  
  
## <a name="adowfc-equivalent"></a>該当するショートカットは ADO/WFC  
 パッケージ: **com.ms.wfc.data**  
  
|定数|  
|--------------|  
|AdoEnums.Resync.ALLVALUES|  
|AdoEnums.Resync.UNDERLYINGVALUES|  
  
## <a name="applies-to"></a>適用対象  
 [Resync メソッド](../../../ado/reference/ado-api/resync-method.md)
