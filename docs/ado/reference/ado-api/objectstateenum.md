---
title: "ObjectStateEnum |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- ObjectStateEnum
helpviewer_keywords:
- ObjectStateEnum enumeration [ADO]
ms.assetid: 32746558-097b-4749-989e-519aadf7e3f4
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: be8153e48ce652acd713633114e6a21d4a22721a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="objectstateenum"></a>ObjectStateEnum
オブジェクトがオープンかクローズは、コマンドを実行するか、データを取得するデータ ソースに接続するかどうかを指定します。  
  
|定数|値|Description|  
|--------------|-----------|-----------------|  
|**取得のみ**|0|オブジェクトが閉じられたことを示します。|  
|**可能です。**|1|オブジェクトが開かれていることを示します。|  
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
