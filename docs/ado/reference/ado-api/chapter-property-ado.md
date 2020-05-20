---
title: Chapter プロパティ (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADORecordsetConstruction::Chapter
- ADORecordsetConstruction::put_Chapter
- ADORecordsetConstruction::get_Chapter
helpviewer_keywords:
- Chapter property [ADO]
ms.assetid: 8aa90cb0-f588-4141-9dc9-3b22918394ee
author: rothja
ms.author: jroth
ms.openlocfilehash: 04991b5246b338b89008e0188463dee580f81e3e
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82763153"
---
# <a name="chapter-property-ado"></a>Chapter プロパティ (ADO)
[ADORecordsetConstruction Interface](../../../ado/reference/ado-api/adorecordsetconstruction-interface.md)オブジェクトから OLE DB**チャプター**オブジェクトを取得します。値の設定もできます。 **Put_Chapter**を使用して**チャプター**オブジェクトを設定すると、行のサブセットが ADO[レコードセットオブジェクト](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトに変換されます。 これにより、**行セット**オブジェクトの現在のチャプターが設定されます。 このプロパティは読み取り/書き込み可能です。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT get_Chapter([out, retval] long* plChapter);  
HRESULT put_Chapter([in] long lChapter);  
```  
  
## <a name="parameters"></a>パラメーター  
 *plChapter*  
 チャプターのハンドルへのポインター。  
  
 *LChapter*  
 チャプターのハンドル。  
  
## <a name="return-values"></a>戻り値  
 このプロパティメソッドは、S_OK および E_FAIL を含む標準の HRESULT 値を返します。  
  
## <a name="applies-to"></a>適用対象  
 [ADORecordsetConstruction インターフェイス](../../../ado/reference/ado-api/adorecordsetconstruction-interface.md)
