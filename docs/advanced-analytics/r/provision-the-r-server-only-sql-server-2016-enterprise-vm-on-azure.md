---
title: "Azure での機械学習の仮想マシンをプロビジョニング |Microsoft ドキュメント"
ms.custom: 
ms.date: 10/16/2017
ms.prod: r-server
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8826df7-aa67-4768-baa9-bdc875c4a766
caps.latest.revision: 12
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 8cc1fcfdeae8742a93916dfb08c9db1215f88721
ms.openlocfilehash: 7cb9e069fc3b537f8aab9d048a152435ad0cc6ac
ms.contentlocale: ja-jp
ms.lasthandoff: 10/17/2017

---
# <a name="provision-a-virtual-machine-for-machine-learning-on-azure"></a>Azure での機械学習の仮想マシンのプロビジョニングします。

Azure 上のバーチャル マシンは、機械学習ソリューションの完全なサーバー環境をすばやく構成するための便利なオプションです。 この記事では、機械学習で R Server、マシン学習サーバー、または SQL Server を含むいくつかの仮想マシン イメージが一覧表示します。

この一覧は、包括的ながのみを検出を容易にするには、Machine Learning のサーバーまたは SQL Server マシン ラーニング Services に関連付けられているイメージの名前を提供ものではありません。

> [!TIP]
> 新しいバージョンの Azure ポータルと Azure Marketplace を使用することをお勧めします。 クラシック ポータルで Azure ギャラリーを参照するときに、一部のイメージは使用できません。

## <a name="how-to-provision-a-virtual-machine"></a>仮想マシンをプロビジョニングする方法

初めて使用する Azure Vm を使用する場合は、ポータルを使用して、仮想マシンの構成の詳細については、次の記事を参照してくださいをお勧めします。

