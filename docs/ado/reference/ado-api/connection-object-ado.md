---
title: "接続オブジェクト (ADO) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
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
- Connection
helpviewer_keywords:
- Connection object [ADO]
ms.assetid: ef6b1824-5b12-43db-89d7-8f3d13896d4d
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 7beb64b0620b1a5b603c02cb36904e3a42f5b3f7
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="connection-object-ado"></a>接続オブジェクト (ADO)
データ ソースへの接続を開くを表します。  
  
## <a name="remarks"></a>解説  
 A**接続**オブジェクトは、データ ソースとの一意のセッションを表します。 クライアント/サーバー データベース システムでは、サーバーへの実際のネットワーク接続と同じ場合があります。 プロバイダー、いくつかのコレクション、メソッド、またはのプロパティがサポートする機能によって、**接続**オブジェクトを使用できない可能性があります。  
  
 コレクション、メソッド、およびプロパティの使用、**接続**オブジェクトを次を行うことができます。  
  
-   開く前に接続を構成、 [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md)、 [ConnectionTimeout](../../../ado/reference/ado-api/connectiontimeout-property-ado.md)、および[モード](../../../ado/reference/ado-api/mode-property-ado.md)プロパティです。 **ConnectionString**の既定のプロパティは、**接続**オブジェクト。  
  
-   設定、 [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)プロパティを呼び出すクライアントを[OLE DB 用の Microsoft カーソル サービス](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md)、一括更新をサポートしています。  
  
-   既定のデータベースとの接続の設定、 [DefaultDatabase](../../../ado/reference/ado-api/defaultdatabase-property.md)プロパティです。  
  
-   セットへの接続でのトランザクションの分離レベルを開く、 [IsolationLevel](../../../ado/reference/ado-api/isolationlevel-property.md)プロパティです。  
  
-   OLE DB プロバイダーを指定、[プロバイダー](../../../ado/reference/ado-api/provider-property-ado.md)プロパティです。  
  
-   作成、および後で切断を持つデータ ソースへの物理的な接続、[開く](../../../ado/reference/ado-api/open-method-ado-connection.md)と[閉じる](../../../ado/reference/ado-api/close-method-ado.md)メソッドです。  
  
-   接続のコマンドを実行、 [Execute](../../../ado/reference/ado-api/execute-method-ado-connection.md)メソッドの実行を構成して、 [CommandTimeout](../../../ado/reference/ado-api/commandtimeout-property-ado.md)プロパティです。  
  
    > [!NOTE]
    >  実行するには、クエリ コマンド オブジェクトを使用せずにクエリ文字列を渡す、 **Execute**のメソッド、**接続**オブジェクト。 ただし、[コマンド](../../../ado/reference/ado-api/command-object-ado.md)コマンド テキストを保持し、再実行するか、またはクエリ パラメーターを使用するときに、オブジェクトが必要です。  
  
-   プロバイダーは、それらをサポートしている場合は、入れ子になったトランザクションを含め、開いている接続に対してトランザクションを管理、 [BeginTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md)、 [CommitTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md)、および[RollbackTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md)メソッドおよび[属性](../../../ado/reference/ado-api/attributes-property-ado.md)プロパティです。  
  
-   使用して、データ ソースから返されたエラーを調べて、[エラー](../../../ado/reference/ado-api/errors-collection-ado.md)コレクション。  
  
-   使用されている ADO 実装からバージョンを読み取る、[バージョン](../../../ado/reference/ado-api/version-property-ado.md)プロパティです。  
  
-   使用してデータベースに関するスキーマ情報を取得、 [OpenSchema](../../../ado/reference/ado-api/openschema-method.md)メソッドです。  
  
 作成することができます**接続**他の定義済みのオブジェクトとは別にオブジェクト。  
  
 場合と同様ネイティブ メソッドの名前付きコマンドまたはストアド プロシージャを実行することができます、**接続**オブジェクトを次のセクションで示すようにします。 名前付きコマンドがストアド プロシージャのと同じ名前を持つ、"ネイティブ呼び出しメソッドを呼び出す"で、**接続**オブジェクトは常にストアド プロシージャではなく名前付きのコマンドを実行します。  
  
> [!NOTE]
>  この機能を使用しないでください (場合と同様、ネイティブ メソッドの名前付きコマンドまたはストアド プロシージャを呼び出して、**接続**オブジェクト)、Microsoft® .NET Framework アプリケーションのため機能競合の基になる実装.NET Framework を方法には、com 相互運用します。  
  
## <a name="execute-a-command-as-a-native-method-of-a-connection-object"></a>接続オブジェクトのネイティブ メソッドとしてコマンドを実行します。  
 コマンドを実行するには、付与、コマンドを使用して名前、**コマンド**オブジェクト[名前](../../../ado/reference/ado-api/name-property-ado.md)プロパティです。 設定、 **ActiveConnection**のプロパティ、**コマンド**接続するオブジェクト。 メソッドがある場合のように、コマンド名が使用されているステートメントを発行し、**接続**すべてのパラメーターの前に、オブジェクトと**レコード セット**オブジェクトのかどうか、すべての行が返されます。 設定、 **Recordset**プロパティをその結果をカスタマイズする**レコード セット**です。 例:  
  
```  
Dim cnn As New ADODB.Connection  
Dim cmd As New ADODB.Command  
Dim rst As New ADODB.Recordset  
...  
cnn.Open "..."  
cmd.Name = "yourCommandName"  
cmd.ActiveConnection = cnn  
...  
'Your command name, any parameters, and an optional Recordset.  
cnn. "parameter", rst  
```  
  
## <a name="execute-a-stored-procedure-as-a-native-method-of-a-connection-object"></a>接続オブジェクトのネイティブ メソッドとしてストアド プロシージャを実行します。  
 ストアド プロシージャを実行する場合と同様、メソッドで、ストアド プロシージャ名が使用されているステートメントを発行、**接続**任意のパラメーターの前に、オブジェクトです。 ADO とパラメーターの型「最善の推測」になります。 例:  
  
```  
Dim cnn As New ADODB.Connection  
...  
'Your stored procedure name and any parameters.  
cnn. "parameter"  
```  
  
 **接続**オブジェクトにスクリプトを実行しても安全です。  
  
 このセクションには、次のトピックが含まれています。  
  
-   [接続オブジェクトのプロパティ、メソッド、およびイベント](../../../ado/reference/ado-api/connection-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [コマンド オブジェクト (ADO)](../../../ado/reference/ado-api/command-object-ado.md)   
 [Errors コレクション (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)   
 [プロパティのコレクション (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [レコード セット オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [付録 A: プロバイダー](../../../ado/guide/appendixes/appendix-a-providers.md)
