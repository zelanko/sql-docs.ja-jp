---
title: "SQL Server インスタンスの machine learning コンポーネントのアップグレード |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/31/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server (starting with 2016 CTP3)
ms.assetid: 4da80998-f929-4fad-a86f-87d09c1a79ef
caps.latest.revision: 15
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2d9d7ddd95bdbcf6efca98ed94bc305924902b98
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="upgrade-machine-learning-components-in-a-sql-server-instance"></a>SQL Server インスタンスの machine learning コンポーネントをアップグレードします。

Microsoft Machine Learning Server for Windows には、SQL Server のインスタンスに関連付けられた R コンポーネントのアップグレードに使用できるツールが含まれています。 ツールの 2 つのバージョン: ウィザード、およびコマンド ライン ユーティリティです。

この記事では、これらのツールを使用して、SQL Server の互換性のあるインスタンスをアップグレードする方法と、アップグレードされたインスタンスを以前に戻す方法について説明します。

SQL Server 更新プログラムの一環としてアップグレードを取得する場合は、このアップグレード プロセスを使用する必要はありません。 新しいサービス パックまたはサービス リリースをインストールするときに、マシン学習コンポーネントは最新バージョンに常に自動的にアップグレードされます。 のみ affored SLQ Server サービスのリリースより速いペースでコンポーネントをアップグレードする場合は、この proess を使用します。

**適用されます:** SQL Server 2016 の R Services、SQL Server 2017 機械学習のサービス

> [!NOTE]
> この記事の執筆時に、アップグレードは、互換性のある SQL Server 2016 インスタンスにのみ適用されます。  アップグレードは、SQL Server 2017 のサポートされていますが、Microsoft Machine Learning Server アップグレードに使用するの新しいバージョンがリリースされていません。

## <a name="upgrade-an-instance"></a>インスタンスをアップグレードします。

アップグレード プロセスと呼びます**バインディング**新しいモダン ライフ サイクル ポリシーを使用する SQL Server マシン ラーニング コンポーネントのサポートのモデルを変更するため、します。 ただし、アップグレードには、SQL Server データベースのサポートのモデルは変わりません。

