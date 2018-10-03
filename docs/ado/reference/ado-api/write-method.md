---
title: メソッドの記述 |Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 52561b6d240a58e59490d607c8729b5d878b96a7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47772564"
---
# <a name="write-method"></a>Write メソッド
バイナリ データを書き込みます、 [Stream](../../../ado/reference/ado-api/stream-object-ado.md)オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
Stream.Write Buffer  
```  
  
#### <a name="parameters"></a>パラメーター  
 *Buffer*  
 A**バリアント**書き込むバイトの配列を格納しています。  
  
## <a name="remarks"></a>コメント  
 指定したバイトを書き込む、 **Stream**各バイトの介在するスペースを入れずオブジェクト。  
  
 現在[位置](../../../ado/reference/ado-api/position-property-ado.md)書き込まれたデータに続くバイトに設定されます。 **書き込み**メソッドでは、ストリーム内のデータの残りの部分は切り捨てられません。 これらのバイトを切り捨てる場合は、呼び出す[SetEOS](../../../ado/reference/ado-api/seteos-method.md)します。  
  
 現在過去を記述する場合[EOS](../../../ado/reference/ado-api/eos-property.md) 、位置、[サイズ](../../../ado/reference/ado-api/size-property-ado-stream.md)の**Stream**が高く、新しいバイトを格納して**EOS**移動新しい最後のバイトを**Stream**します。  
  
> [!NOTE]
>  **書き込み**メソッドを使用するバイナリ ストリーム ([型](../../../ado/reference/ado-api/type-property-ado-stream.md)は**adTypeBinary**)。 テキスト ストリーム (**型**は**adTypeText**) を使用して、 [WriteText](../../../ado/reference/ado-api/writetext-method.md)します。  
  
## <a name="applies-to"></a>適用対象  
 [Stream オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [WriteText メソッド](../../../ado/reference/ado-api/writetext-method.md)
