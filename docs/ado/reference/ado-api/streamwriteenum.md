---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4cc9de1481cc683bddafe2f92959977319600f6a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67928632"
---
# <a name="streamwriteenum"></a>StreamWriteEnum
[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)オブジェクトに書き込まれる文字列に行の区切り記号を追加するかどうかを指定します。  
  
|常時|値|[説明]|  
|--------------|-----------|-----------------|  
|**adWriteChar**|0|既定。 指定された (*データ*パラメーターによって指定された) テキスト文字列を**ストリーム**オブジェクトに書き込みます。|  
|**adWriteLine**|1 で保護されたプロセスとして起動されました|**ストリーム**オブジェクトにテキスト文字列と行区切り記号を書き込みます。 [Lineseparator](../../../ado/reference/ado-api/lineseparator-property-ado.md)プロパティが定義されていない場合は、実行時エラーが返されます。|  
  
## <a name="adowfc-equivalent"></a>同等の ADO/WFC  
 これらの定数には、対応する ADO/WFC がありません。  
  
## <a name="applies-to"></a>適用対象  
 [WriteText メソッド](../../../ado/reference/ado-api/writetext-method.md)
