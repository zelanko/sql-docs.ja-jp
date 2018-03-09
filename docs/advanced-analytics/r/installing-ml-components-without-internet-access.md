---
title: "インターネットにアクセスできないマシン ラーニング コンポーネントをインストールする |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/05/2018
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a90c438-d78b-47be-ac05-479de64378b2
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: d7d218dcb5efeddf248230abff85b46da23d389a
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2018
---
# <a name="installing-machine-learning-components-without-internet-access"></a>インターネットにアクセスできないマシン ラーニング コンポーネントをインストールします。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server 2016 および SQL Server 2017 で提供される R、Python のコンポーネントはオープン ソースであるため、Microsoft では既定での R または Python のコンポーネントはインストールされません。 代わりに、関連のインストーラーを提供し、Microsoft ダウンロード センターとその他の信頼済みサイトに便利な機能としてバンドルします。 適切なライセンスに同意する必要があり、し、SQL Server セットアップ R または Python のコンポーネントがインストールされます。

このトピックでは、インストーラーとオフラインのセットアップ プロセスの概要のダウンロード場所を提供します。

## <a name="overview-of-the-offline-installation-process"></a>オフライン インストール プロセスの概要

通常、SQL Server 2016 および SQL Server 2017 で使用されるマシン コンポーネントのセットアップには、インターネット接続が必要です。 SQL Server セットアップを実行すると、機械学習のオプションのいずれかを選択した場合、セットアップを確認、Python または R インストーラー、およびその他の必須コンポーネントとしてします。

+ **コンピューターがインターネットに接続している場合**

    SQL Server を検索し、コンポーネントをダウンロードし、し、セットアップ時にインストールされます。 各オープン ソース R (Python) するコンポーネントをインストールするのとは別にライセンス条項に同意します。

