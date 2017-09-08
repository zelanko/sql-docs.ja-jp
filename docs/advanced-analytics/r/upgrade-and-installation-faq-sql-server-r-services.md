---
title: "アップグレードとインストールに関してよく寄せられる質問 (SQL Server R Services) | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 06/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 001e66b9-6c3f-41b3-81b7-46541e15f9ea
caps.latest.revision: 59
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: fa3cf5a36af30be655286a2e883d2408a6a3de90
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="upgrade-and-installation-faq-sql-server-r-services"></a>アップグレードとインストールに関してよく寄せられる質問 (SQL Server R サービス)

このトピックでは、機械学習の SQL Server のサービスのインストールに関してよく寄せられる質問に対する回答を示します。 アップグレードに関する一般的な質問についても説明します。 いくつかの問題は、プレリリース版からアップグレードでのみ発生します。 したがって、バージョンとエディションの最新のリリースまたはサービスのリリースにアップグレードして最初をできるだけ早く特定することをお勧めします。

**適用されます:** SQL Server 2016 の R Services、SQL Server 2017 機械学習の Services (In-database)

## <a name="performing-setup-for-the-first-time"></a>初めてセットアップを実行します。

設定するための手順に従って [!INCLUDEssCurrent] と」の説明に従って、R コンポーネント。 

+ [SQL Server R Services または Machine Learning サービス データベース内のセットアップします。](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md)
+ [SQL Server 2017 Python をセットアップします。](../python/setup-python-machine-learning-services.md)
+ [スタンドアロン R Server の作成](create-a-standalone-r-server.md)

外部の R または Python スクリプトを使用して、SQL Server をインストールした後は、いくつかの追加の構成手順を実行する必要があります。 これは、外部スクリプト実行機能が有効でないため、既定でに接する領域を削減します。

> [!NOTE]
> SQL Server 2016 の公開リリースの前に発行されたのセットアップ手順を使用しないでください。 セットアップ プロセスは、以前のリリースと、正式なリリース バージョンの間で完全に変更します。 

### <a name="requirements-and-restrictions"></a>要件および制限

によっては、ビルド R Services をインストールするのでは、次の制限事項の一部は、次のことがありますに適用されます。

- 以前のバージョンの SQL Server 2016 の R Services では、8dot3 表記は、作業ディレクトリを含むドライブに必要でした。 プレリリース版をインストールした場合は、SQL Server 2016 Service Pack 1 へのアップグレードとこの要件を削除する必要があります。

- フェールオーバー クラスターには [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] をインストールできません。 

- Azure vm では、追加の構成必要があります。 たとえば、リモート アクセスをサポートするためにファイアウォール例外を作成する必要があります。

- R の別のバージョンまたは Revolution Analytics からの他のリリースとサイド バイ サイド インストールはサポートされていません。

- [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] のプレリリース バージョンを新しくインストールすることは現在サポートされていません。 リリース前のバージョンを使用している場合はできるだけ早くアップグレードします。

- セットアップを開始する前にウイルスを無効にします。 セットアップが完了すると、ツリー全体では可能であれば、SQL Server が使用されるフォルダーでウイルスを一時停止をお勧めします。

### <a name="licensing-agreements-for-unattended-installs"></a>無人インストールのライセンス契約

SQL Server のインスタンスをアップグレードするコマンドラインを使用する場合は、コマンドラインに新しい使用許諾契約パラメーターが含まれていることを確認してください*/IACCEPTROPENLICENSEAGREEMENT*です。 エラーを適切な引数を使用するには、セットアップが失敗する可能性があります。

### <a name="offline-installation-of-r-components-for-localized-version-of-sql-server"></a>ローカライズされた SQL Server のための R コンポーネントのオフライン インストール

インターネット アクセスが許可されていないコンピューターに R Services をインストールするときに、次の 2 つの追加の手順を行う必要があります: を実行する SQL Server セットアップの前にローカル フォルダーに、R コンポーネントのインストーラーをダウンロードする必要があり、正しい l ことを確認するインストーラー ファイルを編集する必要がありますanguage がインストールされます。

R コンポーネントを使用する言語識別子には、SQL Server セットアップの言語と同じである必要がありますまたは**次**ボタンは無効にして、セットアップを完了することはできません。

詳細については、「 [インターネットへのアクセスなしで R コンポーネントをインストールする](../../advanced-analytics/r-services/installing-ml-components-without-internet-access.md)」を参照してください。

## <a name="post-installation-configuration"></a>インストール後の構成

