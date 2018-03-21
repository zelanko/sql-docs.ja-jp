---
title: "Machine Learning サーバー スタンドアロンまたは R Server のスタンドアロン インストール |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/14/2018
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 408e2503-5c7d-4ec4-9d3d-bba5a8c7661d
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: 2ecb60bd02b3fc1ee7ac7101749fa7affc2523bd
ms.sourcegitcommit: 6bd21109abedf64445bdb3478eea5aaa7553fa46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/20/2018
---
# <a name="install-machine-learning-server-standalone-or-r-server-standalone"></a>Machine Learning Server (スタンドアロン) または R Server (スタンドアロン) をインストールします。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server セットアップには、機械学習の SQL Server の外部で実行しているサーバーをインストールするオプションが含まれています。 このオプションは、リモート計算コンテキストを使用できるかなど、複数のプラットフォームに配置できるように、高パフォーマンス マシン ラーニング ソリューションを開発する必要がある場合に便利です。
  
  + SQL Server 2016 または機械学習が有効になっている SQL Server 2017 のインスタンス
  + Hadoop または Spark クラスター内 R サーバーの Machine Learning のサーバー インスタンス
  + R Server または linux マシン ラーニング サーバー

この記事では、SQL Server セットアップを使用して、マシン学習サーバーまたは Microsoft R Server のスタンドアロン バージョンをインストールする方法について説明します。 Enterprise Edition またはソフトウェア アシュアランスがある場合、機械学習のスタンドアロン サーバーをインストールするは無料です。

