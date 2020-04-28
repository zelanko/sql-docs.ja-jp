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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 85bef64902f014e7b5269d6df328128bc8fe8d6e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67937883"
---
# <a name="stringformatenum"></a>StringFormatEnum
[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)を文字列として取得する場合の形式を指定します。  
  
|Constant|値|説明|  
|--------------|-----------|-----------------|  
|**adClipString**|2|*Rowdelimiter*で行を区切り、 *columndelimiter*で列を区切り、Null 値を*nullexpr*で区切ります。 [GetString](../../../ado/reference/ado-api/getstring-method-ado.md)メソッドのこれら3つのパラメーターは、 **Adclipstring**の*StringFormat*でのみ有効です。|  
  
## <a name="adowfc-equivalent"></a>同等の ADO/WFC  
 パッケージ: **com. ms. wfc. データ**  
  
|Constant|  
|--------------|  
|AdoEnums StringFormat|  
  
## <a name="applies-to"></a>適用対象  
 [GetString メソッド (ADO)](../../../ado/reference/ado-api/getstring-method-ado.md)
