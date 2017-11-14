---
title: "IsolationLevelEnum |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
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
- IsolationLevelEnum
helpviewer_keywords:
- IsolationLevelEnum enumeration [ADO]
ms.assetid: 8e17a7bc-b8a3-4ae2-b6c9-ce088ad31fdf
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1f6f18a4cd10c70369d2e0aceb226310d7a5f4ae
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="isolationlevelenum"></a>IsolationLevelEnum
トランザクションの分離のレベルを指定します、[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクト。  
  
|定数|値|Description|  
|--------------|-----------|-----------------|  
|**adXactUnspecified**|-1|プロバイダーを使用している別の分離レベルを指定よりも、レベルを特定できないことを示します。|  
|**adXactChaos**|16|保留中のより高度な分離のトランザクションから変更できません上書きされることを示します。|  
|**adXactBrowse**|256|1 つのトランザクションから表示できることコミットされていない変更の他のトランザクションを示します。|  
|**adXactReadUncommitted**|256|同じ**adXactBrowse**です。|  
|**adXactCursorStability**|4096|1 つのトランザクションから表示できることの変更の他のトランザクションでコミットされた後にのみを示します。|  
|**adXactReadCommitted**|4096|同じ**adXactCursorStability**です。|  
|**adXactRepeatableRead**|65536|1 つのトランザクションから他のトランザクションで行われた変更が表示されないことが、新しいを取得できるそのクエリを再実行を示す**Recordset**オブジェクト。|  
|**adXactIsolated**|1048576|他のトランザクションの分離でトランザクションが実行されたことを示します。|  
|**adXactSerializable**|1048576|同じ**adXactIsolated**です。|  
  
## <a name="adowfc-equivalent"></a>該当するショートカットは ADO/WFC  
 パッケージ: **com.ms.wfc.data**  
  
|定数|  
|--------------|  
|AdoEnums.IsolationLevel.UNSPECIFIED|  
|AdoEnums.IsolationLevel.CHAOS|  
|AdoEnums.IsolationLevel.BROWSE|  
|AdoEnums.IsolationLevel.READUNCOMMITTED|  
|AdoEnums.IsolationLevel.CURSORSTABILITY|  
|AdoEnums.IsolationLevel.READCOMMITTED|  
|AdoEnums.IsolationLevel.REPEATABLEREAD|  
|AdoEnums.IsolationLevel.ISOLATED|  
|AdoEnums.IsolationLevel.SERIALIZABLE|  
  
## <a name="applies-to"></a>適用対象  
 [IsolationLevel プロパティ](../../../ado/reference/ado-api/isolationlevel-property.md)

