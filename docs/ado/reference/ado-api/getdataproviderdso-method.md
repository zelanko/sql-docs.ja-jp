---
title: GetDataProviderDSO メソッド |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- GetDataProviderDSO Method [ADO]
ms.assetid: 5a4c6bd5-0c79-4f81-a977-0561392d8d50
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 5187e8f9fdce65b8e746a4a18a353462bb353d4f
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2019
ms.locfileid: "66698041"
---
# <a name="getdataproviderdso-method"></a>GetDataProviderDSO メソッド
Shape プロバイダーから基になる OLE DB データ ソース オブジェクトを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
HRESULT GetDataProviderDSO(  
      IUnknown **ppDataProviderDSOIUnknown  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 *ppDataProviderDSOIUnknown*  
 [out] 返す基になる OLE DB データ ソース オブジェクトの IUnknown ポインターへのポインター。  
  
## <a name="remarks"></a>コメント  
 このメソッドではない addref インターフェイス ポインター。 呼び出し元が必要な addref を行う必要があります、呼び出し元ポインターを保持する場合、およびリリースします。  
  
## <a name="applies-to"></a>対象  
 [IDSOShapeExtensions インターフェイス](../../../ado/reference/ado-api/idsoshapeextensions-interface.md)
