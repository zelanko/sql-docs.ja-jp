---
title: Connection オブジェクト (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection
helpviewer_keywords:
- Connection object [ADO]
ms.assetid: ef6b1824-5b12-43db-89d7-8f3d13896d4d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 278e2d90ed20b99706f00acf72e2892941c42865
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67933561"
---
# <a name="connection-object-ado"></a>Connection オブジェクト (ADO)
データソースへの開いている接続を表します。  
  
## <a name="remarks"></a>解説  
 **接続**オブジェクトは、データソースとの一意のセッションを表します。 クライアント/サーバーデータベースシステムでは、サーバーへの実際のネットワーク接続と同じになる場合があります。 プロバイダーでサポートされている機能によっては、**接続**オブジェクトの一部のコレクション、メソッド、またはプロパティが使用できないことがあります。  
  
 **接続**オブジェクトのコレクション、メソッド、およびプロパティを使用して、次の操作を実行できます。  
  
-   [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md)、 [ConnectionTimeout](../../../ado/reference/ado-api/connectiontimeout-property-ado.md)、および[Mode](../../../ado/reference/ado-api/mode-property-ado.md)プロパティを使用して接続を開く前に、接続を構成します。 **ConnectionString**は、**接続**オブジェクトの既定のプロパティです。  
  
-   [Cursor location](../../../ado/reference/ado-api/cursorlocation-property-ado.md)プロパティを client に設定して、バッチ更新をサポートする[OLE DB 用の Microsoft Cursor Service](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md)を起動します。  
  
-   [Defaultdatabase](../../../ado/reference/ado-api/defaultdatabase-property.md)プロパティを使用して、接続の既定のデータベースを設定します。  
  
-   [IsolationLevel](../../../ado/reference/ado-api/isolationlevel-property.md)プロパティを使用して、接続で開かれたトランザクションの分離レベルを設定します。  
  
-   [プロバイダー](../../../ado/reference/ado-api/provider-property-ado.md)プロパティを使用して OLE DB プロバイダーを指定してください。  
  
-   [Open](../../../ado/reference/ado-api/open-method-ado-connection.md)メソッドと[Close](../../../ado/reference/ado-api/close-method-ado.md)メソッドを使用して、データソースへの物理接続を確立してから中断します。  
  
-   [Execute](../../../ado/reference/ado-api/execute-method-ado-connection.md)メソッドを使用して接続に対してコマンドを実行し、 [CommandTimeout](../../../ado/reference/ado-api/commandtimeout-property-ado.md)プロパティを使用して実行を構成します。  
  
    > [!NOTE]
    >  Command オブジェクトを使用せずにクエリを実行するには、**接続**オブジェクトの**execute**メソッドにクエリ文字列を渡します。 ただし、コマンドのテキストを永続化して再実行する場合、またはクエリパラメーターを使用する場合は、 [command](../../../ado/reference/ado-api/command-object-ado.md)オブジェクトが必要です。  
  
-   入れ子になったトランザクションを含むオープン接続でトランザクションを管理します。これには、プロバイダーがサポートしている場合は、 [BeginTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md)、 [CommitTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md)、および[RollbackTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md)の各メソッドと[Attributes](../../../ado/reference/ado-api/attributes-property-ado.md)プロパティを使用します。  
  
-   データソースから返されたエラーを[エラー](../../../ado/reference/ado-api/errors-collection-ado.md)コレクションと共に調べます。  
  
-   [Version](../../../ado/reference/ado-api/version-property-ado.md)プロパティで使用されている ADO 実装からバージョンを読み取ります。  
  
-   [OpenSchema](../../../ado/reference/ado-api/openschema-method.md)メソッドを使用して、データベースに関するスキーマ情報を取得します。  
  
 以前に定義された他のオブジェクトとは別に、**接続**オブジェクトを作成できます。  
  
 名前付きコマンドまたはストアドプロシージャは、次のセクションで示すように、**接続**オブジェクトのネイティブメソッドであるかのように実行できます。 名前付きコマンドの名前がストアドプロシージャの名前と同じである場合は、**接続**オブジェクトで "ネイティブメソッドの呼び出し" を呼び出すと、ストアプロシージャではなく、常に名前付きコマンドが実行されます。  
  
> [!NOTE]
>  Microsoft® .NET Framework アプリケーションでは、この機能を使用しないでください (名前付きコマンドまたはストアドプロシージャを、**接続**オブジェクトのネイティブメソッドとして呼び出す) ことはできません。これは、機能の基になる実装が、.NET FRAMEWORK が COM と相互運用する方法と競合するためです。  
  
## <a name="execute-a-command-as-a-native-method-of-a-connection-object"></a>接続オブジェクトのネイティブメソッドとしてコマンドを実行する  
 コマンドを実行する**には、コマンドオブジェクト**[名](../../../ado/reference/ado-api/name-property-ado.md)プロパティを使用して、コマンドに名前を付けます。 **Command**オブジェクトの**ActiveConnection**プロパティを接続に設定します。 次に、コマンド名が**Connection**オブジェクトのメソッドであるかのように使用されているステートメントを実行し、任意のパラメーターを指定します。行が返された場合は、**レコードセット**オブジェクトも指定します。 **レコード**セットのプロパティを設定して、結果の**レコードセット**をカスタマイズします。 次に例を示します。  
  
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
  
## <a name="execute-a-stored-procedure-as-a-native-method-of-a-connection-object"></a>接続オブジェクトのネイティブメソッドとしてストアドプロシージャを実行する  
 ストアドプロシージャを実行するには、ストアドプロシージャ名が**接続**オブジェクトのメソッドであるかのように使用されるステートメントを実行し、その後に任意のパラメーターを指定します。 ADO は、パラメーターの型の "最適な推測" を行います。 次に例を示します。  
  
```  
Dim cnn As New ADODB.Connection  
...  
'Your stored procedure name and any parameters.  
cnn. "parameter"  
```  
  
 **接続**オブジェクトは、スクリプトに対して安全です。  
  
 ここでは、次のトピックについて説明します。  
  
-   [Connection オブジェクトのプロパティ、メソッド、およびイベント](../../../ado/reference/ado-api/connection-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [Command オブジェクト (ADO)](../../../ado/reference/ado-api/command-object-ado.md)   
 [Errors コレクション (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)   
 [Properties コレクション (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [付録 A: プロバイダー](../../../ado/guide/appendixes/appendix-a-providers.md)
