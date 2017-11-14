---
title: "CommandTypeEnum |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- CommandTypeEnum
helpviewer_keywords:
- CommandTypeEnum enumeration [ADO]
ms.assetid: 4b1feb9c-a855-40fe-a906-efe688687e9f
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: bc2cd3acc56c11bdab98d58c1adc76d98eb1579d
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="commandtypeenum"></a>CommandTypeEnum
コマンドの引数を解釈する方法を指定します。  
  
 ユーザーが指定したを検証することが重要*クラスヒント*アプリケーションのユーザーに実行する ADO の危険性のあるコマンドを挿入する機会を提供しないようにする値。  
  
|定数|値|Description|  
|--------------|-----------|-----------------|  
|**adCmdUnspecified**|-1|コマンドの型引数を指定しません。|  
|**adCmdText**|1|評価[CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md)コマンドまたはストアド プロシージャのテキストの定義として呼び出します。|  
|**adCmdTable**|2|評価**CommandText**列を持つがすべて、内部的に生成された SQL クエリによって返されるテーブル名とします。|  
|**adCmdStoredProc**|4|評価**CommandText**としてストアド プロシージャの名前。|  
|**adCmdUnknown**|8|既定値です。 示しますコマンドの種類、 **CommandText**プロパティが不明です。<br /><br /> ADO で解釈するいくつかの試行は、コマンドの種類が認識されていない場合、 **CommandText**です。<br /><br /> -   **CommandText**コマンドまたはストアド プロシージャの呼び出しのテキストの定義として解釈されます。 これと同じ動作**adCmdText**です。<br />-   **CommandText**ストアド プロシージャの名前を指定します。 これと同じ動作**adCmdStoredProc**です。<br />-   **CommandText**は、テーブルの名前として解釈されます。 内部的に生成された SQL クエリでは、すべての列が返されます。 これと同じ動作**adCmdTable**です。|  
|**adCmdFile**|256|評価**CommandText**の永続的に格納されたファイル名として[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)です。 と共に使用**レコード セット**。[開く](../../../ado/reference/ado-api/open-method-ado-recordset.md)または[Requery](../../../ado/reference/ado-api/requery-method.md)のみです。|  
|**adCmdTableDirect**|512|評価**CommandText**として、テーブル名を持つ列がすべて返されます。 と共に使用**Recordset.Open**または**Requery**のみです。 使用する、[シーク](../../../ado/reference/ado-api/seek-method.md)メソッド、 **Recordset**で開く必要があります**adCmdTableDirect**です。<br /><br /> この値と組み合わせることはできません、 [ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md)値**adAsyncExecute**です。|  
  
## <a name="adowfc-equivalent"></a>該当するショートカットは ADO/WFC  
 パッケージ: **com.ms.wfc.data**  
  
|定数|  
|--------------|  
|AdoEnums.CommandType.UNSPECIFIED|  
|AdoEnums.CommandType.TEXT|  
|AdoEnums.CommandType.TABLE|  
|AdoEnums.CommandType.STOREDPROC|  
|AdoEnums.CommandType.UNKNOWN|  
|AdoEnums.CommandType.FILE|  
|AdoEnums.CommandType.TABLEDIRECT|  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[CommandType プロパティ (ADO)](../../../ado/reference/ado-api/commandtype-property-ado.md)|[Execute メソッド (ADO コマンド)](../../../ado/reference/ado-api/execute-method-ado-command.md)|  
|[Execute メソッド (ADO 接続)](../../../ado/reference/ado-api/execute-method-ado-connection.md)|[Open メソッド (ADO レコード セット)](../../../ado/reference/ado-api/open-method-ado-recordset.md)|  
|[Requery メソッド](../../../ado/reference/ado-api/requery-method.md)||

