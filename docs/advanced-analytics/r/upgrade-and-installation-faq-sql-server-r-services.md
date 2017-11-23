---
title: "SQL Server の Machine Learning のアップグレードとインストールに関する FAQ |Microsoft ドキュメント"
ms.date: 10/31/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 001e66b9-6c3f-41b3-81b7-46541e15f9ea
caps.latest.revision: "59"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: 3c4fb79f04daeff6d98856b521fa1602a2334cdd
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="upgrade-and-installation-faq-for-sql-server-machine-learning"></a>SQL Server の Machine Learning のアップグレードとインストールに関する FAQ

このトピックでは、機械学習の SQL Server 機能のインストールに関してよく寄せられる質問に対する回答を示します。 アップグレードに関する一般的な質問についても説明します。

+ いくつかの問題は、プレリリース版からアップグレードでのみ発生します。 したがって、するを識別するバージョンおよびエディション最初にこれらの注意事項を読み取る前にお勧めします。
+ 最近のリリースで修正された問題を解決するには、最新のリリースまたはできるだけ早くのサービスのリリースにアップグレードします。

**適用されます:** SQL Server 2016 の R Services、SQL Server 2017 機械学習の Services (In-database)

## <a name="performing-setup-for-the-first-time"></a>初めてセットアップを実行します。

設定するための手順に従って[!INCLUDE[sscurrent_md](../../includes/sscurrent_md.md)]と R コンポーネントをここで説明します。 

+ [SQL Server R Services または Machine Learning サービス データベース内のセットアップします。](../r/set-up-sql-server-r-services-in-database.md)
+ [SQL Server 2017 Python をセットアップします。](../python/setup-python-machine-learning-services.md)
+ [スタンドアロン R サーバーを作成します。](../r/create-a-standalone-r-server.md)

> [!IMPORTANT]
> 
> SQL Server と R または Python スクリプトを使用する前に、機能を学習、マシンをインストールした後は、いくつかの追加の構成手順を完了する必要があります。 外部スクリプト実行機能が既定で無効になっているためにです。

### <a name="requirements-and-restrictions"></a>要件と制限

インストールする SQL Server のビルドによって、次の制限の一部は、次の場合がありますに適用。

- 以前のバージョンの SQL Server 2016 の R Services では、8dot3 表記は、作業ディレクトリを含むドライブに必要でした。 プレリリース版をインストールした場合 SQL Server 2016 Service Pack 1 にアップグレードすると、この問題を解決する必要があります。 SP1 以降後は、この要件はリリースに適用されません。

- 現時点では、インストールすることはできません[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]フェールオーバー クラスターにします。 

- Azure vm では、追加の構成必要があります。 たとえば、リモート アクセスをサポートするためにファイアウォール例外を作成する必要があります。

- R の別のバージョンまたは Revolution Analytics からの他のリリースとサイド バイ サイド インストールはサポートされていません。

- [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] のプレリリース バージョンを新しくインストールすることは現在サポートされていません。 リリース前のバージョンを使用している場合はできるだけ早くアップグレードします。

- セットアップを開始する前にウイルスを無効にします。 セットアップが完了したら、ことをお勧めウイルス スキャンが使用するフォルダーを中断[!INCLUDE[ssnoversion](../../includes/ssnoversion.md)]です。 可能であれば、全体のスキャンを中断[!INCLUDE[ssnoversion](../../includes/ssnoversion.md)]ツリー。

### <a name="licensing-agreements-for-unattended-installs"></a>無人インストールのライセンス契約

SQL Server のインスタンスをアップグレードするコマンドラインを使用する場合は、コマンドラインが、両方が含まれていることを確認してください、 [!INCLUDE[ssnoversion](../../includes/ssnoversion.md)] R、Python のアグリーメントのパラメーター、およびライセンス契約の新しいパラメーターをライセンスします。

### <a name="offline-installation-of-machine-learning-components-for-a-localized-version-of-sql-server"></a>ローカライズされたバージョンの SQL Server の machine learning コンポーネントのオフライン インストール

インストールするときに[!INCLUDE[ssnoversion](../../includes/ssnoversion.md)]インターネット アクセスが許可されていないコンピューターで machine learning コンポーネント、追加の手順を実行する必要があります。

