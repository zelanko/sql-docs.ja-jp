---
title: メソッドを作成 |Microsoft ドキュメント
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
- _Stream::raw_Write
- _Stream::Write
helpviewer_keywords:
- Write method [ADO]
ms.assetid: 02982e6a-ac5f-4af2-b82e-ce12534b84b2
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 62ab48632de559f56f034ca0db10a968a43be32a
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35283231"
---
# <a name="write-method"></a>Write メソッド
バイナリ データを書き込む、[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
Stream.Write Buffer  
```  
  
#### <a name="parameters"></a>パラメーター  
 *バッファー*  
 A**バリアント**書き込まれるバイトの配列を格納しています。  
  
## <a name="remarks"></a>コメント  
 指定されたバイトを書き込む、**ストリーム**オブジェクトの各バイト間に介在するは空白なし。  
  
 現在[位置](../../../ado/reference/ado-api/position-property-ado.md)が書き込まれたデータに続くバイトに設定します。 **書き込み**メソッドでは、ストリーム内のデータの残りの部分は切り捨てられません。 これらのバイトを切り捨てる場合は、呼び出す[SetEOS](../../../ado/reference/ado-api/seteos-method.md)です。  
  
 現在を超えて書き込む場合[EOS](../../../ado/reference/ado-api/eos-property.md) 、位置、[サイズ](../../../ado/reference/ado-api/size-property-ado-stream.md)の**ストリーム**が増えたり、新しい (バイト単位) を格納して**EOS**移動されます新しい最後のバイトまで、**ストリーム**です。  
  
> [!NOTE]
>  **書き込み**バイナリ ストリームを持つメソッドを使用 ([型](../../../ado/reference/ado-api/type-property-ado-stream.md)は**adTypeBinary**)。 テキスト ストリーム (**型**は**adTypeText**)、使用[WriteText](../../../ado/reference/ado-api/writetext-method.md)です。  
  
## <a name="applies-to"></a>適用対象  
 [Stream オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [WriteText メソッド](../../../ado/reference/ado-api/writetext-method.md)
