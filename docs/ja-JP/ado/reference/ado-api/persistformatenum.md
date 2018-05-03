---
title: PersistFormatEnum |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- PersistFormatEnum
helpviewer_keywords:
- PersistFormatEnum enumeration [ADO]
ms.assetid: ebe1a2ab-e9f1-43a2-8f94-b190c9613d70
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4e1d0a42d0f5aef6c18512f10dfe2579e5d484aa
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="persistformatenum"></a>PersistFormatEnum
保存する形式を指定します、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)です。  
  
|定数|値|Description|  
|--------------|-----------|-----------------|  
|**adPersistADTG**|0|Microsoft 高度なデータ TableGram (adtg 形式) の形式を示します。|  
|**adPersistADO**|1|ADO の拡張マークアップ言語 (XML) 形式を使用することを示します。 この値は adPersistXML と同じとは下位互換のためです。|  
|**adPersistXML**|1|拡張マークアップ言語 (XML) 形式を示します。|  
|**adPersistProviderSpecific**|2|プロバイダーが永続化することを示します、**レコード セット**独自形式を使用します。|  
  
## <a name="adowfc-equivalent"></a>該当するショートカットは ADO/WFC  
 パッケージ: **com.ms.wfc.data**  
  
|定数|  
|--------------|  
|AdoEnums.PersistFormat.ADTG|  
|AdoEnums.PersistFormat.XML|  
  
## <a name="applies-to"></a>適用対象  
 [Save メソッド](../../../ado/reference/ado-api/save-method.md)
