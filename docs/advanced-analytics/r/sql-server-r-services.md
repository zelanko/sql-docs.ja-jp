---
title: "SQL Server コンピューターのサービスの学習 |Microsoft ドキュメント"
ms.date: 11/09/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba1dea65-40ea-484a-b767-53680c954934
caps.latest.revision: "38"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Active
ms.openlocfilehash: fb770b52f2cacfc527f6bb89955acfbda243c18a
ms.sourcegitcommit: ec5f7a945b9fff390422d5c4c138ca82194c3a3b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/11/2017
---
# <a name="sql-server-machine-learning-services"></a>SQL Server Machine Learning サービス

  SQL Server 2017 Machine Learning サービス (以前 SQL Server 2016 R サービス) は、開発と新しい洞察を得るためのインテリジェント アプリケーションを展開するためのプラットフォームを提供します。 豊富で強力な R 言語とコミュニティのさまざまなパッケージを使用してモデルを作成し、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データを使用して予測を生成することができます。
  
  機械学習を統合しているため、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データの近くで分析を行い、コストとデータの移動に関連付けられているセキュリティ上のリスクを削減できます。
  
SQL Server では、優れたパフォーマンス、セキュリティ、信頼性、および管理容易性を提供するツールとテクノロジの包括的なセットとオープン ソース R 言語をサポートします。 便利で使い慣れた SQL ツールを使用して R ソリューションを展開できます。 また、実稼働アプリケーションは、R ランタイムを呼び出すと、予測および視覚効果を使用して取得[!INCLUDE[tsql](../../includes/tsql-md.md)]です。 取得することも、 [Microsoft R](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler)スケールと RevoScaleR、revoscalepy、MicrososftML など、R ソリューションのパフォーマンスを向上させるためにライブラリです。
  
SQL Server セットアップにより、サーバー コンポーネントとクライアント コンポーネントの両方をインストールできます。
  
## <a name="machine-learning-in-sql-server-2017"></a>機械学習で SQL Server 2017

+ インストール**Machine Learning Services (In-database)**中に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で R または Python スクリプトの実行をセキュリティで保護を有効にする設定、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]コンピューター。
  
    この機能を選択すると、拡張機能は R または Python で記述されたコードの実行をサポートするために、データベース エンジンにインストールされます。 新しいサービスを作成、 [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]、外部のランタイムとの間の通信を管理して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンス。
  
+ インストール**Microsoft Machine Learning Server (スタンドアロン)**別のコンピューターを使用している場合は、計算コンテキストとして SQL Server を使用する必要はありません。 Machine Learning のサーバーには、machine learning コンポーネント、および web サービスとスケーラビリティを備えた分散 machine learning ジョブを実行する機能が含まれています。
  
+    インストール[Microsoft R クライアント](https://docs.microsoft.com/r-server/r-client/what-is-microsoft-r-client)SQL Server または Windows、Linux、または Hadoop 上の Machine Learning サーバーに配置できるソリューションを開発するリモート コンピューターにします。

## <a name="machine-learning-in-sql-server-2016"></a>機械学習の SQL Server 2016

+ インストール**R Services (In-database)**で R スクリプトの実行をセキュリティで保護を有効にする SQL Server 2016 のセットアップ時に、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]コンピューター。
  
    この機能を選択すると、計算コンテキストとして SQL Server を使用して R スクリプトを実行する機能や、ストアド プロシージャで R スクリプトを実行する機能を取得します。
  
+   インストール**Microsoft R Server (スタンドアロン)** SQL Server 2016 セットアップから、開発または R ソリューションを配置するために使用できる別のコンピューターに R コンポーネントをインストールします。


## <a name="which-type-of-machine-learning-service-do-i-need"></a>Machine learning のサービスの種類が必要ですか。

+ R コードを実行する必要がある場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、インストールする必要がありますを使用してストアド プロシージャか SQL Server インスタンスをコンピューティング コンテキストとして使用して、[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]の説明に従って[ここ](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md)です。

+ Microsoft Machine Learning Server (スタンドアロン) は、個別のオプションを使用するために設計されています、 [Microsoft R](https://docs.microsoft.com/r-server/r-reference/introducing-r-server-r-package-reference)と[Python ライブラリを関連](../python/what-is-revoscalepy.md)SQL Server が実行されていない Windows コンピューターにします。 ただし、Enterprise Edition のライセンス for SQL Server は、必要です。
    
    ラップトップまたは開発では、使用するその他のリモート コンピューターで Microsoft Machine Learning Server (スタンドアロン) をインストールしてそのコンピューターを使用して作成しのインスタンスに簡単に展開できるマシン ラーニング ソリューションをテストすることをお勧め[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Machine Learning のサービスが実行されている\(データベースで\)または別のサポートされているコンテキストを計算します。
  
    使用することも、 **mrsdeploy**パッケージを発行して web サービスとして R、Python のジョブを配布する Machine Learning サーバーと共にインストールされます。

## <a name="additional-resources"></a>その他のリソース

+ [SQL Server R Services の概要](../../advanced-analytics/r/getting-started-with-sql-server-r-services.md)
 
    SQL Server で R の使用法についての一般的なシナリオについて説明します

+ [SQL Server R Services (データベース内) をセットアップする](../../advanced-analytics/r/set-up-sql-server-r-services-in-database.md)

    SQL Server セットアップの一部として R と関連付けられたデータベース コンポーネントをインストールします。
  
+ [SQL Server R チュートリアル](../../advanced-analytics/tutorials/sql-server-r-tutorials.md)

    R コードで SQL Server データ ソースを作成する方法とリモート コンピューティング コンテキストを使用する方法について説明します。 SQL 開発者を対象としているその他のチュートリアルでは、SQL Server で R モデルをトレーニングし、展開する方法について説明します。
