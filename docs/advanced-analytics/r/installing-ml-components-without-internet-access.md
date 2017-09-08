---
title: "Machine Learning Components without Internet Access をインストールする |Microsoft ドキュメント"
ms.custom: 
ms.date: 04/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a90c438-d78b-47be-ac05-479de64378b2
caps.latest.revision: 30
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7307104b9ad5df2bb8f034525cc82847d21a14bf
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="installing-machine-learning-components-without-internet-access"></a>Machine Learning Components without Internet Access をインストールします。

SQL Server 2016 または SQL Server 2017 で提供される R、Python のコンポーネントはオープン ソースであるため、Microsoft では既定での R または Python のコンポーネントはインストールされません。

代わりに、関連のインストーラーを提供し、Microsoft ダウンロード センターとその他の信頼済みサイトに便利な機能としてバンドルします。 適切なライセンスに同意する必要があり、し、SQL Server コンポーネントをインストール R または Python をします。

このトピックでは、インストーラーとオフラインのセットアップ プロセスの概要のダウンロード場所を提供します。

## <a name="installation-process"></a>インストール プロセス

通常、SQL Server 2016 および SQL Server 2017 で使用されるマシン コンポーネントのセットアップには、インターネット接続が必要です。 SQL Server セットアップを実行すると、マシン learnig オプションのいずれかを選択した場合、セットアップは確認 Python または R インストーラー、およびその他の必須コンポーネントとしてします。 インターネットに接続する場合は、SQL Server がインストールされます。

> [!IMPORTANT]
> インターネットにアクセスせず、サーバーでセットアップを続行する前にその他のインストーラーをダウンロードする必要があります。

少なくともをインストールする SQL Server のビルド番号またはバージョンはサポートされている R または Python のインストーラーをダウンロードする必要があります。

