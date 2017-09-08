---
title: "Azure で R Server Only SQL Server 2016 Enterprise VM を準備する | Microsoft Docs"
ms.custom: 
ms.date: 06/05/2017
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
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a3bfca0753984f09220d8ca4e4f6933c949daf2b
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="advanced-analytics-virtual-machines-on-azure"></a>Azure で仮想マシンを高度な分析

Azure 上のバーチャル マシンは、機械学習ソリューションの完全なサーバー環境をすばやく構成するための便利なオプションです。 このトピックでは、R サーバー、機械学習で SQL Server または Microsoft の他のデータ サイエンス ツールを含むいくつかの仮想マシン イメージが一覧表示します。

> [!TIP]
> 新しいバージョンの Azure ポータルと Azure Marketplace を使用することをお勧めします。 クラシック ポータルで Azure ギャラリーを参照するときに、一部のイメージは使用できません。

Azure Marketplace には、データ サイエンスをサポートしている複数の仮想マシンが含まれています。 この一覧は、包括的ながのみ検出を容易にするために、サービスの学習 Microsoft R Server または SQL Server のいずれかのマシンが含まれるイメージの名前を提供ものではありません。

## <a name="how-to-provision-a-vm"></a>VM をプロビジョニングする方法

初めて使用する Azure Vm を使用する場合は、ポータルを使用して、仮想マシンの構成の詳細については、次の記事を参照してくださいをお勧めします。

