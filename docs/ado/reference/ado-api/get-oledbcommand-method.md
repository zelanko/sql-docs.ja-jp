---
description: get_OLEDBCommand メソッド
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
ms.openlocfilehash: 56148afcd3c7d3e18e856c6e50a44f35aaa1bc64
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2020
ms.locfileid: "88775131"
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
 [IADOCommandConstruction](/previous-versions/windows/desktop/aa965677(v=vs.85))