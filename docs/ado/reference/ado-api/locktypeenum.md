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
author: rothja
ms.author: jroth
ms.openlocfilehash: e609a51d6b9f42cb6101ff485633302193757fbd
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/28/2020
ms.locfileid: "87242652"
---
# <a name="locktypeenum"></a>LockTypeEnum
編集中にレコードに適用されるロックの種類を指定します。  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|**adLockBatchOptimistic**|4|オプティミスティックバッチ更新を示します。 バッチ更新モードでは必須です。|  
|**adLockOptimistic**|3|オプティミスティックロック、レコードごとのレコードを示します。 プロバイダーはオプティミスティックロックを使用し、 [Update](../../../ado/reference/ado-api/update-method.md)メソッドを呼び出したときにのみレコードをロックします。|  
|**adLockPessimistic**|2|ペシミスティックロック、レコードごとのレコードを示します。 プロバイダーは、レコードを正常に編集するために必要な処理を実行します。通常は、編集後すぐにデータソースのレコードをロックします。|  
|**adLockReadOnly**|1|読み取り専用レコードを示します。 データを変更することはできません。|  
|**adLockUnspecified**|-1|はロックの種類を指定していません。 複製の場合、複製は元と同じロックの種類で作成されます。|  
  
## <a name="adowfc-equivalent"></a>同等の ADO/WFC  
 パッケージ: **com. ms. wfc. データ**  
  
|定数|  
|--------------|  
|AdoEnums.LockType.BATCHOPTIMISTIC|  
|AdoEnums|  
|AdoEnums|  
|AdoEnums|  
|AdoEnums|  
  
## <a name="applies-to"></a>適用対象  

:::row:::
    :::column:::
        [Clone メソッド (ADO)](../../../ado/reference/ado-api/clone-method-ado.md)  
        [LockType プロパティ (ADO)](../../../ado/reference/ado-api/locktype-property-ado.md)  
    :::column-end:::
    :::column:::
        [Open メソッド (ADO Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md)  
        [WillExecute イベント (ADO)](../../../ado/reference/ado-api/willexecute-event-ado.md)  
    :::column-end:::
:::row-end:::
