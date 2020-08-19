---
description: Type プロパティ (ADO Stream)
title: Type プロパティ (ADO Stream) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::Type
- _Stream::get_Type
- _Stream::put_Type
helpviewer_keywords:
- Type property [ADO Stream]
ms.assetid: f6a17e8c-7a28-48d0-bded-76b9e0cf7639
author: rothja
ms.author: jroth
ms.openlocfilehash: 8fd1519092d72f8a562bb266d2aa6d547d8e37df
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88441734"
---
# <a name="type-property-ado-stream"></a>Type プロパティ (ADO Stream)
[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)に格納されているデータの型 (バイナリまたはテキスト) を示します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 **ストリーム**オブジェクトに格納されているデータの型を指定する[streamtypeenum](../../../ado/reference/ado-api/streamtypeenum.md)値を設定または返します。 既定値は **adTypeText**です。 ただし、バイナリデータが最初に新しい空の **ストリーム**に書き込まれる場合、その **型** は **adtypebinary**に変更されます。  
  
## <a name="remarks"></a>解説  
 **Type**プロパティは、現在の位置が**ストリーム**の先頭 ([位置](../../../ado/reference/ado-api/position-property-ado.md)が 0) であり、他の任意の位置で読み取り専用である場合にのみ、読み取り/書き込みになります。  
  
 **Type**プロパティによって、**ストリーム**の読み取りと書き込みに使用するメソッドが決まります。 テキスト **ストリーム**の場合は、 [ReadText](../../../ado/reference/ado-api/readtext-method.md) と [WriteText](../../../ado/reference/ado-api/writetext-method.md)を使用します。 バイナリ **ストリーム**の場合は、 [読み取り](../../../ado/reference/ado-api/read-method.md) と [書き込み](../../../ado/reference/ado-api/write-method.md)を使用します。  
  
## <a name="applies-to"></a>適用対象  
 [Stream オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [RecordType プロパティ (ADO)](../../../ado/reference/ado-api/recordtype-property-ado.md)   
 [Type プロパティ (ADO)](../../../ado/reference/ado-api/type-property-ado.md)
