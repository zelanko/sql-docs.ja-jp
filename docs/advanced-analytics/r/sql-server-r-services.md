---
title: "SQL Server コンピューターのサービスの学習 |Microsoft ドキュメント"
ms.date: 12/04/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba1dea65-40ea-484a-b767-53680c954934
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Active
ms.openlocfilehash: 37362b8a3f6d8b41fe6b52f8445b9ba08ca54aa3
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2018
---
# <a name="sql-server-machine-learning-services"></a>SQL Server Machine Learning サービス
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server 2017 Machine Learning サービス (以前 SQL Server 2016 R サービス) は、開発と新しい洞察を得るためのインテリジェント アプリケーションを展開するためのプラットフォームを提供します。 機械学習を統合しているため、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データの近くで分析を行い、コストとデータの移動に関連付けられているセキュリティ上のリスクを削減できます。
  
+ SQL Server 2016 で簡単に開発し、データ サイエンス用の一般的な R 言語に基づくソリューションを配置できます。 

    機能などがあります、 [Microsoft R](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) R ソリューション、および最新のアルゴリズムで新しいスケーラビリティとパフォーマンスを提供するライブラリ[MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package)です。
+ SQL Server の 2017 で開発およびデータ サイエンス ソリューションを使用できるようにするには、R と Python の両方を使用できます。 

    [Revoscalepy](../python/what-is-revoscalepy.md) Python のライブラリには、リモート計算コンテキストと RevoScaleR でと同程度のスケーラビリティが用意されています。

SQL Server には、包括的な一連のツールとテクノロジの machine learning のワークロード用のパフォーマンスの向上、セキュリティ、および管理容易性がサポートしています。 R、または Python 便利なを使用したソリューション、使い慣れた SQL 方法とツールを展開することができます。 そのまま使用[!INCLUDE[tsql](../../includes/tsql-md.md)]モデルを構築またはビジュアルを取得する、実稼働アプリケーションから R または Python ランタイムを呼び出す。 を通じてのみ、T-SQL を使用して予測を生成するには場合は、モデルのトレーニングが既に、[ネイティブ スコアリング](../sql-native-scoring.md)です。

## <a name="machine-learning-in-sql-server-2017"></a>機械学習で SQL Server 2017

+ インストール**Machine Learning Services (In-database)**中に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で R または Python スクリプトの実行をセキュリティで保護を有効にする設定、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]コンピューター。
  
    この機能を選択すると、拡張機能は R または Python で記述されたコードの実行をサポートするために、データベース エンジンにインストールされます。 新しいサービスを作成、 [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]、外部のランタイムとの間の通信を管理して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンス。
  
+ インストール**Microsoft Machine Learning Server (スタンドアロン)**別のコンピューターを使用している場合は、計算コンテキストとして SQL Server を使用する必要はありません。 Machine Learning のサーバーには、machine learning コンポーネント、および web サービスとスケーラビリティを備えた分散 machine learning ジョブを実行する機能が含まれています。
  
+ インストール[Microsoft R クライアント](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client)SQL Server または Windows、Linux、または Hadoop 上の Machine Learning サーバーに配置できるソリューションを開発するリモート コンピューターにします。

## <a name="machine-learning-in-sql-server-2016"></a>機械学習の SQL Server 2016

+ インストール**R Services (In-database)**で R スクリプトの実行をセキュリティで保護を有効にする SQL Server 2016 のセットアップ時に、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]コンピューター。
  
    この機能を選択すると、計算コンテキストとして SQL Server を使用して R スクリプトを実行する機能や、ストアド プロシージャで R スクリプトを実行する機能を取得します。
  
+ インストール**Microsoft R Server (スタンドアロン)** SQL Server 2016 セットアップから、開発または R ソリューションを配置するために使用できる別のコンピューターに R コンポーネントをインストールします。

## <a name="how-to-get-started"></a>作業を開始する方法

SQL Server セットアップでは、2 つのオプションを提供します。

+ SQL Server と統合されて、データベース内分析機能をインストールまたは
+ SQL Server のインスタンスなしを大規模に機械学習をサポートする、マシン学習サーバー (または Microsoft R サーバー) のスタンドアロン バージョンをインストールします。

R コードを実行する必要がある場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、インストールする必要がありますを使用してストアド プロシージャか SQL Server インスタンスをコンピューティング コンテキストとして使用して、 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] 」の説明に従って、[セットアップ ガイド](../../advanced-analytics/r/set-up-sql-server-r-services-in-database.md)です。 このオプションは、最大のデータのセキュリティと SQL Server のツールとの統合を提供します。

Microsoft Machine Learning Server (スタンドアロン) は、個別のオプションを使用するために設計されています、 [Microsoft R](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference)と[Python ライブラリを関連](../python/what-is-revoscalepy.md)SQL Server が実行されていない Windows コンピューターにします。 このオプションでは、SQL Server の Enterprise Edition のライセンスが必要です。
    
ラップトップまたは開発では、使用するその他のリモート コンピューターで Machine Learning Server (スタンドアロン) をインストールしてそのコンピューターを使用して作成しのインスタンスに簡単にデプロイする機械学習ソリューションをテストすることをお勧め[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]つまりMachine Learning のサービスを実行している\(データベースで\)または別のサポートされているコンテキストを計算します。
  
使用することも、 **mrsdeploy**パッケージを発行して web サービスとして R、Python のジョブを配布する Machine Learning サーバーと共にインストールされます。

## <a name="additional-resources"></a>その他のリソース

+ [SQL Server の Machine Learning のサービスの概要](../../advanced-analytics/r/getting-started-with-sql-server-r-services.md)
 
    SQL Server で R の使用法についての一般的なシナリオについて説明します

+ [SQL Server マシン学習サービスや R サービス データベース内の設定します。](../../advanced-analytics/r/set-up-sql-server-r-services-in-database.md)

    SQL Server セットアップの一部として R と関連付けられたデータベース コンポーネントをインストールします。
  
+ [SQL Server と R のチュートリアル](../../advanced-analytics/tutorials/sql-server-r-tutorials.md)

    R コードで SQL Server データ ソースを作成する方法とリモート コンピューティング コンテキストを使用する方法について説明します。 SQL 開発者を対象としているその他のチュートリアルでは、SQL Server で R モデルをトレーニングし、展開する方法について説明します。
