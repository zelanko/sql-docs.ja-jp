---
title: Read メソッド |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Stream::raw_Read
- _Stream::Read
helpviewer_keywords:
- Read method [ADO]
ms.assetid: 838502de-80f1-4eeb-8838-dd3d9403e567
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 992631b8fb3864b6d7404f86d2f65de222f0b1c8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67917416"
---
# <a name="read-method"></a>Read メソッド
バイナリ[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)オブジェクトから、指定されたバイト数を読み取ります。  
  
## <a name="syntax"></a>構文  
  
```  
  
Variant = Stream.Read ( NumBytes)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *NumBytes*  
 省略可能。 ファイルから読み取るバイト数、または既定の[Streamreadenum](../../../ado/reference/ado-api/streamreadenum.md)値**adreadall**を指定する**Long**値です。  
  
## <a name="return-value"></a>戻り値  
 **Read**メソッドは、指定されたバイト数またはストリーム全体を**ストリーム**オブジェクトから読み取り、結果のデータを**バリアント**として返します。  
  
## <a name="remarks"></a>解説  
 *Numbytes*が**ストリーム**の残りのバイト数よりも大きい場合は、残っているバイトだけが返されます。 読み取られたデータは、 *Numbytes*によって指定された長さと一致するように埋め込まれていません。 読み取るバイトが残っていない場合は、null 値を持つバリアントが返されます。 **Read**を使用して後方に読み取ることはできません。  
  
> [!NOTE]
>  *Numbytes*は常にバイトを計測します。 テキスト**ストリーム**オブジェクト ([型](../../../ado/reference/ado-api/type-property-ado-stream.md)は**adTypeText**) の場合は、 [ReadText](../../../ado/reference/ado-api/readtext-method.md)を使用します。  
  
## <a name="applies-to"></a>適用対象  
 [Stream オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [ReadText メソッド](../../../ado/reference/ado-api/readtext-method.md)
