---
title: "put_OLEDBCommand メソッド |Microsoft ドキュメント"
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
helpviewer_keywords: put_OLEDBCommand method [ADO]
ms.assetid: ca6a5804-bf5c-4afc-99db-22904bc0b33d
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3584728624fb01d49a693bfbb2d09a655311d55b
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="putoledbcommand-method"></a>put_OLEDBCommand メソッド
このメソッドは、何も実行し、常に S_OK を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
HRESULT put_OLEDBCommand(  
      IUnknown *pOLEDBCommand  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 *pOLEDBCommand*  
 [in]OLE DB コマンド オブジェクトへのポインター。  
  
## <a name="applies-to"></a>適用対象  
 [IADOCommandConstruction](https://msdn.microsoft.com/library/windows/desktop/aa965677.aspx)
