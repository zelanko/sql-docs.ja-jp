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
manager: craigg
ms.openlocfilehash: 1b5bbc04c94d491c096db047d574cc3b5fd8ee38
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63156633"
---
# <a name="read-method"></a>Read メソッド
バイナリから、指定したバイト数を読み取ります[Stream](../../../ado/reference/ado-api/stream-object-ado.md)オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
Variant = Stream.Read ( NumBytes)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *NumBytes*  
 任意。 A**長い**ファイルから読み取るバイト数を指定する値または[StreamReadEnum](../../../ado/reference/ado-api/streamreadenum.md)値**adReadAll**、既定値します。  
  
## <a name="return-value"></a>戻り値  
 **読み取り**メソッドは指定された数のバイトまたはからストリーム全体を読み取ります、 **Stream**オブジェクトし、結果として得られるデータとして返します、**バリアント**します。  
  
## <a name="remarks"></a>コメント  
 場合*NumBytes*内の残りのバイト数よりは、 **Stream**、残りのバイトのみが返されます。 指定された長さに一致するように読み取られたデータが埋め込まれていません*NumBytes*します。 読み取るデータがない場合は、null 値を持つバリアントが返されます。 **読み取り**旧バージョンと読み取りに使用することはできません。  
  
> [!NOTE]
>  *NumBytes*常にバイトを測定します。 テキストの**Stream**オブジェクト ([型](../../../ado/reference/ado-api/type-property-ado-stream.md)は**adTypeText**) を使用して、 [ReadText](../../../ado/reference/ado-api/readtext-method.md)します。  
  
## <a name="applies-to"></a>適用対象  
 [Stream オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [ReadText メソッド](../../../ado/reference/ado-api/readtext-method.md)
