---
title: "WriteText メソッド |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Stream::raw_WriteText
- _Stream::WriteText
helpviewer_keywords:
- WriteText method [ADO]
ms.assetid: 7a669048-13f4-4574-a2b1-985e089729d5
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d7facdd886b6bf048afb9f17a6d9c7c0a69ced57
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="writetext-method"></a>WriteText メソッド
指定したテキストに文字列を[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
Stream.WriteText Data, Options  
```  
  
#### <a name="parameters"></a>パラメーター  
 *データ*  
 A**文字列**書き込まれる文字のテキストを含む値です。  
  
 *および*  
 省略可。 A [StreamWriteEnum](../../../ado/reference/ado-api/streamwriteenum.md)指定した文字列の末尾行区切り記号を記述する必要があるかどうかを指定する値。  
  
## <a name="remarks"></a>解説  
 指定した文字列に書き込まれる、**ストリーム**介在するスペースや各文字列間の文字のないオブジェクトです。  
  
 現在[位置](../../../ado/reference/ado-api/position-property-ado.md)が書き込まれたデータの次の文字に設定します。 **WriteText**メソッドでは、ストリーム内のデータの残りの部分は切り捨てられません。 これらの文字を切り捨てる場合は、呼び出す[SetEOS](../../../ado/reference/ado-api/seteos-method.md)です。  
  
 現在を超えて書き込む場合[EOS](../../../ado/reference/ado-api/eos-property.md)位置、[サイズ](../../../ado/reference/ado-api/size-property-ado-stream.md)の**ストリーム**任意新しい文字に増加し、 **EOS**新しい最後のバイトまでの移動、**ストリーム**です。  
  
> [!NOTE]
>  **WriteText**メソッドがテキスト ストリームで使用される ([型](../../../ado/reference/ado-api/type-property-ado-stream.md)は**adTypeText**)。 バイナリ ストリームの (**型**は**adTypeBinary**)、使用して[書き込み](../../../ado/reference/ado-api/write-method.md)です。  
  
## <a name="applies-to"></a>適用対象  
 [ストリーム オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [Write メソッド](../../../ado/reference/ado-api/write-method.md)

