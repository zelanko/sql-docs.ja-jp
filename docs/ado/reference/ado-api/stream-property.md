---
title: "プロパティをストリーミング |Microsoft ドキュメント"
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
- ADOStreamConstruction::GetStream
- ADOStreamConstruction::PutStream
- ADOStreamConstruction::put_Stream
- ADOStreamConstruction::Stream
- ADOStreamConstruction::get_Stream
helpviewer_keywords:
- Stream property
ms.assetid: 4a44f9f6-0265-4c00-8def-d85b6af923b1
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d6ee0a6a3827d0f2d3c7b7bf781f7fc1fd73a765
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="stream-property"></a>ストリームのプロパティ
OLE DB の設定を取得または**ストリーム**オブジェクトから/上、 **ADOStreamConstruction**オブジェクト。  
  
 読み取りと書き込みが可能です。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT get_Stream([out, retval] IUnknown** ppStream);  
HRESULT put_Stream([in] IUnknown* pStream);  
```  
  
## <a name="parameters"></a>パラメーター  
 *ppStream*  
 OLE DB へのポインター**ストリーム**オブジェクト。  
  
 *pStream*  
 OLE DB**ストリーム**オブジェクト。  
  
## <a name="return-values"></a>戻り値  
 このプロパティのメソッドでは、標準の HRESULT 値を返します。 これには、S_OK および E_FAIL が含まれます。  
  
## <a name="applies-to"></a>適用対象  
 [ADOStreamConstruction インターフェイス](../../../ado/reference/ado-api/adostreamconstruction-interface.md)

