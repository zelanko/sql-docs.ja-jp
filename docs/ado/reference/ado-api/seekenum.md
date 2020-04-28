---
title: SeekEnum |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- SeekEnum
helpviewer_keywords:
- SeekEnum enumeration [ADO]
ms.assetid: f0ec0c92-8253-47c6-9a14-e5dbccbad219
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 886825b4d32354572a5162487add419b00ec35d6
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67931065"
---
# <a name="seekenum"></a>SeekEnum
実行する[シーク](../../../ado/reference/ado-api/seek-method.md)の種類を指定します。  
  
|Constant|値|説明|  
|--------------|-----------|-----------------|  
|**Adseekの Steq**|1|*Keyvalues*と等しい最初のキーをシークします。|  
|**adSeekLastEQ**|2|*Keyvalues*と等しい最後のキーをシークします。|  
|**adSeekAfterEQ**|4|*Keyvalues*と等しいキー、またはその直後に一致したキーをシークします。|  
|**adSeekAfter**|8|*Keyvalues*との一致が発生した直後にキーをシークします。|  
|**adSeekBeforeEQ**|16|*Keyvalues*と等しいキー、またはその一致が発生した直前のキーをシークします。|  
|**adSeekBefore**|32|*Keyvalues*との一致が発生する直前に、キーをシークします。|  
  
## <a name="adowfc-equivalent"></a>同等の ADO/WFC  
 パッケージ: **com. ms. wfc. データ**  
  
|Constant|  
|--------------|  
|AdoEnums を検索します。|  
|AdoEnums を検索します。|  
|AdoEnums. AFTEREQ|  
|AdoEnums|  
|AdoEnums。|  
|AdoEnums|  
  
## <a name="applies-to"></a>適用対象  
 [Seek メソッド](../../../ado/reference/ado-api/seek-method.md)
