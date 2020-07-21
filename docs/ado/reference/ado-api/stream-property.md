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
author: rothja
ms.author: jroth
ms.openlocfilehash: cdcd6d9fb734f50c110a3e59e9d24874ea71b974
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82759600"
---
# <a name="stream-property"></a>Stream プロパティ
**ADOStreamConstruction**オブジェクトからの OLE DB**ストリーム**オブジェクトを取得します。値の設定もできます。  
  
 読み取りと書き込みが可能です。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT get_Stream([out, retval] IUnknown** ppStream);  
HRESULT put_Stream([in] IUnknown* pStream);  
```  
  
## <a name="parameters"></a>パラメーター  
 *ppStream*  
 OLE DB**ストリーム**オブジェクトへのポインター。  
  
 *pStream*  
 OLE DB**ストリーム**オブジェクト。  
  
## <a name="return-values"></a>戻り値  
 このプロパティメソッドは、標準の HRESULT 値を返します。 これには、S_OK と E_FAIL が含まれます。  
  
## <a name="applies-to"></a>適用対象  
 [ADOStreamConstruction インターフェイス](../../../ado/reference/ado-api/adostreamconstruction-interface.md)
