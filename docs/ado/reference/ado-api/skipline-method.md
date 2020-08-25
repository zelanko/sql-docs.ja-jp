---
description: SkipLine メソッド
title: SkipLine メソッド |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_SkipLine
- _Stream::SkipLine
helpviewer_keywords:
- Skipline method [ADO]
ms.assetid: 0abc00fe-ee09-4c8e-b1f2-48ee9c5f3329
author: rothja
ms.author: jroth
ms.openlocfilehash: c0897d90ffeccabbce57525f268214577a523d92
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2020
ms.locfileid: "88777471"
---
# <a name="skipline-method"></a>SkipLine メソッド
テキスト [ストリーム](./stream-object-ado.md)を読み取るときに、1行全体をスキップします。  
  
## <a name="syntax"></a>構文  
  
```  
  
Stream.SkipLine  
```  
  
## <a name="remarks"></a>解説  
 次の行区切り記号までのすべての文字がスキップされます。 既定では、 [Lineseparator](./lineseparator-property-ado.md) は **adcrlf**です。 以前の [eos](./eos-property.md)をスキップしようとすると、現在の位置は **eos**のままになります。  
  
 **SkipLine**メソッドは、テキストストリームと共に使用されます ([型](./type-property-ado-stream.md)は**adTypeText**)。  
  
## <a name="applies-to"></a>適用対象  
 [Stream オブジェクト (ADO)](./stream-object-ado.md)