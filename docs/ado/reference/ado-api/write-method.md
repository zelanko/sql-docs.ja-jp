---
title: Write メソッド |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_Write
- _Stream::Write
helpviewer_keywords:
- Write method [ADO]
ms.assetid: 02982e6a-ac5f-4af2-b82e-ce12534b84b2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 84e10e8edb6cca3c4e56ac1dd0106b3c641af872
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67945903"
---
# <a name="write-method"></a>Write メソッド
バイナリデータを[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)オブジェクトに書き込みます。  
  
## <a name="syntax"></a>構文  
  
```  
  
Stream.Write Buffer  
```  
  
#### <a name="parameters"></a>パラメーター  
 *Buffer*  
 書き込むバイト配列を格納している**Variant** 。  
  
## <a name="remarks"></a>解説  
 指定されたバイトは、各バイト間にスペースを入れずに**ストリーム**オブジェクトに書き込まれます。  
  
 現在の[位置](../../../ado/reference/ado-api/position-property-ado.md)は、書き込まれたデータに続くバイトに設定されます。 **Write**メソッドは、ストリーム内の残りのデータを切り捨てません。 これらのバイトを切り捨てる場合は、 [SetEOS](../../../ado/reference/ado-api/seteos-method.md)を呼び出します。  
  
 現在の[EOS](../../../ado/reference/ado-api/eos-property.md)位置を超えて書き込む場合、**ストリーム**の[サイズ](../../../ado/reference/ado-api/size-property-ado-stream.md)は新しいバイト数を含むように増加し、 **EOS**は**ストリーム**の新しい最後のバイトに移動します。  
  
> [!NOTE]
>  **Write**メソッドはバイナリストリームで使用されます ([Type](../../../ado/reference/ado-api/type-property-ado-stream.md)は**adtypebinary**です)。 テキストストリーム (**型**は**adTypeText**) の場合は、 [WriteText](../../../ado/reference/ado-api/writetext-method.md)を使用します。  
  
## <a name="applies-to"></a>適用対象  
 [Stream オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [WriteText メソッド](../../../ado/reference/ado-api/writetext-method.md)
