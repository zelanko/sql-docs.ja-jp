---
title: "チャプター プロパティ (ADO) |Microsoft ドキュメント"
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
- ADORecordsetConstruction::Chapter
- ADORecordsetConstruction::put_Chapter
- ADORecordsetConstruction::get_Chapter
helpviewer_keywords: Chapter property [ADO]
ms.assetid: 8aa90cb0-f588-4141-9dc9-3b22918394ee
caps.latest.revision: "13"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 026fc2e66f9dca3243791f3cd2c1e984f13087d8
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="chapter-property-ado"></a>チャプター プロパティ (ADO)
OLE DB の設定を取得または**章**オブジェクトから/上、 [ADORecordsetConstruction インターフェイス](../../../ado/reference/ado-api/adorecordsetconstruction-interface.md)オブジェクト。 使用すると**put_Chapter**を設定する、**章**オブジェクト、ADO に行のサブセットになって[Recordset オブジェクト](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト。 これにより、設定の現在のチャプター、**行セット**オブジェクト。 このプロパティは読み取り/書き込み可能です。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT get_Chapter([out, retval] long* plChapter);  
HRESULT put_Chapter([in] long lChapter);  
```  
  
## <a name="parameters"></a>パラメーター  
 *plChapter*  
 チャプターのハンドルへのポインター。  
  
 *LChapter*  
 チャプターのハンドルです。  
  
## <a name="return-values"></a>戻り値  
 このプロパティのメソッドでは、S_OK および E_FAIL を含む、標準の HRESULT 値を返します。  
  
## <a name="applies-to"></a>適用対象  
 [ADORecordsetConstruction インターフェイス](../../../ado/reference/ado-api/adorecordsetconstruction-interface.md)
