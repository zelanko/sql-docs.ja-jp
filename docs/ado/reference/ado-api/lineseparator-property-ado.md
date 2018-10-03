---
title: LineSeparator プロパティ (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::LineSeparator
helpviewer_keywords:
- LineSeparator property [ADO]
ms.assetid: 0b20fbb8-6b83-48ec-b442-f96c8a4bafbb
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0b55f82e92ff74ba359074613205bc8086af81b5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47639360"
---
# <a name="lineseparator-property-ado"></a>LineSeparator プロパティ (ADO)
テキストの行区切り記号として使用する文字をバイナリ示します[Stream](../../../ado/reference/ado-api/stream-object-ado.md)オブジェクト。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 設定または取得を[LineSeparatorsEnum](../../../ado/reference/ado-api/lineseparatorsenum.md)で使用される行の区切り記号を示す値、 **Stream**します。 既定値は**adCRLF**します。  
  
## <a name="remarks"></a>コメント  
 **LineSeparator**テキストの内容を読み取るときに行を解釈するために使用**Stream**します。 行をスキップすることができます、 [SkipLine](../../../ado/reference/ado-api/skipline-method.md)メソッド。  
  
 **LineSeparator**はテキストでのみ使用**Stream**オブジェクト ([型](../../../ado/reference/ado-api/type-property-ado-stream.md)は**adTypeText**)。 場合、このプロパティは無視されます**型**は**adTypeBinary**します。  
  
## <a name="applies-to"></a>適用対象  
 [Stream オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [Stream オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