+ **コンピューターにインターネットへのアクセスがあるない場合**

    セットアップを続行する前に、その他のインストーラーをダウンロードする必要があります。 少なくともをインストールする SQL Server のバージョンがサポートされている R または Python のインストーラーをダウンロードします。

    サーバーの構成によっては、追加のコンポーネントを必要があります。  参照してください[追加コンポーネント](#bkmk_OtherComponents)詳細についてはします。

    インストーラーをダウンロードしたら、使用する SQL Server セットアップの一部として、機能をインストールする場合。

### <a name="step-1-obtain-additional-installers"></a>手順 1. その他のインストーラーを入手します。

一般に、別々 のインストーラーは、オープン ソース アプリケーションおよび独自のコンポーネントに提供されます。 SQL Server セットアップ ウィザードが正しい順序でインストールされることを確認します。 ただし、一部のリリースは、コンポーネントの 1 つだけのセットを更新して可能性があります。 参照してください、[インストーラーのテーブル](#bkmk_2017Installers)については、リリースごとです。

**R の**

R 言語には、SQL Server 2016 以降はサポートされています。 

+ インストーラーで**SRO**名前で、オープン ソース コンポーネントを提供します。
+ インストーラーで**SRS**名にデータベースの統合を含め、マイクロソフトによって提供されるコンポーネントが含まれています。

**Python の**

Python 言語には、SQL Server 2017 以降が必要です。 

+ インストーラーで**SPO**名には、マイクロソフト Python のオープンし、オープン ソース コンポーネントを提供します。
+ インストーラーで**SPS**名前では、Microsoft Python サーバーの場合があり、データベースの統合を含め、マイクロソフトによって提供されるコンポーネントが含まれています。

**ダウンロードする方法**

1. インストーラーをダウンロード、 [Microsoft ダウンロード センター サイト](#installerlocs)インターネットにアクセスし、それを実行するのではなく、インストーラーを保存するコンピュータにします。
2. Machine learning のコンポーネントをインストールするコンピューターにインストーラー (CAB) ファイルをコピーします。
3. SQL Server 2016 では、セットアップ ウィザードは、既定で英語をインストールします。 別の言語を使用してインストールするために必要なインストーラーのファイル名の変更」の説明に従って:[別の言語のロケールの変更に必要な](#modslocales)します。
    SQL Server 2017、適切な言語はインスタンスのロケールに基づいて識別されます。
4. 必要な MPI または .NET Core などその他のコンポーネントをダウンロードします。
5. 必要に応じて、オープン ソース コンポーネントのアーカイブ済みのソース コードをダウンロードすることができますが、これは、SQL Server セットアップに必要ありませんいつでも完了することができます。 詳細については、次を参照してください。 [R Server for Windows](https://docs.microsoft.com/r-server/install/r-server-install-windows)です。

SQL Server 2016 での R Services のオフライン インストール プロセスのステップ バイ ステップ チュートリアルについては、ことをお勧めして資料、 [SQL Server ユーザー諮問チーム](https://blogs.msdn.microsoft.com/sqlcat/2016/10/20/do-it-right-deploying-sql-server-r-services-on-computers-without-internet-access/)です。 アーティクルは、スクリーン ショットが含まれていて、修正プログラムの適用とスリップ ストリームのセットアップ シナリオについても説明します。

### <a name="step-2-run-offline-setup-using-the-sql-server-setup-wizard"></a>手順 2. SQL Server セットアップ ウィザードを使用してオフラインのセットアップを実行します。

1. SQL Server セットアップ ウィザードを実行します。
2. セットアップ ウィザードでは、[ライセンス] ページが表示されたら、クリックして**Accept**です。
3. 入力を求めるダイアログ ボックスが開き、**インストール パス**に必要なパッケージ。
4. をクリックして**参照**先ほどコピーしたインストーラー ファイルを含むフォルダーを検索します。
5. 目的のファイルが見つかったら、**[次へ]** をクリックして、コンポーネントが利用可能であることを示します。
6. SQL Server セットアップ ウィザードを完了します。
7. サービスが有効になっているかどうかを確認する必要なインストール後の手順を実行します。

## <a name="installerlocs"></a>Machine learning のコンポーネントをダウンロードする場所

インストールする SQL Server のバージョンに一致するファイルを取得してください。

+ [SQL Server 2016 の R コンポーネントを取得するには](#bkmk_2016Installers)

+ [SQL Server 2017 の R または Python のコンポーネントを取得するには](#bkmk_2017Installers)

Python のサポートは、SQL Server 2017 CTP 2.0 以降で提供されます。 SQL Server 2016 を含む、以前のバージョンは、Python をサポートしていません。

### <a name="bkmk_2017Installers"></a>SQL Server 2017 のダウンロード

リリース  |ダウンロード リンク  |
---------|---------|
**SQL Server 2017 CTP 1**     |
Microsoft R Open     |[SRO_3.3.0.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836819)
Microsoft R Server     |[SRS_9.0.0.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836818)
**SQL Server 2017 CTP 1.1** |
Microsoft R Open     |[SRO_3.3.2.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=834568)
Microsoft R Server     |[SRS_9.0.1.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=834567)
**SQL Server 2017 CTP 1.4** |
Microsoft R Open     |[SRO_3.3.2.100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=842483)
Microsoft R Server     |[SRS_9.0.2.100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=842482)
**SQL Server 2017 CTP 2.0** |
Microsoft R Open     |[SRO_3.3.3.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=842800)
Microsoft R Server     |[SRS_9.1.0.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=842799)
Microsoft の Python のオープン     |[SPO_9.1.0.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=842828)
Microsoft Python Server    |[SPS_9.1.0.0__1033.cab](https://go.microsoft.com/fwlink/?LinkId=842848)
**SQL Server 2017 RC1** |
Microsoft R Open     |[SRO_3.3.3.22_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851503)|
Microsoft R Server     |[SRS_9.2.0.22_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851498)|
Microsoft の Python のオープン     |[SPO_9.2.0.22_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851499)|
Microsoft Python Server    |[SPS_9.2.0.22_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851504)|
**SQL Server 2017 RC 2** |
Microsoft R Open     |[SRO_3.3.3.23_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851493)|
Microsoft R Server     |[SRS_9.2.0.23_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851505)|
Microsoft の Python のオープン     |[SPO_9.2.0.23_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851506)|
Microsoft Python Server    |[SPS_9.2.0.23_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851497)|
**SQL Server 2017 RTM** |
Microsoft R Open     |[SRO_3.3.3.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851496)|
Microsoft R Server      |[SRS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851507)|
Microsoft の Python のオープン     |[SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502) |
Microsoft Python Server    |[SPS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851508) |
**SQL Server 2017 CU1** |
Microsoft R Open     |変更はありません。以前の使用|
Microsoft R Server      |[SRS_9.2.0.100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851501)|
Microsoft の Python のオープン     |変更はありません。以前の使用 |
Microsoft Python Server    |[SPS_9.2.0.100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851500) |
**SQL Server 2017 CU2** |
Microsoft R Open     |変更はありません。以前の使用|
Microsoft R Server      |変更はありません。以前の使用|
Microsoft の Python のオープン     |変更はありません。以前の使用|
Microsoft Python Server    |変更はありません。以前の使用|
**SQL Server 2017 CU3** |
Microsoft R Open     |[SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)|
Microsoft R Server      |[SRS_9.2.0.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863893)|
Microsoft の Python のオープン     |変更はありません。以前の使用|
Microsoft Python Server    |[SPS_9.2.0.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863892)|
**SQL Server 2017 CU4** |
Microsoft R Open     |変更はありません。以前の使用|
Microsoft R Server      |[SRS_9.2.0.400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866212&clcid=1033)|
Microsoft の Python のオープン     |変更はありません。以前の使用|
Microsoft Python Server    |[SPS_9.2.0.400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866213&clcid=1033)|

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

## <a name="modslocales"></a>別の言語のロケールをインストールします。

ダウンロードするかどうか、します。SQL Server セットアップの一部として、インターネット アクセスのセットアップ ウィザードを使用しているコンピューター上の CAB ファイルは、ローカルの言語を検出し、インストーラーの言語を自動的に変更します。

ただし、SQL Server のバージョンによって、インターネットにアクセスできないコンピューターにローカライズされた R コンポーネントをインストールする追加の手順を実行する必要があります。

+ **SQL Server 2016 用**

   ローカルの共有に、R インストーラーをダウンロードした後は、手動でインストールする言語の適切な言語識別子を挿入する、ダウンロードしたファイルの名前を編集する必要があります。

    たとえば、日本語バージョンの SQL Server をインストールするには変更するファイルの名前 SRS_8.0.3.0_ から**1033**SRS_8.0.3.0_ に .cab**1041**.cab です。

    > [!IMPORTANT]
    > この問題は、だけに以前のバージョンを適用し、今後のリリースで修正されました。
    > **インストーラーには、適切な言語をインストールできないこと、メッセージが返された場合のみこの回避策を使用します。**

+ **SQL server 2017**

    ダウンロードします。R、Python またはコンポーネントの CAB ファイルです。
    
    サーバー ロケールに基づく言語が検出されました。 ダウンロードしたを使用して、適切なロケールが自動的にインストールします。CAB ファイルです。

## <a name="slipstream-upgrades"></a>スリップ ストリーム アップグレード

スリップストリーム セットアップとは、問題のあるインスタンスのインストールに修正プログラムまたは更新プログラムを適用して、既存の問題を修復する機能を指します。 この方法の利点は、SQL Server がセットアップの実行と同時に更新されるため、後で別途再起動する必要がないことです。

+ サーバーにインターネット アクセスがない場合は、更新処理を開始する**前に**、SQL Server インストーラーをダウンロードし、対応するバージョンの R コンポーネント インストーラーをダウンロードする必要があります。  R コンポーネントは、既定では、SQL Server は含まれません。

+ 既存のインストールにこれらのコンポーネントを追加する場合は、更新されたバージョンの SQL Server インストーラー、およびその他のコンポーネントの対応する更新されたバージョンを使用します。 R の機能がインストールされることを指定すると、インストーラーは、一致する、機械学習のコンポーネントのインストーラーのバージョンが検索されます。

## <a name="command-line-arguments-for-specifying-component-locations"></a>コンポーネントの場所を指定するためのコマンドライン引数

オフラインのセットアップを実行して、コマンドラインから、事前にダウンロードしたコンポーネントの場所を指定する次のコマンドライン引数を指定する必要があります。 ただし、; 必要な追加のコンポーネントをインストールする追加のフラグを設定する必要はありません.NET core などの前提条件は、既定で自動的にインストールされます。

**インストーラーの場所**

- `/UPDATESOURCE` SQL Server 更新プログラムのインストーラーを含むローカル ファイルの場所を指定するには
- `/MRCACHEDIRECTORY` R コンポーネントの CAB ファイルを含むフォルダーを指定するには
- `/MPYCACHEDIRECTORY` Python コンポーネントの CAB ファイルを含むフォルダーを指定するには

**SQL Server 2016 での R コンポーネント**

- `/ADVANCEDANALYTICS` 外部スクリプトのエンジンのサポートを取得するには
- `/IACCEPTROPENLICENSETERMS="True"` 個別の R 使用許諾契約書に同意するには

**SQL Server 2017 で R コンポーネント**

- `/ADVANCEDANALYTICS` 外部スクリプトのエンジンのサポートを取得するには
- `/SQL_INST_MR` R を使用するには
- `/IACCEPTROPENLICENSETERMS="True"` 個別の R 使用許諾契約書に同意するには

**SQL Server 2017 で Python コンポーネント**

- `/ADVANCEDANALYTICS` 外部スクリプトのエンジンのサポートを取得するには
- `/SQL_INST_MPY` Python を使用するには
- `/IACCEPTPYTHONLICENSETERMS="True"` 個別の Python 使用許諾契約書に同意するには

> [!NOTE]
> SQL Server セットアップでパラメーターを使用して、スタート パッドのサービス アカウントを変更できません。 既定のサービス アカウントを使用してインストールして SQL Server 構成マネージャーを使用して、サービス アカウントを変更することをお勧めします。 その後、必ず、スタート パッド サービスを再起動してください。

## <a name="see-also"></a>参照

[Microsoft R Server をインストールします。](https://docs.microsoft.com/r-server/install/r-server-install-windows)

この記事では、R Services のサポート チームが SQL Server 2016 では、無人インストールまたは R services のアップグレードを実行する方法を示します:[インターネットにアクセスできないコンピューターでの R Services の配置](https://blogs.msdn.microsoft.com/sqlcat/2016/10/20/do-it-right-deploying-sql-server-r-services-on-computers-without-internet-access/)です。
