---
title: Machine learning - SQL Server Machine Learning Services のデータ コレクションをトラブルシューティングします。
ms.prod: sql
ms.technology: machine-learning
ms.date: 02/28/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 3c9d8d6cc8c0a5cfdc697c5daaa3b56631d74116
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67963028"
---
# <a name="troubleshoot-data-collection-for-machine-learning"></a>Machine learning のデータ コレクションをトラブルシューティングします。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、自分で問題を解決または Microsoft の顧客のヘルプをサポートするときに使用する必要があります、データの収集手段について説明します。

**適用対象:** SQL Server 2016 R Services、SQL Server 2017 の Machine Learning サービス (R および Python)

## <a name="sql-server-version-and-edition"></a>SQL Server のバージョンとエディション

SQL Server 2016 R Services は、R の統合サポートするように SQL Server の最初のリリースです。 SQL Server 2016 Service Pack 1 (SP1) では、外部スクリプトを実行する機能など、いくつかの主な強化されています。 SQL Server 2016 のカスタマーの場合は、SP1 のインストールを検討する必要がありますまたはそれ以降。

SQL Server 2017 では、Python 言語の統合を追加します。 以前のリリースでは、Python 機能の統合を取得できません。

エディションとバージョンでは、アシスタンスは、この記事では、それぞれのビルド番号の一覧を参照してください、 [SQL Server のバージョン](https://social.technet.microsoft.com/wiki/contents/articles/783.sql-server-versions.aspx#Service_Pack_editions)します。

使用している SQL Server のエディション、によっては、使用不可能、または制限付きな機械学習機能可能性があります。 Enterprise、Developer、Standard、および Express エディションでの機械学習機能の次の記事の一覧。

* [エディションと SQL Server のサポートされる機能](https://docs.microsoft.com/sql/sql-server/editions-and-components-of-sql-server-2016)
* [SQL Server のエディションでの R と Python の機能](r/differences-in-r-features-between-editions-of-sql-server.md)

## <a name="r-language-and-tool-versions"></a>R 言語とツールのバージョン

一般に、R Services の機能または Machine Learning サービスの機能を選択するときにインストールされている Microsoft R のバージョンは、SQL Server のビルド番号によって決定されます。 アップグレードまたは SQL Server 修正プログラムを適用した場合のアップグレードまたはその R コンポーネントの修正プログラムを適用もする必要があります。

リリースと R コンポーネントのダウンロードへのリンクの一覧は、次を参照してください。[インターネットへのアクセスなしで machine learning コンポーネントをインストール](https://docs.microsoft.com/sql/advanced-analytics/r/installing-ml-components-without-internet-access)します。 インターネットにアクセスできるコンピューターで R の必要なバージョンが識別され、自動的にインストールされます。

SQL Server データベース エンジンのバインドと呼ばれるプロセスでの R Server コンポーネントを個別にアップグレードすることになります。 そのため、SQL Server で R コードを実行するときに使用する R のバージョンがインストールされているバージョンの SQL Server と R の最新のバージョンに、サーバーを移行したかどうかに応じて異なる場合があります。

### <a name="determine-the-r-version"></a>R のバージョンを確認します。

R のバージョンを確認する最も簡単な方法では、次のステートメントを実行してランタイム プロパティを取得します。

```sql
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

最後の手段としてインストールされているバージョンを確認するサーバー上のファイルを開くことができます。 これを行うには、R ランタイムと現在の作業ディレクトリの場所を取得する、rlauncher.config ファイルを見つけます。 任意のプロパティを誤って変更しないように、ファイルのコピーを開くことをお勧めします。

* SQL Server 2016
  
  `C:\Program Files\Microsoft SQL Server\MSSQL13.<instance_name\MSSQL\Binn\rlauncher.config`

* SQL Server 2017
  
  `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\MSSQL\Binn\rlauncher.config`

R バージョンと RevoScaleR のバージョンを取得するには、R コマンド プロンプトを開くか、インスタンスに関連付けられている RGui を開きます。

* SQL Server 2016
  
  `C:\Program Files\Microsoft SQL Server\MSSQL13.<instancename>\R_SERVICES\bin\x64\RGui.exe`

* SQL Server 2017
  
  `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\R_SERVICES\bin\x64\RGui.exe`

R コンソールには、起動時にバージョン情報が表示されます。 たとえば、次のバージョンは、SQL Server 2017 の既定の構成を表します。

    *Microsoft R Open 3.3.3*

    *The enhanced R distribution from Microsoft*

    *Microsoft packages Copyright (C) 2017 Microsoft*

    *Loading Microsoft R Server packages, version 9.1.0.*

## <a name="python-versions"></a>Python のバージョン

Python バージョンを取得するいくつかの方法はあります。 最も簡単な方法は、Management Studio またはその他の SQL クエリ ツールからこのステートメントの実行には。

```sql
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

Machine Learning サービスが実行されていない場合は、pythonlauncher.config ファイルを調べることで、インストールされた Python バージョンを指定できます。 任意のプロパティを誤って変更しないように、ファイルのコピーを開くことをお勧めします。

1. SQL server 2017 ののみ。 `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\MSSQL\Log\ExtensibilityLog\pythonlauncher.config`
2. 値を取得**PYTHONHOME**します。
3. 現在の作業ディレクトリの値を取得します。

> [!NOTE]
> SQL Server 2017 に Python および R の両方をインストールする場合は、R と Python 言語用に作業ディレクトリとワーカー アカウントのプールが共有されます。

## <a name="are-multiple-instances-of-r-or-python-installed"></a>R の複数のインスタンスまたは Python がインストールされているか。

R ライブラリの 1 つ以上のコピーがコンピューターにインストールされているかどうかを確認します。 この重複は場合に発生します。

* セットアップ時に、R Services (In-database) と R Server (スタンドアロン) の両方を選択します。
* SQL Server だけでなく、Microsoft R Client をインストールするとします。
* Visual Studio、R Studio、Microsoft R Client、または別の R IDE の R ツールを使用して、異なる一連の R ライブラリがインストールされました。
* コンピューターは、SQL Server の複数のインスタンスをホストし、1 つ以上のインスタンスは、machine learning を使用します。

Python に同じ条件が適用されます。

複数のライブラリまたはランタイムがインストールされていることを確認する場合は、SQL Server インスタンスによって使用されている Python や R ランタイムに関連付けられているエラーのみが発生することを確認します。

## <a name="origin-of-errors"></a>エラーの発生元

R コードを実行しようとしたときに表示されるエラーは、次のソースのいずれかから取得できます。

* ストアド プロシージャ sp_execute_external_script を含む、SQL Server データベース エンジン
* SQL Server スタート パッドの信頼
* Extensibility framework、R と Python ランチャー サテライト プロセスなどの他のコンポーネント
* Microsoft のオープンなどのプロバイダーは、データベースに接続 (ODBC)
* R 言語

最初にサービスを使用する場合は、サービスから発信されたどのメッセージを通知する困難ができます。 メッセージが表示されていたコンテキストだけでなく、正確なメッセージ文字列をキャプチャすることをお勧めします。 クライアント ソフトウェアを使用して machine learning のコードを実行するのに注意してください。

* Management Studio を使用しているでしょうか。 外部のアプリケーションか。
* ストアド プロシージャ内で直接またはリモート クライアントでは、R コードを実行する、ですか。

## <a name="sql-server-log-files"></a>SQL Server ログ ファイル

最新の SQL Server エラー ログを取得します。 エラー ログの完全なセットは、次の既定のログ ディレクトリからのファイルで構成されます。

* SQL Server 2016
  
  `C:\Program Files\Microsoft SQL Server\MSSQL13.SQL2016\MSSQL\Log\ExtensibilityLog`

* SQL Server 2017
  
  `C:\Program Files\Microsoft SQL Server\MSSQL14.SQL2016\MSSQL\Log\ExtensibilityLog`

> [!NOTE]
> 正確なフォルダー名は、インスタンス名によって異なります。

## <a name="errors-returned-by-spexecuteexternalscript"></a>Sp_execute_external_script から返されるエラー

Sp_execute_external_script コマンドを実行するときに存在する場合、返されたエラーの完全なテキストを取得します。

R または Python の問題を考慮の対象から削除するには、このスクリプトは、R または Python のランタイムを起動し、データに前後へ渡すを実行できます。

**R 用**

```sql
exec sp_execute_external_script @language =N'R',  
@script=N'OutputDataSet<-InputDataSet',  
@input_data_1 =N'select 1 as hello'  
with result sets (([hello] int not null));  
go
```

**Python 用**

```sql
exec sp_execute_external_script @language =N'Python',  
@script=N'OutputDataSet= InputDataSet',  
@input_data_1 =N'select 1 as hello'  
with result sets (([hello] int not null));  
go
```

## <a name="errors-generated-by-the-extensibility-framework"></a>機能拡張フレームワークによって生成されたエラー

SQL Server では、外部スクリプト言語のランタイムに個別のログを生成します。 Python や R 言語によっては、これらのエラーは生成されません。 言語固有のランチャーとそのサテライト プロセスなど、SQL Server の機能拡張コンポーネントから生成されます。

これらのログは、次の既定の場所から取得できます。

* SQL Server 2016
  
  `C:\Program Files\Microsoft SQL Server\MSSQL13.<instance_name>\MSSQL\Log\ExtensibilityLog`

* SQL Server 2017
  
  `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\MSSQL\Log\ExtensibilityLog`

> [!NOTE]
> 正確なフォルダー名は、インスタンス名によって異なります。 構成によっては、別のドライブにフォルダーがあります。

たとえば、次のログ メッセージに関連する機能拡張フレームワーク。

* *MSSQLSERVER01 ユーザーの LogonUser に失敗しました*
  
  外部スクリプトを実行しているワーカー アカウントが、インスタンスにアクセスできない可能性があります。

* *InitializePhysicalUsersPool できませんでした。*
  
  このメッセージは、セキュリティ設定が外部スクリプトを実行するために必要なワーカー アカウントのプールを作成してからセットアップを防止は可能性があります。

* *セキュリティ コンテキスト マネージャーの初期化に失敗しました*

* *サテライトのセッション マネージャの初期化に失敗しました*

## <a name="system-events"></a>システム イベント

1. Windows イベント ビューアーを開き、検索、**システム イベント**文字列が含まれるメッセージについてログを*スタート パッド*します。
2. ExtLaunchErrorlog ファイルを開くし、文字列を検索*ErrorCode*します。 ErrorCode に関連付けられているメッセージを確認します。

たとえば、次のメッセージには、SQL Server の機能拡張フレームワークに関連する一般的なシステム エラーは。

* *SQL Server スタート パッド (MSSQLSERVER) サービスは、次のエラーのため開始できませんでした。  <text>*

* *サービスは、適切なタイミングで開始または制御要求に応答しませんでした。*

* *タイムアウトは、SQL Server スタート パッド (MSSQLSERVER) サービスの接続の待機中に (120000 ミリ秒) に到達しました。*

## <a name="dump-files"></a>ダンプ ファイル

デバッグに関する知識を持つ場合は、スタート パッドでのエラーを分析、ダンプ ファイルを使用することができます。

1. SQL Server のセットアップ ブートス トラップのログを含むフォルダーを見つけます。 たとえば、SQL Server 2016 で、既定のパスは C:\Program files \microsoft SQL server \130\setup bootstrap \log でした。
2. 拡張機能に固有のブートス トラップのログ サブフォルダーを開きます。
3. サポート リクエストを送信する場合は、このフォルダーの内容全体を zip 形式のファイルに追加します。 たとえば、C:\Program files \microsoft SQL server \130\setup Bootstrap\Log\LOG\ExtensibilityLog です。
  
正確な場所は、システムによって異なる場合があり、C ドライブ以外の場合があります。 Machine learning がインストールされているインスタンスのログを取得することを確認します。

## <a name="configuration-settings"></a>構成設定

このセクションには、その他のコンポーネントまたは R または Python スクリプトを実行すると、エラーの原因ができるプロバイダーが一覧表示します。

### <a name="what-network-protocols-are-available"></a>どのようなネットワーク プロトコルが使用できるでしょうか。

Machine Learning サービスでは、拡張機能のコンポーネント間の内部通信用と外部の R または Python クライアントとの通信に次のネットワーク プロトコルが必要です。

* 名前付きパイプ
* TCP/IP

インストールされている場合と、プロトコルがインストールされているかどうかを判断するが有効になっているかどうかを決定する SQL Server 構成マネージャーを開きます。

### <a name="security-configuration-and-permissions"></a>セキュリティの構成とアクセス許可

ワーカー アカウント。

1. コントロール パネルで、開く**ユーザーとグループ**、外部スクリプト ジョブを実行するために使用するグループを見つけます。 既定では、グループは**SQLRUserGroup**します。
2. グループが存在して、少なくとも 1 つのワーカー アカウントが含まれていることを確認します。
3. SQL Server Management studio で R または Python のジョブを実行するインスタンスを選択します。 選択**セキュリティ**、し SQLRUserGroup のログオンがあるかどうかを確認します。
4. ユーザー グループのアクセス許可を確認します。

個々 のユーザー アカウント。

1. インスタンスが混合モード認証、SQL ログインまたは Windows 認証のみをサポートしているかどうかを決定します。 この設定の影響、R または Python コードの要件。
2. R コードを実行する必要があるユーザーごとに、必要な場所 R からオブジェクトを書き込む、データにアクセスする、またはオブジェクトが作成される各データベースに対するアクセス許可レベルを決定します。
3. スクリプトの実行を有効にするには、ロールの作成や、必要に応じて、次のロールにユーザーを追加します。

   - すべてが*db_owner*:必要な任意の外部スクリプトを実行します。
   - *db_datawriter*:R または Python から結果を書き込む。
   - *db_ddladmin*:新しいオブジェクトを作成します。
   - *db_datareader*:R または Python コードで使用されるデータを読み取る。
4. SQL Server 2016 をインストールしたときに、既定のスタートアップ アカウントを変更するかどうかに注意してください。
5. 新しい R パッケージをインストールまたは他のユーザーがインストールされた R パッケージを使用して、ユーザーに必要な場合をインスタンス上のパッケージ管理を有効にし、追加のアクセス許可を割り当てる必要があります。 詳細については、次を参照してください。[を有効にするか、R パッケージの管理を無効にする](r/r-package-how-to-enable-or-disable.md)します。

### <a name="what-folders-are-subject-to-locking-by-antivirus-software"></a>どのようなフォルダーでは、ウイルス対策ソフトウェアによってロックされるでしょうか。

ウイルス対策ソフトウェアは、セットアップの機械学習機能と成功したスクリプトの実行の両方を防ぐことが、フォルダーをロックできます。 SQL Server のツリー内のフォルダーがウイルス スキャンの対象がかどうかを決定します。

ただし、インスタンスで複数のサービスまたは機能をインストールすると、インスタンスによって使用されているすべての可能なフォルダーを列挙する困難ができます。 たとえば、新機能が追加されると、新しいフォルダーあり必要があります識別除外します。

さらに、一部の機能は実行時に新しいフォルダーを動的に作成します。 たとえば、インメモリ OLTP テーブル、ストアド プロシージャ、および関数は、実行時に新しいディレクトリを作成します。 これらのフォルダー名は、Guid を含めることが多くの場合、および予測ことはできません。 SQL Server の信頼されたスタート パッドが R の新しい作業ディレクトリを作成し、ジョブ Python スクリプトを作成します。

SQL Server のプロセスとその機能で必要なすべてのフォルダーを除外できない可能性があります、ために、SQL Server インスタンス ディレクトリ ツリー全体を除外することをお勧めします。

### <a name="is-the-firewall-open-for-sql-server-does-the-instance-support-remote-connections"></a>For SQL Server ファイアウォールを開くにはでしょうか。 インスタンスは、リモート接続をサポートしますか。

1. SQL Server がリモート接続をサポートするかどうかを確認するのを参照してください。[リモート サーバー接続を構成する](../database-engine/configure-windows/view-or-configure-remote-server-connection-options-sql-server.md)します。

2. SQL Server のファイアウォール規則が作成されたかどうかを決定します。 既定のインストールで、セキュリティ上の理由ができない可能性があります、インスタンスに接続するリモートの R または Python クライアントの。 詳細については、次を参照してください。 [SQL Server への接続のトラブルシューティング](../database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine.md)します。

## <a name="see-also"></a>関連項目

[SQL Server での machine learning をトラブルシューティングします。](machine-learning-troubleshooting-faq.md)
