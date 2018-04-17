---
title: インターネットにアクセスせず、機械学習の SQL Server コンポーネントのインストール |Microsoft ドキュメント
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 3ba344147b5d57a1c0168fbb5be93ae24b02b179
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="install-sql-server-machine-learning-components-without-internet-access"></a>SQL Server コンピューターがインターネットにアクセスできないコンポーネントの学習をインストールします。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

既定では、インストーラーが必要な取得を Microsoft ダウンロード サイトに接続し、更新されたコンポーネントのコンピューターの SQL Server に関する学習します。 ファイアウォールの制約は、インストーラーがこれらのサイトに到達することを防ぐ場合、は、ファイルをダウンロード、オフライン サーバーにファイルを転送し、セットアップを実行する、インターネットに接続されたデバイスを使用できます。

## <a name="get-the-installation-media"></a>インストール メディアを入手する

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]

> [!NOTE]  
> ローカル インストールの場合は、セットアップを管理者として実行する必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をリモート共有からインストールする場合は、そのリモート共有に対する読み取り権限と実行権限を持つドメイン アカウントを使用する必要があります。  
 
 ###  <a name="bkmk_ga_instalpatch"></a> インストールのパッチ要件 

SQL Server の前提条件としてインストールされる特定のバージョンの Microsoft VC++ 2013 ランタイム バイナリに問題が見つかりました。 VC ランタイム バイナリに対するこの更新プログラムをインストールしないと、特定のシナリオにおいて、SQL Server で安定性の問題が発生する可能性があります。 SQL Server をインストールする前に、「[SQL Server リリース ノート](../../sql-server/sql-server-2016-release-notes.md#bkmk_ga_instalpatch)」にある手順に従って、ご使用のコンピューターに VC ランタイム バイナリのパッチが必要かどうかを確認してください。  


## <a name="download-cab-files"></a>.Cab ファイルをダウンロードします。

インターネットに接続されたサーバーでは、オフライン インストールに必要な .cab ファイルをダウンロードします。 セットアップ プログラムでは、.cab ファイルを使用して、補足の機能をインストールします。

リリース  |ダウンロード リンク  |
---------|---------|
**SQL Server 2017 初期リリース** |
Microsoft R Open     |[SRO_3.3.3.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851496)|
Microsoft R Server      |[SRS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851507)|
Microsoft の Python のオープン     |[SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502) |
Microsoft Python サーバー    |[SPS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851508) |
**SQL Server 2017 CU1** |
Microsoft R Open     |変更はありません。以前の使用|
Microsoft R Server      |[SRS_9.2.0.100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851501)|
Microsoft の Python のオープン     |変更はありません。以前の使用 |
Microsoft Python サーバー    |[SPS_9.2.0.100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851500) |
**SQL Server 2017 CU2** |
Microsoft R Open     |変更はありません。以前の使用|
Microsoft R Server      |変更はありません。以前の使用|
Microsoft の Python のオープン     |変更はありません。以前の使用|
Microsoft Python サーバー    |変更はありません。以前の使用|
**SQL Server 2017 CU3** |
Microsoft R Open     |[SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)|
Microsoft R Server      |[SRS_9.2.0.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863893)|
Microsoft の Python のオープン     |変更はありません。以前の使用|
Microsoft Python サーバー    |[SPS_9.2.0.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863892)|
**SQL Server 2017 CU4** |
Microsoft R Open     |変更はありません。以前の使用|
Microsoft R Server      |[SRS_9.2.0.400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866212&clcid=1033)|
Microsoft の Python のオープン     |変更はありません。以前の使用|
Microsoft Python サーバー    |[SPS_9.2.0.400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866213&clcid=1033)|

### <a name="bkmk_2016Installers"></a>SQL Server 2016 のダウンロード

> [!IMPORTANT]
> 
> SQL Server 2016 SP1 CU4、または SP1 CU5 のオフライン インストール、SRO_3.2.2.16000_1033.cab をダウンロードします。 セットアップ ダイアログ ボックスで指定されている、FWLINK 831785 から SRO_3.2.2.13000_1033.cab をダウンロードした場合は、累積更新プログラムをインストールする前に SRO_3.2.2.16000_1033.cab としてファイルを変更します。

リリース  |ダウンロード リンク  |
---------|---------|
**SQL Server 2016 RTM**     |
Microsoft R Open     |[SRO_3.2.2.803_1033.cab](https://go.microsoft.com/fwlink/?LinkId=761266)
Microsoft R Server     |[SRS_8.0.3.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=735051)
**SQL Server 2016 CU 1**     |
Microsoft R Open     |[SRO_3.2.2.10000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=808803)
Microsoft R Server     |[SRS_8.0.3.10000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=808805)
**SQL Server 2016 CU 2**     |
Microsoft R Open     |[SRO_3.2.2.12000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=827398)
Microsoft R Server     |[SRS_8.0.3.12000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=827399)
**SQL Server 2016 CU 3**     |
Microsoft R Open     |変更はありません。以前の使用|
Microsoft R Server     | 変更はありません。以前の使用 |
**SQL Server 2016 CU 4**     |
Microsoft R Open     |[SRO_3.2.2.13000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=831785)|
Microsoft R Server     |[SRS_8.0.3.13000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=831676)|
**SQL Server 2016 CU 5**     |
Microsoft R Open     |変更はありません。以前の使用|
Microsoft R Server     |変更はありません。以前の使用|
**SQL Server 2016 CU 6**     |
Microsoft R Open     |変更はありません。以前の使用|
Microsoft R Server     |[SRS_8.0.3.14000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=850316)  |
**SQL Server 2016 CU 7**     |
Microsoft R Open     |変更はありません。以前の使用|
Microsoft R Server     |変更はありません。以前の使用 |
**SQL Server 2016 SP 1**     |
Microsoft R Open     |[SRO_3.2.2.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824879)
Microsoft R Server     |[SRS_8.0.3.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824881)
**SQL Server 2016 SP 1 CU1**     |
Microsoft R Open     |変更はありません。以前の使用|
Microsoft R Server     |変更はありません。以前の使用|
**SQL Server 2016 SP 1 CU2**     |
Microsoft R Open     |[SRO_3.2.2.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836819)|
Microsoft R Server    |[SRS_8.0.3.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836818)|
**SQL Server 2016 SP 1 CU3**     |
Microsoft R Open     |変更はありません。以前の使用|
Microsoft R Server     |変更はありません。以前の使用|
**SQL Server 2016 SP 1 CU4 と GDR**     |
Microsoft R Open     |変更はありません。以前の使用|
Microsoft R Server    |[SRS_8.0.3.17000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=850317)
**SQL Server 2016 SP 1 CU5**     |
Microsoft R Open     |変更はありません。以前の使用|
Microsoft R Server    |変更はありません。以前の使用 |

Microsoft R のソース コードを表示したい場合はダウンロード可能な .tar フォーマットでアーカイブとして: [R Server のダウンロードのインストーラー](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows#download)

### <a name = "bkmk_OtherComponents"></a>追加の前提条件

環境によっては、次の必須コンポーネント用に、インストーラーのローカル コピーを作成しなければならない場合があります。

コンポーネント  |バージョン
---------|---------
[SQL Server 2016 用 Microsoft AS OLE DB プロバイダー](https://go.microsoft.com/fwlink/?linkid=834405)     |  13.0.1601.5
[Microsoft .NET Core](https://go.microsoft.com/fwlink/?linkid=834319)     | 1.0.1
[Microsoft MPI](https://go.microsoft.com/fwlink/?linkid=834316)     | 7.1.12437.25
[Microsoft Visual C++ 2013 再頒布可能パッケージ](https://go.microsoft.com/fwlink/?linkid=799853)     | 12.0.30501.0
[Microsoft Visual C++ 2015 再頒布可能パッケージ](https://go.microsoft.com/fwlink/?linkid=828641)     | 14.0.23026.0

## <a name="transfer-files"></a>ファイルを転送します。

Zip 形式の SQL Server インストール メディアとセットアップをインストールしているコンピューターに既にダウンロードしたファイルを転送します。

など、任意のフォルダーに CAB ファイルを配置**ダウンロード**またはセットアップ ユーザーの temp フォルダー: C:\Users < ユーザー名 > \AppData\Local\Temp です。

En_sql_server_2017.iso ファイルを任意のフォルダーに配置します。 ダブルクリックして**setup.exe**インストールを開始します。

### <a name="run-setup"></a>セットアップの実行

セットアップを追加、インターネットから切断されているコンピューターで SQL Server セットアップを実行すると、**オフライン インストール**前の手順でコピーした .cab ファイルの場所を指定できるように、ウィザード ページです。

1. SQL Server セットアップ ウィザードを起動します。

2. セットアップ ウィザードでは、オープン ソース R または Python コンポーネントでの [ライセンス] ページが表示されたら、クリックして**Accept**です。 ライセンス条項に同意を使用すると、次の手順に進むことができます。

3. **オフライン インストール**] ページの [**インストール パス**、先ほどコピーした .cab ファイルを含むフォルダーを指定します。

4. 続行次の画面に表示されるインストールを完了するように求められます。

インストールが完了したら、サービスを再起動し、サーバーと構成」の説明に従って、スクリプトの実行を有効にする[インストール SQL Server 2017 Machine Learning Services (In-database)](sql-machine-learning-services-windows-install.md)または[SQL Server のインストール2016 R Services (In-database)](sql-r-services-windows-install.md)です。

## <a name="slipstream-upgrades-for-offline-servers"></a>オフライン サーバーのスリップ ストリーム アップグレード

スリップストリーム セットアップとは、問題のあるインスタンスのインストールに修正プログラムまたは更新プログラムを適用して、既存の問題を修復する機能を指します。 この方法の利点は、SQL Server がセットアップの実行と同時に更新されるため、後で別途再起動する必要がないことです。

+ サーバーにインターネット アクセスがない場合は、更新処理を開始する**前に**、SQL Server インストーラーをダウンロードし、対応するバージョンの R コンポーネント インストーラーをダウンロードする必要があります。  R コンポーネントは、既定では、SQL Server は含まれません。

+ 既存のインストールにこれらのコンポーネントを追加する場合は、更新されたバージョンの SQL Server インストーラー、およびその他のコンポーネントの対応する更新されたバージョンを使用します。 R の機能がインストールされることを指定すると、インストーラーは、一致する、機械学習のコンポーネントのインストーラーのバージョンが検索されます。

## <a name="get-help"></a>ヘルプの参照

ヘルプをインストールまたはアップグレードが必要ですか。 よく寄せられる質問と既知の問題への回答は、次の記事を参照してください。

* [アップグレードとインストールに関する FAQ - Machine Learning サービス](../r/upgrade-and-installation-faq-sql-server-r-services.md)

インスタンスのインストール状態をチェックして、一般的な問題を修正、これらのカスタム レポートを実行してください。

* [SQL Server R Services のカスタム レポート](../r/monitor-r-services-using-custom-reports-in-management-studio.md)

この記事では、R Services のサポート チームが SQL Server 2016 では、無人インストールまたは R services のアップグレードを実行する方法を示します:[インターネットにアクセスできないコンピューターでの R Services の配置](https://blogs.msdn.microsoft.com/sqlcat/2016/10/20/do-it-right-deploying-sql-server-r-services-on-computers-without-internet-access/)です。


## <a name="next-steps"></a>次の手順

R の開発者は、単純な例についてで始めることができ、SQL Server での R の動作の基礎を学習します。 次の手順は、次のリンクを参照してください。

+ [チュートリアル: T-SQL で R を実行します。](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [R 開発者向けチュートリアル: データベース内の分析](../tutorials/sqldev-in-database-r-for-sql-developers.md)

Python 開発者は、これらのチュートリアルに従って SQL Server で Python を使用する方法を学習できます。

+ [チュートリアル: T-SQL で Python を実行します。](../tutorials/run-python-using-t-sql.md)
+ [Python 開発者のためのチュートリアル: データベース内の分析](../tutorials/sqldev-in-database-python-for-sql-developers.md)

実際のシナリオに基づく機械学習の例を表示するを参照してください。[機械学習のチュートリアル](../tutorials/machine-learning-services-tutorials.md)です。