+ [R Server のインストール](#bkmk_installRServer)-SQL Server 2016 セットアップを使用
+ [Machine Learning のサーバーをインストール](#bkmk_installMLServer)-SQL Server 2017 セットアップを使用
+ [Microsoft R Server の既存のインスタンスをアップグレードします。](#bkmk_upgrade)
+ [インストールするものの判断に役立つ](#bkmk_tips)

##  <a name="bkmk_installMLServer"></a> Machine Learning Server (スタンドアロン) のインストールします。

この機能は、エンタープライズ ライセンスまたは対応するものが必要です。 **SQL Server 2017**です。

Microsoft R Server の以前のバージョンをインストールした場合は、最初にアンインストールすることをお勧めします。

コンピューターがインターネットにアクセスできる、事前にコンポーネントのインストーラーをダウンロードする必要があります。 詳細については、次を参照してください。[インターネットにアクセスできないマシン ラーニング コンポーネントをインストールする](./installing-ml-components-without-internet-access.md)です。

1. SQL Server 2017 セットアップを実行します。

2. クリックして、**インストール**タブをクリックし、選択**Machine Learning Server (スタンドアロン) の新規インストール**です。
    
     ![Machine Learning サーバーをスタンドアロンでインストール](media/2017setup-installation-page-mlsvr.png "の Machine Learning Server のスタンドアロン インストールを開始")

3. ルールのチェックが完了したら、SQL Server のライセンス条項に同意し、新規インストールを選択します。

4. **機能の選択**ページで、次のオプションは既に選択されている必要があります。

    - マイクロソフトの機械学習のサーバー (スタンドアロン)

    - R と Python 既定で選択します。 いずれかの言語の選択を解除することができますが、サポートされている言語の少なくとも 1 つをインストールすることをお勧めします。

     ![Machine Learning サーバーをスタンドアロンでインストール](media/2017setup-features-page-mlsvr-rpy.png "の Machine Learning Server のスタンドアロン インストールを開始")
    
    その他のオプションはすべて無視します。 
    
    > [!NOTE]
    > インストールしないように、**共有機能**コンピューターで既に Machine Learning サービスが SQL Server データベース内の分析用にインストールされたかどうか。 これには、重複するライブラリが作成されます。
    > 
    > SQL Server で実行される R または Python スクリプトは、その他のデータベース エンジン サービスで使用されるメモリの競合にならないように SQL Server で管理されて、一方はスタンドアロンの machine learning サーバーこのような制約を持たないまた、他のデータベース操作に干渉することができます. 最後に、操作運用のよく使用されている RDP セッション経由でリモート アクセスは、通常データベース管理者によってブロックされます。
    > 
    > これらの理由から、SQL Server の Machine Learning のサービスから別のコンピューターには、Machine Learning Server (スタンドアロン) をインストールすることを一般にお勧めします。

5.  ダウンロードし、機械学習のコンポーネントをインストールするためのライセンス条項に同意します。 両方の言語をインストールする場合は別のライセンス契約は Microsoft R および Python の必要です。
    
     ![Python の使用許諾契約書](media/2017setup-python-license.png "Python 使用許諾契約書")
    
    これらのコンポーネントと、必要な前提条件のインストール時間がかかる可能性があります。 **[同意する]** ボタンが使用できない状態になっている場合は、**[次へ]** をクリックします。

6.  **[インストールの準備完了]** ページで、選択内容を確認し、**[インストール]** をクリックします。

自動またはオフラインのインストールの詳細については、次を参照してください。[コマンドラインからの Microsoft R Server のインストール](../../advanced-analytics/r/install-microsoft-r-server-from-the-command-line.md)です。

##  <a name="bkmk_installRServer"></a> Microsoft R Server (スタンドアロン) のインストール

この機能は、エンタープライズ ライセンスまたは対応するものが必要です。 **SQL Server 2016**です。

以前のバージョンの Revolution Analytics ツールまたはパッケージをインストールした場合は、最初にアンインストールする必要があります。 参照してください[Microsoft R Server の以前のバージョンからアップグレード](#bkmk_Uninstall)です。

1. SQL Server 2016 セットアップを実行します。 Service Pack 1 以降をインストールすることをお勧めします。

2. **インストール** タブで、をクリックして**R Server (スタンドアロン) の新規インストール**です。
    
     ![R Server のスタンドアロンのセットアップを開始](media/2016-setup-installation-rsvr.png "R Server のスタンドアロンのセットアップを開始")
    
3.  **[機能の選択]** ページで、次のオプションが既に選択されています。
    
    **R Server (スタンドアロン)**  
    
    ![機能の選択 R Server のスタンドアロンの](media/2016setup-rserver-features.png "機能の R Server のスタンドアロンの選択")
    
    その他のすべてのオプションは無視できます。 
    
    > [!NOTE]
    > インストールしないように、**共有機能**SQL Server データベース内の分析の R サービスが既にインストールされているコンピューターでセットアップを実行している場合。 これには、重複するライブラリが作成されます。
    > 
    > SQL Server で実行されている R スクリプトは、その他のデータベース エンジン サービスで使用されるメモリの競合にならないように SQL Server で管理されて、一方、スタンドアロン R Server はこのような制約がないので、他のデータベース操作に干渉することができます。
    > 
    > 一般に、SQL Server の Machine Learning のサービスから別のコンピューターには、Machine Learning Server (スタンドアロン) をインストールすることをお勧めします。

4.  Microsoft R Open のダウンロードとインストールに関するライセンス条項に同意します。 **[同意する]** ボタンが使用できない状態になっている場合は、**[次へ]** をクリックします。
    
    これらのコンポーネントと、必要な前提条件のインストール時間がかかる可能性があります。
    
5.  **[インストールの準備完了]** ページで、選択内容を確認し、**[インストール]** をクリックします。

## <a name="bkmk_upgrade"></a> R Server の既存のインスタンスをアップグレードします。

Microsoft R Server (スタンドアロン) の以前のバージョンをインストールする場合は、新しいバージョンの R コンポーネントを使用するインスタンスをアップグレードできます。 アップグレードでは、最新ソフトウェア ライフ サイクルのサポート ポリシーを使用してサポート ポリシーも変更されます。 これにより、SQL Server リリースよりも別のスケジュールでより多くの場合、更新するインスタンス。

1. ここに挙げた場所から別の Windows ベースのインストーラーをダウンロードします。 

    + [機械学習の windows Server をインストールします。](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install)
    + [R Server 9.1 を Windows をインストールします。](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows)

2. インストーラーを実行し、指示に従います。 インストールする機能を選択する ページで、アップグレードする R Server の各インスタンスを選択します。

## <a name ="bkmk_tips"></a> インストールのヒントとフォロー アップ

このセクションでは、セットアップに関連する追加の情報を提供します。

### <a name="which-version-should-i-install"></a>どちらのバージョンをインストールする必要がありますか。

+ **Microsoft R Server**が最初に SQL Server 2016 の一部として提供され、R 言語をサポートします。 Microsoft R Server の最新バージョンでは、9.0.1 はでした。

+ **Microsoft Machine Learning Server**が SQL Server 2017 と共にリリースされた機能の多くの更新、最新のバージョンは、Python のサポートを含むです。 SQL Server 2017 累積的な更新プログラム 1 がリリースされているバージョン 9.2.1.24 の Machine Learning Server が含まれます。 この更新プログラムは、する場合は、最新の Python Api お勧めします。

+ **インプレース アップグレード**: セットアップには、SQL Server ライセンスが必要です。 と SQL Server のリリース パターンとアップグレードが通常に揃えて配置します。 これにより、開発ツールが SQL Server コンピューティング コンテキストで実行されているバージョンと同期します。 ただし、別の Windows ベースのインストーラーを使用するより頻繁に更新]、[最新のソフトウェア ライフ サイクルのサポート ポリシーを取得します。 また、SQL Server 2016 または SQL Server 2017 のインスタンスをアップグレードするのにこのインストーラーを使用することができます。

### <a name="default-installation-folders"></a>既定のインストール フォルダー

R Server をインストールするときにまたは Machine Learning サーバーは SQL Server セットアップを使用して、R ライブラリは、セットアップを使用して SQL Server のバージョンに関連付けられたフォルダーにインストールされます。 このフォルダーには、また、サンプル データ、R 基本パッケージのドキュメントおよびドキュメントの R ツールとランタイムを検索するされます。

ただし、別の Windows インストーラーを使用してインストールする場合、または別の Windows インストーラーを使用してアップグレードする場合は、R ライブラリは、別のフォルダーにインストールされます。

だけリファレンスについては、R Services (In-database) または Machine Learning Services (In-database)、SQL Server のインスタンスがインストールし、そのインスタンスが、同じコンピューターで、R ライブラリとツールは既定でインストール別のフォルダーにします。

次の表は、各インストール パスを一覧表示します。

|バージョン| インストール方法 | 既定のフォルダー|
|----|----|----|
|R Server (スタンドアロン) |SQL Server 2016 セットアップ ウィザード|`C:\Program Files\Microsoft SQL Server\130\R_SERVER`|
|R Server (スタンドアロン) |Windows スタンドアロン インストーラー|`C:\Program Files\Microsoft\R Server\R_SERVER`|
|Machine Learning Server (スタンドアロン) |  R 言語のオプションを使用して、SQL Server 2017 セットアップ ウィザード |`C:\Program Files\Microsoft SQL Server\140\R_SERVER`|
|Machine Learning Server (スタンドアロン) |  Python 言語オプションと、SQL Server 2017 セットアップ ウィザード |`C:\Program Files\Microsoft SQL Server\140\PYTHON_SERVER`|
|Machine Learning Server (スタンドアロン) |  Windows スタンドアロン インストーラー |`C:\Program Files\Microsoft\R Server\R_SERVER`|
|R Services (データベース内) |SQL Server 2016 セットアップ ウィザード|`C:\Program Files\Microsoft SQL Server\MSSQL13.<instance_name>\R_SERVICES`|
|Machine Learning Services (データベース内) |R 言語のオプションを使用して、SQL Server 2017 セットアップ ウィザード|`C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\R_SERVICES`  |
|Machine Learning Services (データベース内) |Python 言語オプションと、SQL Server 2017 セットアップ ウィザード| `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\PYTHON_SERVICES` |
### <a name="development-tools"></a>開発ツール

開発 IDE はセットアップの一部としてインストールされていません。 その他のツールは必要ありませんに R または Python の分布を使用して指定するようにすべての標準的なツールが含まれます。

新しいリリースを試してみることをお勧め[!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)]です。 Visual Studio では、R と、Python と両方ともデータベース開発ツール、SQL Server との接続および BI ツールをサポートします。 ただし、RStudio を含む、任意の希望する開発環境を使用することができます。

## <a name="troubleshooting"></a>トラブルシューティング

このセクションでは、Machine Learning サーバーまたは R サーバーをインストールする場合の注意すべきいくつかの一般的な問題を一覧表示します。

### <a name="incompatible-version-of-r-client-and-r-server"></a>R Client および R Server の互換性のないバージョン

Microsoft R クライアントをインストール、使用して、リモート SQL Server のコンピューティング コンテキストで R を実行する場合は、次のようなエラーが発生した可能性があります。

*Microsoft R Server 8.0.3 のバージョンの互換性がないコンピューターに 9.0.0 のバージョンの Microsoft R クライアントを実行しています。互換性のあるバージョンをダウンロードしてインストールしてください。*

SQL Server 2016 が必要な SQL Server R Services で実行されていた R のバージョンが Microsoft R クライアントでのライブラリと同じであること。 以降のバージョンで、その要件が削除されました。 ただし、常に、機械学習のコンポーネントの最新バージョンを取得してインストールするすべてのサービス パックお勧めします。 

Microsoft R Server の以前のバージョンをした Microsoft R クライアント 9.0.0 との互換性を確保する必要がある場合は、この説明されている更新プログラムをインストール[サポートの記事](https://support.microsoft.com/kb/3210262)です。

### <a name="installing-microsoft-r-server-on-an-instance-of-sql-server-installed-on-windows-core"></a>Windows Core にインストールされた SQL Server のインスタンスへの Microsoft R Server のインストール

RTM バージョンの SQL Server 2016 でが既知の問題 Microsoft R Server を Windows Server Core エディションでインスタンスに追加するときにします。 この問題は修正されています。

この問題が発生した場合は、修正プログラムを適用することができます[プログラム KB3164398](https://support.microsoft.com/kb/3164398)を Windows Server Core 上の既存のインスタンスに R の機能を追加します。   詳細については、 [「Can't install Microsoft R Server Standalone on a Windows Server Core operating system」](https://support.microsoft.com/kb/3168691)(Windows Server Core オペレーティング システムに Microsoft R Server (スタンドアロン) をインストールすることはできません) を参照してください。

###  <a name="bkmk_Uninstall"></a> Microsoft R Server の以前のバージョンからアップグレードします。

Microsoft R Server のプレリリース版がインストールされている場合は、それをアンインストールしてから新しいバージョンにアップグレードする必要があります。

**R Server (スタンドアロン) をアンインストールするには**

1.  **[コントロール パネル]** を開き、**[プログラムの追加と削除]** をクリックし、 `Microsoft SQL Server 2016 <version number>`を選択します。

2.  コンポーネントに対する **[追加]**、**[修復]**、または **[削除]** オプションを含むダイアログ ボックスが表示されたら、**[削除]** を選択します。
  
3.  **[機能の選択]** ページの **[共有機能]** で **[R Server (スタンドアロン)]** を選択します。 **[次へ]** をクリックし、**[完了]** をクリックして、選択したコンポーネントのみをアンインストールします。

### <a name="installation-fails-with-error-only-one-revolution-enterprise-product-can-be-installed-at-a-time"></a>インストールに失敗し "Revolution Enterprise 製品は一度に 1 つしかインストールできません" というエラーが表示される

このエラーは、以前の Revolution Analytics 製品またはプレリリース版の SQL Server R Services がインストールされている場合に発生する可能性があります。 以前のバージョンが存在する場合は、そのアンインストールを行ってから、Microsoft R Server の新しいバージョンをインストールしてください。 他のバージョンの Revolution Enterprise ツールとのサイド バイ サイド インストールはサポートされていません。

ただし、サイド バイ サイド インストールは、R Server (スタンドアロン) を [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] または SQL Server 2016 と共に使用する場合はサポートされます。

### <a name="unable-to-uninstall-older-components"></a>以前のコンポーネントをアンインストールできない

以前のバージョンの削除時に問題が発生する場合は、レジストリを編集して関連するキーを削除することが必要な場合があります。

> [!IMPORTANT]
> この問題は、プレリリース版の Microsoft R Server または CTP バージョンの SQL Server 2016 R Services がインストールされている場合にのみ発生します。
  
1. Windows レジストリを開き、 `HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall`キーを見つけます。
2. 次のエントリのいずれかが存在し、キーに値 `sEstimatedSize2`のみが含まれる場合は、該当するエントリを削除します。
  
    -   E0B2C29E-B8FC-490B-A043-2CAE75634972        (8.0.2 の場合)
  
    -   46695879-954E-4072-9D32-1CC84D4158F4        (8.0.1 の場合)
  
    -   2DF16DF8-A2DB-4EC6-808B-CB5A302DA91B        (8.0.0 の場合)
  
    -   5A2A1571-B8CD-4AAF-9303-8DF463DABE5A        (7.5.0 の場合)
  
## <a name="see-also"></a>参照

[Machine Learning Server (スタンドアロン)](../../advanced-analytics/r/r-server-standalone.md)
