---
title: "機械学習の getting Started with SQL Server |Microsoft ドキュメント"
ms.custom: SQL2016_New_Updated
ms.date: 12/07/2016
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
ms.assetid: 5b28a663-effe-41f6-9bda-eda95f0c6943
caps.latest.revision: "34"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: c114d320e71a93ffc6614ae6cfb1b535af2510e1
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2017
---
# <a name="getting-started-with-sql-server-machine-learning"></a>機械学習の getting Started with SQL Server

SQL Server の machine Learning のサービスは、セキュリティ リスクやデータの移動 unnecesarily にデータを公開することがなくデータ サイエンス タスクをサポートするために設計されています。

+ SQL Server 2016 では、好みの R ツールを使用はパフォーマンスが向上しているときに何十億ものレコードのために、分析を拡張できます。 機械学習を SQL Server と統合することは、R コードに再コーディングすることがなく実稼働環境に配置できるも意味にします。

+ SQL Server 2017 では、同じ拡張機能フレームワークを使用する Python コードのサポートを追加します。

このトピックでは、R、Python でのデータベースを使用するための主要なシナリオについて説明し、独自のソリューションの開始に役立つリソースを提供します。

適用されます SQL Server 2016 の R Services、SQL Server 2017 機械学習の Services (In-database)。

> [!NOTE]
> SQL Server 2016 では、R 言語に対してのみサポートされています。 Python 言語のサポートには、SQL Server 2017 CTP 2.0 が必要です。

## <a name="step-1-set-up-sql-server-machine-learning-services"></a>手順 1. SQL Server マシン ラーニング Services をセットアップします。

1. SQL Server セットアップを実行し、SQL Server データベース エンジンの少なくとも 1 つのインスタンスをインストールします。
2. 外部のランタイムの実行をサポートする機能を追加します。
3. SQL Server 2016 では、既定で R が追加されます。 SQL Server の 2017 を追加する言語を選択する必要があります。 R または Python のいずれかを選択したり、両方を有効にすることができます。
4. セットアップを完了すると、外部スクリプトの実行を有効にする追加の手順を実行し、サーバーを再起動します。

**リソース**

+ [Machine Learning での SQL Server を設定します。](../../advanced-analytics/r/set-up-sql-server-r-services-in-database.md)

> [!TIP]  
> R ジョブ用のサーバーを作成する必要があり、SQL Server は不要な場合は、 [Microsoft R Server](https://msdn.microsoft.com/library/mt674874.aspx)をお試しください。  

## <a name="step-2-develop-your-r-or-python-solutions"></a>手順 2. R、Python ソリューションを開発します。

データ サイエンティスト通常使用 R または Python が自分のラップトップ コンピューターや開発ワークステーションでデータを探索し、ビルド、および適切な予測モデルを実現するまでは、予測モデルを調整します。 

Machine Learning サービスを使用する SQL Server では、このプロセスを変更する必要はありません。 R または Python コードを実行するにはインストールが完了したら、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ローカルまたはリモートで。

![rsql_keyscenario2](media/rsql-keyscenario2.png) 

+ **必要に応じて、IDE を使用して**です。 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] クライアント コンポーネントは、データ サイエンティストに実験や開発に必要なすべてのツールを提供します。 これらのツールには、R ランタイム、標準的な R 演算のパフォーマンスを向上させる Intel Math Kernel Library、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]での R コードの実行をサポートする一連の拡張 R パッケージが含まれます。  

+ **リモートまたはローカルでの作業**です。 データ サイエンティストは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続し、通常どおり、ローカル分析のためにクライアントにデータを移動できます。 ただし、より優れたソリューションは、 **ScaleR** API を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンピューターに計算をプッシュすることです。これにより、コストのかかる安全でないデータ移動を回避できます。

+ **R または Python スクリプトを埋め込む[!INCLUDE[tsql](../../includes/tsql-md.md)]ストアド プロシージャ**です。 コードは完全に最適化された、ときに、不要なデータ移動を回避し、タスクのデータ処理を最適化するストアド プロシージャでラップします。


**リソース**

