---
title: "SqlBindR.exe を使って R Services のインスタンスをアップグレードする | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server (starting with 2016 CTP3)"
ms.assetid: 4da80998-f929-4fad-a86f-87d09c1a79ef
caps.latest.revision: 15
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 8
---
# SqlBindR.exe を使って R Services のインスタンスをアップグレードする
Microsoft R Server for Windows に含まれる新しいツール **SqlBindR.exe** を使って、インスタンスの R コンポーネントをアップグレードできます。 このプロセスは、SQL Server 2016 インスタンスのライセンス モデルを新しい Microsoft Modern Software Lifecycle Support ライセンスに変更するので、**バインド**と呼ばれます。

一般に、このライセンス システムにより、データ サイエンティストは常に最新バージョンの R を使うことができます。マイクロソフト ソフトウェア ライセンスの条項および利点の詳細については、「[Run Microsoft R Server for Windows](https://msdnstage.redmond.corp.microsoft.com/en-us/microsoft-r/rserver-install-windows?branch=r-server-nov16-dev)」 (Microsoft R Server for Windows を実行する) をご覧ください。

インスタンスをバインドするときは、次の 3 つの処理が行われます。
+ インスタンスのサポート ポリシーが、SQL Server 2016 のサポート ポリシーから、新しい Microsoft Modern Software License 使用許諾契約に変更されます。
+ そのインスタンスに関連付けられている R コンポーネントは、現在は新しい Modern Software License 条項の下にある R サーバー バージョンのロック ステップにおいて、各リリースで自動的にアップグレードされます。
+ 新しいパッケージを追加する場合以外は、インスタンスを手動で更新できなくなります。 

各リリースでのインスタンスのアップグレードを停止する場合は、「[Run Microsoft R Server for Windows](https://msdn.microsoft.com/microsoft-r/rserver-install-windows)」 (Microsoft R Server for Windows を実行する) で説明されているように、インスタンスを**バインド解除**した後、Microsoft R Server コンポーネントをアンインストールする必要があります。 プロセスが完了すると、将来の R Server のアップグレードはインスタンスに反映されなくなります。

> [!NOTE] アップグレード プロセスは、Cumulative Update 3.0 がパッチされた SQL Server 2016 インスタンスに対してのみサポートされます。  
> 
> SQL Server vNext で R Services を使っている場合は、このアップグレードを適用する必要はありません。 R コンポーネントは、各マイルストーンで常に自動的にアップグレードされます。

## <a name="how-to-upgrade-an-instance"></a>インスタンスをアップグレードする方法


1. アップグレードするインスタンスがあるコンピューター上で、Microsoft R Server のインストーラーを実行します。
2. インストールが完了した後、**SqlBindR.exe** ツールが含まれるフォルダーに移動します。 既定の場所は次のとおりです。`C:\Program Files\Microsoft\R Server\Setup`
2. 管理者としてコマンド プロンプトを開きます。
3. 次のコマンドを入力して、使用可能なインスタンスの一覧を表示します。`SqlBindR.exe /list`
4. **SqlBindR.exe** コマンドを実行し、*/bind* 引数でアップグレードするインスタンスの名前を指定します。 
   たとえば、既定のインスタンスだけをアップグレードするには、次のように入力します。 `SqlBindR.exe /bind MSSQL14.MSSQLSERVER`

## <a name="how-to-downgrade-an-instance-of-r-services"></a>R Services のインスタンスをダウングレードする方法

インスタンスの状態を元に戻すには、SqlBindR ツールを実行してライセンスを削除した後、インスタンスを修復または再インストールする必要があります。

1. **SqlBindR.exe** コマンドを実行し、*/unbind* 引数でインスタンスを指定します。 
   たとえば、次のコマンドを実行すると、既定のインスタンスが SQL Server ライセンスと SQL Server 更新スケジュールに従うように戻ります。 `SqlBindR.exe /unbind MSSQL14.MSSQLSERVER`
2. インスタンスを元の状態に復元するには、次のいずれかのようにします。
    + インスタンスを修復します。 修復操作は、インストールされているすべての機能に更新を適用します。
    + アンインストールおよび再インストールしてから、すべてのサービス リリースを適用します。 インスタンスを開始し直す必要があります。
3. R Server が削除された後、インスタンスと共にインストールされたすべてのパッケージも削除されるので、再インストールする必要があります。

## <a name="requirements"></a>必要条件
アップグレードは、次の要件を満たす SQL Server 2016 のインスタンスに対してのみサポートされます。
+ SQL Server 2016 SP1 以降
+ Cumulative Update 3.0 (OD) が適用されていること

現在のアップグレードは、コマンド ライン ツールを使うことによってのみサポートされます。 対話型インターフェイスは、今後のリリースで提供されます。

## <a name="sqlbindrexe-command-syntax"></a>sqlbindr.exe コマンドの構文


### <a name="usage"></a>使用方法

`sqlbindr [/list] [/bind <SQL_instance_ID>] [/unbind <SQL_instance_ID>]`

### <a name="parameters"></a>パラメーター

|名前|Description|
|------|------|
|*list*| 現在のコンピューター上にあるすべての SQL データベース インスタンスの ID を一覧表示します|
|*bind*| 指定された SQL データベース インスタンスを R Server の最新バージョンにアップグレードし、インスタンスが R Server の今後のアップグレードを自動的に取得するようにします|
|*unbind*|R Server の最新バージョンを指定した SQL データベース インスタンスからアンインストールし、R Server の今後のアップグレードがインスタンスに影響を与えないようにします|

### <a name="errors"></a>エラー

このツールでは、次のエラー メッセージが返されます。

|[エラー]|解決策|
|------|------|
|An error occurred while binding the instance (インスタンスのバインド中にエラーが発生しました)| インスタンスをバインドできませんでした。 サポートに問い合わせてください。|
|The instance is already bound (インスタンスは既にバインドされています)| *bind* コマンドを実行しましたが、指定したインスタンスは既にバインドされています。 別のインスタンスを選択してください。|
|The instance is not bound (インスタンスはバインドされていません)| *unbind* コマンドを実行しましたが、指定したインスタンスはバインドされていません。 別のインスタンスを選択してください。|
|Not a valid SQL instance ID (有効な SQL インスタンス ID ではありません)| インスタンス名を間違って入力した可能性があります。 *list* 引数を指定してコマンドを再度実行し、使用可能なインスタンス ID を確認してください。|
|No instances found (インスタンスが見つかりませんでした)| このコンピューターには、SQL Server R Services のインスタンスはありません。|
|インスタンスには、互換性のあるバージョンの SQL R Services (データベース内) がインストールされている必要があります。| 詳細については、https://go.microsoft.com/fwlink/?linkid=835761 をご覧ください。|
|An error occurred while unbinding the instance (インスタンスのバインド解除中にエラーが発生しました)| インスタンスをバインド解除できませんでした。 サポートに問い合わせてください。|
|An unexpected error has occurred (予期しないエラーが発生しました)| その他のエラーです。 サポートに問い合わせてください。  |
|No SQL instances found (SQL インスタンスが見つかりませんでした)| このコンピューターには、SQL Server のインスタンスはありません。 |


## <a name="see-also"></a>参照

[R Server リリース ノート](https://msdn.microsoft.com/microsoft-r/notes/r-server-notes)
