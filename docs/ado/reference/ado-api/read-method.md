---
title: Read メソッド |Microsoft Docs
ms.prod: sql
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 75b39b758d48a173bcfbe84e3fecbd20cce5ee12
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82754269"
---
# <a name="read-method"></a>Read メソッド
バイナリ[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)オブジェクトから、指定されたバイト数を読み取ります。  
  
## <a name="syntax"></a>構文  
  
```  
  
Variant = Stream.Read ( NumBytes)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *NumBytes*  
 任意。 ファイルから読み取るバイト数、または既定の[Streamreadenum](../../../ado/reference/ado-api/streamreadenum.md)値**adreadall**を指定する**Long**値です。  
  
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
