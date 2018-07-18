---
title: WriteText メソッド |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
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
manager: craigg
ms.openlocfilehash: c38b1e8573e59d4446ff0a4dbfebf1cc627b3863
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35283191"
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
  
 *[オプション]*  
 任意。 A [StreamWriteEnum](../../../ado/reference/ado-api/streamwriteenum.md)指定した文字列の末尾行区切り記号を記述する必要があるかどうかを指定する値。  
  
## <a name="remarks"></a>コメント  
 指定した文字列に書き込まれる、**ストリーム**介在するスペースや各文字列間の文字のないオブジェクトです。  
  
 現在[位置](../../../ado/reference/ado-api/position-property-ado.md)が書き込まれたデータの次の文字に設定します。 **WriteText**メソッドでは、ストリーム内のデータの残りの部分は切り捨てられません。 これらの文字を切り捨てる場合は、呼び出す[SetEOS](../../../ado/reference/ado-api/seteos-method.md)です。  
  
 現在を超えて書き込む場合[EOS](../../../ado/reference/ado-api/eos-property.md)位置、[サイズ](../../../ado/reference/ado-api/size-property-ado-stream.md)の**ストリーム**任意新しい文字に増加し、 **EOS**新しい最後のバイトまでの移動、**ストリーム**です。  
  
> [!NOTE]
>  **WriteText**メソッドがテキスト ストリームで使用される ([型](../../../ado/reference/ado-api/type-property-ado-stream.md)は**adTypeText**)。 バイナリ ストリームの (**型**は**adTypeBinary**)、使用して[書き込み](../../../ado/reference/ado-api/write-method.md)です。  
  
## <a name="applies-to"></a>適用対象  
 [Stream オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [Write メソッド](../../../ado/reference/ado-api/write-method.md)