+ [Virtual Machines - 作業の開始](https://azure.microsoft.com/documentation/learning-paths/virtual-machines/)
+ [Windows 仮想マシンの概要](https://azure.microsoft.com/documentation/articles/virtual-machines-windows-hero-tutorial/)

## <a name="find-a-machine-learning-image"></a>Machine learning のイメージが見つかりません

1. クリックして、Azure ポータル (portal.azure.com) から**仮想マシン**、 をクリックして**新規**です。

2. 名前でリソースをフィルター処理に使用することができます ページの上部にある検索ボックスを見つけます。 

3. "R Server"(または"ML Server") を入力、**フィルター**関連リソースの一覧を表示するコントロール。 をクリックして**Marketplace での検索**を仮想マシンを表示します。

    > [!TIP]
    > 
    > フィルター コントロールの他の考えられる文字列「データ サイエンス」、"machine learning"です。
    > 
    > 使用して、`%`ワイルドカード検索する仮想マシンの名前にします。 たとえば、入力`"`% ジュリア %` or `%R %' です。

4. R Server for Windows を取得するには、次のように選択します。 **R サーバーのみ SQL Server 2016 Enterprise**です。
  
    [R Server](https://msdn.microsoft.com/microsoft-r/rserver-whats-new)として SQL Server Enterprise Edition の機能では、ライセンスしますが、version 9.1 は、スタンドアロン サーバーとしてインストールしは最新のライフ サイクルのサポート ポリシー下にあるサービスが実行します。

    > [!NOTE] 
    > 
    > これは、分類、検索、SQL Server 2017 と、9.2.1 を含む新しい仮想マシンのリリースのリリースの Machine Learning Server です。
    > それまでは、SQL Server インストール センターを使用して、アップグレード オプション を選択して、このバーチャル マシンにインストールされている SQL Server のバージョンを更新できます。 詳細については、次を参照してください。[インストール ウィザードを使用して SQL Server のアップグレード](https://docs.microsoft.com/sql/database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup)です。

5. 仮想マシンが作成されてが実行されているをクリックして、**接続**接続を開くし、新しいコンピューターにログインするにはボタン。

5. 接続した後は、追加の R パッケージ、または優先の開発ツールをインストールできます。

### <a name="install-additional-r-tools"></a>追加の R ツールをインストールします。

Microsoft R Server の既定では、R の基本インストールでインストールされるすべての R ツール (RTerm、RGui など) が含まれています。 RGui へのショートカットはデスクトップにも追加されました。

ただし、RStudio、R Tools for Visual Studio (RTVS) または Microsoft R クライアントなど、追加の R ツールをインストールしておくこともできます。 ダウンロード場所と手順については、次のリンクを参照してください。

+ [R Tools for Visual Studio](https://docs.microsoft.com/visualstudio/rtvs/installation)
+ [Microsoft R Client](https://msdn.microsoft.com/microsoft-r/install-r-client-windows)
+ [RStudio for Windows](https://www.rstudio.com/products/rstudio/download/)

インストールが完了したら、すべての R 開発ツールが Microsoft R Server ライブラリを使用するように、既定の R ランタイムの場所を必ず変更します。

### <a name="configure-r-server-to-support-web-services"></a>Web サービスをサポートするために R サーバーを構成します。

追加の構成が必要なは、web サービスの展開、リモートの実行を使用するか、組織内の配置サーバーとして R Server を活用します。 手順については、次を参照してください。[分析を操作運用する R サーバーを構成する](https://docs.microsoft.com/machine-learning-server/install/operationalize-r-server-one-box-config)です。

> [!NOTE]
> RevoScaleR または MicrosoftML などのパッケージを使用する場合は、追加の構成は必要ありません。

## <a name="other-virtual-machines"></a>他の仮想マシン

次のイメージは、Azure Marketplace から使用可能な完全に構成された機械学習ツールが SQL Server が必ずしも含まれていません。

### <a name="data-science-virtual-machine"></a>データ サイエンス仮想マシン

Microsoft R Server だけでなく Python (Anaconda ディストリビューション)、Jupyter ノートブック サーバー、Visual Studio Community エディション、Power BI Desktop で、Azure SDK、および SQL Server Express edition では、このイメージが事前に構成します。

Windows のバージョンが Windows Server 2012 で実行し、モデリングと分析を含むさまざまな特別なツールが含まれています[CNTK](https://www.microsoft.com/cognitive-toolkit/)、 [mxNet](https://mxnet.incubator.apache.org/)などの一般的な R パッケージおよび**xgboost**.

Linux の各エディションでは、Ubuntu、Centos、および Centos CSP に提供され、データ科学技術や開発作業の多くの一般的なツールが含まれています。

詳細については、次を参照してください。 [Linux と Windows Azure データ サイエンス仮想マシンへの概要](https://docs.microsoft.com/azure/machine-learning/data-science-virtual-machine/provision-vm)です。

このイメージはされましたが最近追加されました。 

+ ジュリアは、将来の拡張性の高い、強力なデータ サイエンス言語のサポート 
+ JupyterHub トレーニング クラスを実行し、同じサーバーの共有が別々 のノートブックとディレクトリを使用するすべての受講者を対象にするときに便利なオプションがします。

サポートされているツールおよびマシン ラーニング フレームワークの詳細については、次を参照してください[、データ サイエンス仮想マシンについて理解する。](https://docs.microsoft.com/azure/machine-learning/data-science-virtual-machine/dsvm-tools-overview)

### <a name="r-server-virtual-machines"></a>R Server の仮想マシン

加え、 **R サーバーのみ SQL Server 2016 Enterprise**イメージを R サーバーを含むスタンドアロン バーチャル マシンを取得することができます。 イメージは、Linux CentOS バージョン 7.2、Linux Red Hat バージョン 7.2、および Ubuntu バージョン 16.04 で利用できます。

詳細については、次を参照してください[クラウド内の Machine Learning サーバー。](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-in-the-cloud)

 > [!NOTE]
 > これらの仮想マシンは、Azure Marketplace でこれまで入手可能であった **RRE for Windows Virtual Machine** の後継です。

### <a name="sql-server-virtual-machines"></a>SQL Server 仮想マシン

SQL Server マシンが Azure での学習を使用するための 2 つのオプションがあります。

+ プレインストールされている SQL Server R Services を含むバーチャル マシンのイメージのいずれかを取得します。
+ Azure の仮想マシンを作成し、独自のライセンス キーを使用して SQL Server の Enterprise または Developer edition をインストールします。 
  
    その後、セットアップを実行して追加し、前述のように、機械学習サービスを有効にする: [Azure の仮想マシンで SQL Server R Services をインストールする](../r/installing-sql-server-r-services-on-an-azure-virtual-machine.md)です。
+ 機械学習のサポートおよびプレビューに新しい R サービスの機能を現在使用できるサービス層を使用して Azure SQL データベースを作成します。 詳細については、次を参照してください。 [Azure SQL DB](../r/using-r-in-azure-sql-database.md)です。

> [!NOTE]
> 現時点を SQL Server の Machine Learning のサービスが SQL Server 2017 の Linux 仮想マシンでサポートされていません。 ただし、T-SQL で予測関数を使用してトレーニング済みモデルのスコア付けを行うことができます。 詳細については、次を参照してください。 [SQl Server のネイティブ スコアリング](../sql-native-scoring.md)です。 

### <a name="virtual-machines-for-deep-learning"></a>深層学習用の仮想マシン 

以前は、Microsoft は、、データ サイエンス仮想マシンに既存データ サイエンス仮想マシンを追加することがある、詳細な学習 Toolkit 提供されます。 このツールキットは深層学習の一般的なツールが含まれています、詳細な学習の仮想マシンによって置き換えられるようになりました。

+ 深層学習フレームワークの GPU エディションなどの Microsoft 認知 Toolkit TensorFlow、Keras、Caffe
+ GPU の組み込みドライバー
+ イメージとテキスト処理のためのツールのコレクション
+ Enterprise 開発ツール Microsoft R Server Developer Edition、Anaconda Python などの Python と R Jupyter ノートブック
+ Python、R、SQL Server、および多くの開発用ツール
+ イメージとテキストについてのエンド ツー エンドのサンプル

ディープ学習の仮想マシンでは、Windows 2016 または Ubuntu Linux プラットフォームのいずれかがあります。 詳細については、次を参照してください。[深層学習や AI フレームワーク](https://docs.microsoft.com/azure/machine-learning/data-science-virtual-machine/dsvm-deep-learning-ai-frameworks)です。

> [!IMPORTANT]
> 
> この仮想マシンを展開するには、制限付きの Azure リージョンで使用可能な Azure GPU NC シリーズの仮想マシンのイメージが必要です。 可用性の詳細については、次を参照してください。[地域で利用可能な製品](https://azure.microsoft.com/en-us/regions/services/)です。 仮想マシンをプロビジョニングする際に必ず使用して**HDD**ディスクの種類としていない**SSD**です。

## <a name="frequently-asked-questions"></a>よく寄せられる質問

このセクションには、機械学習の Microsoft からの仮想マシンに関する一般的な質問が含まれています。

### <a name="can-i-install-a-virtual-machine-with-sql-server-2017"></a>SQL Server 2017 で仮想マシンをインストールできますか。

Machine Learning のサービスを含む SQL Server 2017 年 1 Enterprise Edition 用の Windows ベースの仮想マシンは、間もなく提供されます。 これらのブログ サイトでお知らせを確認します。

+ [Cortana インテリジェンス機械学習と](https://blogs.technet.microsoft.com/machinelearning/)
+ [Data Platform Insider](https://blogs.technet.microsoft.com/dataplatforminsider/)

### <a name="how-do-i-access-data-in-an-azure-storage-account"></a>Azure ストレージ アカウントのデータにアクセスするにはどうすればよいですか。

Azure ストレージ アカウントからデータを使用する必要がある場合、データのアクセスまたは移動にはいくつかの選択肢があります。

+ ストレージ アカウントのデータを [AzCopy](https://azure.microsoft.com/documentation/articles/storage-use-azcopy/#copy-files-in-azure-file-storage-with-azcopy-preview-version-only)などのユーティリティを使用してローカル ファイル システムにコピーします。 

+ ファイルをストレージ アカウントのファイル共有に追加し、そのファイル共有を VM のネットワーク ドライブとしてマウントします。  詳細については、「 [Windows で Azure File Storage を使用する](https://azure.microsoft.com/documentation/articles/storage-dotnet-how-to-use-files/)」を参照してください。 

### <a name="how-do-i-use-data-from-azure-data-lake-storage-adls"></a>Azure Data Lake ストレージ (ADLS) からデータを使用するにはどうすればよいですか。

WebHDFS を使用すると同じ方法を HDFS ファイル システム、ストレージ アカウントを参照する場合は、RevoScaleR、ADLS ストレージからデータを読み取ることができます。  詳細については、この記事を参照してください: [Azure Data Lake Store のファイル システム操作を実行するを使用して R](https://blogs.msdn.microsoft.com/microsoftrservertigerteam/2017/03/14/using-r-to-perform-filesystem-operations-on-azure-data-lake-store/)です。