+ [Virtual Machines - 作業の開始](https://azure.microsoft.com/documentation/learning-paths/virtual-machines/)
+ [Windows 仮想マシンの概要](https://azure.microsoft.com/en-us/documentation/articles/virtual-machines-windows-hero-tutorial/)

### <a name="find-an-image"></a>イメージを検索します。

1. Azure のダッシュ ボードから をクリックして**Marketplace**です。

    - をクリックして**インテリジェンスや分析**または**データベース**で"R"を入力し、**フィルター** R Server 仮想マシンの一覧を表示するコントロール。
    - その他の考えられる文字列、**フィルター**コントロールは*データ サイエンス*と*機械学習*
    - VM 名などを含む対象の文字列を検索する検索で % ワイルドカードを使用して*R*または*ジュリア*です。

2. R Server for Windows を取得するには、次のように選択します。 **R サーバーのみ SQL Server 2016 Enterprise**です。
  
    [R Server](https://msdn.microsoft.com/microsoft-r/rserver-whats-new) 9.1 のバージョンは、SQL Server Enterprise Edition の機能としてライセンス供与します。 スタンドアロン サーバーとしてインストールされ、最新のライフ サイクルのサポート ポリシー下にあるサービスを提供します。

3. VM を作成して実行したら、 **[接続]** ボタンをクリックして接続を開き、新しいコンピューターにログインします。

4. 接続した後は、追加の R ツールや開発ツールをインストールする必要があります。

### <a name="install-additional-r-tools"></a>追加の R ツールをインストールします。

Microsoft R Server の既定では、R の基本インストールでインストールされるすべての R ツール (RTerm、RGui など) が含まれています。 R をすぐに使用し始める場合、RGui のショートカットはデスクトップに追加されています。

ただし、RStudio、Visual Studio (RTVS) または Microsoft R クライアントの R ツールなど、追加の R ツールをインストールしておくこともできます。 ダウンロード場所と手順については、次のリンクを参照してください。
+ [R Tools for Visual Studio](https://docs.microsoft.com/visualstudio/rtvs/installation)
+ [Microsoft R Client](https://msdn.microsoft.com/microsoft-r/install-r-client-windows)
+ [RStudio for Windows](https://www.rstudio.com/products/rstudio/download/)

インストールが完了したら、すべての R 開発ツールが Microsoft R Server ライブラリを使用するように、既定の R ランタイムの場所を必ず変更します。

### <a name="configure-server-for-web-services"></a>Web サービスのサーバーを構成します。

仮想マシンに R Server が含まれている場合は、Web サービスの展開、リモート実行、または組織内の配置サーバーとしての R Server の活用を行うには、追加構成が必要です。 手順については、[R Server を運用可能にするための構成](https://msdn.microsoft.com/microsoft-r/operationalize/configuration-initial)に関するページを参照してください。

> [!NOTE]
> RevoScaleR または MicrosoftML などのパッケージを使用する場合は、追加の構成は必要ありません。

## <a name="r-server-images"></a>R Server のイメージ

### <a name="microsoft-data-science-virtual-machine"></a>Microsoft データ サイエンス仮想マシン

Microsoft R Server だけでなく Python (Anaconda ディストリビューション)、Jupyter ノートブック サーバー、Visual Studio Community エディション、Power BI Desktop で、Azure SDK、および SQL Server Express edition で構成されているものです。

Windows のバージョンでは、Windows Server 2012 で実行し、モデリングと分析、CNTK と mxnet、xgboost、Vowpal Wabbit などの一般的な R パッケージを含むさまざまな特別なツールが含まれています。

### <a name="linux-data-science-virtual-machine"></a>Linux データ サイエンス仮想マシン

データ サイエンスと開発アクティビティに対して、Python や R ジュリア Microsoft R Open、Microsoft R Server Developer Edition、Anaconda Python、および Jupyter ノートブックを含む一般的なツールも含まれています。

この VM イメージが最近更新された JupyterHub、ローカル OS アカウント認証、および Github アカウントの認証など、さまざまな認証方法を複数のユーザーによる使用を有効にするオープン ソース ソフトウェアが含まれます。 JupyterHub は、トレーニング クラスを実行し、個別のノートブックやディレクトリを使用してでは、同じサーバーを共有するすべての受講者をする場合に特に便利なオプションです。

Ubuntu、Centos、および Centos CSP のイメージが提供されます。

### <a name="r-server-only-sql-server-2016-enterprise"></a>R Server のみ SQL Server 2016 Enterprise

この仮想マシンには、スタンドアロン インストーラーが含まれています。 [R Server 9.1 です。](https://msdn.microsoft.com/microsoft-r/rserver-whats-new) 新しいソフトウェアの最新のライフ サイクルのライセンス モデルをサポートします。

 R Server も Linux CentOS バージョン 7.2、Linux RedHat バージョン 7.2、および Ubuntu バージョン 16.04 用のイメージで使用できます。

 > [!NOTE]
 > これらの仮想マシンは、Azure Marketplace でこれまで入手可能であった **RRE for Windows Virtual Machine** の後継です。

## <a name="sql-server-images"></a>SQL Server イメージ

R Services (In-database) または Machine Learning のサービスを使用するには、SQL Server の Enterprise または Developer edition、仮想マシンのいずれかをインストールし、」の説明に従って、機械学習サービスを追加: [SQL Server R Services をインストールします。Azure の仮想マシン](../../advanced-analytics/r-services/installing-sql-server-r-services-on-an-azure-virtual-machine.md)です。

> [!NOTE]
> 現時点では、SQL Server の 2017 のまたは Azure SQL データベースで machine learning のサービスは、Linux 仮想マシンでサポートされません。 Windows 用 SQL Server 2016 SP1 または SQL Server 2017 のいずれかを使用する必要があります。

データ サイエンス仮想マシンには、SQL Server 2016 が既に有効になっている、R services の機能にも含まれます。


## <a name="other-vms"></a>他の Vm

### <a name="deep-learning-toolkit-for-the-data-science-virtual-machine"></a>ツールキットの学習データ サイエンス仮想マシンの詳細

このバーチャル マシンは、同じコンピューター、データ サイエンス仮想マシンで使用できるツールを習得が mxnet、CNTK、TensorFlow、および Keras の GPU のバージョンとします。 このイメージは、Azure の GPU N シリーズ インスタンスでのみ使用できます。 

深層学習 toolkit には、学習 CIFAR 10 データベース上の画像認識や MNIST データベースで文字認識のサンプルを含む、GPU を使用するソリューションの詳細なサンプルのセットも提供します。 GPU のインスタンスは、米国中南部、米国東部、西ヨーロッパ、東南アジアで現在使用できます。

> [!IMPORTANT]
> GPU インスタンスは、現時点では米国中南部でのみ使用できます。


## <a name="frequently-asked-questions"></a>よく寄せられる質問

### <a name="can-i-install-a-virtual-machine-with-sql-server-2017"></a>SQL Server 2017 で仮想マシンをインストールできますか。

イメージが使用可能なが含まれている SQL Server 2017 CTP 2.0 には Linux 環境の現在これらの環境が Machine Learning サービス サポートされません。 

パブリックのリリース後に使用可能になります Machine Learning のサービスを含む SQL Server 2017 年 1 Enterprise Edition 用の Windows ベースの仮想マシン。 

代わりに、SQL Server 2016 のイメージを使用して前述のように、R のインスタンスをアップグレードします。 [SqlBindR を使用してインスタンスをアップグレード](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)です。 

または、仮想マシンを作成しの CTP 2.0 のプレビューをダウンロードして[SQL Server 2017](https://www.microsoft.com/sql-server/sql-server-2017)です。

### <a name="how-do-i-access-data-in-an-azure-storage-account"></a>Azure ストレージ アカウントのデータにアクセスするにはどうすればよいですか。

Azure ストレージ アカウントからデータを使用する必要がある場合、データのアクセスまたは移動にはいくつかの選択肢があります。

+ ストレージ アカウントのデータを [AzCopy](https://azure.microsoft.com/documentation/articles/storage-use-azcopy/#copy-files-in-azure-file-storage-with-azcopy-preview-version-only)などのユーティリティを使用してローカル ファイル システムにコピーします。 

+ ファイルをストレージ アカウントのファイル共有に追加し、そのファイル共有を VM のネットワーク ドライブとしてマウントします。  詳細については、「 [Windows で Azure File Storage を使用する](https://azure.microsoft.com/documentation/articles/storage-dotnet-how-to-use-files/)」を参照してください。 

### <a name="how-do-i-use-data-from-azure-data-lake-storage-adls"></a>Azure Data Lake ストレージ (ADLS) からデータを使用するにはどうすればよいですか。

WebHDFS を使用すると同じ方法を HDFS ファイル システム、ストレージ アカウントを参照する場合は、RevoScaleR、ADLS ストレージからデータを読み取ることができます。  詳細については、この記事を参照してください: [Azure Data Lake Store のファイル システム操作を実行するを使用して R](https://blogs.msdn.microsoft.com/microsoftrservertigerteam/2017/03/14/using-r-to-perform-filesystem-operations-on-azure-data-lake-store/)です。

## <a name="see-also"></a>参照

[SQL Server R サービス](https://msdn.microsoft.com/library/mt604845.aspx)