+ SQL Server セットアップを実行する前に、ローカル フォルダーに、R または Python コンポーネント インストーラーをダウンロードします。
+ 場合によっては、適切な言語がインストールされていることを確認してください。 インストーラー ファイルを編集する必要があります。
+ 機械学習のコンポーネントに使用される言語識別子には、SQL Server セットアップの言語と同じである必要がありますか、セットアップを完了することはできません。

詳細については、次を参照してください。[インターネットにアクセスできないマシン ラーニング コンポーネントをインストールする](../r/installing-ml-components-without-internet-access.md)です。

## <a name="post-installation-configuration"></a>インストール後の構成

R、または Python で機械学習を使用するには追加の構成が SQL Server セットアップの実行後に必要です。 必要とされる正確な手順は、サーバー、および SQL Server インスタンスとデータベースの構成方法のセキュリティ レベルによって異なります。

インストール後の手順を確認する追加の手順に必要となる環境の一覧内のすべてのオプションを確認します。

+ [学習のデータベースに SQL Server コンピューターをセットアップします。](set-up-sql-server-r-services-in-database.md) 

## <a name="upgrades-or-uninstallation"></a>アップグレードまたはアンインストール

このセクションには、特定のアップグレード シナリオの詳細な手順が含まれています。

### <a name="how-to-upgrade-sql-server"></a>SQL Server をアップグレードする方法

SQL Server のバージョンをアップグレードするには、セットアップ ウィザードを再実行します。

+ [SQL Server をアップグレードする](../../database-engine/install-windows/upgrade-sql-server.md)
+ [インストール ウィザードを使用して SQL Server をアップグレードします。](../../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md)

バインディングと呼ばれるプロセスを使用してコンポーネントを学習、マシンだけをアップグレードすることができます。 
+ [Machine learning のコンポーネントをアップグレードする SqlBindR を使用します。](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)

### <a name="end-of-support-for-in-place-upgrades-from-prerelease-versions"></a>プレリリース バージョンからのインプレース アップグレードのサポートの終了

SQL Server 2016 のプレリリース バージョンからのアップグレードがサポートされていません。 これには、SQL Server 2016 CTP3、CTP3.1、CTP3.2、RC0、または RC1 が含まれます。

次のバージョンは、SQL Server 2016 のプレリリース バージョンと共にインストールされました。

| バージョン | ビルド         |
|---------|---------------|
| CTP 3.0 | 13.0.xxx      |
| CTP 3.1 | 13.0.801.12   |
| CTP 3.2 | 13.0.900.73   |
| CTP 3.3 | 13.0.1000.281 |
| RC1     | 13.0.1200.242 |
| RC2     | 13.0.1300.275 |
| RC3     | 13.0.1400.361 |

バージョンを使用している疑いがある場合は、実行`@@VERSION`SQL Server Management Studio からのクエリにします。

一般に、アップグレードのプロセスのとおりです。

1. スクリプトとデータをバックアップします。
2. プレリリース版をアンインストールします。
3. リリース バージョンをインストールします。

SQL Server のプレリリース版をアンインストールするマシン ラーニング コンポーネントは複雑になることができ、特別なスクリプトを実行する必要があります。 についてのテクニカル サポートに問い合わせてください。

### <a name="support-for-slipstream-upgrades"></a>スリップストリーム アップグレードのサポート

スリップストリーム セットアップとは、問題のあるインスタンスのインストールに修正プログラムまたは更新プログラムを適用して、既存の問題を修復する機能を指します。 このメソッドの場合は、同時にセットアップを実行した後で、別の再起動を回避で SQL Server を更新します。

サーバーがインターネットにアクセスを持たない場合は、SQL Server インストーラーをダウンロードすることを確認します。 更新処理を開始する*前*に、R コンポーネントのインストーラーの一致するバージョンを個別にダウンロードする必要もあります。 

ダウンロードの場所を参照してください。[インターネットにアクセスできないマシン ラーニング コンポーネントをインストールする](installing-ml-components-without-internet-access.md)です。

すべてのセットアップ ファイルがローカル ディレクトリにコピーされたら、コマンド ラインから「SETUP.EXE」と入力してセットアップ ユーティリティを起動します。

- 使用して、 */UPDATESOURCE*累積更新プログラムまたはサービス パック版など、SQL Server 更新を含むローカル ファイルの場所を指定する引数。

- 使用して、 */MRCACHEDIRECTORY* R コンポーネントの CAB ファイルを含むフォルダーを指定する引数。

