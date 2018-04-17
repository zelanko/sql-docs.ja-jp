---
title: Machine learning のコンポーネントを SQL Server で Microsoft Machine Learning のサーバーにバインド |Microsoft ドキュメント
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 3f0818d67bb866326786598f67bb2caac368dda6
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="bind-machine-learning-components-on-sql-server-to-microsoft-machine-learning-server"></a>Machine learning のコンポーネントを SQL Server で Microsoft Machine Learning のサーバーにバインドします。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事のプロセス説明*バインディング*の SQL Server マシン ラーニング Services または Microsoft Machine Learning のサーバーに SQL Server R Services (In-database) インスタンスで R、Python のパッケージをアップグレードするために、高速なリリース パターン。 

バインディングの処理は、サービスの更新メカニズムを変更します。 バインド、せずに、サービス パックや累積更新プログラム (CU) をインストールする場合にのみ、R、Python のパッケージのバージョンが更新されます。 バインディングでは、新しいパッケージのバージョンは、CU リリース スケジュールとは無関係に、インスタンスに適用できます。

バインディングでは、データベース エンジンのインスタンス、データベース エンジン インスタンスではなく自体の Machine Learning または R コンポーネントだけに影響します。 (In-database) インスタンスにのみ適用されます。 (スタンドアロン) のインストールは、スコープ内にない。

