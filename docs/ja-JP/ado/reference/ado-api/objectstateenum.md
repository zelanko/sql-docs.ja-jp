---
title: ObjectStateEnum |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ObjectStateEnum
helpviewer_keywords:
- ObjectStateEnum enumeration [ADO]
ms.assetid: 32746558-097b-4749-989e-519aadf7e3f4
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 72faa0a53bb7eb24fc1011112c9c2aa171f91129
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="objectstateenum"></a>ObjectStateEnum
オブジェクトがオープンかクローズは、コマンドを実行するか、データを取得するデータ ソースに接続するかどうかを指定します。  
  
|定数|値|Description|  
|--------------|-----------|-----------------|  
|**adStateClosed**|0|オブジェクトが閉じられたことを示します。|  
|**adStateOpen**|1|オブジェクトが開かれていることを示します。|  
|**adStateConnecting**|2|オブジェクトが接続することを示します。|  
|**adStateExecuting**|4|オブジェクトが、コマンドを実行することを示します。|  
|**adStateFetching**|8|オブジェクトの行が取得されていることを示します。|  
  
## <a name="adowfc-equivalent"></a>該当するショートカットは ADO/WFC  
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
