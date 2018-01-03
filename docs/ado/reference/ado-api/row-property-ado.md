---
title: "行のプロパティ (ADO) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- ADORecordConstruction::PutRow
- ADORecordConstruction::GetRow
- ADORecordConstruction::get_Row
- ADORecordConstruction::Row
- ADORecordConstruction::put_Row
helpviewer_keywords: Row property [ADO]
ms.assetid: 21019d89-2dd1-4a26-ac6f-384b81d66949
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ed9e10206acfd86477a7f982676c1cb82711a1b4
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="row-property-ado"></a>行のプロパティ (ADO)
OLE DB の設定を取得または**行**からまたは上のオブジェクト、 [ADORecordConstruction インターフェイス](../../../ado/reference/ado-api/adorecordconstruction-interface.md)オブジェクト。 使用すると**put_Row**を設定する、**行**オブジェクトの行が ADO に変わる**レコード**オブジェクト。  
  
## <a name="readwritesyntax"></a>読み取り/書き込みです。構文  
  
```  
HRESULT get_Row([out, retval] IUnknown** ppRow);  
HRESULT put_Row([in] IUnknown* pRow);  
```  
  
## <a name="parameters"></a>パラメーター  
 *ppRow*  
 OLE DB へのポインター**行**オブジェクト。  
  
 *PRow*  
 OLE DB**行**オブジェクト。  
  
## <a name="return-values"></a>戻り値  
 このプロパティのメソッドでは、S_OK および E_FAIL を含む、標準の HRESULT 値を返します。  
  
## <a name="applies-to"></a>適用対象  
 [ADORecordConstruction インターフェイス](../../../ado/reference/ado-api/adorecordconstruction-interface.md)