一般に、このライセンス システムにより、データ サイエンティストは常に最新バージョンの R を使うことができます。モダン ライフサイクル ポリシーの条項について詳しくは、「[Support Timeline for Microsoft R Server](https://msdn.microsoft.com/microsoft-r/rserver-servicing-support)」(Microsoft R Server のサポート タイムライン) をご覧ください。

インスタンスをバインドするときは、複数の処理が行われます。

+ サポート モデルが変更されます。 SQL Server サービスのリリースに依存するのではなく、サポートは、新しいモダン ライフ サイクル ポリシーに基づいています。
+ 機械学習のインスタンスに関連付けられているコンポーネントは、新しいモダン ライフ サイクル ポリシー下にある最新バージョンを使用してロック ステップで、リリースされるたびに自動的にアップグレードされます。 
+ 新しい R または Python パッケージを追加する場合があります。 たとえば、新しい R パッケージの追加から Microsoft R Server の以前の更新など[MicrosoftML](../using-the-microsoftml-package.md)、 [olapR](../r/how-to-create-mdx-queries-using-olapr.md)、および[sqlrutils](../r/how-to-create-a-stored-procedure-using-sqlrutils.md)です。
+ 新しいパッケージを追加する場合以外は、インスタンスを手動で更新できなくなります。
+ 事前トレーニング済みモデルを追加するオプションがあります。

後で場合リリースごとにインスタンスのアップグレードを停止することは、する必要があります**バインド解除**」の説明に従ってインスタンス[ここ](#bkmk_Unbind)、マシン学習の説明に従ってアップグレードをアンインストールこの記事の内容: [Microsoft R Server for Windows に実行](https://msdn.microsoft.com/microsoft-r/rserver-install-windows)です。 プロセスが完了したら、将来の機械学習の Machine Learning Server ベースのアップグレードは、インスタンスには適用されなくです。

### <a name="bkmk_prereqs"></a>アップグレードの前提条件

1. アップグレードの候補となるインスタンスを識別します。
    + R Services がインストールされた SQL Server 2016
    + 少なくとも Service Pack 1 と CU3

2. 取得**Microsoft R Server**、個別の Windows インストーラーをダウンロードしています。

    [スタンドアロン Windows インストーラーを使用して R Server 9.0.1 を Windows にインストールする方法](https://msdn.microsoft.com/microsoft-r/rserver-install-windows#howtoinstall)

> [!TIP]
> 
> SqlBindR.exe が見つかりませんか。 おそらくをダウンロードしていない R Server まだです。 このユーティリティは、Microsoft R Server 用の Windows インストーラーでのみ使用できます。

### <a name="bkmk_BindWizard"></a>新しいセットアップ ウィザードを使用したアップグレードします。

1. アップグレードするインスタンスがコンピューターに新しい R Server のインストーラーを起動します。
  ![Microsoft R サーバーのセットアップ ウィザード](media/r-server-installer-01.PNG)
2. Microsoft R Server 9.1.0 のライセンス契約に同意し、をクリックして**次**です。
3. R オープン ソース コンポーネントのライセンス条件に同意し、をクリックして**次**です。
4. **インストール フォルダーの選択**既定値を受け入れるか、R ライブラリをインストールする別の場所を指定します。 
5. インストーラーでは、バインドの候補となるすべてのローカル インスタンスを識別します。 インスタンスが表示されない場合は、有効なインスタンスが見つからなかったことを意味します。 サーバーを修正、または R Services がインストールされているかどうかを確認する必要があります。
6. アップグレードして、をクリックする任意のインスタンスの横にあるチェック ボックスをオンに**次**です。
7. 処理時間がかかることができます。
    
    インストール中、SQL Server R Services によって使用される R ライブラリは、Microsoft R Server 9.1.0 のライブラリに置き換えられます。
    
    スタート パッドが、処理して影響はありませんが、R_SERVICES フォルダーでのライブラリが削除されでライブラリを使用する、サービスのプロパティは変更されます`C:\Program Files\Microsoft\R Server\R_SERVER`です。

### <a name="bkmk_BindCmd"></a>コマンドラインを使用したアップグレードします。

Microsoft R Server のインストール後に、単なる SqlBindR.exe ツールをコマンドラインから実行できます。

1. 管理者としてコマンド プロンプトを開き、sqlbindr.exe を含むフォルダーに移動します。 既定の場所は`C:\Program Files\Microsoft\R Server\Setup`
2. 次のコマンドを入力して、使用可能なインスタンスの一覧を表示します。 `SqlBindR.exe /list`
  
   一覧表示されている完全なインスタンス名をメモしておきます。 たとえば、インスタンス名があります`MSSQL13.MSSQLSERVER`既定のインスタンス、またはそのようなものの`SERVERNAME.MYNAMEDINSTANCE`します。
3. "*/bind*" 引数を指定して **SqlBindR.exe** コマンドを実行し、前の手順で返された、アップグレードするインスタンスの名前を指定します。

   たとえば、既定のインスタンスをアップグレードするには、次のように入力します。`SqlBindR.exe /bind MSSQL13.MSSQLSERVER`
4. アップグレードが完了したら、変更されたインスタンスに関連付けられているスタート パッド サービスを再起動します。


## <a name="bkmk_Unbind"></a>元に戻すまたはインスタンスをバインド解除

SQL Server がインストールされている元のライブラリを使用する SQL Server のインスタンスの復元を行う必要があります、**バインド解除**操作します。 こうことか、Microsoft R Server のセットアップ ウィザードを再実行して、コマンドラインから SqlBindR ユーティリティを実行しています。

バインド解除するときに完了、Microsoft R Server 9.1.0 のライブラリが削除され、SQL Server R Services によって使用される元の R ライブラリを復元します。

使用する既定のフォルダーでの R ライブラリ R_SERVICES、SQL Server スタート パッドのプロパティが編集された`C:\Program Files\Microsoft\R Server\R_SERVER`です。

### <a name="unbind-using-the-wizard"></a>ウィザードを使用してバインドを解除します。

1. Microsoft R server 9.1.0 新しいインストーラーをダウンロードします。
2. バインドを解除するインスタンスがコンピューターにインストーラーを実行します。
2. インストーラーでは、バインドの対象となるローカル インスタンスを識別します。
3. 元の SQL Server R Services の構成に戻すには対象のインスタンスの横にあるチェック ボックスをオフにします。
4. Microsoft R Server 9.1.0 のライセンス契約に同意します。 R サーバーを削除する場合でも、使用許諾契約書に同意する必要があります。
5. **[完了]**をクリックします。 プロセスがかかります。

### <a name="unbind-using-the-command-line"></a>コマンドラインを使用してバインドを解除します。

1. コマンド プロンプトを開き、前のセクションで説明したように **sqlbindr.exe** が含まれているフォルダーに移動します。

2. **SqlBindR.exe** コマンドを実行し、"*/unbind*" 引数でインスタンスを指定します。

   たとえば、次のコマンドでは、既定のインスタンスを元に戻します。
   
    `SqlBindR.exe /unbind MSSQL13.MSSQLSERVER`

## <a name="known-issues"></a>既知の問題

このセクションでは、SqlBindR.exe ユーティリティまたは SQL Server インスタンスに影響を与える Microsoft R Server のセットアップ ユーティリティを使用してアップグレードを使用する特定の既知の問題を一覧表示します。

### <a name="restoring-packages-that-were-previously-installed"></a>以前にインストールされたパッケージを復元します。

Microsoft R Server 9.0.1 に含まれているアップグレードのユーティリティで、ユーティリティは、元のパッケージを復元できませんでしたまたは R コンポーネントを完全に、ユーザーが、インスタンスの修復を実行することを必要とするすべてのサービス リリースを適用し、インスタンスを再起動します。

ただし、Microsoft R Server 9.1.0、ため、アップグレードのユーティリティの最新バージョンは自動的に元の R の機能を復元します。 そのため、R コンポーネントを再インストールするか、サーバーを再更新プログラムは必要ありません。 ただし、最初のインストール後に追加された任意の R パッケージをインストールする必要があります。

このタスクがはるかに簡単にインストールし、パッケージの共有パッケージ管理の役割を使用している場合: R コマンドを使用するには、データベース内のレコードを使用して、ファイル システムにインストールされているパッケージを同期して、その逆です。 詳細については、次を参照してください[のインストールと R パッケージを管理する。](installing-and-managing-r-packages.md)

### <a name="cannot-perform-upgrade-from-901"></a>9.0.1 からアップグレードを実行することはできません。

以前にアップグレードする SQL Server 2016 の R Services のインスタンス 9.0.1、Microsoft R server 9.1.0 新しいインストーラーを実行するがすべての有効なインスタンスの一覧を表示され、し、既定では以前にバインドされたインスタンスを選択します。 続行した場合は、以前にバインドされたインスタンスは連結ではありません。 その結果、以前の 9.0.1 のインストールを削除、いずれかの関連するパッケージが新しいバージョンの Microsoft R Server (9.1.0) がインストールされていません。

この問題を回避するには、次のように R Server の既存のインストールを変更できます。
1. コントロール パネルで、開く**プログラム追加と削除**です。
2. Microsoft R Server を見つけてクリックして**変更/変更**です。
3. インストーラーが起動したら、9.1.0 にバインドするインスタンスを選択します。

### <a name="binding-or-unbinding-leaves-multiple-temporary-folders"></a>バインド、またはバインドは、複数の一時フォルダーを残します

場合があります、バインディングおよびバインド解除操作は、一時フォルダーをクリーンアップに失敗します。
次のように名前を持つフォルダーを検索する場合、インストールが完了した後に削除できます。`R_SERVICES_<guid>`

> [!NOTE]
> インストールが完了するまで待機することを確認します。 1 つのバージョンに関連付けられた R ライブラリを削除してから、新しい R ライブラリを追加するのに長時間かかることができます。 操作が完了したら、一時フォルダーは削除されます。

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
|The instance is not bound (インスタンスはバインドされていません)| *unbind* コマンドを実行しましたが、指定したインスタンスはバインドされていません。 互換性のある別のインスタンスを選びます。|
|Not a valid SQL instance ID (有効な SQL インスタンス ID ではありません)| インスタンス名を間違って入力した可能性があります。 *list* 引数を指定してコマンドを再度実行し、使用可能なインスタンス ID を確認してください。|
|No instances found (インスタンスが見つかりませんでした)| このコンピューターには、SQL Server R Services のインスタンスはありません。|
|インスタンスには、互換性のあるバージョンの SQL R Services (データベース内) がインストールされている必要があります。| 詳しくは、このトピックの互換性の要件をご覧ください。|
|An error occurred while unbinding the instance (インスタンスのバインド解除中にエラーが発生しました)| インスタンスをバインド解除できませんでした。 サポートに問い合わせてください。|
|An unexpected error has occurred (予期しないエラーが発生しました)| その他のエラーです。 サポートに問い合わせてください。  |
|No SQL instances found (SQL インスタンスが見つかりませんでした)| このコンピューターには、SQL Server のインスタンスはありません。 |

詳細については、Microsoft R Server のリリース ノートを参照してください。

+ [R Server の新機能](https://docs.microsoft.com/r-server/whats-new-in-r-server)

+ [R Server の既知の問題](https://docs.microsoft.com/r-server/resources-known-issues)

