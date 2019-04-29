---
title: Flush メソッド (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::Flush
- _Stream::raw_Flush
helpviewer_keywords:
- Flush method [ADO]
ms.assetid: 938522b4-f836-4c80-8d27-a598a000f0ee
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 66deae3833a738075259928855881f87b64ef0dd
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63028117"
---
# <a name="flush-method-ado"></a>Flush メソッド (ADO)
内容を強制的、 [Stream](../../../ado/reference/ado-api/stream-object-ado.md)を基になるオブジェクトへの ADO のバッファーに残っている、 **Stream**が関連付けられています。  
  
## <a name="syntax"></a>構文  
  
```  
  
Stream.Flush  
```  
  
## <a name="remarks"></a>コメント  
 基になるオブジェクトにストリーム バッファーの内容を送信するこのメソッドを使用できます。 ノードまたはのソースでは、URL で表されるファイルなど、 **Stream**オブジェクト。 すべての変更することを確認する場合、このメソッドを呼び出す必要がありますの内容に加え、 **Stream**書き込まれています。 ただし、ADO を使用した必要はありませんは、通常を呼び出す**フラッシュ**ADO は継続的にバック グラウンドで可能な限り、バッファーをフラッシュします。 コンテンツの変更、 **Stream**キャッシュされないまでに、自動的に行われる**フラッシュ**が呼び出されます。  
  
 閉じる、 **Stream**で、[閉じる](../../../ado/reference/ado-api/close-method-ado.md)メソッドの内容をフラッシュ、 **Stream**は自動的に明示的に呼び出す必要はありません**をフラッシュ**直前**閉じる**します。  
  
## <a name="applies-to"></a>適用対象  
 [Stream オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
