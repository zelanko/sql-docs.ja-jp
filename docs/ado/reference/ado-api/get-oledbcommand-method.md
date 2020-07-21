---
title: get_OLEDBCommand メソッド |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- get_OLEDBCommand method [ADO]
ms.assetid: 23d551f5-3d5b-434b-ade6-fef15f1710e7
author: rothja
ms.author: jroth
ms.openlocfilehash: 043e432bfef39f90fbeb5b147487272c4d284bdb
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82760078"
---
# <a name="get_oledbcommand-method"></a>get_OLEDBCommand メソッド
基になる OLE DB コマンドを返します。最初に ADO コマンドで設定されたすべてのパラメーター情報を OLE DB コマンドに反映します。  
  
## <a name="syntax"></a>構文  
  
```  
  
HRESULT get_OLEDBCommand(  
      IUnknown **ppOLEDBCommand  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 *ppOLEDBCommand*  
 入出力基になる OLE DB コマンドの IUnknown ポインターが書き込まれるポインター位置へのポインター。  
  
## <a name="applies-to"></a>適用対象  
 [IADOCommandConstruction](https://msdn.microsoft.com/d8e54333-00eb-4b72-bf4a-ca92c7ca5f86)
