---
title: "Parameters コレクション (ADO) |Microsoft ドキュメント"
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
- Command15::get_Parameters
- Command15::Parameters
- Command15::GetParameters
helpviewer_keywords:
- Parameters collection [ADO]
ms.assetid: 497cae10-3913-422a-9753-dcbb0a639b1b
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9dcfec51eb94eb1ca290ebb3323012e2aaa558b5
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="parameters-collection-ado"></a>Parameters コレクション (ADO)
すべてが含まれています、[パラメーター](../../../ado/reference/ado-api/parameter-object.md)のオブジェクト、[コマンド](../../../ado/reference/ado-api/command-object-ado.md)オブジェクト。  
  
## <a name="remarks"></a>解説  
 A**コマンド**オブジェクトには、**パラメーター**コレクションから成る**パラメーター**オブジェクト。  
  
 使用して、[更新](../../../ado/reference/ado-api/refresh-method-ado.md)メソッドを**コマンド**オブジェクトの**パラメーター**コレクション ストアド プロシージャまたはパラメーター化クエリのパラメーター情報をプロバイダーの取得指定されている、**コマンド**オブジェクト。 ストアド プロシージャの呼び出しまたはパラメーター化クエリ; 一部のプロバイダーをサポートしません。呼び出す、**更新**メソッドを**パラメーター**このようなプロバイダーを使用する場合に、コレクションには、エラーが返されます。  
  
 定義していない、独自場合**パラメーター**オブジェクトとするアクセス、**パラメーター**呼び出す前にコレクション、**更新**メソッド、ADO の呼び出しは自動的に、メソッドのコレクションを設定するとします。  
  
 呼び出すストアド プロシージャに関連付けられている、またはパラメーター化されたクエリ パラメーターのプロパティがわかっている場合は、パフォーマンスを向上させるために、プロバイダーに呼び出しを最小限に抑えることができます。 使用して、 [CreateParameter](../../../ado/reference/ado-api/createparameter-method-ado.md)メソッドを作成**パラメーター**適切なプロパティの設定および使用するオブジェクトを[Append](../../../ado/reference/ado-api/append-method-ado.md)に追加する方法、 **パラメーター**コレクション。 これにより設定およびパラメーターについては、プロバイダーを呼び出さずにパラメーター値を取得できます。 手動で設定する必要がある、パラメーター情報を提供しないプロバイダーを作成している場合、**パラメーター**にパラメーターを使うことができる、このメソッドを使用して、コレクション。 使用して、[削除](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)を削除する**パラメーター**オブジェクトから、**パラメーター**必要な場合は、コレクション。  
  
 内のオブジェクト、**パラメーター**のコレクション、 **Recordset** (したがってが使用できなくなる) スコープ外に移動してときに、**レコード セット**が閉じられます。  
  
 ストアド プロシージャを呼び出すときに**コマンド**、ストアド プロシージャの戻り値の出力パラメーターは次のように取得します。  
  
1.  ストアド プロシージャを呼び出すパラメーターを持たず、ときに、**更新**メソッドを**パラメーター**コレクションを呼び出す前に呼び出す必要があります、 **Execute**メソッドを**コマンド**オブジェクト。  
  
2.  パラメーターとパラメーターを明示的に追加してストアド プロシージャを呼び出すとき、**パラメーター**使用して、コレクション**追加**、戻り値の出力パラメーターが、に追加される**パラメーター**コレクション。 戻り値を追加する必要があります最初、**パラメーター**コレクション。 使用して**Append**に他のパラメーターを追加する、**パラメーター**定義の順序でのコレクション。 たとえば、ストアド プロシージャ SPWithParam では、2 つのパラメーターがあります。 最初のパラメーターでは、*で*、それぞれ (20) として定義されている入力パラメーターと 2 番目のパラメーターは、 *OutParam*それぞれ (20) として定義されている出力パラメーターです。 次のコードで戻り値の出力パラメーターを取得することができます。  
  
    ```  
    ' Open Connection Conn  
    set ccmd = CreateObject("ADODB.Command")  
    ccmd.Activeconnection= Conn  
  
    ccmd.CommandText="SPWithParam"  
    ccmd.commandType = 4 'adCmdStoredProc  
  
    ccmd.parameters.Append ccmd.CreateParameter(, adInteger, adParamReturnValue, , NULL)   ' return value  
    ccmd.parameters.Append ccmd.CreateParameter("InParam", adVarChar, adParamInput, 20, "hello world")   ' input parameter  
    ccmd.parameters.Append ccmd.CreateParameter("OutParam", adVarChar, adParamOuput, 20, NULL)   ' output parameter  
  
    ccmd.execute()  
  
    ' Access ccmd.parameters(0) as return value of this stored procedure  
    ' Access ccmd.parameters("OutParam") as the output parameter of this stored procedure.  
  
    ```  
  
3.  パラメーターと呼び出すことによって、パラメーターを構成して、ストアド プロシージャを呼び出すときに、**項目**メソッドを**パラメーター**コレクション、ストアド プロシージャの戻り値の出力パラメーターのことができます取得する、**パラメーター**コレクション。 たとえば、ストアド プロシージャ SPWithParam では、2 つのパラメーターがあります。 最初のパラメーターでは、*で*、それぞれ (20) として定義されている入力パラメーターと 2 番目のパラメーターは、 *OutParam*それぞれ (20) として定義されている出力パラメーターです。 次のコードで戻り値の出力パラメーターを取得することができます。  
  
    ```  
    ' Open Connection Conn  
    set ccmd = CreateObject("ADODB.Command")  
    ccmd.Activeconnection= Conn  
  
    ccmd.CommandText="SPWithParam"  
    ccmd.commandType = 4 'adCmdStoredProc  
  
    ccmd.parameters.Item("InParam").value = "hello world" ' input parameter  
    ccmd.execute()  
  
    ' Access ccmd.parameters(0) as return value of stored procedure  
    ' Access ccmd.parameters(2) or ccmd.parameters("OutParam") as the output parameter.  
    ```  
  
 このセクションには、次のトピックが含まれています。  
  
-   [パラメーター コレクションのプロパティ、メソッド、およびイベント](../../../ado/reference/ado-api/parameters-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [Append メソッド (ADO)](../../../ado/reference/ado-api/append-method-ado.md)   
 [CreateParameter メソッド (ADO)](../../../ado/reference/ado-api/createparameter-method-ado.md)   
 [パラメーター オブジェクト](../../../ado/reference/ado-api/parameter-object.md)

