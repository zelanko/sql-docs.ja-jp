---
title: StreamReadEnum |Microsoft ドキュメント
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
- StreamReadEnum
helpviewer_keywords:
- StreamReadEnum enumeration [ADO]
ms.assetid: cfa1b416-003a-436f-a21b-bd2397e54db3
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 32b606d6f960dc77f8d90257b8c18d19703620d9
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="streamreadenum"></a>StreamReadEnum
ストリーム全体、または次の行をから読み取る必要があるかどうかを指定します、[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)オブジェクト。  
  
|定数|値|Description|  
|--------------|-----------|-----------------|  
|**adReadAll**|-1|既定値です。 以降に現在の位置からのストリームからすべてのバイトを読み取り、 [EOS](../../../ado/reference/ado-api/eos-property.md)マーカー。 これは唯一の有効な**StreamReadEnum**とバイナリ ストリーム値 ([型](../../../ado/reference/ado-api/type-property-ado-stream.md)は**adTypeBinary**)。|  
|**adReadLine**|-2|ストリームから次の行を読み取ります (によって指定された、 [LineSeparator](../../../ado/reference/ado-api/lineseparator-property-ado.md)プロパティ)。|  
  
## <a name="adowfc-equivalent"></a>該当するショートカットは ADO/WFC  
 これらの定数には、対応する ADO/WFC はありません。  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[Read メソッド](../../../ado/reference/ado-api/read-method.md)|[ReadText メソッド](../../../ado/reference/ado-api/readtext-method.md)|
