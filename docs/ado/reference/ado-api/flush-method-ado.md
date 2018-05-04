---
title: Flush メソッド (ADO) |Microsoft ドキュメント
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
- _Stream::Flush
- _Stream::raw_Flush
helpviewer_keywords:
- Flush method [ADO]
ms.assetid: 938522b4-f836-4c80-8d27-a598a000f0ee
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d13058d961007e891042ca6aada3fafd09e83a7b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="flush-method-ado"></a>Flush メソッド (ADO)
内容を強制的、[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)を基になるオブジェクトに ADO バッファーに残っている、**ストリーム**が関連付けられています。  
  
## <a name="syntax"></a>構文  
  
```  
  
Stream.Flush  
```  
  
## <a name="remarks"></a>解説  
 このメソッドは、基になるオブジェクトにストリーム バッファーの内容を送信する使用できます: ノードまたはのソースでは、URL で表されるファイルなど、**ストリーム**オブジェクト。 すべての変更することを確認する場合、このメソッドを呼び出す必要がありますの内容に加えられた、**ストリーム**書き込まれています。 ただし、ADO と必要はありません通常を呼び出す**フラッシュ**ADO は継続的にバック グラウンドで可能な限り、バッファーをフラッシュします。 コンテンツの変更、**ストリーム**は自動的に行わ、までにキャッシュされていない**フラッシュ**と呼びます。  
  
 閉じる、**ストリーム**で、[閉じる](../../../ado/reference/ado-api/close-method-ado.md)メソッドの内容はフラッシュ、**ストリーム**自動的に; がありますに明示的に呼び出す必要はありません**をフラッシュ**直前**閉じる**です。  
  
## <a name="applies-to"></a>適用対象  
 [Stream オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
