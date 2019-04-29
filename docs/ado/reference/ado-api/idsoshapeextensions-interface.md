---
title: IDSOShapeExtensions インターフェイス |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- IDSOShapeExtensions interface [ADO]
ms.assetid: ad4ba313-1161-4bc7-b8f6-4083305bc81e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 36f91ea537b1ad2a5e52221400f41bf88dc544b0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63028039"
---
# <a name="idsoshapeextensions-interface"></a>IDSOShapeExtensions インターフェイス
SHAPE プロバイダーの基になる OLE DB データ ソース オブジェクトを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
interface IDSOShapeExtensions: public IUnknown {  
public:  
      HRESULT  GetDataProviderDSO(  
            IUnknown **ppDataProviderDSOIUnknown  
      );  
};  
```  
  
## <a name="methods"></a>メソッド  
  
|||  
|-|-|  
|[GetDataProviderDSO メソッド](../../../ado/reference/ado-api/getdataproviderdso-method.md)|Shape プロバイダーから基になる OLE DB データ ソース オブジェクトを取得します。|  
  
## <a name="requirements"></a>必要条件  
 **バージョン：** ADO 2.0 以降  
  
 **ライブラリ:** msado15.dll  
  
 **UUID:** 00000283-0000-0010-8000-00AA006D2EA4
