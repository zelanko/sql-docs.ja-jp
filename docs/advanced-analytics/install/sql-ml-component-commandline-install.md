---
title: コマンド プロンプトの SQL Server Machine Learning R と Python のコンポーネントのインストール
description: R 言語と Python の統合、SQL Server データベース エンジンのインスタンスを追加する SQL Server コマンド ライン セットアップを実行します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 03/13/2019
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 3f78447054d96f1552ae09c62f3b8a2f18bc58bf
ms.sourcegitcommit: e9fcd10c7eb87a4f09ac2d8f7647018e83a5f5c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2019
ms.locfileid: "57976352"
---
# <a name="install-sql-server-machine-learning-r-and-python-components-from-the-command-line"></a>SQL Server の学習、コマンドラインからの R と Python のコンポーネントのインストールします。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、手順の intalling SQL Server の machine learning のコマンド ラインからコンポーネント。

+ [データベース内の新しいインスタンス](#indb)
+ [既存のデータベース エンジン インスタンスに追加します。](#add-existing)
+ [サイレント インストール](#silent)
+ [新しいスタンドアロン サーバー](#shared-feature)

セットアップ ユーザー インターフェイスとサイレント、basic、または完全な相互作用を指定することができます。 この記事を補足するもの[コマンド プロンプトから SQL Server のインストール](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)R と Python の machine learning コンポーネントに固有のパラメーターについて説明します。

## <a name="pre-install-checklist"></a>インストール前のチェックリスト

+ 管理者特権でコマンド プロンプトからコマンドを実行します。 

+ データベース エンジンのインスタンスは、データベース内のインストールに必要です。 できますが、R または Python でだけの機能をインストールすることはできません[既存のインスタンスに段階的に追加](#add-existing)します。 データベース エンジンだけ R と Python をする場合はインストール、[スタンドアロン サーバー](#shared-feature)します。

+ フェールオーバー クラスターにインストールしないでください。 R と Python のプロセスを分離するために使用されるセキュリティ メカニズムは、Windows Server フェールオーバー クラスター環境と互換性がありません。

+ ドメイン コント ローラーにインストールしないでください。 セットアップの Machine Learning サービスの部分は失敗します。

+ スタンドアロンとデータベース内のインスタンスを同じコンピューターにインストールしないでください。 スタンドアロン サーバーは、同じリソースを両方のインストールのパフォーマンスを弱体化の競合が発生します。


## <a name="command-line-arguments"></a>コマンドライン引数

機能の引数は、用語の契約をライセンスされている処理として必要です。 

コマンド プロンプトを使用してインストールする場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、/Q パラメーターを使用した非表示モード、または /QS パラメーターを使用した簡易非表示モードがサポートされます。 /QS スイッチでは、進捗状況のみが表示され、入力はできません。また、該当する場合でもエラー メッセージは表示されません。 /QS パラメーターは、/Action=install を指定した場合にのみサポートされます。

| 引数 | 説明 |
|-----------|-------------|
| /FEATURES = AdvancedAnalytics | データベースのバージョンがインストールされます。SQL Server 2017 Machine Learning サービス (In-database) または SQL Server 2016 R Services (In-database)。  |
| /FEATURES = SQL_INST_MR | SQL Server 2017 のみに適用されます。 AdvancedAnalytics とは、これをペアリングします。 Microsoft R Open と独自の R パッケージを含む、(データベース内) R 機能をインストールします。 SQL Server 2016 R Services の機能は R のみ、そのリリース パラメーターがありません。|
| /FEATURES = SQL_INST_MPY | SQL Server 2017 のみに適用されます。 AdvancedAnalytics とは、これをペアリングします。 Anaconda と独自の Python パッケージを含む、(データベース) の Python 機能をインストールします。 |
| /FEATURES = SQL_SHARED_MR | スタンドアロン バージョンの R の機能をインストールします。SQL Server 2017 Machine Learning Server (スタンドアロン) または SQL Server 2016 R Server (スタンドアロン)。 スタンドアロン サーバーには、データベース エンジンのインスタンスにバインドされていない「共有機能」です。|
| /FEATURES = SQL_SHARED_MPY | SQL Server 2017 のみに適用されます。 スタンドアロン バージョンの Python 機能がインストールされます。SQL Server 2017 Machine Learning Server (スタンドアロン)。 スタンドアロン サーバーには、データベース エンジンのインスタンスにバインドされていない「共有機能」です。|
| /IACCEPTROPENLICENSETERMS  | オープン ソースの R コンポーネントを使用するためのライセンス条項を承諾したことを示します。 |
| /IACCEPTPYTHONLICENSETERMS | Python コンポーネントを使用するためのライセンス条項を承諾したことを示します。 |
| /IACCEPTSQLSERVERLICENSETERMS | SQL Server を使用するためのライセンス条項を承諾したことを示します。|
| /MRCACHEDIRECTORY | オフラインのセットアップでは、R コンポーネント CAB ファイルを含むフォルダーを設定します。 |
| /MPYCACHEDIRECTORY | 将来使用するために予約されています。 インターネット接続がないコンピューター上のインストール用の Python コンポーネントの CAB ファイルを保存するのにには、%temp% を使用します。 |


## <a name="indb"></a> データベース内のインスタンスのインストール

データベース エンジンのインスタンスを追加するために必要なのデータベース内分析、 **AdvancedAnalytics**のインストールに機能します。 データベース エンジンのインスタンスをインストールするには高度な分析、または[既存のインスタンスに追加](#add-existing)します。 

プロンプト画面に表示されることがなく、対話型の進行状況に関する情報を表示するには、/qs 引数を使用します。

> [!IMPORTANT]
> インストール後に、2 つの追加の構成手順が残ります。 これらのタスクが実行されるまで、統合は完了しません。 参照してください[post-installation tasks](#post-install)手順についてはします。

### <a name="sql-server-2017-database-engine-advanced-analytics-with-python-and-r"></a>SQL Server 2017: データベース エンジン、Python と R による分析の詳細

データベース エンジンのインスタンスの同時インストールでは、インスタンス名と管理者 (Windows) ログインを提供します。 すべてのライセンス条項への同意だけでなく、コアと言語のコンポーネントをインストールするための機能が含まれます。

```cmd
Setup.exe /qs /ACTION=Install /FEATURES=SQLEngine,ADVANCEDANALYTICS,SQL_INST_MR,SQL_INST_MPY
/INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="<Windows-username>" 
/IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS /IACCEPTPYTHONLICENSETERMS
```

この同じコマンドを使用してデータベース エンジン SQL Server ログインが混合認証します。

```cmd
Setup.exe /q /ACTION=Install /FEATURES=SQLEngine,ADVANCEDANALYTICS,SQL_INST_MR,SQL_INST_MPY
/INSTANCENAME=MSSQLSERVER /SECURITYMODE=SQL /SAPWD="%password%" /SQLSYSADMINACCOUNTS="<sql-username>" 
/IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS /IACCEPTPYTHONLICENSETERMS
```

この例は、Python のみ、表示機能を省略することで 1 つの言語を追加することができます。

```cmd  
Setup.exe /qs /ACTION=Install /FEATURES=SQLEngine,ADVANCEDANALYTICS,SQL_INST_MPY 
/INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="<username>" 
/IACCEPTSQLSERVERLICENSETERMS  /IACCEPTPYTHONLICENSETERMS
```

### <a name="sql-server-2016-database-engine-and-advanced-analytics-with-r"></a>SQL Server 2016: データベース エンジンと R を使用した高度な分析

このコマンドは、同じ SQL Server 2016 セットアップで利用可能なない SQL Server 2017 には、Python の要素を使用せずします。

```cmd  
Setup.exe /qs /ACTION=Install /FEATURES=SQLEngine,ADVANCEDANALYTICS,SQL_INST_MR
/INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="<Windows-username>" 
/IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS 
```

## <a name="post-install"></a> インストール後の構成 (必須)

データベース内のインストールのみに適用されます。

セットアップが完了したら、R、Python、Microsoft R と Python のパッケージ、Microsoft R Open、Anaconda、ツール、サンプル、およびスクリプトは、ディストリビューションの一部であると、データベース エンジンのインスタンスがあります。 

多くのタスクが 2 つは、インストールを完了する必要があります。

1. データベース エンジン サービスを再起動します。

1. この機能を使用する前に、外部スクリプトを有効にします。 指示に従って[インストール SQL Server 2017 Machine Learning Services (In-database)](sql-machine-learning-services-windows-install.md)として次の手順。 

SQL Server 2016 の場合は、代わりにこの記事を使用して[インストール SQL Server 2016 R Services (In-database)](sql-r-services-windows-install.md)します。

## <a name="add-existing"></a> 既存のデータベース エンジン インスタンスに高度な分析を追加します。

既存のデータベース エンジン インスタンスにデータベース内の高度な分析を追加するときに、インスタンス名を指定します。 たとえば、以前 SQL Server 2017 データベース エンジンと Python をインストールした場合でしたコマンドを使用するこの R. を追加するには

```cmd  
Setup.exe /qs /ACTION=Install /FEATURES=SQL_INST_MR /INSTANCENAME=MSSQLSERVER 
/IACCEPTSQLSERVERLICENSETERMS  /IACCEPTROPENLICENSETERMS
```



## <a name="silent"></a> サイレント インストール

サイレント インストールでは、.cab ファイルの場所のチェックを抑制します。 このため、.cab ファイルがアンパックされる場所を指定する必要があります。 Python、%temp * CAB ファイルを配置する必要があります。 フォルダーを設定する、R のパスを使用してこの一時ディレクトリをことができます。
 
```cmd  
Setup.exe /q /ACTION=Install /FEATURES=SQLEngine,ADVANCEDANALYTICS,SQL_INST_MR,SQL_INST_MPY 
/INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="<username>" 
/IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS /IACCEPTPYTHONLICENSETERMS 
/MRCACHEDIRECTORY=%temp% 
```

## <a name="shared-feature"></a> スタンドアロン サーバーのインストール

スタンドアロン サーバーには、データベース エンジンのインスタンスにバインドされていない「共有機能」です。 次の例では、両方のリリースの有効な構文を示します。

SQL Server 2017 には、スタンドアロン サーバー上の Python および R がサポートされています。

```cmd
Setup.exe /q /ACTION=Install /FEATURES=SQL_SHARED_MR,SQL_SHARED_MPY  
/IACCEPTROPENLICENSETERMS /IACCEPTPYTHONLICENSETERMS /IACCEPTSQLSERVERLICENSETERMS
```

SQL Server 2016 は R のみ。

```cmd
Setup.exe /q /ACTION=Install /FEATURES=SQL_SHARED_MR 
/IACCEPTROPENLICENSETERMS /IACCEPTSQLSERVERLICENSETERMS
```

セットアップが完了したら、サーバー、Microsoft のパッケージでは、オープン ソース ディストリビューションの R、Python、ツール、サンプル、およびスクリプトはディストリビューションの一部である必要があります。 

\Program files\Microsoft SQL Server\140 (または 130) へ移動 \R_SERVER\bin\x64、R コンソール ウィンドウを開くおよびダブルクリック動作**RGui.exe**します。 R が初めてですか。 このチュートリアルを試してください。[基本的な R コマンドと RevoScaleR 関数:25 の一般的な例として](https://docs.microsoft.com/machine-learning-server/r/tutorial-r-to-revoscaler)します。

Python のコマンドを開くには、SQL Server\140\PYTHON_SERVER\bin\x64 \Program files\Microsoft に移動し、ダブルクリックして**python.exe**します。

## <a name="get-help"></a>ヘルプの参照

インストールまたはアップグレードに関するヘルプ よく寄せられる質問と既知の問題への回答は、次の記事を参照してください。

* [アップグレードとインストールに関する FAQ - Machine Learning サービス](../r/upgrade-and-installation-faq-sql-server-r-services.md)

インスタンスのインストール状態を確認し、一般的な問題を修正には、これらのカスタム レポートをお試しください。

* [SQL Server R Services 用のカスタム レポート](../r/monitor-r-services-using-custom-reports-in-management-studio.md)

## <a name="next-steps"></a>次のステップ

R 開発者は、簡単な例で作業を開始し、SQL Server での R の動作の基本を学習します。 次の手順で、次のリンクを参照してください。

+ [チュートリアル: T-SQL での R を実行します。](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [チュートリアル: R の開発者向けのデータベース内分析](../tutorials/sqldev-in-database-r-for-sql-developers.md)

Python の開発者は、これらのチュートリアルに従って、SQL Server で Python を使用する方法を学ぶことができます。

+ [チュートリアル: T-SQL での Python を実行します。](../tutorials/run-python-using-t-sql.md)
+ [チュートリアル: Python 開発者向けのデータベース内分析](../tutorials/sqldev-in-database-python-for-sql-developers.md)

実際のシナリオに基づく機械学習の例を表示するを参照してください。 [Machine learning のチュートリアル](../tutorials/machine-learning-services-tutorials.md)します。