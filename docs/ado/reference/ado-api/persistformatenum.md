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
manager: jroth
ms.openlocfilehash: 7167067d0dc5942bc898c4cc2f01cad2a44ec559
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66703474"
---
# <a name="persistformatenum"></a>PersistFormatEnum
保存先となる形式を指定します、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)します。  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|**adPersistADTG**|0|Microsoft 高度なデータ TableGram (adtg 形式) の形式を示します。|  
|**adPersistADO**|1|ADO の拡張マークアップ言語 (XML) 形式が使用されることを示します。 この値は adPersistXML と同じでは、下位互換のためです。|  
|**adPersistXML**|1|拡張マークアップ言語 (XML) 形式を示します。|  
|**adPersistProviderSpecific**|2|プロバイダーは保持になっていることを示します、**レコード セット**独自形式を使用します。|  
  
## <a name="adowfc-equivalent"></a>ADO と WFC と同等  
 パッケージ: **com.ms.wfc.data**  
  
|定数|  
|--------------|  
|AdoEnums.PersistFormat.ADTG|  
|AdoEnums.PersistFormat.XML|  
  
## <a name="applies-to"></a>適用対象  
 [Save メソッド](../../../ado/reference/ado-api/save-method.md)
