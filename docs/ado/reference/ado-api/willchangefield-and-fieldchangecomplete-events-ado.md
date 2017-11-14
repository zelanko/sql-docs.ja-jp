---
title: "WillChangeField および FieldChangeComplete イベント (ADO) |Microsoft ドキュメント"
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
- FieldChangeComplete
- Recordset::WillChangeField
- Recordset::FieldChangeComplete
- WillChangeField
helpviewer_keywords:
- WillChangeField event [ADO]
- fieldchangecomplete event [ADO]
ms.assetid: 3e49fb89-c45b-4d39-823e-3cc887c59b37
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9d9ce0412a76f34f653273d294e7f8add031a9d9
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="willchangefield-and-fieldchangecomplete-events-ado"></a>WillChangeField および FieldChangeComplete イベント (ADO)
**WillChangeField**保留中の操作が 1 つまたは複数の値を変更する前に、イベントが呼び出された[フィールド](../../../ado/reference/ado-api/field-object.md)内のオブジェクト、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)です。 **FieldChangeComplete**イベントは 1 つ以上の値の後に呼び出されます**フィールド**オブジェクトが変更されています。  
  
## <a name="syntax"></a>構文  
  
```  
  
WillChangeField cFields, Fields, adStatus, pRecordset  
FieldChangeComplete cFields, Fields, pError, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>パラメーター  
 *cFields*  
 A**長い**の数を示す**フィールド**オブジェクト*フィールド*です。  
  
 *フィールド*  
 **WillChangeField**、*フィールド*パラメーターは配列の**バリアント**を格納している**フィールド**元の値を持つオブジェクト。 **FieldChangeComplete**、*フィールド*パラメーターは配列の**バリアント**を格納している**フィールド**値が変更されたオブジェクト.  
  
 *pError*  
 [エラー](../../../ado/reference/ado-api/error-object.md)オブジェクト。 場合に発生したエラーを説明の値*adStatus*は**adStatusErrorsOccurred**です。 それ以外の場合、設定されていません。  
  
 *adStatus*  
 [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md)状態値。  
  
 ときに**WillChangeField**が呼び出されると、このパラメーターに設定されている**adStatusOK**イベントの原因となった操作が成功した場合。 設定されている**adStatusCantDeny**場合、このイベントは、保留中の操作の取り消しを要求できません。  
  
 ときに**FieldChangeComplete**が呼び出されると、このパラメーターに設定されている**adStatusOK**イベントの原因となった操作が成功した場合または**adStatusErrorsOccurred**場合操作に失敗しました。  
  
 前に**WillChangeField**戻り値は、このパラメーターに設定する**adStatusCancel**保留中の操作のキャンセルを要求します。  
  
 前に**FieldChangeComplete**戻り値は、このパラメーターに設定する**adStatusUnwantedEvent**を後続の通知を防ぐためにします。  
  
 *pRecordset*  
 A **Recordset**オブジェクト。 **Recordset**のこのイベントが発生しました。  
  
## <a name="remarks"></a>解説  
 A **WillChangeField**または**FieldChangeComplete**を設定するときに、イベントが発生する可能性があります、[値](../../../ado/reference/ado-api/value-property-ado.md)プロパティは、通話、[更新](../../../ado/reference/ado-api/update-method.md)メソッドフィールドと値の配列パラメーターです。  
  
## <a name="see-also"></a>参照  
 [ADO イベント モデルの例 (vc++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [ADO イベント ハンドラーの概要](../../../ado/guide/data/ado-event-handler-summary.md)

