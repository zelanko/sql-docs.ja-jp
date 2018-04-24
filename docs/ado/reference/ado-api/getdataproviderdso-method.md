---
title: GetDataProviderDSO メソッド |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- GetDataProviderDSO Method [ADO]
ms.assetid: 5a4c6bd5-0c79-4f81-a977-0561392d8d50
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fca773c6db137999da36daf0151a51a1becf79c6
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
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
  
## <a name="remarks"></a>解説  
 このメソッドは、インターフェイス ポインターいない addref をしません。 呼び出し元は、ポインターを保持するために計画をしている場合、呼び出し元が必要な addref を行う必要がありますと解放します。  
  
## <a name="applies-to"></a>適用対象  
 [IDSOShapeExtensions インターフェイス](../../../ado/reference/ado-api/idsoshapeextensions-interface.md)
