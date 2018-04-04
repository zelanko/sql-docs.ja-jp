---
title: 機械学習でのデータ コレクション SQL Server のトラブルシューティングします。
ms.custom: ''
ms.date: 06/16/2017
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- R
ms.author: heidist
author: HeidiSteen
manager: cgronlun
ms.workload: Inactive
ms.openlocfilehash: bb4c8d097cd548ad256f84d513e597e934873e69
ms.sourcegitcommit: 059fc64ba858ea2adaad2db39f306a8bff9649c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/04/2018
---
# <a name="troubleshoot-data-collection-for-machine-learning"></a>機械学習のデータ コレクションをトラブルシューティングします。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、セットアップ、構成、または機械学習の SQL Server でのパフォーマンスの問題を解決しようとしたときに収集する必要がありますのデータの種類について説明します。 このようなデータには、ログ、エラー メッセージ、およびシステム情報が含まれています。

最も役に立つ情報源についても説明セルフヘルプごとに診断を実行するとします。 この情報の収集は、machine learning の SQL Server の機能に関連する問題のテクニカル サポートを要求するときにも役立ちます。

**適用されます:** SQL Server 2016 の R Services、SQL Server 2017 機械学習のサービス (R および Python)

## <a name="sql-server-and-r-versions"></a>SQL Server と R のバージョン

バージョンが新規インストールまたはアップグレードするかどうかを確認します。 アップグレードである場合は、実行された方法を決定します。

- どのバージョンからアップグレードするでしたか。 
- 以前のコンポーネントを削除しましたまたはアップグレードした後で配置しますか。
- アップグレード中に、機能の選択を変更するか。 

### <a name="which-edition-of-sql-server-is-installed-and-which-version"></a>SQL Server のエディションがインストールされているバージョンとしますか。 

SQL Server R Services は、SQL Server 2016 で導入されました。 以前のバージョンは、機械学習をサポートしていません。 さらに、2016年のリリースの後続のサービス パックには、多くのバグの修正プログラムと機能強化が含まれています。 最初の手順としては、Service Pack 1 またはそれ以降のインストールを検討してください。

SQL Server の 2017 のサポートは、Python 言語まで拡張されます。 Python のサポートは、以前のリリースでは指定されませんでした。

