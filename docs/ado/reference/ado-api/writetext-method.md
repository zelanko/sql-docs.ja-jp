---
title: WriteText メソッド |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_WriteText
- _Stream::WriteText
helpviewer_keywords:
- WriteText method [ADO]
ms.assetid: 7a669048-13f4-4574-a2b1-985e089729d5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a3b50db388151de1f5b99d8d9a3f48904e6d7c2c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47679890"
---
# <a name="writetext-method"></a>WriteText メソッド
指定したテキスト文字列を書き込みます、 [Stream](../../../ado/reference/ado-api/stream-object-ado.md)オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
Stream.WriteText Data, Options  
```  
  
#### <a name="parameters"></a>パラメーター  
 *データ*  
 A**文字列**書き込まれる文字内のテキストを表す値です。  
  
 *[オプション]*  
 任意。 A [StreamWriteEnum](../../../ado/reference/ado-api/streamwriteenum.md)行区切り記号を指定した文字列の最後に書き込む必要があるかどうかを指定する値。  
  
## <a name="remarks"></a>コメント  
 指定した文字列が書き込まれる、 **Stream**オブジェクト間のスペースや各文字列の間に文字なし。  
  
 現在[位置](../../../ado/reference/ado-api/position-property-ado.md)書き込まれたデータの次の文字に設定されます。 **WriteText**メソッドでは、ストリーム内のデータの残りの部分は切り捨てられません。 これらの文字を切り捨てる場合は、呼び出す[SetEOS](../../../ado/reference/ado-api/seteos-method.md)します。  
  
 過去の現在の記述する場合[EOS](../../../ado/reference/ado-api/eos-property.md) 、位置、[サイズ](../../../ado/reference/ado-api/size-property-ado-stream.md)の**Stream** 、新しい文字を含めるに延長される予定と**EOS**新しい最後のバイトを移動、 **Stream**します。  
  
> [!NOTE]
>  **WriteText**メソッドは、テキスト ストリームの使用 ([型](../../../ado/reference/ado-api/type-property-ado-stream.md)は**adTypeText**)。 バイナリ ストリームの (**型**は**adTypeBinary**) を使用して、[書き込み](../../../ado/reference/ado-api/write-method.md)します。  
  
## <a name="applies-to"></a>適用対象  
 [Stream オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [Write メソッド](../../../ado/reference/ado-api/write-method.md)
