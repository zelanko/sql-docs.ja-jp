---
title: SetEOS メソッド |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_SetEOS
- _Stream::SetEOS
helpviewer_keywords:
- SetEOS method [ADO]
ms.assetid: 707c18ca-6a56-4970-bbd6-ae1fb86a0b8a
author: rothja
ms.author: jroth
ms.openlocfilehash: 9dbe2846674d760163fa9eb3ab78e07e68b80d0e
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82759898"
---
# <a name="seteos-method"></a>SetEOS メソッド
ストリームの末尾である位置を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Stream.SetEOS  
```  
  
## <a name="remarks"></a>解説  
 **SetEOS**は、現在[位置](../../../ado/reference/ado-api/position-property-ado.md)をストリームの末尾にすることによって、 [EOS](../../../ado/reference/ado-api/eos-property.md)プロパティの値を更新します。 現在の位置の後に続くバイトまたは文字は切り捨てられます。  
  
 [Write](../../../ado/reference/ado-api/write-method.md)、 [WriteText](../../../ado/reference/ado-api/writetext-method.md)、および[CopyTo](../../../ado/reference/ado-api/copyto-method-ado.md)では、既存の**ストリーム**オブジェクトの余分な値は切り捨てられないため、新しいストリームの末尾の位置を**SetEOS**で設定することにより、これらのバイトまたは文字を切り捨てることができます。  
  
> [!CAUTION]
>  **Eos**を実際のストリームの末尾の前の位置に設定すると、新しい**eos**位置以降のすべてのデータが失われます。  
  
## <a name="applies-to"></a>適用対象  
 [Stream オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