R、または Python で機械学習を使用するには追加の構成が SQL Server セットアップの実行後に必要です。 追加の手順は、および SQL Server インスタンスとデータベース サーバーのセキュリティ レベルに応じて必要があります。 追加の構成が必要があるかどうかを決定するセットアップ手順から手順を確認します。

[Sql Server R サービス データベース内の設定します。](set-up-sql-server-r-services-in-database.md)

- R、Python などの外部スクリプトの実行をサポートする機能は、データベース セキュリティの既定で無効にし、有効にする必要があります。

- R、Python またはを実行するスタート パッドで使用されるワーカー アカウントに、インスタンスへのアクセスがあることを確認します。 [スタート パッドのアカウントのグループの暗黙の認証を有効にする] を参照してください。

- サーバー上のリモート アクセスを有効にするにまたは SQL Server で着信通信を許可するファイアウォール規則を作成する必要があります。

- 予定のワークロードによっては、機械学習タスク用のサーバーを最適化する必要があります。 

## <a name="upgrades-or-uninstallation"></a>アップグレードまたはアンインストール

このセクションには、特定のアップグレード シナリオの詳細な手順が含まれています。

SQL Server 2016 の R Services のプレリリース版からのアップグレードがサポートされていません。 アンインストールして、できるだけ早くリリース バージョンをインストールすることをお勧めします。

### <a name="support-for-slipstream-upgrades"></a>スリップストリーム アップグレードのサポート

スリップストリーム セットアップとは、問題のあるインスタンスのインストールに修正プログラムまたは更新プログラムを適用して、既存の問題を修復する機能を指します。 この方法の利点は、SQL Server がセットアップの実行と同時に更新されるため、後で別途再起動する必要がないことです。

サーバーにインターネットへのアクセスがない場合は、SQL Server インストーラーをダウンロードしてください。 更新処理を開始する**前**に、R コンポーネントのインストーラーの一致するバージョンを個別にダウンロードする必要もあります。 

ダウンロード場所については、「 [インターネットへのアクセスなしで R コンポーネントをインストールする](installing-ml-components-without-internet-access.md)」を参照してください。

すべてのセットアップ ファイルがローカル ディレクトリにコピーされたら、コマンド ラインから「SETUP.EXE」と入力してセットアップ ユーティリティを起動します。

- "*/UPDATESOURCE*" 引数を使用して、累積的な更新プログラムや Service Pack リリースなどの SQL Server 更新プログラムを含むローカル ファイルの場所を指定します。

- "*/MRCACHEDIRECTORY*" 引数を使用して、R コンポーネント CAB ファイルを含むフォルダーを指定します。

