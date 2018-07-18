---
title: get_OLEDBCommand メソッド |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- get_OLEDBCommand method [ADO]
ms.assetid: 23d551f5-3d5b-434b-ade6-fef15f1710e7
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e7b2668c3693078c7027b26fa61df73b81161970
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2018
ms.locfileid: "38979354"
---
# <a name="getoledbcommand-method"></a>get_OLEDBCommand メソッド
基になる OLE DB コマンドの最初のパラメーター情報を ADO コマンドで OLE DB コマンドを設定の反映を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
HRESULT get_OLEDBCommand(  
      IUnknown **ppOLEDBCommand  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 *ppOLEDBCommand*  
 [out]ポインターの位置を基になる OLE DB コマンドの IUnknown ポインターが書き込まれる場所へのポインター。  
  
## <a name="applies-to"></a>適用対象  
 [IADOCommandConstruction](http://msdn.microsoft.com/d8e54333-00eb-4b72-bf4a-ca92c7ca5f86)
