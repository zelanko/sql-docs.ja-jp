---
title: Requery メソッド |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::Requery
- Recordset15::raw_Requery
helpviewer_keywords:
- Requery method [ADO]
ms.assetid: d81ab76f-1aa8-4ccf-92ec-b65254dc3ea1
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9098ef1000efc4f84f217d1bf13a4d849fa666a8
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="requery-method"></a>Requery メソッド
データが更新、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトの基になるクエリを再実行してオブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
recordset.Requery Options  
```  
  
#### <a name="parameters"></a>パラメーター  
 *Options*  
 省略可。 含むビットマスク[ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md)と[CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md)値がこの操作に影響します。  
  
> [!NOTE]
>  場合*オプション*に設定されている**adAsyncExecute**、この操作は非同期的に実行し、 [RecordsetChangeComplete](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)断定ときにイベントが発行されます。 **ExecuteOpenEnum**値**adExecuteNoRecords**または**adExecuteStream**では使用できません**Requery**です。  
  
## <a name="remarks"></a>解説  
 使用して、 **Requery**の内容全体を更新する方法、 **Recordset**によって元のコマンドと、2 回目のデータを取得するデータ ソースからのオブジェクト。 呼び出すことと同じではこのメソッドを呼び出す、[閉じる](../../../ado/reference/ado-api/close-method-ado.md)と[開く](../../../ado/reference/ado-api/open-method-ado-recordset.md)続けてメソッドです。 現在のレコードを編集して、新しいレコードを追加すると、エラーが発生した場合。  
  
 中に、 **Recordset**オブジェクトが開いている場合、カーソルの特性を定義するプロパティ ([カーソル](../../../ado/reference/ado-api/cursortype-property-ado.md)、 [LockType](../../../ado/reference/ado-api/locktype-property-ado.md)、 [MaxRecords](../../../ado/reference/ado-api/maxrecords-property-ado.md) 。、など) は読み取り専用です。 したがって、 **Requery**メソッド、現在のカーソルの更新のみ可能です。 カーソルのプロパティを変更し、結果を表示、使用する必要があります、[閉じる](../../../ado/reference/ado-api/close-method-ado.md)メソッド、プロパティが読み取り/書き込みをもう一度にならないようにします。 プロパティの設定と呼び出しを変更することができますし、[開く](../../../ado/reference/ado-api/open-method-ado-recordset.md)メソッドにカーソルを閉じて再度開きます。  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [実行、クエリを再実行、およびメソッドの例 (VB) をオフに](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vb.md)   
 [実行、クエリを再実行、およびメソッドの例 (VBScript) をオフに](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vbscript.md)   
 [実行、クエリを再実行、およびメソッドの例 (vc++) をオフに](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vc.md)   
 [CommandText プロパティ (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md)