詳細については、サポート チーム ブログを参照してください:[インターネットにアクセスできないコンピューターでの R Services の展開](https://blogs.msdn.microsoft.com/sqlcat/2016/10/20/do-it-right-deploying-sql-server-r-services-on-computers-without-internet-access/)

### <a name="upgrading-r-components-offline"></a>オフラインの R コンポーネントをアップグレードします。

インターネットに接続されていないサーバーをインストールまたはアップグレードする場合は、更新を始める前に、更新されたバージョンの R コンポーネントを手動でダウンロードする必要があります。 詳細については、「 [インターネットへのアクセスなしで R コンポーネントをインストールする](../../advanced-analytics/r-services/installing-ml-components-without-internet-access.md)」を参照してください。

### <a name="schedule-for-update-of-r-components"></a>R コンポーネントの更新のスケジュール

修正プログラムまたは SQL Server 2016 の機能強化がリリースされると、R コンポーネントがアップグレードまたは、インスタンスには既に、R Services の機能が含まれている場合も、更新します。

SQL Server 2017 を使用している場合、R コンポーネントをアップグレードが自動的にインストールします。

年 12 月 2016 でことも、SQL Server のリリース サイクルよりも高速リズムに R コンポーネントをアップグレードする*バインディング*を最新のソフトウェア ライフ サイクル ポリシーには、R Services のインスタンス。 現在サポートは 2016 インスタンスのアップグレードにのみ提供されます。 ただし、R Server の新しいバージョンがリリースされたときに、2017 インスタンスもアップグレードすることができます。

詳しくは、[「Use SqlBindR to Upgrade an Instance of SQL Server R Services」](../../advanced-analytics/r-services/use-sqlbindr-exe-to-upgrade-an-instance-of-r-services.md)(SqlBindR を使用して SQL Server R Services のインスタンスをアップグレードする) をご覧ください

### <a name="upgrading-from-a-pre-release-version-of-sql-server-2016"></a>SQL Server 2016 のリリース前のバージョンからアップグレードします。

一般に、インプレース アップグレードは、プレリリース版のサポートされていません。

R Services を正常にインストールするには、以前のバージョンをアンインストールする必要があります[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]と関連するその R コンポーネントを SQL Server 2016 CTP3、CTP3.1、CTP3.2、RC0、RC1 などです。

プレリリース版をアンインストールする複雑で、特別なスクリプトを実行している必要があります。サポートが必要な場合は、テクニカル サポートに問い合わせることをお勧めします。

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

バージョンを使用している疑いがある場合は、実行`@@VERSION`SQL Server Management Studio からです。

### <a name="problems-with-setup-of-r-server-standalone"></a>R Server (スタンドアロン) のセットアップに関する問題

このセクションでは、SQL Server 2016 セットアップを使用して Microsoft R Server (スタンドアロン) のインストールに固有の問題について説明します。 R Server のアップグレードに関連する一般的な問題は、MSDN サイトを参照してください[Microsoft R Server](https://msdn.microsoft.com/microsoft-r/)です。

#### <a name="failure-to-install-localized-versions"></a>ローカライズされたバージョンのインストールに失敗しました。

を R サーバーのインストール、オフラインを実行するときにプレリリース版できないするローカライズされた言語を使用します。

一般に、セットアップを実行する前に、サーバーがインターネットにアクセスを持たない R Server のすべてのインストール パッケージをダウンロードしてインストール中に、ファイルの場所を指定します。

ただし、言語識別子に関連付けられている場合、インストーラー パッケージがない SQL Server セットアップの言語と同じ R コンポーネントのインストールのページが表示されたら、**次**ボタンが無効になりを続行することはできません、インストール。 この問題を回避するには、一致する識別子を使用するパッケージに名前を変更することができます。

たとえば、パッケージのインストール パッケージの名前があります`SRO_3.2.2.0_1031.cab`です。
104 言語 SQL Server をインストールするファイルの名前を変更`SRO_3.2.2.0_1041.cab`です。

#### <a name="installing-r-services-and-r-server-standalone-on-the-same-computer"></a>同じコンピューターに R Services と R Server のスタンドアロン インストール

一般に、同じコンピューターに R Services (In-database) と R Server (スタンドアロン) をインストールするのには推奨されません。 ただし、サーバーに十分な容量がある場合、R Server のスタンドアロンが開発ツールとして役立ちます可能性があります。 機能を使用して、操作運用 R Server のデータ移動なし R Server から SQL Server のデータにアクセスする必要もあります。

R Server と R Services の両方を同じコンピューターにインストールする場合の R ライブラリには、同じ 2 つのセットがインストールされていることに注意してください。 SQL server インスタンスで使用するための 1 つ、開発用の 1 つを使用または R Server で使用します。

SQL Server 2016 の以前のバージョンで R Server (スタンドアロン) と R Services (In-database) の両方を同時にインストールすることによって、セットアップ「アクセス拒否」メッセージで失敗します。 この問題は、SQL Server 2016 の Service Pack 1 で修正されました。

このエラーが発生してこれらの機能をアップグレードする必要がある場合は、SQL Server 2016 sp1 のスリップ ストリーム インストールを実行することをお勧めします。 これにはアンインストールを必要として、再インストールの両方の問題を解決するのには 2 つの方法があります。

1. R Services (In-database) をアンインストールし、SQLRUserGroup のユーザー アカウントが削除されたかどうかを確認します。

2. サーバーを再起動し、R Server (スタンドアロン) を再インストールします。

3. 実行の SQL Server セットアップの詳細を 1 回、この時間を選択**を既存の SQL Server の機能の追加**です。

4. インスタンスを選択してから、 **R Services (In-database)**を追加するオプションです。

場合によっては、障害が発生した以前のインストールを削除するこの手順は失敗します。 その場合は、アンインストールして、次のように再インストールする必要があります。

1. 同時に、R Services (In-database) と R Server (スタンドアロン) をアンインストールします。

2. ローカル ユーザー アカウント (SQLRUserGroup) を削除します。

3. サーバーを再起動します。

4. SQL Server セットアップを実行し、R Services (In-database) の機能のみを追加します。 選択しない**R Server (スタンドアロン)**です。

## <a name="see-also"></a>参照

 [SQL Server R Services の概要](../r/getting-started-with-sql-server-r-services.md)

 [Microsoft R Server のスタンドアロンの概要](../r/getting-started-with-microsoft-r-server-standalone.md)