場合は、SQL Server のサービスの機械学習のコンポーネントを戻す対象にいつでもすることができます_のバインドを解除_」の説明に従ってインスタンス[ここ](#bkmk_Unbind)と Machine Learning のサーバーをアンインストールします。

**適用されます:** SQL Server 2016 の R Services、SQL Server 2017 機械学習のサービス

## <a name="binding-vs-upgrading"></a>アップグレードするとバインド

機械学習のコンポーネントをアップグレードするプロセスと呼びます**バインディング**新しい最新ソフトウェア ライフ サイクル ポリシーを使用する SQL Server マシン ラーニング コンポーネントのサポートのモデルを変更するため、します。 

一般に、新しいサービス モデルへの切り替えにより、データ サイエンティストは、R または Python の最新バージョンに常に使用できます。 最新のライフ サイクル ポリシーの条件の詳細については、次を参照してください。 [Microsoft R Server のサポート タイムライン](https://docs.microsoft.com/machine-learning-server/resources-servicing-support)です。

> [!NOTE]
> アップグレードでは、SQL Server データベースのサポートのモデルが変更され、SQL Server のバージョンは変更されません。

インスタンスをバインドするときは、複数の処理が行われます。

+ サポート モデルが変更されます。 SQL Server サービスのリリースに依存するのではなく、サポートは、新しいモダン ライフ サイクル ポリシーに基づいています。
+ インスタンスに関連付けられているマシン ラーニング コンポーネントは、各リリースでは、新しいモダン ライフ サイクル ポリシーに従った現在のバージョンのロックの手順で自動的にアップグレードされます。 
+ 新しい R または Python パッケージを追加する場合があります。 たとえば、新しい R パッケージの追加 Microsoft R Server 9.1 に基づいて以前の更新など[MicrosoftML](../using-the-microsoftml-package.md)、 [olapR](../r/how-to-create-mdx-queries-using-olapr.md)、および[sqlrutils](../r/how-to-create-a-stored-procedure-using-sqlrutils.md)です。
+ 新しいパッケージを追加する場合以外は、インスタンスを手動で更新できなくなります。
+ Microsoft によって提供される事前トレーニング済みモデルをインストールするオプションが表示されます。

## <a name="bkmk_prereqs"></a>Prerequisites

アップグレードの候補となるインスタンスの特定から始めます。 場合は、インストーラーを実行し、バインド オプションを選択して、アップグレードと互換性があるインスタンスの一覧を返します。

サポートされるアップグレードと要件の一覧については、次の表を参照してください。

| SQL Server のバージョン| サポートされているアップグレード| 注|
|-----|-----|------|
| SQL Server 2016| Machine Learning サーバー 9.2.1| 必要な最小 Service Pack 1 と CU3 です。 R Services をインストールして有効にする必要があります。|
| SQL Server 2017| Machine Learning サーバー 9.2.1| Machine Learning Services (In-database) をインストールして有効にする必要があります。 |

## <a name="bind-or-upgrade-an-instance"></a>バインドまたはのインスタンスをアップグレード

学習のサーバーの Windows コンピューターには、コンピューターをアップグレードする言語および SQL Server のインスタンスに関連付けられているツールについて学習に使用できるツールが含まれています。 ツールの 2 つのバージョン: ウィザード、およびコマンド ライン ユーティリティです。

ウィザードまたはコマンド ライン ツールを実行することができます、前に、機械学習のコンポーネントのスタンドアロン インストーラーの最新バージョンをダウンロードする必要があります。

+ [機械学習の windows Server 9.2.1 をインストールします。](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install)

+ [オフライン インストールに必要なコンポーネントをダウンロードします。](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-offline)

### <a name="bkmk_BindWizard"></a>新しいセットアップ ウィザードを使用したアップグレードします。

1. Machine Learning のサーバーの新しいインストーラーを起動します。 アップグレードするインスタンスがコンピューターでインストーラーを実行してください。

    ![Microsoft Machine Learning のサーバーのセットアップ ウィザード](media/mls-921-installer-start.PNG)

2. ページで、 **、インストールを構成する**をアップグレードするコンポーネントを確認し、互換性のあるインスタンスの一覧を確認します。 インスタンスが表示されない場合は、確認、[の前提条件](#bkmk_prereqs)です。

    インスタンスをアップグレードするには、インスタンス名の横にあるチェック ボックスを選択します。 インスタンスを選択しない場合は、Machine Learning のサーバーの別のインストールが作成され、SQL Server ライブラリは変更されていません。

    ![Microsoft Machine Learning のサーバーのセットアップ ウィザード](media/configure-the-installation.PNG)

3. **使用許諾契約書**] ページで、[**これらの条項に同意**Machine Learning のサーバーのライセンス条項に同意します。 

4. 連続するページで、Microsoft R Open または Python Anaconda ディストリビューションなど、選択したすべてのオープン ソース コンポーネントの追加のライセンス条件に同意を提供します。

5. **少し** ページで、インストール フォルダーのメモしておきます。 既定のフォルダーは`~\Program Files\Microsoft\ML Server`します。

    インストール フォルダーを変更する場合は、クリックして**詳細**ウィザードの最初のページに戻ります。 ただし、前のすべての選択を行う必要があります。

6. オフライン コンポーネントをインストールする場合は、Microsoft R Open、Python サーバー、および Python のオープンなどの必要なマシン ラーニング コンポーネントの場所の促さ可能性があります。

インストール プロセス中に SQL Server で使用される R または Python のライブラリが置き換えられ、スタート パッドを更新して、新しいコンポーネントを使用します。 その結果、インスタンスは、以前 R_SERVICES の既定のフォルダーでライブラリを使用、アップグレード後にこれらのライブラリとが削除ライブラリを使用する、新しい場所に、スタート パッド サービスのプロパティが変更されます。

### <a name="bkmk_BindCmd"></a>コマンドラインを使用したアップグレードします。

ウィザードを使用したくない場合は、Machine Learning のサーバーをインストールし、インスタンスをアップグレードするためのコマンドラインから SqlBindR.exe ツールを実行します。

> [!TIP]
> 
> SqlBindR.exe が見つかりませんか。 おそらくをダウンロードしていないこれらのコンポーネントです。 このユーティリティは、Machine Learning サーバー用の Windows インストーラーでのみ使用できます。

1. 管理者としてコマンド プロンプトを開き、sqlbindr.exe を含むフォルダーに移動します。 既定の場所は `C:\Program Files\Microsoft\MLServer\Setup`

2. 次のコマンドを入力して、使用可能なインスタンスの一覧を表示します。 `SqlBindR.exe /list`
  
   一覧表示されている完全なインスタンス名をメモしておきます。 たとえば、インスタンス名があります`MSSQL14.MSSQLSERVER`、既定のインスタンスまたはよう`SERVERNAME.MYNAMEDINSTANCE`です。

3. 実行、 **SqlBindR.exe**コマンドと、 */bind*引数、し、前の手順で返されたインスタンス名を使用して、アップグレードするインスタンスの名前を指定します。

   たとえば、既定のインスタンスをアップグレードするには、次のように入力します。  `SqlBindR.exe /bind MSSQL14.MSSQLSERVER`

4. アップグレードが完了したら、変更されている任意のインスタンスに関連付けられている、スタート パッド サービスを再起動します。

## <a name="bkmk_Unbind"></a>元に戻すまたはインスタンスをバインド解除

不要になったする、機械学習の Machine Learning のサーバーを使用してコンポーネントをアップグレードする場合は、する必要があります_バインド解除_インスタンスし、マシン学習サーバーをアンインストールします。

+ インスタンスをバインド解除します。

    インスタンスのバインドを解除し、これら 2 つのメソッドのいずれかを使用して、SQL Server がインストールされている元のライブラリに戻すことができます。

    + [セットアップ ウィザードを使用して](#bkmk_wizunbind)Machine Learning のサーバーのインスタンスのすべての機能の選択を解除
    + [SqlBindR ユーティリティを使用して](#bkmk_cmdunbind)で、`/unbind`インスタンス名を引数。

    バインドを解除のプロセスが完了したら、将来の機械学習の Machine Learning Server ベースのアップグレードは、インスタンスには適用されなくです。

+ 機械学習のサーバーをアンインストールします。

    手順については、次を参照してください。 [Windows 用の Machine Learning サーバーのアンインストール](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-uninstall)です。 

### <a name="bkmk_wizunbind"></a> ウィザードを使用してバインドを解除します。

1. Machine Learning サーバー用のインストーラーを見つけます。 インストーラーを削除した場合は、もう一度、ダウンロードするか、別のコンピューターからコピーする必要があります。
2. バインド解除するインスタンスがコンピューターでインストーラーを実行してください。
2. インストーラーでは、バインドの対象となるローカル インスタンスを識別します。
3. 元の構成に戻すには対象のインスタンスの横にあるチェック ボックスをオフにします。
4. ライセンス契約に同意します。 インストールするときへもライセンス条項の同意を示す必要があります。
5. **[完了]**をクリックします。 プロセスがかかります。

### <a name="bkmk_cmdunbind"></a> コマンドラインを使用してバインドを解除します。

1. コマンド プロンプトを開き、前のセクションで説明したように **sqlbindr.exe** が含まれているフォルダーに移動します。

2. **SqlBindR.exe** コマンドを実行し、"*/unbind*" 引数でインスタンスを指定します。

   たとえば、次のコマンドでは、既定のインスタンスを元に戻します。
   
    `SqlBindR.exe /unbind MSSQL14.MSSQLSERVER`

## <a name="known-issues"></a>既知の問題

このセクションでは、SqlBindR.exe ユーティリティまたは SQL Server インスタンスに影響を与える可能性があります Machine Learning のサーバーのアップグレードを使用する特定の既知の問題を一覧表示します。

### <a name="restoring-packages-that-were-previously-installed"></a>以前にインストールされたパッケージを復元します。

Microsoft R Server 9.0.1 に含まれているアップグレードのユーティリティで、ユーティリティは、元のパッケージを復元できませんでしたまたは R コンポーネントを完全に、ユーザーが、インスタンスの修復を実行することを必要とするすべてのサービス リリースを適用し、インスタンスを再起動します。

ただし、アップグレードのユーティリティの最新バージョンは自動的に元の R の機能を復元します。 そのため、R コンポーネントを再インストールするか、サーバーを再更新プログラムは必要ありません。 ただし、最初のインストール後に追加された任意の R パッケージをインストールする必要があります。

このタスクがはるかに簡単にインストールし、パッケージの共有パッケージ管理の役割を使用している場合: R コマンドを使用するには、データベース内のレコードを使用して、ファイル システムにインストールされているパッケージを同期して、その逆です。 詳細については、次を参照してください。 [for SQL Server の R パッケージの管理](r-package-management-for-sql-server-r-services.md)です。

### <a name="problems-with-multiple-upgrades-from-sql-server"></a>SQL Server からの複数のアップグレードに関する問題

以前にアップグレードする SQL Server 2016 の R Services のインスタンス 9.0.1、Microsoft R server 9.1.0 新しいインストーラーを実行すると場合、は、そのすべての有効なインスタンスの一覧を表示であり、し、既定では以前にバインドされたインスタンスを選択します。 続行した場合は、以前にバインドされたインスタンスは連結ではありません。 その結果、以前の 9.0.1 のインストールを削除、いずれかの関連するパッケージが新しいバージョンの Microsoft R Server (9.1.0) がインストールされていません。

この問題を回避するには、次のように R Server の既存のインストールを変更できます。
1. コントロール パネルで、開く**プログラム追加と削除**です。
2. Microsoft R Server を見つけてクリックして**変更/変更**です。
3. インストーラーが起動したら、9.1.0 にバインドするインスタンスを選択します。

### <a name="binding-or-unbinding-leaves-multiple-temporary-folders"></a>バインド、またはバインドは、複数の一時フォルダーを残します

場合があります、バインディングおよびバインド解除操作は、一時フォルダーをクリーンアップに失敗します。
次のように名前を持つフォルダーを検索する場合、インストールが完了した後に削除できます。 `R_SERVICES_<guid>`

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

+ [Machine Learning のサーバーの既知の問題](https://docs.microsoft.com/machine-learning-server/resources-known-issues)

+ [R Server の以前のリリースから機能の発表内容](https://docs.microsoft.com/r-server/whats-new-in-r-server)

+ [非推奨、廃止された、または変更された機能](https://docs.microsoft.com/machine-learning-server/resources-deprecated-features)
