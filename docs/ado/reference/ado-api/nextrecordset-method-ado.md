---
title: "NextRecordset メソッド (ADO) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- NextRecordset
- Recordset15::NextRecordset
- Recordset15::raw_NextRecordset
helpviewer_keywords:
- NextRecordset method [ADO]
ms.assetid: ab1fa449-a695-4987-b1ee-bc68f89418dd
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e7650cb3516311f3eb93e93304ba9d20ec874466
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="nextrecordset-method-ado"></a>NextRecordset メソッド (ADO)
現在のクリア[レコード セット](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトを返します**レコード セット**一連のコマンドを進めることで。  
  
## <a name="syntax"></a>構文  
  
```  
  
Set recordset2 = recordset1.NextRecordset(RecordsAffected )  
```  
  
## <a name="return-value"></a>戻り値  
 返します、 **Recordset**オブジェクト。 モデルでは、構文、 *recordset1*と*recordset2*は、同じ**レコード セット**オブジェクト、または別のオブジェクトを使用できます。 個別を使用する場合**Recordset**オブジェクト、リセット、 **ActiveConnection**元のプロパティ**レコード セット**(*recordset1*)後**NextRecordset**を呼び出したエラーを生成します。  
  
#### <a name="parameters"></a>パラメーター  
 *RecordsAffected*  
 省略可。 A**長い**する変数、現在の操作の影響を受けるレコードの数はプロバイダーに返されます。  
  
> [!NOTE]
>  このパラメーターでは、操作によって影響を受けたレコードの数のみを返しますレコードの数を生成するために使用する select ステートメントから返されません、 **Recordset**です。  
  
## <a name="remarks"></a>解説  
 使用して、 **NextRecordset**複合コマンド ステートメントの次のコマンドまたは複数の結果を返すストアド プロシージャの結果を返すメソッド。 開く場合、**レコード セット**複合コマンド ステートメントに基づいて、オブジェクト (たとえば、"選択\*table1; からSELECT \* table2 の") を使用して、 [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md)メソッドを[コマンド](../../../ado/reference/ado-api/command-object-ado.md)または[開く](../../../ado/reference/ado-api/open-method-ado-recordset.md)メソッドを**Recordset**、ADO は最初のコマンドのみを実行しに結果を返します*recordset*です。 ステートメント内の後続のコマンドの結果にアクセスするには、呼び出し、 **NextRecordset**メソッドです。  
  
 その他の結果がある限り、 **Recordset**複合ステートメントを含んでいない切断されているか、プロセス境界を越えてマーシャ リング、 **NextRecordset**メソッドは引き続き返す**Recordset**オブジェクト。 行を返すコマンドが正常に実行されますが、レコード、返されたが返されない場合**Recordset**オブジェクトは開いているが、空になります。 テストを作成することを確認して、この場合、 [BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)と[EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)プロパティが両方とも**True**です。 ない場合は 行を返す実行するコマンドを正常に返された**レコード セット**オブジェクトが閉じ、テストによってことを確認することができますが、[状態](../../../ado/reference/ado-api/state-property-ado.md)プロパティを**レコード セット**です。 ない多くの結果がある場合に*recordset*に設定されます*Nothing*です。  
  
 **NextRecordset**メソッドでは使用できません、切断されている**レコード セット**オブジェクト、場所[ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md)に設定されている**Nothing**(Microsoft Visual Basic で) またはその他の言語には NULL です。  
  
 編集が即時更新モードで実行中の場合は、呼び出し、 **NextRecordset**メソッドには、エラーが生成されます。 関数を呼び出す、[更新](../../../ado/reference/ado-api/update-method.md)または[ただし](../../../ado/reference/ado-api/cancelupdate-method-ado.md)メソッド最初。  
  
 情報を入力して、複合ステートメントで 1 つ以上のコマンドのパラメーターを渡す、[パラメーター](../../../ado/reference/ado-api/parameters-collection-ado.md)コレクション、または元の配列を渡すことによって**開く**または**Execute**呼び出し、パラメーターは、コマンド系列内の各コマンドと同じ順序コレクションまたは配列でなければなりません。 出力パラメーターの値を読み取る前に、すべての結果を読み取りが完了する必要があります。  
  
 複合ステートメント内の各コマンドを実行すると、OLE DB プロバイダーを決定します。 [Microsoft OLE DB Provider for SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md)、たとえば、複合ステートメントを受信したとき、バッチ内のすべてのコマンドを実行します。 その結果**レコード セット**を呼び出すときに返される単に**NextRecordset**です。  
  
 ただし、他のプロバイダー可能性がありますの次のコマンドで実行ステートメント NextRecordset が呼び出された後にのみです。 これらのプロバイダーでは、明示的に閉じる場合、 **Recordset**全体コマンド ステートメントをステップ実行する前にオブジェクトの他のコマンドは実行されません。  
  
## <a name="applies-to"></a>適用対象  
 [レコード セット オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [NextRecordset メソッドの例 (VB)](../../../ado/reference/ado-api/nextrecordset-method-example-vb.md)   
 [NextRecordset メソッドの例 (vc++)](../../../ado/reference/ado-api/nextrecordset-method-example-vc.md)   

