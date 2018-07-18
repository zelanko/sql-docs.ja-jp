---
title: ParentRow プロパティ (ADO) |Microsoft ドキュメント
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
- ADORecordConstruction::put_ParentRow
- ADORecordConstruction::ParentRow
- ADORecordConstruction::putParentRow
helpviewer_keywords:
- ParentRow property [ADO]
ms.assetid: 5ea8029b-eda4-490b-ae84-2ad036fb582f
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 86122a7cb075816809dd8868c1db94adf1b81612
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35280561"
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
