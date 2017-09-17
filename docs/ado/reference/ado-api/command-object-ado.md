---
title: "コマンド オブジェクト (ADO) |Microsoft ドキュメント"
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
- Command
helpviewer_keywords:
- Command object [ADO]
ms.assetid: a02c22fb-542d-465e-a629-30fd59dcbebf
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 863c922dce68f5e3108136baf90ebc5a3d0b697a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="command-object-ado"></a>コマンド オブジェクト (ADO)
データ ソースに対して実行しようとする特定のコマンドを定義します。  
  
## <a name="remarks"></a>解説  
 使用して、**コマンド**データベースを照会して、レコードを取得するオブジェクト、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)を一括操作を実行するか、データベースの構造を操作するオブジェクト。 プロバイダーの機能をいくつかに基づいて**コマンド**参照されているときに、コレクション、メソッド、またはプロパティすると、エラーが発生する可能性があります。  
  
 コレクション、メソッド、およびプロパティの使用、**コマンド**オブジェクトを次を行うことができます。  
  
-   コマンド (たとえば、SQL ステートメント) の実行可能ファイルのテキストを定義すると、 [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md)プロパティです。 または、コマンドまたはクエリ構造体の単純なその他の文字列 (たとえば、XML テンプレートのクエリ) を定義してコマンドを[CommandStream](../../../ado/reference/ado-api/commandstream-property-ado.md)プロパティです。  
  
-   必要に応じてで使用されるコマンド言語を示す、 **CommandText**または**CommandStream**で、 [Dialect](../../../ado/reference/ado-api/dialect-property.md)プロパティです。  
  
-   パラメーター化クエリまたはストアド プロシージャの引数を定義[パラメーター](../../../ado/reference/ado-api/parameter-object.md)オブジェクトおよび[パラメーター](../../../ado/reference/ado-api/parameters-collection-ado.md)コレクション。  
  
-   パラメーター名をプロバイダーに渡す必要があるかどうかを示す、 [NamedParameters](../../../ado/reference/ado-api/namedparameters-property-ado.md)プロパティです。  
  
-   コマンドを実行し、返す、 **Recordset**オブジェクトで該当する場合、 [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md)メソッドです。  
  
-   コマンドの種類の指定、 [CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md)パフォーマンスを最適化するために実行する前にプロパティです。  
  
-   プロバイダーを実行する前に、コマンドの準備 (またはコンパイル済み) のバージョンを保存するかどうかを制御、 [Prepared](../../../ado/reference/ado-api/prepared-property-ado.md)プロパティです。  
  
-   プロバイダーがコマンドの実行を待機する秒数を設定、 [CommandTimeout](../../../ado/reference/ado-api/commandtimeout-property-ado.md)プロパティです。  
  
-   開いている接続に関連付ける、**コマンド**オブジェクトを設定してその[ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md)プロパティです。  
  
-   設定、[名前](../../../ado/reference/ado-api/name-property-ado.md)プロパティを識別する、**コマンド**オブジェクト、関連するメソッドとして[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクト。  
  
-   渡す、**コマンド**オブジェクトを[ソース](../../../ado/reference/ado-api/source-property-ado-recordset.md)のプロパティ、 **Recordset**データを取得します。  
  
-   プロバイダー固有の属性へのアクセス、[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)コレクション。  
  
> [!NOTE]
>  使用せず、クエリを実行する、**コマンド**オブジェクト、クエリ文字列を渡す、 [Execute](../../../ado/reference/ado-api/execute-method-ado-connection.md)のメソッド、**接続**オブジェクトか、 [を開く](../../../ado/reference/ado-api/open-method-ado-recordset.md)のメソッド、 **Recordset**オブジェクト。 ただし、**コマンド**コマンド テキストを保持し、再実行するか、またはクエリ パラメーターを使用するときに、オブジェクトが必要です。  
  
 作成する、**コマンド**以前に定義されたとは別にオブジェクト**接続**オブジェクト、設定、 **ActiveConnection**プロパティを有効な接続文字列にします。 ADO が作成されますが、**接続**オブジェクトでは、オブジェクト変数にそのオブジェクトは代入しません。 ただし、複数を関連付ける場合**コマンド**同じ接続では、オブジェクトを明示的に作成し、開く必要があります、**接続**オブジェクトですこの割り当て、**接続。**オブジェクト変数オブジェクト。 確認して、**接続**に割り当てる前に、オブジェクトが正常に開かれた、 **ActiveConnection**のプロパティ、**コマンド**オブジェクトを割り当てるため、閉じられた**接続**オブジェクト、エラーが発生します。 設定しない場合、 **ActiveConnection**のプロパティ、**コマンド**ADO が新たに作成オブジェクトをこのオブジェクト変数**接続**ごとにオブジェクト**コマンド**オブジェクト、同じ接続文字列を使用する場合でもです。  
  
 実行する、**コマンド**呼び出してその[名](../../../ado/reference/ado-api/name-property-ado.md)プロパティに関連付けられている**接続**オブジェクト。 **コマンド**必要があります、 **ActiveConnection**プロパティに設定、**接続**オブジェクト。 場合、**コマンド**パラメーターには、その値を引数としてメソッドに渡します。  
  
 2 つ以上**コマンド**オブジェクトが同じ接続し、いずれかで実行される**コマンド**オブジェクトが出力パラメーターを持つストアド プロシージャ、エラーが発生します。 各実行**コマンド**オブジェクト、別個の接続を使用して、またはその他のすべての接続を切断**コマンド**接続からのオブジェクト。  
  
 **パラメーター**コレクションの既定のメンバーは、**コマンド**オブジェクト。 その結果、次の 2 つのコード ステートメントは等価です。  
  
```  
objCmd.Parameters.Item(0)  
objCmd(0)  
```  
  
-   **コマンド**オブジェクトはスクリプトを実行しても安全ではありません。  
  
 このセクションには、次のトピックが含まれています。  
  
-   [コマンド オブジェクトのプロパティ、メソッド、およびイベント](../../../ado/reference/ado-api/command-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [接続オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Parameters コレクション (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)   
 [プロパティのコレクション (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [付録 a: プロバイダー](../../../ado/guide/appendixes/appendix-a-providers.md)
