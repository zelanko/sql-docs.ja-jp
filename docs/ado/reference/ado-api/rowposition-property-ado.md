---
title: RowPosition プロパティ (ADO) |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
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
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0b852ff5fab54e11f3fd39c2ca92266c95587987
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35281341"
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
  
## <a name="remarks"></a>コメント  
 このプロパティ設定されている場合場合、**行セット**上のオブジェクト、 **RowPosition**オブジェクトは異なる、**行セット**上のオブジェクト、 **Recordset**オブジェクト、後者前者をオーバーライドします。 現在、同じ動作が適用されます**章**の**RowPosition**もします。  
  
## <a name="applies-to"></a>適用対象  
 [ADORecordsetConstruction インターフェイス](../../../ado/reference/ado-api/adorecordsetconstruction-interface.md)
