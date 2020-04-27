---
title: PersistFormatEnum |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- PersistFormatEnum
helpviewer_keywords:
- PersistFormatEnum enumeration [ADO]
ms.assetid: ebe1a2ab-e9f1-43a2-8f94-b190c9613d70
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2a26fd370e80cb288ee62b0fc53ed6670300172e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "67917612"
---
# <a name="persistformatenum"></a>PersistFormatEnum
[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)を保存する形式を指定します。  
  
|Constant|[値]|説明|  
|--------------|-----------|-----------------|  
|**adPersistADTG**|0|Microsoft Advanced Data TableGram (ADTG) 形式を示します。|  
|**adPersistADO**|1|ADO の独自の拡張マークアップ言語 (XML) 形式が使用されることを示します。 この値は adPersistXML と同じであり、旧バージョンとの互換性のために用意されています。|  
|**adPersistXML**|1|拡張マークアップ言語 (XML) 形式を示します。|  
|**adPersistProviderSpecific**|2|プロバイダーが独自の形式を使用して**レコードセット**を永続化することを示します。|  
  
## <a name="adowfc-equivalent"></a>同等の ADO/WFC  
 パッケージ: **com. ms. wfc. データ**  
  
|Constant|  
|--------------|  
|AdoEnums ADTG|  
|AdoEnums の形式|  
  
## <a name="applies-to"></a>適用対象  
 [Save メソッド](../../../ado/reference/ado-api/save-method.md)
