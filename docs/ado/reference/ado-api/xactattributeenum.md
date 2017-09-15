---
title: "XactAttributeEnum |Microsoft ドキュメント"
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
- XactAttributeEnum
helpviewer_keywords:
- XactAttributeEnum enumeration [ADO]
ms.assetid: e7dcecd3-7dc7-445c-b922-f700c3067fbc
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b150737eb6323e124569193df7b10e52ac08668f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="xactattributeenum"></a>XactAttributeEnum
トランザクション属性を指定します、[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクト。  
  
|定数|値|Description|  
|--------------|-----------|-----------------|  
|**adXactAbortRetaining**|262144|保持中止を呼び出して実行[RollbackTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md)を自動的に新しいトランザクションを開始します。 すべてのプロバイダーは、この動作をサポートします。|  
|**adXactCommitRetaining**|131072|保持コミットを呼び出すことによって実行[CommitTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md)を自動的に新しいトランザクションを開始します。 すべてのプロバイダーは、この動作をサポートします。|  
  
## <a name="adowfc-equivalent"></a>該当するショートカットは ADO/WFC  
 パッケージ: **com.ms.wfc.data**  
  
|定数|  
|--------------|  
|AdoEnums.XactAttribute.ABORTRETAINING|  
|AdoEnums.XactAttribute.COMMITRETAINING|  
  
## <a name="applies-to"></a>適用対象  
 [属性プロパティ (ADO)](../../../ado/reference/ado-api/attributes-property-ado.md)
