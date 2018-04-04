---
title: Azure での機械学習の仮想マシンをプロビジョニング |Microsoft ドキュメント
ms.custom: ''
ms.date: 10/31/2017
ms.reviewer: ''
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c8826df7-aa67-4768-baa9-bdc875c4a766
caps.latest.revision: ''
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.openlocfilehash: 62e1c347a3c5ee110e6865cd8c13ade76ba62b80
ms.sourcegitcommit: 270de8a0260fa3c0ecc37f91eec4a5aee9b9834a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2018
---
# <a name="provision-a-virtual-machine-for-machine-learning-on-azure"></a>Azure での機械学習の仮想マシンのプロビジョニングします。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Azure 上のバーチャル マシンは、機械学習ソリューションの完全なサーバー環境をすばやく構成するための便利なオプションです。

この記事では、いくつかの関連するバーチャル マシンと同様に機械学習、SQL Server を含むバーチャル マシンのイメージが一覧表示します。

この記事では、変更または仮想マシンで既存の SQL Server インスタンスのアップグレードに関するよく寄せられる質問に対する回答も提供します。

+ [現在の仮想マシンの一覧](#bkmk_list)

## <a name="provision-a-virtual-machine-with-sql-server-and-machine-learning"></a>SQL Server での仮想マシンをプロビジョニングし、機械学習

初めて使用する Azure Vm を使用する場合は、ポータルを使用して、仮想マシンの構成の詳細については、次の記事を参照してくださいをお勧めします。

+ [Virtual Machines - 作業の開始](https://azure.microsoft.com/documentation/learning-paths/virtual-machines/)
+ [Windows 仮想マシンの概要](https://azure.microsoft.com/documentation/articles/virtual-machines-windows-hero-tutorial/)

新しいバージョンの Azure ポータルまたは Azure Marketplace を使用することを確認します。 クラシック ポータルで Azure ギャラリーを参照するときに、一部のイメージは使用できません。

**仮想マシンを作成します。**

1. Azure ポータルを開く: [portal.azure.com](https:portal.azure.com)です。

2. をクリックして**仮想マシン**、 をクリックしてまたは**新規**です。

3. **[追加]**をクリックします。

4. ページの上部にある [検索] ボックスには、関連する仮想マシンの一覧を表示するには、"Machine Learning Server"または"SQL Server"を入力します。

5. 、要件を確認し、をクリックして**作成**作業を開始します。

6. 仮想マシンが作成されてが実行されているをクリックして、**接続**接続を開くし、新しいコンピューターにログインするにはボタン。

5. 接続したら、追加の R または Python のパッケージをインストールしたり、希望する開発ツールを構成できます。

### <a name="connect-to-the-virtual-machine"></a>仮想マシンに接続します。

クライアントが仮想マシンで実行されている SQL Server に接続する方法は、クライアントとネットワークの構成の場所によって異なります。

詳細については、次を参照してください。 [Azure で SQL Server 仮想マシンへの接続](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-connect)です。

## <a name="frequently-asked-questions"></a>よく寄せられる質問

このセクションには、機械学習の Microsoft からの仮想マシンに関する一般的な質問が含まれています。

### <a name="can-i-install-a-virtual-machine-with-sql-server-2017"></a>SQL Server 2017 で仮想マシンをインストールできますか。

Machine Learning のサービスを含む SQL Server 2017 年 1 Enterprise Edition 用の Windows ベースの仮想マシンは、2017 年 11 月バージョンから利用可能です。 

新しいデータ サイエンス仮想マシンに関するお知らせは、これらのブログ サイトを確認してください。

+ [Cortana インテリジェンスと機械学習](https://blogs.technet.microsoft.com/machinelearning/)
+ [Data Platform Insider](https://blogs.technet.microsoft.com/dataplatforminsider/)

### <a name="adding-sql-server-to-an-existing-virtual-machine"></a>既存のバーチャル マシンへの SQL Server の追加

仮想マシンを作成するだけでなく、学習、既存の仮想マシンに SQL Server をインストールし、機械学習機能を有効にする SQL Server コンピューターが既に含まれているイメージを使用します。 Enterprise または Developer edition、リソースの制約を回避することをお勧めします。 インストールでは、独自のライセンス キーを使用することも必要です。

セットアップを実行するときは、機械学習機能と R (Python) には、少なくとも 1 つの言語を選択することを確認します。 追加の手順は、SQL Server と通信し、仮想マシンでのネットワーク接続を有効にする machine learning サービスを有効にするために必要です。

詳細については、次を参照してください。 [Azure の仮想マシンで SQL Server R Services をインストールする](../r/installing-sql-server-r-services-on-an-azure-virtual-machine.md)です。

### <a name="using-machine-learning-in-azure-sql-database"></a>Azure SQL データベースでの機械学習の使用

現時点では、Azure SQL での R のサポートのプレビューは、継続的な開発作業の中断されています。 詳細については、次を参照してください。 [Azure SQL DB](../r/using-r-in-azure-sql-database.md)です。

### <a name="can-i-upgrade-the-sql-server-version-on-a-virtual-machine"></a>仮想マシンで SQL Server のバージョンをアップグレードできますか。

SQL Server 2016 のイメージはサポートが R、Python を使用する場合もコンポーネントを学習するもう一方のコンピューターをアップグレードする SQL Server 2017 にアップグレードすることができます。

インストールされている SQL Server のバージョンを更新するには、仮想マシンでは、SQL Server インストール センターを開き、、**アップグレード**オプション。 どの仮想マシンによって作成されると、ライセンス必要があります。

詳細については、次を参照してください。[インストール ウィザードを使用して SQL Server のアップグレード](https://docs.microsoft.com/sql/database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup)です。

### <a name="can-i-upgrade-just-the-machine-learning-components"></a>機械学習のコンポーネントだけをアップグレードできますか。

RevoScaleR、MicrosoftML、または revoscalepy 新しいアップグレードを公開する際は、機械学習と呼ばれるプロセスを使用して、SQL Server で使用されるコンポーネントをアップグレードすることができます_バインディング_です。 これ操作により、SQL Server のバージョンが変更されることはありませんが、インスタンスのサポート ポリシーは変更できます。

詳細については、次を参照してください。 [machine learning SQL Server コンポーネントがアップグレードに使用する SqlBindR](../r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)です。

### <a name="how-do-i-access-data-in-an-azure-storage-account"></a>Azure ストレージ アカウントのデータにアクセスするにはどうすればよいですか。

Azure ストレージ アカウントからデータを使用する必要がある場合、データのアクセスまたは移動にはいくつかの選択肢があります。

+ ストレージ アカウントのデータを [AzCopy](https://azure.microsoft.com/documentation/articles/storage-use-azcopy/#copy-files-in-azure-file-storage-with-azcopy-preview-version-only)などのユーティリティを使用してローカル ファイル システムにコピーします。 

+ ファイルをストレージ アカウントのファイル共有に追加し、そのファイル共有を VM のネットワーク ドライブとしてマウントします。 詳細については、「 [Windows で Azure File Storage を使用する](https://azure.microsoft.com/documentation/articles/storage-dotnet-how-to-use-files/)」を参照してください。 

### <a name="how-do-i-use-data-from-azure-data-lake-storage-adls"></a>Azure Data Lake ストレージ (ADLS) からデータを使用するにはどうすればよいですか。

RevoScaleR を使用して、HDFS の同じようにファイル システム ストレージ アカウントを参照する webHDFS を使用して、ADLS ストレージからデータを読み取ることができます。 詳細については、この記事を参照してください: [Azure Data Lake Store のファイル システム操作を実行するを使用して R](https://blogs.msdn.microsoft.com/microsoftrservertigerteam/2017/03/14/using-r-to-perform-filesystem-operations-on-azure-data-lake-store/)です。

### <a name="i-cant-find-the-rre-virtual-machine"></a>RRE 仮想マシンが見つかりません

以前で提供されていた、「RRE Windows 仮想マシンの」Azure Marketplace は、"Machine Learning Server for Windows の"イメージ置き換えられています。

Machine Learning サーバー イメージも Linux CentOS バージョン 7.2、Linux RedHat バージョン 7.2、および Ubuntu バージョン 16.04 を使用できます。

詳細については、次を参照してください[クラウド内の Machine Learning サーバー。](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-in-the-cloud)

### <a name="configuring-machine-learning-server-or-r-server-to-support-web-services"></a>Web サービスをサポートするには、Machine Learning のサーバーまたは R サーバーの構成

Machine Learning のサーバーを含む仮想マシンを使用する場合は、追加の構成が web サービスの展開、リモートの実行を使用するか、組織内の配置サーバーとして、仮想マシンを使用する必要があります。

手順については、次を参照してください。[分析を操作運用するマシン ラーニング サーバーを構成する](https://docs.microsoft.com/machine-learning-server/operationalize/configure-machine-learning-server-one-box)です。

RevoScaleR または MicrosoftML などのパッケージを使用する場合は、追加の構成は必要ありません。

## <a name="bkmk_list"></a> 仮想マシンの一覧

現時点では、次のバーチャル マシンでは、SQL Server での機械学習できます。

|名前| コメント|
|----|----|----|
| **SQL Server 2016**| ***  |
|Windows 上の SQL Server 2016 SP1 Enterprise|R Services の統合の高度な分析します。|
|Windows Server 上の BYOL SQL Server 2016 SP1 Enterprise |R Services の統合の高度な分析します。 |
|Windows Server 2016 での無料のライセンス: SQL Server 2016 SP1 Developer |R Services の統合の高度な分析します。 |
| データ サイエンス仮想マシン - Windows 2012|Microsoft R Server Developer Edition、SQL Server 2016 Developer edition、Anaconda Python 配布、ジュリア Pro developer edition、および Jupyter ノートブックを R. 用など、データ サイエンス用の一般的なツールが含まれています| 
| データ サイエンス仮想マシン - Windows 2016|データベース内 R 分析のサポートは、SQL Server 2016 Developer Edition が含まれています。|
|**SQL Server 2017**| ***   |
|SQL Server 2017 Enterprise Windows Server 2016| Python と R 言語のサポートを備えた machine Learning サービス。|
|BYOL SQL Server 2017 Enterprise Windows Server 2016|Python と R 言語のサポートを備えた machine Learning サービス。|
| Windows Server での無料の SQL Server のライセンス: SQL Server 2017 Developer|Python と R 言語のサポートを備えた machine Learning サービス。|
| **その他**| *** |
| 機械学習のサーバーのみ SQL Server 2017 Enterprise|同様に、SQL Server 2016 Enterprise イメージが Machine Learning のサーバーのスタンドアロン バージョンを含むコア ScaleR と操作運用の機能が Windows の環境を最適化します。|
| Machine Learning Server for Windows|Windows 環境用に最適化された操作運用の機能とは、Machine Learning のサーバーのスタンドアロン バージョンが含まれています。|
|データ サイエンス仮想マシン |Linux の各エディションには、R サーバーが含まれます。 SQL Server 2017 を含む Linux virtual machines では、SQL Server で R または Python コードを実行できません。 ただし、T-SQL で予測関数を使用してトレーニング済みモデルのスコア付けを行うことができます。 詳細については、次を参照してください。 [SQl Server のネイティブ スコアリング](../sql-native-scoring.md)です。|
