---
title: SkipLine メソッド |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_SkipLine
- _Stream::SkipLine
helpviewer_keywords:
- Skipline method [ADO]
ms.assetid: 0abc00fe-ee09-4c8e-b1f2-48ee9c5f3329
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c8439f7d8fabc5675e43fca5bba006b22574b992
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67931046"
---
# <a name="skipline-method"></a>SkipLine メソッド
テキスト[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)を読み取るときに、1行全体をスキップします。  
  
## <a name="syntax"></a>構文  
  
```  
  
Stream.SkipLine  
```  
  
## <a name="remarks"></a>解説  
 次の行区切り記号までのすべての文字がスキップされます。 既定では、 [Lineseparator](../../../ado/reference/ado-api/lineseparator-property-ado.md)は**adcrlf**です。 以前の[eos](../../../ado/reference/ado-api/eos-property.md)をスキップしようとすると、現在の位置は**eos**のままになります。  
  
 **SkipLine**メソッドは、テキストストリームと共に使用されます ([型](../../../ado/reference/ado-api/type-property-ado-stream.md)は**adTypeText**)。  
  
## <a name="applies-to"></a>適用対象  
 [Stream オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
