---
title: Close メソッド (ADO) |Microsoft ドキュメント
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
- Recordset15::Close
- _Stream::Close
- _Record::Close
helpviewer_keywords:
- Close method [ADO]
ms.assetid: 3cdf27d1-a180-4cff-8e42-95dec5fb1b55
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 996da92c866789b91a317c152449f7ca2540d273
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="close-method-ado"></a>Close メソッド (ADO)
開いているオブジェクトとすべての依存オブジェクトを閉じます。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.Close  
```  
  
## <a name="remarks"></a>解説  
 使用して、**閉じる**を終了するメソッド、[接続](../../../ado/reference/ado-api/connection-object-ado.md)、[レコード](../../../ado/reference/ado-api/record-object-ado.md)、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)、または[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)オブジェクト関連付けられたシステム リソースを解放します。 オブジェクトを閉じてから削除されませんがメモリです。プロパティの設定を変更し、後でもう一度開くことができます。 メモリからオブジェクトを完全に回避するのには、オブジェクトを閉じて、オブジェクト変数を設定し、 *Nothing* (Visual Basic で)。  
  
## <a name="connection"></a>接続  
 使用して、**閉じる**を終了するメソッド、**接続**オブジェクトでは、アクティブなも閉じられます**レコード セット**接続に関連付けられているオブジェクト。 A[コマンド](../../../ado/reference/ado-api/command-object-ado.md)オブジェクトに関連付けられている、**接続**を閉じようとしているオブジェクトは残りますが、これが不要になった関連付けられる、**接続**オブジェクトですつまり、その。[ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md)プロパティ設定されます**Nothing**です。 また、**コマンド**オブジェクトの[パラメーター](../../../ado/reference/ado-api/parameters-collection-ado.md)任意のプロバイダー定義パラメーターのコレクションはクリアされます。  
  
 後で呼び出すことができます、[開く](../../../ado/reference/ado-api/open-method-ado-connection.md)メソッドを同じまたは別のデータ ソースへの接続を再確立します。 中に、**接続**オブジェクトが閉じ、データ ソースへの開いている接続を必要とするメソッドを呼び出すと、エラーが発生します。  
  
 閉じる、**接続**オブジェクトの開いているときに**レコード セット**接続上のオブジェクトをロールバック保留中の変更のすべてのページで、**レコード セット**オブジェクト。 明示的に閉じる、**接続**オブジェクト (呼び出し、**閉じる**メソッド) では、トランザクション中に進行状況、エラーが発生します。 場合、**接続**トランザクションが進行中は、オブジェクトがスコープ外分類、ADO 自動的にトランザクションをロールバックします。  
  
## <a name="recordset-record-stream"></a>レコード セットが、レコード、ストリームします。  
 使用して、**閉じる**を終了するメソッド、 **Recordset**、**レコード**、または**ストリーム**オブジェクトが関連付けられているデータとすべての排他アクセスを解放この特定のオブジェクトからデータに幸い可能性があります。 後で呼び出すことができます、[開く](../../../ado/reference/ado-api/open-method-ado-recordset.md)と同じ場合は、変更、オブジェクトを再度開くメソッドの属性です。  
  
 中に、 **Recordset**オブジェクトが閉じられて、ライブのカーソルを必要とするメソッドを呼び出すと、エラーが発生します。  
  
 編集が即時更新モードで実行中の場合は、呼び出し、**閉じる**メソッドが、エラーが生成されます。 代わりに、関数を呼び出す、[更新](../../../ado/reference/ado-api/update-method.md)または[ただし](../../../ado/reference/ado-api/cancelupdate-method-ado.md)メソッド最初。 閉じた場合、 **Recordset**バッチ更新モードで、最後に、すべての変更オブジェクト[UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)呼び出しは失われます。  
  
 使用する場合、[クローン](../../../ado/reference/ado-api/clone-method-ado.md)オープンのコピーを作成するメソッド**レコード セット**オブジェクトの元のまたはクローンを閉じるには影響しません、他のコピーのいずれか。  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[Connection オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|[Record オブジェクト (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|  
|[Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|[Stream オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)|  
  
## <a name="see-also"></a>参照  
 [Open および Close メソッドの例 (VB)](../../../ado/reference/ado-api/open-and-close-methods-example-vb.md)   
 [Open および Close メソッドの例 (VBScript)](../../../ado/reference/ado-api/open-and-close-methods-example-vbscript.md)   
 [Open および Close メソッドの例 (vc++)](../../../ado/reference/ado-api/open-and-close-methods-example-vc.md)   
 [Open メソッド (ADO 接続)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Open メソッド (ADO レコード セット)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Save メソッド](../../../ado/reference/ado-api/save-method.md)
