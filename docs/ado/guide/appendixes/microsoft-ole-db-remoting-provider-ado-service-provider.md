---
title: "Microsoft OLE DB リモート プロバイダー (ADO サービス プロバイダー) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: H1Hack27Feb2017
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- OLE DB remoting provider [ADO]
- providers [ADO], OLE DB remoting provider
- remoting provider [ADO]
ms.assetid: a4360ed4-b70f-4734-9041-4025d033346b
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6d969ae607f15876c21271d2721ed3f33c6949f3
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="microsoft-ole-db-remoting-provider-overview"></a>Microsoft OLE DB のリモート処理のプロバイダーの概要
Microsoft OLE DB リモート プロバイダーをクライアント コンピューターでリモート コンピューター上のデータ プロバイダーを呼び出すためのローカル ユーザーを有効にします。 リモート コンピューター上のローカル ユーザーをした場合と同様、リモート コンピューターのデータ プロバイダーのパラメーターを指定します。 次に、リモート コンピューターにアクセスするリモート プロバイダーによって使用されるパラメーターを指定します。 ローカル ユーザーをした場合とするリモート コンピューターにアクセスできます。

> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。

## <a name="provider-keyword"></a>プロバイダーのキーワード
 OLE DB リモート プロバイダーを起動するには、接続文字列で、次のキーワードと値を指定します。 (プロバイダー名に空白を注意してください)。

```
"Provider=MS Remote"
```

## <a name="additional-keywords"></a>その他のキーワード
 このサービス プロバイダーが呼び出されると、次の他のキーワードが関連します。

|Keyword|Description|
|-------------|-----------------|
|**[データ ソース]**|リモート データ ソースの名前を指定します。 処理のため、OLE DB リモート プロバイダーに渡されます。<br /><br /> このキーワードは、 [.rds ですDataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)オブジェクトの[接続](../../../ado/reference/rds-api/connect-property-rds.md)プロパティです。|

