---
title: Stream プロパティ |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADOStreamConstruction::GetStream
- ADOStreamConstruction::PutStream
- ADOStreamConstruction::put_Stream
- ADOStreamConstruction::Stream
- ADOStreamConstruction::get_Stream
helpviewer_keywords:
- Stream property
ms.assetid: 4a44f9f6-0265-4c00-8def-d85b6af923b1
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 0fecd8a1bfed75bd922ed39bd57144b9f32b6bb6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66710740"
---
# <a name="stream-property"></a>Stream プロパティ
OLE DB の設定を取得または**Stream**オブジェクトとの間で、 **ADOStreamConstruction**オブジェクト。  
  
 読み取りと書き込みが可能です。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT get_Stream([out, retval] IUnknown** ppStream);  
HRESULT put_Stream([in] IUnknown* pStream);  
```  
  
## <a name="parameters"></a>パラメーター  
 *ppStream*  
 OLE DB へのポインター **Stream**オブジェクト。  
  
 *pStream*  
 OLE DB **Stream**オブジェクト。  
  
## <a name="return-values"></a>戻り値  
 このプロパティのメソッドでは、標準の HRESULT 値を返します。 これには、S_OK および E_FAIL が含まれます。  
  
## <a name="applies-to"></a>適用対象  
 [ADOStreamConstruction インターフェイス](../../../ado/reference/ado-api/adostreamconstruction-interface.md)
