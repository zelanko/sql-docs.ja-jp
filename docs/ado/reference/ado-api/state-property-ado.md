---
title: State プロパティ (ADO) |Microsoft ドキュメント
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
- Command25::State
helpviewer_keywords:
- State property [ADO]
ms.assetid: 0b993bac-2653-40b1-bcbb-5b57b6aae2bf
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c7224efc2976873ff0326aa23a18df1cccbce230
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35282031"
---
# <a name="state-property-ado"></a>State プロパティ (ADO)
すべての該当するオブジェクトのオブジェクトの状態がオープンかクローズかどうかを示します。 オブジェクトは、非同期メソッドを実行する場合は、オブジェクトの現在の状態が接続するを実行するかを取得することを示します。  
  
## <a name="return-value"></a>戻り値  
 返します、**長い**ことができる値、 [ObjectStateEnum](../../../ado/reference/ado-api/objectstateenum.md)値。 既定値は**取得のみ**です。  
  
## <a name="remarks"></a>コメント  
 使用することができます、**状態**プロパティをいつでも、指定したオブジェクトの現在の状態を判断します。  
  
 オブジェクトの**状態**プロパティの値の組み合わせを持つことができます。 たとえば、ステートメントを実行すると、このプロパティがの合計値**可能**と**adStateExecuting**です。  
  
 **状態**プロパティは読み取り専用です。  
  
## <a name="applies-to"></a>適用対象  
  
||||  
|-|-|-|  
|[Command オブジェクト (ADO)](../../../ado/reference/ado-api/command-object-ado.md)|[Connection オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|[Record オブジェクト (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|  
|[Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|[Stream オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)||  
  
## <a name="see-also"></a>参照  
 [ConnectionString、ConnectionTimeout、および (VB) の状態プロパティの例](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vb.md)   
 [ConnectionString、ConnectionTimeout、および (vc++) の状態プロパティの例](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vc.md)   
