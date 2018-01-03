---
title: "StreamWriteEnum |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: StreamWriteEnum
helpviewer_keywords: StreamWriteEnum enumeration [ADO]
ms.assetid: bdbf3405-a0bd-4f02-85d4-e3fe8da3f3f7
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 33aac9b12a63346b6d002f84b1d31637d82c8887
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="streamwriteenum"></a>StreamWriteEnum
行区切り記号に書き込まれる文字列に追加するかどうかを指定します、[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)オブジェクト。  
  
|定数|値|Description|  
|--------------|-----------|-----------------|  
|**adWriteChar**|0|既定値です。 指定した文字列を書き込みます (によって指定された、*データ*パラメーター) を**ストリーム**オブジェクト。|  
|**adWriteLine**|@shouldalert|テキスト文字列と行区切り記号を書き込みます、**ストリーム**オブジェクト。 場合、 [LineSeparator](../../../ado/reference/ado-api/lineseparator-property-ado.md)プロパティが定義されていませんし、実行時エラーが返されます。|  
  
## <a name="adowfc-equivalent"></a>該当するショートカットは ADO/WFC  
 これらの定数には、対応する ADO/WFC はありません。  
  
## <a name="applies-to"></a>適用対象  
 [WriteText メソッド](../../../ado/reference/ado-api/writetext-method.md)
