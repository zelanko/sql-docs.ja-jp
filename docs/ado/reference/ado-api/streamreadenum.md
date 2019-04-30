---
title: StreamReadEnum |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- StreamReadEnum
helpviewer_keywords:
- StreamReadEnum enumeration [ADO]
ms.assetid: cfa1b416-003a-436f-a21b-bd2397e54db3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 26ccabf3e73a67c14e7201f26e4ebf739a6352cb
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63311861"
---
# <a name="streamreadenum"></a>StreamReadEnum
ストリーム全体、または次の行をから読み取る必要があるかどうかを指定します、 [Stream](../../../ado/reference/ado-api/stream-object-ado.md)オブジェクト。  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|**adReadAll**|-1|既定値です。 以降に現在の位置から、ストリームからすべてのバイトを読み取り、 [EOS](../../../ado/reference/ado-api/eos-property.md)マーカー。 これは唯一の有効な**StreamReadEnum**バイナリ ストリーム値 ([型](../../../ado/reference/ado-api/type-property-ado-stream.md)は**adTypeBinary**)。|  
|**adReadLine**|-2|ストリームから次の行を読み取ります (で指定された、 [LineSeparator](../../../ado/reference/ado-api/lineseparator-property-ado.md)プロパティ)。|  
  
## <a name="adowfc-equivalent"></a>ADO と WFC と同等  
 これらの定数には、ADO と WFC 対応はありません。  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[Read メソッド](../../../ado/reference/ado-api/read-method.md)|[ReadText メソッド](../../../ado/reference/ado-api/readtext-method.md)|
