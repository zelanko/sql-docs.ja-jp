---
description: GetDataProviderDSO メソッド
title: GetDataProviderDSO メソッド |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- GetDataProviderDSO Method [ADO]
ms.assetid: 5a4c6bd5-0c79-4f81-a977-0561392d8d50
author: rothja
ms.author: jroth
ms.openlocfilehash: e21e45d72cd5140c542fb6d6d0b150c414fb9832
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2020
ms.locfileid: "88775071"
---
# <a name="getdataproviderdso-method"></a>GetDataProviderDSO メソッド
基になる OLE DB データソースオブジェクトをシェイププロバイダーから取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
HRESULT GetDataProviderDSO(  
      IUnknown **ppDataProviderDSOIUnknown  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 *ppDataProviderDSOIUnknown*  
 入出力 基になる OLE DB データソースオブジェクトの IUnknown を返すポインターへのポインター。  
  
## <a name="remarks"></a>解説  
 このメソッドは、インターフェイスポインターを addref しません。 呼び出し元がポインターを保持することを計画している場合、呼び出し元は必要な addref と release を実行する必要があります。  
  
## <a name="applies-to"></a>適用対象  
 [IDSOShapeExtensions インターフェイス](./idsoshapeextensions-interface.md)