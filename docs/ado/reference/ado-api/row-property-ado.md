---
description: Row プロパティ (ADO)
title: Row プロパティ (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADORecordConstruction::PutRow
- ADORecordConstruction::GetRow
- ADORecordConstruction::get_Row
- ADORecordConstruction::Row
- ADORecordConstruction::put_Row
helpviewer_keywords:
- Row property [ADO]
ms.assetid: 21019d89-2dd1-4a26-ac6f-384b81d66949
author: rothja
ms.author: jroth
ms.openlocfilehash: 3048bf470ed27adb3fb3ceaaef3c7658c1fb93fb
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2020
ms.locfileid: "88777631"
---
# <a name="row-property-ado"></a>Row プロパティ (ADO)
[ADORecordConstruction Interface](./adorecordconstruction-interface.md)オブジェクトのまたはから OLE DB **Row**オブジェクトを取得します。値の設定もできます。 **Put_Row**を使用して**行**オブジェクトを設定すると、行が ADO**レコード**オブジェクトに変換されます。  
  
## <a name="readwritesyntax"></a>読み取り/書き込み。文  
  
```  
HRESULT get_Row([out, retval] IUnknown** ppRow);  
HRESULT put_Row([in] IUnknown* pRow);  
```  
  
## <a name="parameters"></a>パラメーター  
 *ppRow*  
 OLE DB **Row** オブジェクトへのポインター。  
  
 *PRow*  
 OLE DB **Row** オブジェクト。  
  
## <a name="return-values"></a>戻り値  
 このプロパティメソッドは、S_OK および E_FAIL を含む標準の HRESULT 値を返します。  
  
## <a name="applies-to"></a>適用対象  
 [ADORecordConstruction インターフェイス](./adorecordconstruction-interface.md)