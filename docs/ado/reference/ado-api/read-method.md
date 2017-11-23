---
title: "Read メソッド |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Stream::raw_Read
- _Stream::Read
helpviewer_keywords: Read method [ADO]
ms.assetid: 838502de-80f1-4eeb-8838-dd3d9403e567
caps.latest.revision: "13"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 740be677f54f8d4b5d30902a792b58d4681df888
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="read-method"></a>Read メソッド
バイナリから指定したバイト数を読み取ります[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
Variant = Stream.Read ( NumBytes)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *NumBytes*  
 省略可。 A**長い**ファイルから読み取るバイト数を指定する値または[StreamReadEnum](../../../ado/reference/ado-api/streamreadenum.md)値**adReadAll**、既定値です。  
  
## <a name="return-value"></a>戻り値  
 **読み取り**メソッドは、指定したバイト数またはからストリーム全体を読み取ります、**ストリーム**オブジェクトし、結果として得られるデータとして返します、**バリアント**です。  
  
## <a name="remarks"></a>解説  
 場合*NumBytes*はバイト数よりも多いのままに、**ストリーム**、残っているバイト数のみが返されます。 指定された長さに合わせて読み取られるデータが埋め込まれていません*NumBytes*です。 読み取るデータがない場合は、値が null のバリアント型が返されます。 **読み取り**旧バージョンと読み取りに使用することはできません。  
  
> [!NOTE]
>  *NumBytes*常にバイトを測定します。 テキストの**ストリーム**オブジェクト ([型](../../../ado/reference/ado-api/type-property-ado-stream.md)は**adTypeText**)、使用して[ReadText](../../../ado/reference/ado-api/readtext-method.md)です。  
  
## <a name="applies-to"></a>適用対象  
 [Stream オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [ReadText メソッド](../../../ado/reference/ado-api/readtext-method.md)
