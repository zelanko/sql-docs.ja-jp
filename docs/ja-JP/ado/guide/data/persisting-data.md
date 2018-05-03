---
title: データの永続化 |Microsoft ドキュメント
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
helpviewer_keywords:
- persisting data [ADO]
- data updates [ADO], persisting data
- data persistence [ADO]
- updating data [ADO], persisting data
ms.assetid: 21c162ca-2845-4dd8-a49d-e715aba8c461
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 94000226ba1bc2a417cfe25b150a5544d2a0f4cb
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="persisting-data"></a>データの永続化
(たとえば、ラップトップを使用)、ポータブル コンピューター、接続および切断されている状態の両方で実行できるアプリケーションの必要性が生成されます。 ADO には、開発者に、クライアント カーソルを保存する機能を提供することによりこのサポートが追加されて**Recordset**をディスクに、後で再読み込みします。  
  
 この種類の機能は、次のようを使用することがいくつかのシナリオはあります。  
  
-   **旅行:** 外出先でアプリケーションを作成する場合がする変更を行い、後で、データベースに再接続し、およびコミットできる新しいレコードを追加する機能を提供します。  
  
-   **参照を更新する頻度:** 多くの場合、アプリケーションでは、テーブルが参照として使用されます — たとえば、税テーブルを記述します。 頻繁に更新されていては読み取り専用です。 アプリケーションを起動するたびにこのサーバーからのデータを読み取るではなくアプリケーションできますだけからデータを読み込むローカルに保存される**Recordset**です。  
  
 ADO では、保存および読み込み**レコード セット**を使用して、 **Recordset.Save**と**Recordset.Open(,,,adCmdFile)** 、ADO 上のメソッド**Recordset**オブジェクト。  
  
 使用することができます、**レコード セットの保存**、ADO を保持する**Recordset**ディスク上のファイルにします。 (保存することも、 **Recordset** ADO に**ストリーム**オブジェクト。 **ストリーム**オブジェクトは、ガイドの後半で説明します)。後で、使用することができます、**開く**を再度開くメソッド、**レコード セット**を使用する準備ができたらです。 既定では、ADO の保存、 **Recordset**専用 Microsoft 高度なデータ TableGram (adtg 形式) 形式にします。 使用してこのバイナリ形式を指定、 **adPersistADTG PersistFormatEnum**値。 または、保存を選択できます、 **Recordset**を代わりに使用して XML として出力**adPersistXML**です。 レコード セットを XML として保存する方法の詳細については、次を参照してください。 [XML 形式で保持するレコード](../../../ado/guide/data/persisting-records-in-xml-format.md)です。  
  
 構文、**保存**メソッドを次に示します。  
  
```  
  
recordset.  
Save  
Destination, PersistFormat  
  
```  
  
 最初に保存するとき、**レコード セット**を指定する省略可能である*先*です。 省略した場合*先*の値に設定の名前を持つ新しいファイルが作成する、[ソース](../../../ado/reference/ado-api/source-property-ado-recordset.md)のプロパティ、**レコード セット**です。  
  
 省略*先*関数を呼び出すと**保存**後の最初の保存または実行時エラーが発生します。 後で呼び出す場合は、**保存**を新しい*先*、**レコード セット**は新しい場所に保存します。 ただし、新しい移行先と元の送信先が両方開いています。  
  
 **保存**閉じません、**レコード セット**または*先*で作業を続行できるように、**レコード セット**し、最新の変更を保存します。 *移行先*まで開いたまま、**レコード セット**を閉じると、他のアプリケーションで読み取るへの書き込みする間*先*です。  
  
 セキュリティ上の理由から、**保存**メソッドは、Microsoft Internet Explorer によって実行されるスクリプトからの低、カスタムのセキュリティ設定の使用のみを許可します。  
  
 場合、**保存**中に、非同期メソッドが呼び出された**レコード セット**フェッチ、実行、または更新操作が進行中、**保存**非同期操作になるまで待機します。完了します。  
  
 最初の行で始まるレコードが保存された、 **Recordset**です。 ときに、**保存**メソッドが完了すると、現在の行位置はの最初の行に移動、 **Recordset**です。  
  
 最良の結果を次のように設定します。、 [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)プロパティを**adUseClient**で**保存**です。 かどうか、プロバイダーがサポートしないすべての機能を保存するために必要な**レコード セット**オブジェクト、カーソル サービスはその機能を提供します。  
  
 ときに、 **Recordset**に保存されて、 **CursorLocation**プロパティに設定**adUseServer**の更新機能、 **Recordset**は制限されます。 通常、1 つのテーブルの更新、挿入、および削除は許可されて (プロバイダーの機能に依存) のみです。 [再同期](../../../ado/reference/ado-api/resync-method.md)メソッドもこの構成では使用できません。  
  
 *先*パラメーターは OLE DB をサポートする任意のオブジェクトに使用できる**IStream**保存することができます、インターフェイス、**レコード セット**ASP に直接**応答**オブジェクト。  
  
 次の例で、**保存**と**開く**メソッドを使用して永続化、 **Recordset**後で再度開きます。  
  
```  
'BeginPersist  
   conn.ConnectionString = _  
   "Provider=SQLOLEDB;Data Source=MySQLServer;" _  
      & "Integrated Security=SSPI;Initial Catalog=pubs"  
   conn.Open  
  
   conn.Execute "create table testtable (dbkey int " & _  
      "primary key, field1 char(10))"  
   conn.Execute "insert into testtable values (1, 'string1')"  
  
   Set rst.ActiveConnection = conn  
   rst.CursorLocation = adUseClient  
  
   rst.Open "select * from testtable", conn, adOpenStatic, _  
      adLockBatchOptimistic  
  
   'Change the row on the client  
   rst!field1 = "NewValue"  
  
   'Save to a file--the .dat extension is an example; choose  
   'your own extension. The changes will be saved in the file  
   'as well as the original data.  
   MyFile = Dir("c:\temp\temptbl.dat")  
   If MyFile <> "" Then  
       Kill "c:\temp\temptbl.dat"  
   End If  
  
   rst.Save "c:\temp\temptbl.dat", adPersistADTG  
   Set rst = Nothing  
  
   'Now reload the data from the file  
   Set rst = New ADODB.Recordset  
   rst.Open "c:\temp\temptbl.dat", , adOpenStatic, _  
      adLockBatchOptimistic, adCmdFile  
  
   Debug.Print "After Loading the file from disk"  
   Debug.Print "   Current Edited Value: " & rst!field1.Value  
   Debug.Print "   Value Before Editing: " & rst!field1.OriginalValue  
  
   'Note that you can reconnect to a connection and  
   'submit the changes to the data source  
   Set rst.ActiveConnection = conn  
   rst.UpdateBatch  
'EndPersist  
```  
  
## <a name="remarks"></a>解説  
 このセクションでは、次のトピックを扱います。  
  
-   [レコードセットの保持に関する詳細情報](../../../ado/guide/data/more-about-recordset-persistence.md)  
  
-   [フィルター処理されたレコードセットおよび階層レコードセットの保持](../../../ado/guide/data/persisting-filtered-and-hierarchical-recordsets.md)  
  
-   [レコードを XML 形式で保持する](../../../ado/guide/data/persisting-records-in-xml-format.md)
