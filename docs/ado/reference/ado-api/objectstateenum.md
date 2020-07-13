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
author: rothja
ms.author: jroth
ms.openlocfilehash: 3f233104501a17f384eb837d5e7390705a44ddc4
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82762301"
---
# <a name="objectstateenum"></a>ObjectStateEnum
オブジェクトが開いているか閉じられているか、データソースに接続しているか、コマンドを実行しているか、データを取得しているかを指定します。  
  
|定数|[値]|説明|  
|--------------|-----------|-----------------|  
|**adStateClosed**|0|オブジェクトが閉じていることを示します。|  
|**adStateOpen**|1|オブジェクトが開いていることを示します。|  
|**adStateConnecting**|2|オブジェクトが接続していることを示します。|  
|**adStateExecuting**|4|オブジェクトがコマンドを実行していることを示します。|  
|**adStateFetching**|8|オブジェクトの行が取得されていることを示します。|  
  
## <a name="adowfc-equivalent"></a>同等の ADO/WFC  
 パッケージ: **com. ms. wfc. データ**  
  
|定数|  
|--------------|  
|AdoEnums を終了しました。|  
|AdoEnums を開きます。|  
|AdoEnums。接続しています。|  
|AdoEnums を実行しています。|  
|AdoEnums を取得します。|  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[State プロパティ (ADO MD)](../../../ado/reference/ado-md-api/state-property-ado-md.md)|[State プロパティ (ADO)](../../../ado/reference/ado-api/state-property-ado.md)|
