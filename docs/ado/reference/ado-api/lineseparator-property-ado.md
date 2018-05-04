---
title: LineSeparator プロパティ (ADO) |Microsoft ドキュメント
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
- _Stream::LineSeparator
helpviewer_keywords:
- LineSeparator property [ADO]
ms.assetid: 0b20fbb8-6b83-48ec-b442-f96c8a4bafbb
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e3c82ab9eccb144f3b8615b8c813eb84f9150024
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="lineseparator-property-ado"></a>LineSeparator プロパティ (ADO)
テキストの行区切り記号として使用するバイナリの文字を示す[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)オブジェクト。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 取得または設定、 [LineSeparatorsEnum](../../../ado/reference/ado-api/lineseparatorsenum.md)で使用される行の区切り記号の文字を示す値、**ストリーム**です。 既定値は**adCRLF**です。  
  
## <a name="remarks"></a>解説  
 **LineSeparator**テキストの内容を読み取るときに行を解釈するために使用**ストリーム**です。 行をスキップすることができます、 [SkipLine](../../../ado/reference/ado-api/skipline-method.md)メソッドです。  
  
 **LineSeparator**はテキストでのみ使用**ストリーム**オブジェクト ([型](../../../ado/reference/ado-api/type-property-ado-stream.md)は**adTypeText**)。 場合、このプロパティは無視されます**型**は**adTypeBinary**です。  
  
## <a name="applies-to"></a>適用対象  
 [Stream オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [Stream オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