ヘルプがどのエディションとバージョンを判断する場合は、この記事では、それぞれのビルド番号の一覧を参照してください。、[バージョンの SQL Server](https://social.technet.microsoft.com/wiki/contents/articles/783.sql-server-versions.aspx#Service_Pack_editions)です。

使用している SQL Server のエディションによっては、使用不可能、または制限付き一部の機械学習の機能可能性があります。

Enterprise、Developer、Standard、および Express エディションの machine learning 機能の一覧については、次の記事を参照してください。

* [エディションと SQL Server のサポートされる機能](https://docs.microsoft.com/sql/sql-server/editions-and-components-of-sql-server-2016)
* [SQL Server のエディション間で R の機能の相違点](https://docs.microsoft.com/sql/advanced-analytics/r/differences-in-r-features-between-editions-of-sql-server)

### <a name="which-version-of-microsoft-r-is-installed"></a>Microsoft R のバージョンがインストールされているか。

一般に、R Services の機能と Machine Learning サービス機能を選択するときにインストールされている Microsoft R のバージョンは、SQL Server のビルド番号によって決定されます。 アップグレードまたは SQL Server 修正プログラムを適用した場合もアップグレードまたはその R コンポーネントの修正プログラムを適用します。

リリースと R コンポーネントのダウンロードへのリンクの一覧は、次を参照してください。[インターネットにアクセスできないマシン ラーニング コンポーネントをインストール](https://docs.microsoft.com/sql/advanced-analytics/r/installing-ml-components-without-internet-access)です。 インターネット アクセス、コンピューターでは、R の必要なバージョンが識別され、自動的にインストールされます。

バインディングと呼ばれるプロセスで、SQL Server データベース エンジンから R サーバー コンポーネントを個別にアップグレードすることができます。 そのため、SQL Server で R コードを実行するときに使用する R のバージョンは、SQL Server のインストールされているバージョンと最新の R バージョンに、サーバーを移行したかどうかに応じて異なる場合があります。

#### <a name="determine-the-r-version"></a>R のバージョンを調べる

R バージョンを確認する最も簡単な方法は、次のようなステートメントを実行して、ランタイム プロパティの取得には。

```SQL
exec sp_execute_external_script
       @language = N'R'
       , @script = N'
# Transform R version properties to data.frame
OutputDataSet <- data.frame(
  property_name = c("R.version", "Revo.version"), 
  property_value = c(R.Version()$version.string, Revo.version$version.string),
  stringsAsFactors = FALSE)
# Retrieve properties like R.home, libPath & default packages
OutputDataSet <- rbind(OutputDataSet, data.frame(
  property_name = c("R.home", "libPaths", "defaultPackages"),
  property_value = c(R.home(), .libPaths(), paste(getOption("defaultPackages"), collapse=", ")),
  stringsAsFactors = FALSE)
)
'
WITH RESULT SETS ((PropertyName nvarchar(100), PropertyValue nvarchar(4000)));

```

> [!TIP] 
> R Services が動作していない場合は、RGui から R スクリプトの部分のみを実行してください。

最後の手段としてインストールされているバージョンを確認するサーバー上のファイルを開くことができます。 これを行うには、R ランタイムと現在の作業ディレクトリの場所を取得する rlauncher.config ファイルを見つけます。 作成し、任意のプロパティを誤って変更しないように、ファイルのコピーを開くことをお勧めします。

* SQL Server 2016
  
  `C:\Program Files\Microsoft SQL Server\MSSQL13.<instance_name\MSSQL\Binn\rlauncher.config`

* SQL Server 2017
  
  `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\MSSQL\Binn\rlauncher.config`

R のバージョンと RevoScaleR バージョンを取得するには、R コマンド プロンプトを開くか、インスタンスに関連付けられている RGui を開きます。

* SQL Server 2016
  
  `C:\Program Files\Microsoft SQL Server\MSSQL13.<instancename>\R_SERVICES\bin\x64\RGui.exe`

* SQL Server 2017
  
  `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\R_SERVICES\bin\x64\RGui.exe`


R コンソールには、スタートアップ時にバージョン情報が表示されます。 たとえば、次のバージョンでは、SQL Server 2017 CTP 2.0 の既定の構成を表します。

    *Microsoft R Open 3.3.3*
    
    *The enhanced R distribution from Microsoft*
    
    *Microsoft packages Copyright (C) 2017 Microsoft*
    
    *Loading Microsoft R Server packages, version 9.1.0.*


### <a name="what-version-of-python-is-installed"></a>Python のバージョンがインストールされているか。

Python のサポートは、SQL Server 2017 Community Technology Preview (CTP) 2.0 でのみ使用可能な以降です。

Python のバージョンを取得するいくつかの方法はあります。 最も簡単な方法は、Management Studio またはその他の SQL クエリ ツールからこのステートメントの実行には。

```SQL
-- Get Python runtime properties:
exec sp_execute_external_script
       @language = N'Python'
       , @script = N'
import sys
import pkg_resources
OutputDataSet = pandas.DataFrame(
                    {"property_name": ["Python.home", "Python.version", "Revo.version", "libpaths"],
                    "property_value": [sys.executable[:-10], sys.version, pkg_resources.get_distribution("revoscalepy").version, str(sys.path)]}
)
'
with WITH RESULT SETS (SQL keywords) ((PropertyName nvarchar(100), PropertyValue nvarchar(4000)));
```

Machine Learning のサービスが実行されていない場合は、pythonlauncher.config ファイルを確認してインストールされている Python バージョンを指定できます。 作成し、任意のプロパティを誤って変更しないように、ファイルのコピーを開くことをお勧めします。

1. SQL server 2017 場合のみ。 `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\MSSQL\Log\ExtensibilityLog\pythonlauncher.config `
2. 値を取得**PYTHONHOME**です。
3. 現在の作業ディレクトリの値を取得します。


> [!NOTE]
> SQL Server 2017 では、Python と R の両方をインストールした、作業ディレクトリとプールのワーカー アカウントは、R および Python 言語で共有されます。

### <a name="are-multiple-instances-of-r-or-python-installed"></a>R の複数のインスタンスは、または Python をインストールしますか。

R ライブラリの 1 つ以上のコピーが、コンピューターにインストールされているかどうかを確認します。 この重複は、場合に発生することができます。

* セットアップ中には、R Services (In-database) と R Server (スタンドアロン) の両方を選択します。 
* SQL サーバーだけでなく、Microsoft R クライアントをインストールするとします。
* R Tools for Visual Studio、R Studio、Microsoft R クライアント、または別の R IDE を使用して、異なる一連の R ライブラリがインストールされました。
* コンピューターが SQL Server の複数のインスタンスをホストし、複数のインスタンスは、機械学習を使用します。

同じ条件は、Python に適用されます。

複数のライブラリまたはランタイムがインストールされていることを確認する場合は、SQL Server インスタンスによって使用されている Python や R ランタイムに関連付けられているエラーのみを取得することを確認します。

## <a name="errors-and-messages"></a>エラーとメッセージ

R コードを実行しようとしたときに表示されるエラーは、次のソースのいずれかから取得できます。

- ストアド プロシージャ sp_execute_external_script を含む、SQL Server データベース エンジン
- SQL Server スタート パッドの信頼 
- Extensibility framework、R と Python ランチャー、サテライト プロセスなどの他のコンポーネント
- Microsoft Open などのプロバイダーは、データベースに接続 (ODBC)
- R 言語

最初にサービスを使用する場合は、どのサービスから発信されたどのメッセージを確認するが困難ができます。 正確なメッセージのテキストだけでなく、メッセージが表示されていたコンテキストをキャプチャすることをお勧めします。 クライアント ソフトウェアを使用してマシン ラーニング コードを実行することに注意してください。

- Management Studio を使用しているか。 外部アプリケーションか。
- 実行中の R コード、リモート クライアントで、またはストアド プロシージャ内で直接?

### <a name="what-errors-has-sql-server-logged"></a>SQL Server ではどのようなエラーを記録するか。

最新の SQL Server エラー ログを取得します。 エラー ログの完全なセットは、次の既定のログ ディレクトリからファイルで構成されます。

* SQL Server 2016
  
  `C:\Program Files\Microsoft SQL Server\MSSQL13.SQL2016\MSSQL\Log\ExtensibilityLog`

* SQL Server 2017
  
  `C:\Program Files\Microsoft SQL Server\MSSQL14.SQL2016\MSSQL\Log\ExtensibilityLog`

> [!NOTE] 
> 正確なフォルダー名は、インスタンス名によって異なります。


### <a name="what-errors-were-returned-by-the-spexecuteexternalscript-command"></a>どのようなエラーは、sp_execute_external_script コマンドによって返されたか。

Sp_execute_external_script コマンドを実行するときに存在する場合、返されたエラーの完全なテキストを取得します。 

R または Python の問題を考慮の対象から削除するには、R または Python ランタイムを起動し、前後にデータを渡しますが、このスクリプトを実行できます。

**R の**

```sql
exec sp_execute_external_script @language =N'R',  
@script=N'OutputDataSet<-InputDataSet',  
@input_data_1 =N'select 1 as hello'  
with result sets (([hello] int not null));  
go
```

**Python の**

```sql
exec sp_execute_external_script @language =N'Python',  
@script=N'OutputDataSet= InputDataSet',  
@input_data_1 =N'select 1 as hello'  
with result sets (([hello] int not null));  
go
```

### <a name="what-errors-are-generated-by-the-extensibility-framework"></a>拡張性フレームワークでは、どのようなエラーが発生しますか。

SQL Server では、外部スクリプトの言語ランタイムに個別のログを生成します。 また、Python や R 言語では、これらのエラーは生成されません。 言語固有の起動ツールや、サテライト プロセスなど、SQL server 拡張機能コンポーネントから生成します。

これらのログは、次の既定の場所から入手できます。

* SQL Server 2016
  
  `C:\Program Files\Microsoft SQL Server\MSSQL13.<instance_name>\MSSQL\Log\ExtensibilityLog`

* SQL Server 2017
  
  `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\MSSQL\Log\ExtensibilityLog `

> [!NOTE] 
> 正確なフォルダー名は、インスタンス名によって異なります。 構成によっては、別のドライブにフォルダーがあります。

たとえば、次のログ メッセージは、拡張性フレームワークに関連します。

* *MSSQLSERVER01 のユーザーの LogonUser エラー*
  
  外部スクリプトを実行しているワーカー アカウントが、インスタンスにアクセスできない可能性があります。

* *InitializePhysicalUsersPool できませんでした。* 
  
  このメッセージは、セキュリティ設定が外部のスクリプトを実行するために必要なワーカー アカウントのプールを作成してからセットアップを妨げていることを可能性があります。

* *セキュリティ コンテキストのマネージャーを初期化できませんでした。* 

* *サテライト セッション マネージャーの初期化に失敗しました*

### <a name="are-there-any-related-system-events"></a>関連するシステム イベントではありますか。

1. Windows イベント ビューアーを開き、検索、**システム イベント**文字列が含まれるメッセージのログ*スタート パッド*です。 
2. ExtLaunchErrorlog ファイルを開くし、文字列検索*ErrorCode*です。 ErrorCode に関連付けられているメッセージを確認します。

たとえば、次のメッセージは、SQL Server extensibility framework に関連する一般的なシステム エラーです。 

* *SQL Server スタート パッド (MSSQLSERVER) サービスは、次のエラーのため開始できませんでした。  <text>*

* *サービスは、適切なタイミングで開始または制御要求に応答しませんでした。* 

* *タイムアウトは、SQL Server スタート パッド (MSSQLSERVER) サービスを接続するを待っているときに (120000 ミリ秒) に到達しました。* 

### <a name="did-any-components-start-and-then-crash"></a>でしたすべてのコンポーネントを起動し、クラッシュしますか。

デバッグに関する知識を持つ場合は、スタート パッドの不具合を分析する、ダンプ ファイルを使用することができます。

1. SQL Server のセットアップ ブートス トラップ ログを含むフォルダーを見つけます。 たとえば、SQL Server 2016 での既定のパスは C:\Program files \microsoft SQL server \130\setup bootstrap \log でした。
2. 拡張機能に固有であるブートス トラップのログ サブフォルダーを開きます。
3. サポート要求を送信する必要がある場合は、zip 形式のファイルをこのフォルダーの内容全体を追加します。 たとえば、C:\Program files \microsoft SQL server \130\setup Bootstrap\Log\LOG\ExtensibilityLog です。
  
正確な場所は、システムによって異なる可能性があり、C ドライブ以外のドライブにあります。 機械学習がインストールされているインスタンスのログを取得することを確認します。 


## <a name="related-tools-and-configuration"></a>関連ツールと構成

このセクションには、その他のコンポーネントまたは R または Python スクリプトを実行すると、エラーの原因ができるプロバイダーが一覧表示します。

### <a name="what-network-protocols-are-available"></a>どのようなネットワーク プロトコルを利用しますか。

Machine Learning のサービスでは、拡張機能のコンポーネント間の内部通信用と外部 R または Python クライアントとの通信用に次のネットワーク プロトコルが必要です。

* 名前付きパイプ
* TCP/IP

インストールされている場合とプロトコルがインストールされているかどうかを判断する、有効になっているかどうかを決定する SQL Server 構成マネージャーを開きます。

### <a name="security-configuration-and-permissions"></a>セキュリティの構成とアクセス許可

ワーカー アカウント。

1. コントロール パネルで、開く**ユーザーとグループ**、外部スクリプトのジョブを実行するために使用するグループを検索します。 グループは、既定では、 **SQLRUserGroup**です。
2. グループが存在して、少なくとも 1 つのワーカー アカウントが含まれていることを確認します。
3. SQL Server Management Studio でインスタンスから R または Python のジョブが実行される、選択選択**セキュリティ**、し SQLRUserGroup のログオンがあるかどうかを確認しています。
4. ユーザー グループのアクセス許可を確認します。

個別のユーザー アカウント。

1. インスタンスが混合モード認証、SQL ログインの場合のみ、または Windows 認証のみをサポートしているかどうかを決定します。 この設定は、R に影響するか、または Python コードの要件です。
2. R コードを実行する必要のあるユーザーごとに、必要な R からのオブジェクトが書き込まれる、データにアクセスする、またはオブジェクトを作成する各データベースに対するアクセス許可レベルを決定します。
3. スクリプトの実行を有効にするには、ロールを作成するか、必要に応じて、次の役割にユーザーを追加します。

   - 以外のすべて*db_owner*: 必要な EXECUTE ANY EXTERNAL SCRIPT です。
   - *db_datawriter*: R または Python から結果を書き込む。 
   - *db_ddladmin*: 新しいオブジェクトを作成します。 
   - *db_datareader*: R または Python コードによって使用されるデータを読み取れません。 
4. SQL Server 2016 をインストールしたときに、既定の開始アカウントを変更するかどうかに注意してください。
5. 新しい R パッケージをインストールしたり他のユーザーによってインストールされた R パッケージを使用する、ユーザーに必要な場合は、インスタンス上のパッケージの管理を有効にし、追加のアクセス許可を割り当てる必要があります。 詳細については、次を参照してください。[を有効にするか、R パッケージの管理を無効にする](r\r-package-how-to-enable-or-disable.md)です。

### <a name="what-folders-are-subject-to-locking-by-antivirus-software"></a>どのようなフォルダーは、ウイルス対策ソフトウェアによってロックされる可能性がありますか。

ウイルス対策ソフトウェアは、機械学習機能と成功したスクリプトの実行のセットアップの両方を防ぐことが、フォルダーをロックできます。 SQL Server ツリー内の任意のフォルダーがウイルス スキャンの対象がかどうかを決定します。

ただし、インスタンスには、複数のサービスまたは機能がインストールされて、インスタンスによって使用されているすべての可能なフォルダーを列挙するが困難ができます。 たとえば、新機能が追加されると、新しいフォルダー必要があります識別、除外します。

さらに、一部の機能は実行時に新しいフォルダーを動的に作成します。 たとえば、インメモリ OLTP テーブル、ストアド プロシージャ、および関数は、実行時に新しいディレクトリを作成します。 これらのフォルダー名は多くの場合、Guid が含まれてし、予測することはできません。 SQL Server の信頼されたスタート パッドは、R の新しい作業ディレクトリを作成し、Python スクリプトのジョブを作成します。

SQL Server のプロセスとその機能に必要なすべてのフォルダーを除外することができない可能性があります、ために、SQL Server インスタンス ディレクトリ ツリー全体を除外することをお勧めします。

### <a name="is-the-firewall-open-for-sql-server-does-the-instance-support-remote-connections"></a>SQL Server 用ファイアウォールに開いているか。 インスタンスは、リモート接続をサポートしますか。

1. SQL Server がリモート接続をサポートするかどうかを確認するのを参照してください。[リモート サーバー接続を構成する](../database-engine/configure-windows/view-or-configure-remote-server-connection-options-sql-server.md)です。

2. SQL Server のファイアウォール規則が作成されているかどうかを決定します。 セキュリティ上の理由から、既定のインストールでは、その可能性があります可能でないインスタンスに接続するリモート R または Python クライアント。 詳細については、次を参照してください。 [SQL Server への接続のトラブルシューティング](../database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine.md)です。

### <a name="can-you-run-r-script-outside-t-sql"></a>T-SQL の外部 R スクリプトを実行できますか。

その他の R ツールを使用して、SQL Server インスタンスに関連付けられている R ランタイムを実行しようとすることができます。 このように、必要なライブラリがインストールされているかどうかを確認できます。

R の基本インストールには、スクリプトの実行を対話形式のコマンド ラインで、できるだけ RGui から R スクリプトを実行に使用できる複数のツールが含まれています。

R ランタイムが機能している、スクリプトがエラーを返す場合は、R Tools for Visual Studio など、専用の R 開発環境でスクリプトをデバッグしようとすることをお勧めします。

お勧め確認し、R とデータベース エンジンの間でデータを移動するときに発生する可能性がありますのあるデータ型に関する問題を修正するスクリプトを少し修正することです。 詳細については、次を参照してください。 [R ライブラリとデータ型](r/r-libraries-and-data-types.md)です。

さらに、ストアド プロシージャとしてより簡単に使用した形式で、R スクリプトをバンドルするのに sqlrutils パッケージを使用することができます。 詳細については、以下をご覧ください。
* [Sqlrutils パッケージを使用して R コードをストアド プロシージャを生成します。](r/generating-an-r-stored-procedure-for-r-code-using-the-sqlrutils-package.md)
* [Sqlrutils を使用してストアド プロシージャを作成します。](r/how-to-create-a-stored-procedure-using-sqlrutils.md)

## <a name="see-also"></a>参照

[機械学習で SQL Server をトラブルシューティングします。](machine-learning-troubleshooting-faq.md)