サーバーの構成によっては、.NET Core など、追加のコンポーネントを必要があります。  参照してください[追加コンポーネント](#bkmk_OtherComponents)詳細についてはします。

インストーラーをダウンロードしたら、使用する SQL Server セットアップの一部として、機能をインストールする場合。

### <a name="step-1-obtain-additional-installers"></a>手順 1. その他のインストーラーを入手します。

**R** SQL Server 2016 および SQL Server 2017 では、2 つの異なるインストーラーを取得する必要があります。 SQL Server セットアップ ウィザードを使用すると、正しい順序でインストールされます。

+ インストーラーで**SRO**名前で、オープン ソース コンポーネントを提供します。
+ Insallers **SRS**名にデータベースの統合を含め、マイクロソフトによって提供されるコンポーネントが含まれています。


**Python** SQL Server の 2017 では、1 つの CAB ファイルとすべての前提条件をダウンロードします。


1. [Microsoft ダウンロード センター サイト](#installerlocs)から、インターネット アクセスのあるコンピューターにインストーラーをダウンロードし 、保存します (実行はしません)。
2. Machine learning のコンポーネントをインストールするコンピューターにインストーラー (CAB) ファイルをコピーします。
3. 現時点では、セットアップ ウィザードは、既定では英語版をインストールします。 別の言語を使用してインストールするインストーラーのファイルの名前変更」の説明に従って:[別の言語ロケールに必要な変更](#modslocales)です。
4. 必要な MPI または .NET Core などその他のコンポーネントをダウンロードします。
5. 必要に応じて、オープン ソース コンポーネントのアーカイブ済みのソース コードをダウンロードすることができますが、これは、SQL Server セットアップに必要ありませんいつでも完了することができます。 詳細については、次を参照してください。 [R Server for Windows](https://msdn.microsoft.com/microsoft-r/rserver-install-windows)です。


> [!NOTE]
> 必ず、インストールする SQL Server のバージョンに対応したファイルを取得してください。
> 
> Python のサポートは、SQL Server 2017 CTP 2.0 で提供されます。 SQL Server 2016 を含む、以前のバージョンは、Python をサポートしていません。

SQL Server 2016 での R Services のオフライン インストール プロセスのステップ バイ ステップ チュートリアルについては、ことをお勧めして資料、 [SQL Server ユーザー諮問チーム](https://blogs.msdn.microsoft.com/sqlcat/2016/10/20/do-it-right-deploying-sql-server-r-services-on-computers-without-internet-access/)です。 この記事では、修正プログラムの適用と、スリップ ストリームのセットアップ シナリオについても説明されています。


### <a name="step-2-run-offline-setup-using-the-sql-server-setup-wizard"></a>手順 2. SQL Server セットアップ ウィザードを使用してオフラインのセットアップを実行します。

1. SQL Server セットアップ ウィザードを実行します。
2. セットアップ ウィザードでは、[ライセンス] ページが表示されたら、クリックして**Accept**です。
3. 入力を求めるダイアログ ボックスが開き、**インストール パス**に必要なパッケージ。
4. をクリックして**参照**先ほどコピーしたインストーラー ファイルを含むフォルダーを検索します。
5. 目的のファイルが見つかったら、**[次へ]** をクリックして、コンポーネントが利用可能であることを示します。
10. SQL Server セットアップ ウィザードを完了します。
11. サービスが有効になっているかどうかを確認する必要なインストール後の手順を実行します。

## <a name="installerlocs"></a>ダウンロード

リリース  |ダウンロード リンク  
---------|---------
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
Microsoft R Open     |[SRO_3.2.2.13000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=831785)
Microsoft R Server     |[SRS_8.0.3.13000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=831676)  |
**SQL Server 2016 SP 1**     |
Microsoft R Open     |[SRO_3.2.2.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824879)
Microsoft R Server     |[SRS_8.0.3.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824881)
**SQL Server 2016 SP 1 GDR**     |
Microsoft R Open     |[SRO_3.2.2.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836819)
Microsoft R Server     |[SRS_8.0.3.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836818)
**SQL Server 2017 CTP 1**     |
Microsoft R Open     |[SRO_3.3.0.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836819)
Microsoft R Server     |[SRS_9.0.0.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836818)
**SQL Server 2017 CTP 1.1** |
Microsoft R Open     |[SRO_3.3.2.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=834568)
Microsoft R Server     |[SRS_9.0.1.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=834567)
**SQL Server 2017 CTP 1.4** |
Microsoft R Open     |[SRO_xxxx_1033.cab](https://go.microsoft.com/fwlink/?LinkId=842483)
Microsoft R Server     |[SRS_xxx.xxx_1033.cab](https://go.microsoft.com/fwlink/?LinkId=842482)
**SQL Server 2017 (CTP 2.0)** |
Microsoft R Open     |[SRO_3.3.3.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=842800)
Microsoft R Server     |[SRS_9.1.0.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=842799)
Microsoft の Python のオープン     |[SPO_9.1.0.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=842828)
Microsoft Python サーバー    |[SPS_9.1.0.0__1033.cab](https://go.microsoft.com/fwlink/?LinkId=842848)

Microsoft R のソース コードを表示したい場合はダウンロード可能な .tar フォーマットでアーカイブとして: [R Server のダウンロードのインストーラー](https://msdn.microsoft.com/microsoft-r/rserver-install-windows#download)

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

インターネットに接続して SQL Server のセットアップ ウィザードを実行し、コンピューターに .cab ファイルをダウンロードすると、ローカルの言語が検出され、インストーラーの言語が自動的に変更されます。

一方、インターネットに接続接続にローカライズされたバージョンの SQL Server のいずれかをコンピューターにインストールし、R インストーラーをローカル共有にインストールする場合、ダウンロードしたファイルの名前を手動で編集し、インストールする言語の正しい言語識別子を挿入する必要があります。

たとえば、日本語バージョンの SQL Server をインストールする場合は、ファイル名を SRS_8.0.3.0_**1033**.cab から SRS_8.0.3.0_**1041**.cab に変更します。


## <a name="slipstream-upgrades"></a>スリップ ストリーム アップグレード

スリップストリーム セットアップとは、問題のあるインスタンスのインストールに修正プログラムまたは更新プログラムを適用して、既存の問題を修復する機能を指します。 この方法の利点は、SQL Server がセットアップの実行と同時に更新されるため、後で別途再起動する必要がないことです。

+ サーバーにインターネット アクセスがない場合は、更新処理を開始する**前に**、SQL Server インストーラーをダウンロードし、対応するバージョンの R コンポーネント インストーラーをダウンロードする必要があります。  R コンポーネントは、既定では、SQL Server は含まれません。

+ 場合*追加*これらのコンポーネントを*既存*インストール、SQL Server インストーラーの更新バージョンを使用し、その他のコンポーネントのバージョンが更新されて、対応します。 R の機能がインストールされることを指定すると、インストーラーが一致する、機械学習のコンポーネントのインストーラーのバージョンで検索します。

## <a name="command-line-arguments-for-setup"></a>セットアップのコマンドライン引数

無人セットアップを実行するときに、次のコマンドライン引数を提供する必要があります。 その他すべてをインストールする追加のフラグを設定する必要はありませんメモには、コンポーネントが必要です。 .NET core などの前提条件は、既定で自動的にインストールされます。

**インストーラーの場所**

- `/UPDATESOURCE`SQL Server 更新プログラムのインストーラーを含むローカル ファイルの場所を指定するには
- `/MRCACHEDIRECTORY`R コンポーネントの CAB ファイルを含むフォルダーを指定するには

**SQL Server 2016 での R コンポーネント**

- `/ADVANCEDANALYTICS`外部スクリプトのエンジンのサポートを取得するには
- `/IACCEPTROPENLICENSETERMS="True"`個別の R 使用許諾契約書に同意するには

**SQL Server SQL Server 2017 で R コンポーネント**

- `/ADVANCEDANALYTICS`外部スクリプトのエンジンのサポートを取得するには
- `/SQL_INST_MR`R を使用するには
- `/IACCEPTROPENLICENSETERMS="True"`個別の R 使用許諾契約書に同意するには

**SQL Server 2017 で Python コンポーネント**

- `/ADVANCEDANALYTICS`外部スクリプトのエンジンのサポートを取得するには
- `/SQL_INST_MPY`Python を使用するには
- `/IACCEPTPYTHONLICENSETERMS="True"`個別の R 使用許諾契約書に同意するには

> [!TIP]
> この記事では、R Services のサポート チームが SQL Server 2016 では、無人インストールまたは R services のアップグレードを実行する方法を示します:[インターネットにアクセスできないコンピューターでの R Services の配置](https://blogs.msdn.microsoft.com/sqlcat/2016/10/20/do-it-right-deploying-sql-server-r-services-on-computers-without-internet-access/)です。

## <a name="see-also"></a>参照

[Microsoft R Server をインストールします。](https://msdn.microsoft.com/microsoft-r/rserver-install-windows)


