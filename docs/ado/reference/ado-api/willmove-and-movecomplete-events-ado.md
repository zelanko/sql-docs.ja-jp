---
title: 移動イベントと MoveComplete イベント (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset::MoveComplete
- WillMove
- MoveComplete
- Recordset::WillMove
helpviewer_keywords:
- MoveComplete event [ADO]
- WillMove event [ADO]
ms.assetid: 1a3d1042-4f30-4526-a0c7-853c242496db
author: rothja
ms.author: jroth
ms.openlocfilehash: a714b0c8f6d41060dfe66e898f01d7ce1037e516
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82764443"
---
# <a name="willmove-and-movecomplete-events-ado"></a>WillMove および MoveComplete イベント (ADO)
"イベントの**移動**" は、保留中の操作が[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)内の現在の位置を変更する前に呼び出されます。 **MoveComplete**イベントは、**レコードセット**内の現在の位置が変更された後に呼び出されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
WillMove adReason, adStatus, pRecordset  
MoveComplete adReason, pError, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>パラメーター  
 *adReason*  
 このイベントの理由を指定する[Eventreason 列挙](../../../ado/reference/ado-api/eventreasonenum.md)値。 この値には、 **Adrsnmovefirst**、 **adrsnmovefirst**、 **adrsnmovefirst**、 **adRsnMovePrevious**、 **Adrsnmovefirst**、または**adrsnmovefirst**を指定できます。  
  
 *pError*  
 [エラー](../../../ado/reference/ado-api/error-object.md)オブジェクトです。 *Adstatus*の値が**adstatuserrorて**いる場合に発生したエラーについて説明します。それ以外の場合、パラメーターは設定されません。  
  
 *adStatus*  
 [Eventstatusenum](../../../ado/reference/ado-api/eventstatusenum.md)状態の値です。  
  
 を呼び**出すと、** イベントの原因となった操作が成功した場合、このパラメーターは**adstatusok**に設定されます。 このイベントが保留中の操作の取り消しを要求できない場合は、 **Adstatuscantdeny**に設定されます。  
  
 **MoveComplete**が呼び出されると、このパラメーターは、イベントの原因となった操作が成功した場合は**adstatusok**に、操作が失敗した場合は**Adstatuserror curred**に設定されます。  
  
 が**戻る前に**、このパラメーターを**adstatuscancel**に設定して保留中の操作の取り消しを要求するか、このパラメーターを**adStatusUnwantedEvent**に設定して、後続の通知が行われないようにします。  
  
 **MoveComplete**が返される前に、このパラメーターを**adStatusUnwantedEvent**に設定して、後続の通知が行われないようにします。  
  
 *pRecordset*  
 [レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトです。 このイベントが発生した**レコードセット**。  
  
## <a name="remarks"></a>Remarks  
 [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md)、 [Move](../../../ado/reference/ado-api/move-method-ado.md)、 [MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)、 [MoveLast](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)、 [MoveNext](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)、 [MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)、 [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md)、および[Requery](../../../ado/reference/ado-api/requery-method.md)の各**レコードセット**操作によって、 **MoveComplete**イベントが**発生する可能性**があります。 これらのイベントは、 [Filter](../../../ado/reference/ado-api/filter-property.md)、 [Index](../../../ado/reference/ado-api/index-property.md)、 [Bookmark](../../../ado/reference/ado-api/bookmark-property-ado.md)、 [AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md)、および[AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md)の各プロパティによって発生することがあります。 これらのイベントは、子**レコード**セットに**レコードセット**イベントが関連付けられていて、親**レコードセット**が移動された場合にも発生します。  
  
 *AdReason*パラメーターを含むイベントのイベント通知を完全に停止するには、使用可能な*adReason*値ごとに*adstatus*パラメーターを**adStatusUnwantedEvent**に設定する必要があります。  
  
## <a name="see-also"></a>参照  
 [ADO Events モデルの例 (VC + +)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [ADO イベントハンドラーの概要](../../../ado/guide/data/ado-event-handler-summary.md)   
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