詳細については、サポート チーム ブログを参照してください:[インターネットにアクセスできないコンピューターでの R Services の配置](https://blogs.msdn.microsoft.com/sqlcat/2016/10/20/do-it-right-deploying-sql-server-r-services-on-computers-without-internet-access/)です。

### <a name="get-machine-learning-components-for-offline-installs"></a>オフライン インストールの machine learning コンポーネントを取得します。

インターネットに接続されていないサーバーをアップグレードまたはインストールする場合は、機械学習のコンポーネントの手動で更新を開始する前の更新バージョンをダウンロードする必要があります。 

+ [インターネットにアクセスできないマシン ラーニング コンポーネントをインストールする](../../advanced-analytics/r/installing-ml-components-without-internet-access.md)です。

### <a name="support-policy-and-schedule-for-update-of-machine-learning-components"></a>Machine learning のコンポーネントの更新プログラムのポリシーとスケジュールをサポートします。

修正プログラムまたは SQL Server の機能強化がリリースされると、machine learning のコンポーネントが自動的にアップグレードまたは更新されると、インスタンスに機能が既に含まれている場合。

年 12 月 2016 では、SQL Server のリリース サイクルよりも高速わかりませんマシン ラーニング コンポーネントをアップグレードできます。 そのためには*バインディング*を最新のソフトウェア ライフ サイクル ポリシーには、SQL Server のインスタンス。 機械学習ツールの新しいバージョンが、機械学習開発チームでリリースされるたびには、最新バージョンをダウンロードし、機械学習のために使用する SQL Server インスタンスに適用します。

詳細については、以下をご覧ください。

+ [Microsoft R Server と Machine Learning のサーバーのサポート タイムライン](https://docs.microsoft.com/machine-learning-server/resources-servicing-support)
+ [SQL Server のインスタンスをアップグレードする SqlBindR を使用して](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)です。

## <a name="r-server-standalone"></a>R Server (スタンドアロン)

このセクションでは、SQL Server 2016 セットアップを使用する Microsoft R Server (スタンドアロン) のインストールに固有の問題について説明します。 

Machine Learning のサーバーを R サーバーからのアップグレードに関連する問題については、次を参照してください。 [Machine Learning Server for Windows のインストール](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install)です。

### <a name="problems-when-r-services-and-r-server-standalone-are-installed-on-the-same-computer"></a>R Services および R Server のスタンドアロンが同じコンピューターにインストールされているときの問題

SQL Server 2016 の以前のバージョンでも同時に R Server (スタンドアロン) と R Services (In-database) の両方をインストールすると、「アクセス拒否」メッセージで失敗するセットアップが発生します。 この問題は、SQL Server 2016 の Service Pack 1 で修正されました。

このエラーが発生しました、これらの機能をアップグレードする必要がある場合は、SQL Server 2016 sp1 のスリップ ストリーム インストールを実行します。 アンインストールと再インストールを必要とする、問題を解決するのには 2 つの方法ができます。

1. R Services (In-database) をアンインストールし、SQLRUserGroup のユーザー アカウントが削除されたかどうかを確認します。

2. サーバーを再起動し、R Server (スタンドアロン) を再インストールします。

3. 実行の SQL Server セットアップの詳細を 1 回、この時間を選択**を既存の SQL Server の機能の追加**です。

4. インスタンスを選択してから、 **R Services (In-database)**を追加するオプションです。

この手順は、問題を解決するのには失敗すると、次の回避策を試してください。

1. 同時に、R Services (In-database) と R Server (スタンドアロン) をアンインストールします。

2. ローカル ユーザー アカウント (SQLRUserGroup) を削除します。

3. サーバーを再起動します。

4. SQL Server セットアップを実行し、R Services (In-database) の機能のみを追加します。 選択しない**R Server (スタンドアロン)**です。

一般に、同じコンピューターに R Services (In-database) と R Server (スタンドアロン) の両方をインストールしないようにお勧めします。 ただし、サーバーを持っていれば、十分な容量、あります R Server のスタンドアロンの開発ツールとして役立ちます可能性。 もう 1 つの可能なシナリオに、R サーバーの操作運用の機能を使用するものデータ移動なしの SQL Server データにアクセスする必要があります。

## <a name="see-also"></a>参照

 [SQL Server R Services の概要](../r/getting-started-with-sql-server-r-services.md)

 [Microsoft R Server のスタンドアロンの概要](../r/getting-started-with-microsoft-r-server-standalone.md)
