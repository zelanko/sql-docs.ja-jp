---
title: コマンド プロンプトの SQL Server マシン ラーニング コンポーネントのインストール |Microsoft ドキュメント
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 814e0f8172e02d9b02be95888c8dab286429e533
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34707960"
---
# <a name="install-sql-server-machine-learning-components-from-the-command-line"></a>コマンドラインから machine learning の SQL Server コンポーネントをインストールします。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、コマンドラインからのコンポーネントを学習 intalling SQL Server コンピューターの説明します。

+ [データベース内の新しいインスタンス](#indb)
+ [既存のデータベース エンジン インスタンスへの追加します。](#add-existing)
+ [サイレント インストール](#silent)
+ [新しいスタンドアロン サーバー](#shared-feature)

セットアップのユーザー インターフェイスをサイレント モード、basic、または完全の相互作用を指定できます。 この記事の内容を補足するもの[コマンド プロンプトからの SQL Server のインストール](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)R、Python の machine learning コンポーネントに固有のパラメーターに対応します。

## <a name="pre-install-checklist"></a>インストール前のチェックリスト

+ 管理者特権でコマンド プロンプトからコマンドを実行します。 

+ データベース エンジンのインスタンスは、データベース内のインストールに必要です。 実行できますが、R や Python で同様の機能をインストールすることはできません[既存のインスタンスに増分追加](#add-existing)です。 データベース エンジンがないまま R、Python だけをする場合はインストール、[スタンドアロン サーバー](#shared-feature)です。

+ フェールオーバー クラスターにインストールされません。 R、Python のプロセスを分離するために使用されるセキュリティ メカニズムは、Windows Server フェールオーバー クラスター環境と互換性がありません。

+ ドメイン コント ローラーにインストールされません。 セットアップの Machine Learning サービス部分は失敗します。

+ 同じコンピューターにスタンドアロンおよびデータベース内のインスタンスをインストールしないでください。 スタンドアロン サーバーは、同じリソースを両方のインストールのパフォーマンスを弱体化の競合が発生します。


## <a name="command-line-arguments"></a>コマンドライン引数

機能引数は、用語の契約をライセンスが必要です。 

コマンド プロンプトを使用してインストールする場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、/Q パラメーターを使用した非表示モード、または /QS パラメーターを使用した簡易非表示モードがサポートされます。 /QS スイッチでは、進捗状況のみが表示され、入力はできません。また、該当する場合でもエラー メッセージは表示されません。 /QS パラメーターは、/Action=install を指定した場合にのみサポートされます。

| 引数 | 説明 |
|-----------|-------------|
| /FEATURES = AdvancedAnalytics | データベースのバージョンがインストールされます。 SQL Server 2017 Machine Learning Services (In-database) または SQL Server 2016 R Services (In-database)。  |
| /FEATURES = SQL_INST_MR | SQL Server 2017 のみに適用されます。 これは、AdvancedAnalytics とペアします。 Microsoft R オープンおよび独自の R パッケージを含む、(In-database) R の機能をインストールします。 SQL Server 2016 の R Services の機能は R 専用で、そのリリースのパラメーターがないようにします。|
| /機能 SQL_INST_MPY を = | SQL Server 2017 のみに適用されます。 これは、AdvancedAnalytics とペアします。 Anaconda、独自の Python パッケージなど、(In-database) Python 機能をインストールします。 |
| /FEATURES = SQL_SHARED_MR | スタンドアロン バージョンの R の機能をインストールします。 SQL Server 2017 Machine Learning サーバー (スタンドアロン) または SQL Server 2016 R Server (スタンドアロン)。 スタンドアロン サーバーは、データベース エンジンのインスタンスにバインドされていない「共有機能」です。|
| /機能 SQL_SHARED_MPY を = | SQL Server 2017 のみに適用されます。 スタンドアロン バージョンの Python 機能をインストールします。 SQL Server 2017 Machine Learning サーバー (スタンドアロン)。 スタンドアロン サーバーは、データベース エンジンのインスタンスにバインドされていない「共有機能」です。|
| /IACCEPTROPENLICENSETERMS  | オープン ソース R コンポーネントを使用するライセンス条項に同意を受け入れたことを示します。 |
| /IACCEPTPYTHONLICENSETERMS | Python コンポーネントを使用するライセンス条項に同意を受け入れたことを示します。 |
| /IACCEPTSQLSERVERLICENSETERMS | SQL Server を使用してライセンス条項に同意を受け入れたことを示します。|
| /MRCACHEDIRECTORY | オフラインのセットアップでは、R コンポーネントの CAB ファイルを含むフォルダーを設定します。 |
| /MPYCACHEDIRECTORY | オフラインのセットアップでは、Python コンポーネントの CAB ファイルを含むフォルダーを設定します。 |


## <a name="indb"></a> データベース内のインスタンスのインストール

データベース内分析機能があるデータベース エンジンのインスタンスを追加するために必要な**AdvancedAnalytics**のインストールに機能します。 高度な分析は、with、データベース エンジンのインスタンスをインストールするか、[既存のインスタンスに追加](#add-existing)です。 

プロンプトが画面に表示されることがなく、対話型の進行状況に関する情報を表示するには、/qs 引数を使用します。

> [!IMPORTANT]
> インストールが完了したら、次の 2 つの追加の構成手順が残ります。 これらのタスクが実行されるまで、統合は完了しません。 参照してください[post-installation tasks](#post-install)手順についてはします。

### <a name="sql-server-2017-database-engine-advanced-analytics-with-python-and-r"></a>SQL Server 2017: データベース エンジン、Python と R で分析を高度な

データベース エンジンのインスタンスを同時にインストールには、インスタンス名と管理者 (Windows) ログインを提供します。 すべてのライセンス条項に同意だけでなく、コアと言語のコンポーネントをインストールするための機能があります。

```  
Setup.exe /qs /ACTION=Install /FEATURES=SQLEngine,ADVANCEDANALYTICS,SQL_INST_MR,SQL_INST_MPY
/INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="<Windows-username>" 
/IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS /IACCEPTPYTHONLICENSETERMS
```

この同じコマンドを使用してデータベース エンジン SQL Server ログインが混合認証します。

```
Setup.exe /q /ACTION=Install /FEATURES=SQLEngine,ADVANCEDANALYTICS,SQL_INST_MR,SQL_INST_MPY
/INSTANCENAME=MSSQLSERVER /SECURITYMODE=SQL /SAPWD="%password%" /SQLSYSADMINACCOUNTS="<sql-username>" 
/IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS /IACCEPTPYTHONLICENSETERMS
```

この例は Python のみ、機能を省略することで、1 つの言語を追加できることを示すです。

```  
Setup.exe /qs /ACTION=Install /FEATURES=SQLEngine,ADVANCEDANALYTICS,SQL_INST_MPY 
/INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="<username>" 
/IACCEPTSQLSERVERLICENSETERMS  /IACCEPTPYTHONLICENSETERMS
```

### <a name="sql-server-2016-database-engine-and-advanced-analytics-with-r"></a>SQL Server 2016: データベース エンジンと R での高度な分析

このコマンドは、同じ SQL Server 2016 セットアップで使用されていない SQL Server の 2017 せずに、Python 要素、します。

```  
Setup.exe /qs /ACTION=Install /FEATURES=SQLEngine,ADVANCEDANALYTICS,SQL_INST_MR
/INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="<Windows-username>" 
/IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS 
```

## <a name="post-install"></a> インストール後の構成 (必須)

データベース内のインストールのみに適用されます。

セットアップが完了したら、R、Python Microsoft R、Python パッケージ、Microsoft R Open、Anaconda、ツール、サンプル、およびスクリプトは、配布の一部であると、データベース エンジンのインスタンスがあります。 

2 つ以上のタスクは、インストールを完了する必要があります。

1. データベース エンジン サービスを再起動します。

1. この機能を使用する前に、外部スクリプトを有効にします。 指示に従って[インストール SQL Server 2017 Machine Learning Services (In-database)](sql-machine-learning-services-windows-install.md)として、次の手順です。 

SQL Server 2016 の場合は、代わりにこの記事の内容を使用して[インストール SQL Server 2016 R Services (In-database)](sql-r-services-windows-install.md)です。

## <a name="add-existing"></a> 既存のデータベース エンジン インスタンスに対して高度な分析を追加します。

データベース内の高度な分析を既存のデータベース エンジン インスタンスを追加する場合は、インスタンス名を指定します。 たとえば、インストールしていた場合、データベース エンジンの SQL Server 2017 と Python、でしたこのコマンドを使用する R. の追加

```  
Setup.exe /qs /ACTION=Install /FEATURES=SQL_INST_MR /INSTANCENAME=MSSQLSERVER 
/IACCEPTSQLSERVERLICENSETERMS  /IACCEPTROPENLICENSETERMS
```



## <a name="silent"></a> サイレント インストール

サイレント インストールでは、.cab ファイルの場所のチェックを抑制します。 このため、.cab ファイルがアンパックされる場所を指定する必要があります。 この一時ディレクトリができます。
 
```  
Setup.exe /q /ACTION=Install /FEATURES=SQLEngine,ADVANCEDANALYTICS,SQL_INST_MR,SQL_INST_MPY 
/INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="<username>" 
/IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS /IACCEPTPYTHONLICENSETERMS 
/MRCACHEDIRECTORY=%temp% /MPYCACHEDIRECTORY=%temp%
```

## <a name="shared-feature"></a> スタンドアロン サーバー インストール

スタンドアロン サーバーは、データベース エンジンのインスタンスにバインドされていない「共有機能」です。 次の例では、両方のリリースの有効な構文を示します。

SQL Server 2017 には、スタンドアロン サーバーでの Python と R がサポートされています。

```
Setup.exe /q /ACTION=Install /FEATURES=SQL_SHARED_MR,SQL_SHARED_MPY  
/IACCEPTROPENLICENSETERMS /IACCEPTPYTHONLICENSETERMS /IACCEPTSQLSERVERLICENSETERMS
```

SQL Server 2016 は、R 専用。

```
Setup.exe /q /ACTION=Install /FEATURES=SQL_SHARED_MR 
/IACCEPTROPENLICENSETERMS /IACCEPTSQLSERVERLICENSETERMS
```

セットアップが完了したら、サーバー、Microsoft のパッケージでは、オープン ソース ディストリビューションの R、Python、ツール、サンプル、およびスクリプトは、配布の一部である必要があります。 

ウィンドウを開き、R コンソール、\Program files\Microsoft SQL Server\140 (130) に移動して \R_SERVER\bin\x64 をダブルクリックして**RGui.exe**です。 R 初めてですか。 このチュートリアルを実行してください:[基本的な R コマンドと RevoScaleR 関数: 25 の一般的な例として](https://docs.microsoft.com/machine-learning-server/r/tutorial-r-to-revoscaler)です。

Python コマンドを開くに \Program files\Microsoft SQL Server\140\PYTHON_SERVER\bin\x64 に移動し、ダブルクリック**python.exe**です。

## <a name="get-help"></a>ヘルプの参照

ヘルプをインストールまたはアップグレードが必要ですか。 よく寄せられる質問と既知の問題への回答は、次の記事を参照してください。

* [アップグレードとインストールに関する FAQ - Machine Learning サービス](../r/upgrade-and-installation-faq-sql-server-r-services.md)

インスタンスのインストール状態をチェックして、一般的な問題を修正、これらのカスタム レポートを実行してください。

* [SQL Server R Services のカスタム レポート](../r/monitor-r-services-using-custom-reports-in-management-studio.md)

## <a name="next-steps"></a>次のステップ

R の開発者は、単純な例についてで始めることができ、SQL Server での R の動作の基礎を学習します。 次の手順は、次のリンクを参照してください。

+ [チュートリアル: T-SQL で R を実行します。](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [R 開発者向けチュートリアル: データベース内の分析](../tutorials/sqldev-in-database-r-for-sql-developers.md)

Python 開発者は、これらのチュートリアルに従って SQL Server で Python を使用する方法を学習できます。

+ [チュートリアル: T-SQL で Python を実行します。](../tutorials/run-python-using-t-sql.md)
+ [Python 開発者のためのチュートリアル: データベース内の分析](../tutorials/sqldev-in-database-python-for-sql-developers.md)

実際のシナリオに基づく機械学習の例を表示するを参照してください。[機械学習のチュートリアル](../tutorials/machine-learning-services-tutorials.md)です。