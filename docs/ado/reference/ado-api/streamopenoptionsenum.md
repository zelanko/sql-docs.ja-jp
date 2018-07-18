---
title: StreamOpenOptionsEnum |Microsoft ドキュメント
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
- StreamOpenOptionsEnum
helpviewer_keywords:
- StreamOpenOptionsEnum enumeration [ADO]
ms.assetid: 85b6c57f-47ed-46ba-bd92-07882ae9e9d2
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5aca6380229e55ed29c99ea51592e1e618ce0058
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35282621"
---
# <a name="streamopenoptionsenum"></a>StreamOpenOptionsEnum
開くのためのオプションを指定します、[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)オブジェクト。 値は、OR 演算と組み合わせることができます。  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|**adOpenStreamAsync**|1|開く、**ストリーム**非同期モードでのオブジェクト。|  
|**adOpenStreamFromRecord**|4|内容を識別、*ソース*パラメーターを既に開いている[レコード](../../../ado/reference/ado-api/record-object-ado.md)オブジェクト。 既定の動作が扱わ*ソース*ツリー構造でノードを直接参照する URL として。 そのノードに関連付けられている既定のストリームが開かれます。|  
|**adOpenStreamUnspecified**|-1|既定値です。 開始を指定します、**ストリーム**既定のオプションを含むオブジェクト。|  
  
## <a name="adowfc-equivalent"></a>該当するショートカットは ADO/WFC  
 これらの定数には、対応する ADO/WFC はありません。  
  
## <a name="applies-to"></a>適用対象  
 [Open メソッド (ADO Stream)](../../../ado/reference/ado-api/open-method-ado-stream.md)
