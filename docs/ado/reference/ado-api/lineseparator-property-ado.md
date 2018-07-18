---
title: LineSeparator プロパティ (ADO) |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
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
ms.openlocfilehash: 76534a2925954c18d54ca7b14a3811d2544e233f
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35279291"
---
# <a name="lineseparator-property-ado"></a>LineSeparator プロパティ (ADO)
テキストの行区切り記号として使用するバイナリの文字を示す[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)オブジェクト。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 取得または設定、 [LineSeparatorsEnum](../../../ado/reference/ado-api/lineseparatorsenum.md)で使用される行の区切り記号の文字を示す値、**ストリーム**です。 既定値は**adCRLF**です。  
  
## <a name="remarks"></a>コメント  
 **LineSeparator**テキストの内容を読み取るときに行を解釈するために使用**ストリーム**です。 行をスキップすることができます、 [SkipLine](../../../ado/reference/ado-api/skipline-method.md)メソッドです。  
  
 **LineSeparator**はテキストでのみ使用**ストリーム**オブジェクト ([型](../../../ado/reference/ado-api/type-property-ado-stream.md)は**adTypeText**)。 場合、このプロパティは無視されます**型**は**adTypeBinary**です。  
  
## <a name="applies-to"></a>適用対象  
 [Stream オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [Stream オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