+ インストール[R Tools for Visual Studio](https://docs.microsoft.com/visualstudio/rtvs/installation)または RStudio です。  

## <a name="step-3-optimize"></a>手順 3. 最適化

モデルの企業データにスケール アウトする準備ができたら、データ サイエンティストは多くの場合、開発者と協力して DBA や SQL などのプロセスを最適化するために。

+ 機能エンジニアリング
+ データの取り込みやデータの変換
+ ポイントの計算

従来 R を使用するデータ サイエンティストは、特に大規模なデータセットを使用する場合に、パフォーマンスとスケールの両方の問題を必要があります。 一般的なランタイムの実装はシングル スレッドし、ローカル コンピューターで使用可能なメモリに収まらないデータ セットのみに対応できるためです。 SQl Server マシン学習サービスとの統合より多くのデータのパフォーマンスを向上させるため、複数の機能を提供します。

+ **RevoScaleR**。: この R パッケージには、最も一般的な R 関数、並列処理とスケールのために再設計のいくつかの実装が含まれています。 パッケージには、通常ははるかに大きなメモリと計算能力がある [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンピューターに計算をプッシュして、パフォーマンスとスケールをさらに向上させる機能も含まれます。

+ **revoscalepy**です。 この Python ライブラリは、新規および SQL Server 2017 CTP 2.0 でのみ使用可能なは、リモート計算コンテキストなど RevoScaleR で最も人気のある関数を実装しをサポートする多くのアルゴリズムが処理を分散します。

+ タスクに最適な言語を選択します。  R は、SQL を使用して実装するが困難な統計の計算に最適です。 データに対するセットベースの操作での活用[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]最大パフォーマンスを実現します。 列にわたって非常に高速計算用のメモリ内のデータベース エンジンを使用します。

**リソース**

+ [パフォーマンスのケース スタディ](../../advanced-analytics/r/performance-case-study-r-services.md)
+ [R とデータの最適化](../../advanced-analytics/r/r-and-data-optimization-r-services.md)


## <a name="step-4-deploy-and-consume"></a>手順 4. 展開および使用します。

R スクリプトまたはモデルは、実稼働環境の使用可能な状態が、データベース開発者を埋め込むことがコードまたはモデル ストアド プロシージャで保存した R または Python コードをアプリケーションから呼び出すことができるようにします。 R コードの格納と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からの実行には多くの利点があります。便利な [!INCLUDE[tsql](../../includes/tsql-md.md)] インターフェイスを使用でき、計算はすべてデータベースで行われるため、不要なデータ移動を回避できます。

![rsql_keyscenario1](media/rsql-keyscenario1.png)

+ **安全で拡張性の高い**です。 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] では、データベース エンジンをセキュリティで保護した状態で R セッションを分離する新しい拡張可能アーキテクチャを使用します。 また、R コードを実行できるユーザーを制御し、R コードでアクセス可能なデータベースを指定することもできます。 R ランタイムに割り当てられるリソースの量を制御し、大規模な計算によりサーバーの全体的なパフォーマンスが損なわれないようにすることができます。

+ **スケジュールおよび監査**です。 外部スクリプトのジョブの実行と[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]制御することができます、および監査データは、データ サイエンティストが使用されます。 ジョブとその他の T-SQL ジョブまたはストアド プロシージャをスケジュールするのと同じように、外部の R または Python スクリプトを含むワークフローを作成をスケジュールすることもできます。

SQL Server で、リソースの管理およびセキュリ ティー機能の利点を使用するには、展開プロセスに、これらのタスクが含まれます。

+ ストアド プロシージャで最適に実行できる関数に R コードの変換
+ セキュリティを設定して、特定のタスクで使用されるパッケージをロックダウン
+ リソース管理を有効にします。

**リソース**

+ [R のリソース管理](../../advanced-analytics/r/resource-governance-for-r-services.md)
+ [SQL Server の R パッケージの管理](../../advanced-analytics/r/r-package-management-for-sql-server-r-services.md)

## <a name="quick-starts"></a>クイック スタート

モデルを作成して、SQL Server へのデプロイにデータを探索から、すべてのワークフローを理解するには、このチュートリアルを参照してください。

+ [データ サイエンスのエンド ツー エンド チュートリアル](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md)

拡張性と高パフォーマンス分析のため、RevoScaleR パッケージを使用する方法を説明します。

+ [データ サイエンスの詳細: RevoScaleR パッケージの使用](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)

特に、データ開発者の--すべての R コードが提供される! 作成またはモデルをトレーニングする SQL ストアド プロシージャに R を埋め込むし、保存されたモデルから予測を取得する方法を説明します。

+ [SQL 開発者向けの高度な分析 (データベース内)](../tutorials/sqldev-in-database-r-for-sql-developers.md)

ストアド プロシージャから呼び出し元の R の構文を説明します。

+ [Transact-SQL での R コードの使用](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)

## <a name="solutions"></a>ソリューション

他のサンプルについての業界を含む = 特定のソリューション テンプレートを参照してください[SQL Server マシン ラーニング チュートリアル](../tutorials/machine-learning-services-tutorials.md)です。
