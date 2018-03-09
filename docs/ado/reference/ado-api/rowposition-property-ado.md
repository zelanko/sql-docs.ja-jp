---
title: "RowPosition プロパティ (ADO) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
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
- ADORecordConstruction::put_RowPosition
- ADORecordConstruction::PutRowPosition
- ADORecordConstruction::GetRowPosition
- ADORecordConstruction::RowPosition
- ADORecordConstruction::get_RowPosition
helpviewer_keywords:
- RowPosition property [ADO]
ms.assetid: 9d068fed-39bf-4842-afc3-686a2af2145d
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0e384d850a51cc94439a896040951ec3c23f2f6a
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="rowposition-property-ado"></a>RowPosition プロパティ (ADO)
OLE DB の設定を取得または**RowPosition**オブジェクトから/上、 **ADORecordsetConstruction**オブジェクト。 使用すると**put_RowPosition**を設定する、 **RowPosition** 、結果として得られるオブジェクト**Recordset**オブジェクトが使用、 **RowPosition**オブジェクトを現在の行を決定します。  
  
 読み取りと書き込みが可能です。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT get_RowPosition([out, retval] IUnknown** ppRowPos);  
HRESULT put_RowPosition([in] IUnknown* pRowPos);  
```  
  
## <a name="parameters"></a>パラメーター  
 *ppRowPos*  
 OLE DB へのポインター **RowPosition**オブジェクト。  
  
 *PRowPos*  
 OLE DB **RowPosition**オブジェクト。  
  
## <a name="return-values"></a>戻り値  
 このプロパティのメソッドでは、S_OK および E_FAIL を含む、標準の HRESULT 値を返します。  
  
## <a name="remarks"></a>解説  
 このプロパティ設定されている場合場合、**行セット**上のオブジェクト、 **RowPosition**オブジェクトは異なる、**行セット**上のオブジェクト、 **Recordset**オブジェクト、後者前者をオーバーライドします。 現在、同じ動作が適用されます**章**の**RowPosition**もします。  
  
## <a name="applies-to"></a>適用対象  
 [ADORecordsetConstruction インターフェイス](../../../ado/reference/ado-api/adorecordsetconstruction-interface.md)
