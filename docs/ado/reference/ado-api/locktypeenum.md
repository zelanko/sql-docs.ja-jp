---
title: LockTypeEnum |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- LockTypeEnum
helpviewer_keywords:
- LockTypeEnum enumeration [ADO]
ms.assetid: d2894eaf-4450-4ace-aa51-c8b875fd3010
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 9dbc6e9e78fc08be2bba08d0fbeb897496a2058b
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2019
ms.locfileid: "66694936"
---
# <a name="locktypeenum"></a>LockTypeEnum
編集中に、レコードに適用されるロックの種類を指定します。  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|**adLockBatchOptimistic**|4|オプティミスティックな一括更新を示します。 バッチ更新モードで必要です。|  
|**adLockOptimistic**|3|レコードごとのオプティミスティック ロックを示します。 プロバイダーを使用してオプティミスティック ロックを呼び出した場合にのみ、レコードのロック、 [Update](../../../ado/reference/ado-api/update-method.md)メソッド。|  
|**adLockPessimistic**|2|レコードごとの排他的ロックを示します。 プロバイダーでは何が成功したレコードの編集、通常は編集後すぐに、データ ソースのレコードをロックすることを確認するために必要です。|  
|**adLockReadOnly**|1|読み取り専用レコードを示します。 データを変更することはできません。|  
|**adLockUnspecified**|-1|ロックの種類を指定しません。 クローンが元と同じ種類のロックで、複製が作成されます。|  
  
## <a name="adowfc-equivalent"></a>ADO と WFC と同等  
 パッケージ: **com.ms.wfc.data**  
  
|定数|  
|--------------|  
|AdoEnums.LockType.BATCHOPTIMISTIC|  
|AdoEnums.LockType.OPTIMISTIC|  
|AdoEnums.LockType.PESSIMISTIC|  
|AdoEnums.LockType.READONLY|  
|AdoEnums.LockType.UNSPECIFIED|  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[Clone メソッド (ADO)](../../../ado/reference/ado-api/clone-method-ado.md)|[LockType プロパティ (ADO)](../../../ado/reference/ado-api/locktype-property-ado.md)|  
|[Open メソッド (ADO Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md)|[WillExecute イベント (ADO)](../../../ado/reference/ado-api/willexecute-event-ado.md)|
