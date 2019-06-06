---
title: ObjectStateEnum |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ObjectStateEnum
helpviewer_keywords:
- ObjectStateEnum enumeration [ADO]
ms.assetid: 32746558-097b-4749-989e-519aadf7e3f4
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 41b72647af357bc73eb3e9a2f8c3063f2275f6a6
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2019
ms.locfileid: "66707191"
---
# <a name="objectstateenum"></a>ObjectStateEnum
オブジェクトがオープンかクローズは、コマンドの実行またはデータを取得するデータ ソースに接続するかどうかを指定します。  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|**adStateClosed**|0|オブジェクトが閉じられたことを示します。|  
|**adStateOpen**|1|オブジェクトが開かれていることを示します。|  
|**adStateConnecting**|2|オブジェクトが接続することを示します。|  
|**adStateExecuting**|4|オブジェクトのコマンドが実行されていることを示します。|  
|**adStateFetching**|8|オブジェクトの行が取得されていることを示します。|  
  
## <a name="adowfc-equivalent"></a>ADO と WFC と同等  
 パッケージ: **com.ms.wfc.data**  
  
|定数|  
|--------------|  
|AdoEnums.ObjectState.CLOSED|  
|AdoEnums.ObjectState.OPEN|  
|AdoEnums.ObjectState.CONNECTING|  
|AdoEnums.ObjectState.EXECUTING|  
|AdoEnums.ObjectState.FETCHING|  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[State プロパティ (ADO MD)](../../../ado/reference/ado-md-api/state-property-ado-md.md)|[State プロパティ (ADO)](../../../ado/reference/ado-api/state-property-ado.md)|
