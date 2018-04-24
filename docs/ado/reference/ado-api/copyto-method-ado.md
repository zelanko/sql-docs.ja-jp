---
title: CopyTo メソッド (ADO) |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_CopyTo
- _Stream::CopyTo
helpviewer_keywords:
- CopyTo method [ADO]
ms.assetid: b4aa5714-916b-48b8-8b09-cc2708379602
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3164fbdffe9bad363a09f6ff7accf8cf6d55d751
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="copyto-method-ado"></a>CopyTo メソッド (ADO)
指定した数の文字またはバイトのコピー (に応じて[型](../../../ado/reference/ado-api/type-property-ado-stream.md)) で、[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)別**ストリーム**オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
Stream.CopyTo DestStream, NumChars  
```  
  
#### <a name="parameters"></a>パラメーター  
 *DestStream*  
 オブジェクト変数の値を開いているへの参照を含む**ストリーム**オブジェクト。 現在**ストリーム**先にコピー**ストリーム**によって指定された*DestStream*です。 転送先**ストリーム**開かれている必要があります。 いない場合は、実行時エラーが発生します。  
  
> [!NOTE]
>  *DestStream*パラメーターでのプロキシができない可能性があります**ストリーム**オブジェクトのプライベート インターフェイスへのアクセスに要求されるため、**ストリーム**オブジェクトをリモート処理は実行することはできません、クライアントです。  
  
 *NumChars*  
 省略可。 **整数**バイトか、ソース内の現在位置からコピーする文字の数を指定する値**ストリーム**変換先に**ストリーム**です。 既定値は-1 で、すべての文字またはバイトが現在の位置からコピーされるように指定[EOS](../../../ado/reference/ado-api/eos-property.md)です。  
  
## <a name="remarks"></a>解説  
 このメソッドは、指定された文字数またはバイト単位で指定された現在の位置から始まる、コピー、[位置](../../../ado/reference/ado-api/position-property-ado.md)プロパティです。 指定した数値が利用できるまでのバイト数よりも多い場合**EOS**、し、文字またはバイトのみを現在の位置から**EOS**コピーされます。 場合の値*NumChars* -1 で、または省略すると、すべての文字または現在の位置から始まるバイトをコピーします。  
  
 既に存在する場合の文字またはコピー先のストリームにバイトをコピーの終了ポイント以降のすべての内容が残っていると、切り捨ては行われません。 **位置**コピーされる最後のバイトをすぐに続くバイトになります。 これらのバイトを切り捨てる場合は、呼び出す[SetEOS](../../../ado/reference/ado-api/seteos-method.md)です。  
  
 **CopyTo**データの保存先にコピーするために使用する必要があります**ストリーム**ソースと同じ型の**ストリーム**(その**型**プロパティの設定は両方**adTypeText**またはその両方**adTypeBinary**)。 テキストの**ストリーム**オブジェクトを変更することができます、 [Charset](../../../ado/reference/ado-api/charset-property-ado.md)変換先のプロパティの設定**ストリーム**別に設定する 1 つの文字に変換します。 また、テキスト**ストリーム**オブジェクトをバイナリに正常にコピーできる**ストリーム**オブジェクトではなくバイナリ**ストリーム**テキストにオブジェクトをコピーすることはできません**ストリーム**オブジェクト。  
  
## <a name="applies-to"></a>適用対象  
 [Stream オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
