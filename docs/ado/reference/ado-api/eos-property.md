---
description: EOS プロパティ
title: EOS プロパティ |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- EOS
- Stream::EOS
helpviewer_keywords:
- EOS property
ms.assetid: 57e08c5f-f3ed-4ecd-8c66-50b83b1031d1
author: rothja
ms.author: jroth
ms.openlocfilehash: 47a0f2c7f499b5039d6872c5a229dd445fce1b02
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88444014"
---
# <a name="eos-property"></a>EOS プロパティ
現在の位置が [ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)の末尾にあるかどうかを示します。  
  
## <a name="return-values"></a>戻り値  
 現在の位置がストリームの末尾にあるかどうかを示す **ブール** 値を返します。 ストリーム内のバイト数がこれ以上ない場合、 **EOS**は**True**を返します。現在の位置の後により多くのバイトがある場合は、 **False**を返します。  
  
 ストリームの位置の末尾を設定するには、 [SetEOS](../../../ado/reference/ado-api/seteos-method.md) メソッドを使用します。 現在の位置を確認するには、 [position](../../../ado/reference/ado-api/position-property-ado.md) プロパティを使用します。  
  
## <a name="applies-to"></a>適用対象  
 [Stream オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [EOS および LineSeparator プロパティと SkipLine メソッドの例 (VB)](../../../ado/reference/ado-api/eos-and-lineseparator-properties-and-skipline-method-example-vb.md)   
 [Stream オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
