---
title: "get_OLEDBCommand メソッド |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- get_OLEDBCommand method [ADO]
ms.assetid: 23d551f5-3d5b-434b-ade6-fef15f1710e7
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c78a0b7bd79da2bc75c3bcccbcb2bc9acbde8e35
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="getoledbcommand-method"></a>get_OLEDBCommand メソッド
基になる OLE DB コマンド、最初に OLE DB コマンドを ADO コマンドで指定した、パラメーター情報を伝達を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
HRESULT get_OLEDBCommand(  
      IUnknown **ppOLEDBCommand  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 *ppOLEDBCommand*  
 [out]ポインターの位置が、基になる OLE DB コマンドの IUnknown ポインターが書き込まれる場所へのポインター。  
  
## <a name="applies-to"></a>適用対象  
 [IADOCommandConstruction](http://msdn.microsoft.com/en-us/d8e54333-00eb-4b72-bf4a-ca92c7ca5f86)

