---
title: "ParentRow プロパティ (ADO) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- ADORecordConstruction::put_ParentRow
- ADORecordConstruction::ParentRow
- ADORecordConstruction::putParentRow
helpviewer_keywords: ParentRow property [ADO]
ms.assetid: 5ea8029b-eda4-490b-ae84-2ad036fb582f
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8869e091c0f48981d60893ed0d3f698aeee0c8b2
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="parentrow-property-ado"></a>ParentRow プロパティ (ADO)
OLE DB のコンテナーを設定**行**上のオブジェクト、 **ADORecordConstruction**オブジェクト、ADO に行の親になっているため、**レコード**オブジェクト。  
  
 書き込み専用です。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT put_ParentRow([in] IUnknown* pParent);  
```  
  
## <a name="parameters"></a>パラメーター  
 *pParent*  
 行のコンテナーです。  
  
## <a name="return-values"></a>戻り値  
 このプロパティのメソッドでは、S_OK および E_FAIL を含む、標準の HRESULT 値を返します。  
  
## <a name="applies-to"></a>適用対象  
 [ADORecordConstruction インターフェイス](../../../ado/reference/ado-api/adorecordconstruction-interface.md)