## <a name="dynamic-properties"></a>動的プロパティ
 このサービス プロバイダーが呼び出されると、次の動的プロパティに追加、[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクトの[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)コレクション。

|動的なプロパティ名|Description|
|---------------------------|-----------------|
|**DFMode**|DataFactory モードを示します。 目的のバージョンを指定する文字列、 [DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)サーバー上のオブジェクト。 要求の特定のバージョンへの接続を開く前に、このプロパティを設定、 **DataFactory**です。 要求されたバージョンが使用できない場合、試行されます前のバージョンを使用します。 前のバージョンが存在しない場合、エラーが発生します。 場合**DFMode**が、使用可能なバージョンよりも小さい、エラーが発生します。 このプロパティは、接続の確立後は読み取り専用です。<br /><br /> 有効な文字列値は次のいずれかを指定できます。<br /><br /> -「25」、バージョン 2.5 (既定値)<br />-「21」、バージョン 2.1<br />-「20」-version 2.0<br />-「15」、バージョン 1.5|
|**コマンドのプロパティ**|MS リモート プロバイダーによって、サーバーに送信されるコマンド (行セット) のプロパティの文字列に追加される値を示します。 この文字列の既定値は、vt_empty です。|
|**現在 DFMode**|実際のバージョン番号を示す、 **DataFactory**サーバーにします。 バージョンが要求されたかどうかに表示するには、このプロパティを調べ、 **DFMode**プロパティが受け入れられます。<br /><br /> 長整数型の有効な値は次のいずれかを指定できます。<br /><br /> -25-バージョン 2.5 (既定値)<br />-21-バージョン 2.1<br />-20-version 2.0<br />-15: バージョン 1.5<br /><br /> 追加する"DFMode = 20 です。"を接続文字列を使用する場合、 **MSRemote**データを更新するときに、プロバイダーが、サーバーのパフォーマンスを向上させることができます。 この設定で、 **RDSServer.DataFactory**サーバー上のオブジェクトで少ないリソースを消費するモードを使用します。 ただし、次の機能では、この構成では利用できません。<br /><br /> パラメーター化クエリを使用します。<br />呼び出しの前に、パラメーターまたは列の情報を取得する、 **Execute**メソッドです。<br />-設定**更新プログラムを Transact**に**True**です。<br />行のステータスを取得します。<br />呼び出し、**再同期**メソッドです。<br />更新 (明示的にまたは自動的に) を使用して、**更新プログラムが再同期**プロパティです。<br />-設定**コマンド**または**Recordset**プロパティです。<br />使用する**adCmdTableDirect**です。|
|**ハンドラー**|機能を拡張するサーバー側のカスタマイズのプログラム (またはハンドラー) の名前を示す、 [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)、およびハンドラーによって使用されるパラメーター*、* (をコンマで区切って","). A**文字列**値。|
|**インターネット タイムアウト。**|サーバーとの間を移動する要求を待機するミリ秒単位の最大数を示します。 (既定値は 5 分です)。|
|**リモート プロバイダー**|リモート サーバーで使用するデータ プロバイダーの名前を示します。|
|**リモート サーバー**|この接続で使用するサーバー名および通信プロトコルを示します。 このプロパティは、 [.rds ですDataContro](../../../ado/reference/rds-api/datacontrol-object-rds.md)オブジェクト[サーバー](../../../ado/reference/rds-api/server-property-rds.md)プロパティです。|
|**更新プログラムを transact します。**|設定すると**True**、値を指定すると[UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)が実行されること、サーバーで、トランザクションの内部実行されます。 このブール型の動的プロパティの既定値は**False**です。|

 接続文字列のキーワードとしての名前を指定することで書き込み可能な動的なプロパティを設定することもできます。 たとえば、設定、**インターネット タイムアウト**動的なプロパティを指定して 5 秒を。

```
Dim cn as New ADODB.Connection
cn.Open "Provider=MS Remote;Internet Timeout=5000"
```

 設定またはのインデックスとしての名前を指定して動的なプロパティを取得することがありますも、**プロパティ**プロパティです。 次の例は、取得しの現在の値を印刷する方法を示しています、**インターネット タイムアウト**動的プロパティは、および新しい値に設定します。

```
Debug.Print cn.Properties("Internet Timeout")
cn.Properties("Internet Timeout") = 5000
```

## <a name="remarks"></a>解説
 ADO では 2.0、OLE DB リモート プロバイダーのみで指定、 *ActiveConnection*のパラメーター、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト**開く**メソッドです。 ADO 2.1 以降では、プロバイダーも指定する場合に、 *ConnectionString*のパラメーター、[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクト**開く**メソッドです。

 該当するショートカットは、 **.rds ですDataControl**オブジェクト[SQL](../../../ado/reference/rds-api/sql-property.md)プロパティは使用できません。 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト**開く**メソッド*ソース*引数は代わりに使用されます。

 **注**"...; を指定します。リモート プロバイダー MS リモートを = です。..."4 層のシナリオを作成します。 4 層のシナリオでは、テストされていないと、必要はありません。

## <a name="example"></a>例
 この例で、クエリを実行し、**作成者**のテーブル、 **Pubs**という名前のサーバー上のデータベース*通常*です。 リモート データ ソースおよびリモート サーバーの名前で提供される、[開く](../../../ado/reference/ado-api/open-method-ado-connection.md)のメソッド、[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクト、および SQL クエリで指定された、[開く](../../../ado/reference/ado-api/open-method-ado-recordset.md)のメソッド、[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト。 A **Recordset**オブジェクトが返される、編集、およびデータ ソースを更新するために使用します。

```
Dim rs as New ADODB.Recordset
Dim cn as New ADODB.Connection
cn.Open  "Provider=MS Remote;Data Source=pubs;" & _
         "Remote Server=http://YourServer"
rs.Open "SELECT * FROM authors", cn
...                'Edit the recordset
rs.UpdateBatch     'Equivalent of RDS SubmitChanges
...
```

## <a name="see-also"></a>参照
 [OLE DB のリモート処理のプロバイダーの概要](http://msdn.microsoft.com/en-us/4083b72f-68c4-4252-b366-abb70db5ca2b)

