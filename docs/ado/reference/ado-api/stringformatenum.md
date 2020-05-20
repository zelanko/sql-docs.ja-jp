---
title: StringFormatEnum |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- StringFormatEnum
helpviewer_keywords:
- StringFormatEnum enumeration [ADO]
ms.assetid: 28f7d1ec-092b-4323-a39d-d3f882c6c81a
author: rothja
ms.author: jroth
ms.openlocfilehash: 67814e1236bc10e9b008d1684586796dd62950b4
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82759558"
---
# <a name="stringformatenum"></a>StringFormatEnum
[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)を文字列として取得する場合の形式を指定します。  
  
|定数|[値]|説明|  
|--------------|-----------|-----------------|  
|**adClipString**|2|*Rowdelimiter*で行を区切り、 *columndelimiter*で列を区切り、Null 値を*nullexpr*で区切ります。 [GetString](../../../ado/reference/ado-api/getstring-method-ado.md)メソッドのこれら3つのパラメーターは、 **Adclipstring**の*StringFormat*でのみ有効です。|  
  
## <a name="adowfc-equivalent"></a>同等の ADO/WFC  
 パッケージ: **com. ms. wfc. データ**  
  
|定数|  
|--------------|  
|AdoEnums StringFormat|  
  
## <a name="applies-to"></a>適用対象  
 [GetString メソッド (ADO)](../../../ado/reference/ado-api/getstring-method-ado.md)
