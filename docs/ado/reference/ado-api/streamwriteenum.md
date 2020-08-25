---
description: StreamWriteEnum
title: StreamWriteEnum |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- StreamWriteEnum
helpviewer_keywords:
- StreamWriteEnum enumeration [ADO]
ms.assetid: bdbf3405-a0bd-4f02-85d4-e3fe8da3f3f7
author: rothja
ms.author: jroth
ms.openlocfilehash: 343e5fd45a32e45cda342ab01feb64f379054486
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2020
ms.locfileid: "88777161"
---
# <a name="streamwriteenum"></a>StreamWriteEnum
[ストリーム](./stream-object-ado.md)オブジェクトに書き込まれる文字列に行の区切り記号を追加するかどうかを指定します。  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|**adWriteChar**|0|既定値。 指定された ( *データ* パラメーターによって指定された) テキスト文字列を **ストリーム** オブジェクトに書き込みます。|  
|**adWriteLine**|1|**ストリーム**オブジェクトにテキスト文字列と行区切り記号を書き込みます。 [Lineseparator](./lineseparator-property-ado.md)プロパティが定義されていない場合は、実行時エラーが返されます。|  
  
## <a name="adowfc-equivalent"></a>同等の ADO/WFC  
 これらの定数には、対応する ADO/WFC がありません。  
  
## <a name="applies-to"></a>適用対象  
 [WriteText メソッド](./writetext-method.md)