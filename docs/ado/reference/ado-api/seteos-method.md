---
title: SetEOS メソッド |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_SetEOS
- _Stream::SetEOS
helpviewer_keywords:
- SetEOS method [ADO]
ms.assetid: 707c18ca-6a56-4970-bbd6-ae1fb86a0b8a
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c845e565786c02af64c20d72c917ae302c6e156c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="seteos-method"></a>SetEOS メソッド
ストリームの末尾の位置を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Stream.SetEOS  
```  
  
## <a name="remarks"></a>解説  
 **SetEOS**の値を更新、 [EOS](../../../ado/reference/ado-api/eos-property.md)現在をすることで、プロパティ[位置](../../../ado/reference/ado-api/position-property-ado.md)ストリームの末尾。 任意のバイト数または文字の現在の位置は切り捨てられます。  
  
 [書き込み](../../../ado/reference/ado-api/write-method.md)、 [WriteText](../../../ado/reference/ado-api/writetext-method.md)、および[CopyTo](../../../ado/reference/ado-api/copyto-method-ado.md)は既存の余分な値は切り詰められません**ストリーム**オブジェクトをこれらを切り捨てることができますバイトまたはキャラクター設定することにより、新しいストリームの終わりに**SetEOS**です。  
  
> [!CAUTION]
>  設定した場合**EOS** 、ストリームの実際の終了前に、新しいすべてのデータが失われます**EOS**位置。  
  
## <a name="applies-to"></a>適用対象  
 [Stream オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
