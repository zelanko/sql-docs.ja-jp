---
title: StreamWriteEnum | Microsoft Docs
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- StreamWriteEnum
helpviewer_keywords:
- StreamWriteEnum enumeration [ADO]
ms.assetid: bdbf3405-a0bd-4f02-85d4-e3fe8da3f3f7
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 36c18f5452a07e5dc44a9396ee993a163b98d3bd
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="streamwriteenum"></a>StreamWriteEnum
行区切り記号に書き込まれる文字列に追加するかどうかを指定します、[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)オブジェクト。  
  
|定数|[値]|Description|  
|--------------|-----------|-----------------|  
|**adWriteChar**|0|既定値です。 指定した文字列を書き込みます (によって指定された、*データ*パラメーター) を**ストリーム**オブジェクト。|  
|**adWriteLine**|1|テキスト文字列と行区切り記号を書き込みます、**ストリーム**オブジェクト。 場合、 [LineSeparator](../../../ado/reference/ado-api/lineseparator-property-ado.md)プロパティが定義されていませんし、実行時エラーが返されます。|  
  
## <a name="adowfc-equivalent"></a>該当するショートカットは ADO/WFC  
 これらの定数には、対応する ADO/WFC はありません。  
  
## <a name="applies-to"></a>適用対象  
 [WriteText メソッド](../../../ado/reference/ado-api/writetext-method.md)
