---
title: "Microsoft R Server (スタンドアロン) の概要 | Microsoft Docs"
ms.custom: 
ms.date: 10/31/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52347d0d-ce60-4bb8-98d2-6163e87716b0
caps.latest.revision: "21"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.openlocfilehash: 5ff9e6bc9b6cebb4602683180737aa78e7deb6e3
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2017
---
# <a name="getting-started-with-machine-learning-server-standalone"></a>Machine Learning Server (スタンドアロン) の概要
 
SQL Server 2016 では、Microsoft R Server (スタンドアロン) は、高パフォーマンスの分析ソリューションおよびその他のビジネス アプリケーションとの統合を有効にするように、エンタープライズに一般的なオープン ソース R 言語を取り込むのに役立ちました。  

SQL Server 2017、名前は、Python 言語のサポートの追加を反映するように、マシン学習 Server (スタンドアロン) に変更されました。 両方のバージョンの Enterprise Edition またはソフトウェア アシュアランスのユーザーに無料で利用できます。

この記事では、Machine Learning のサーバー (または R Server) を使用する方法およびインストールとサンプルを開始する方法の概要を提供します。

## <a name="why-use-a-standalone-server-for-machine-learning"></a>機械学習のスタンドアロン サーバーを使用する理由

機械学習の SQL Server データを含むソリューションを統合に必要としない場合、Machine Learning サーバーは R、Python の分散、スケーラブルなサポートを提供し、さらに Hadoop、Spark、または Linux にソリューションの配置をサポートします。

Machine Learning のサーバーには、画像分析およびアプリケーションですぐに使用することができます、センチメント分析の事前トレーニング済みモデルも含まれています。

Machine Learning のサーバーの操作運用の機能を展開して、web サービス、リモートの実行、Spark と Hadoop MapReduce のクラスター化されたトポロジを使用して R、Python のソリューションを配布するサポートし、Windows または Linux のサポートします。

**SQL Server 2016**

+ SQL Server 2016 セットアップから Microsoft R Server (スタンドアロン) をインストールします。

    このオプションでは、R Services (In-database) から完全に独立して、スタンドアロンのサーバーを作成します。 このバージョンでは、R がのみがサポートされます。 スタンドアロン サーバーのセットアップは、SQL Server Enterprise Edition のサポート ポリシーに含まれます。 詳しくは、「 [スタンドアロン R Server の作成](../../advanced-analytics/r/create-a-standalone-r-server.md)」をご覧ください。

+ 個別の Windows インストーラーを使用して R サーバーをインストールします。

    このインストーラーは、Microsoft の最新ソフトウェア ライフ サイクルのサポート ポリシーを使用する Microsoft R Server の新しいインスタンスを作成します。 Linux、Cloudera、Teradata など、Hadoop の R Server をインストールすることもできます。
    
    詳細については、次を参照してください。 [Windows 用の R Server 9.1 のインストール](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows)です。

**SQL Server 2017**

+ SQL Server 2017 セットアップから Machine Learning Server (スタンドアロン) をインストールします。 

    このオプションでは、機械学習の R、Python、またはその両方での使用をサポートするために、スタンドアロン サーバーを作成します。 スタンドアロン サーバーのセットアップは、SQL Server Enterprise Edition のサポート ポリシーに含まれます。 詳しくは、「 [スタンドアロン R Server の作成](../../advanced-analytics/r/create-a-standalone-r-server.md)」をご覧ください。  

+ 新しいスタンドアロン Windows インストーラーを使用します。

    このインストール方法では、Microsoft の最新ソフトウェア ライフ サイクルのサポート ポリシーを使用するマシン ラーニング サーバーの新しいインスタンスを作成します。 追加コストなしでの Spark、または Linux の Hadoop で Machine Learning のサーバーをインストールすることもできます。
    
    詳細については、次を参照してください。 [Machine Learning Server for Windows のインストール](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install)です。

**既存のサーバーをアップグレードします。**

+ 既存のサーバーまたはにアップグレードするインスタンスがある場合は、ダウンロードし、更新プログラムを取得する Windows ベースのインストーラーを実行します。 

    詳細については、次を参照してください。[インスタンスをアップグレードするのを使用して SqlBindR](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)です。

## <a name="start-using-machine-learning-server"></a>Machine Learning のサーバーの使用を開始します。

 サーバー コンポーネントを設定して、IDE Machine Learning のサーバーのバイナリを使用するように構成と後、は、RevoScaleR と revoscalepy、MicrosoftML、olapR など、新しい Api を使用してソリューションの開発を開始できます。
    
開始するには、これらのガイドを参照してください。

+ [ソリューション テンプレート](https://docs.microsoft.com/machine-learning-server/r/sample-solutions)

    これらのサンプルは、特定の産業での機械学習を適用する方法を示すソリューションです。 現在のシナリオは、小売、財務や医療、マーケティング部門でです。

+ [R と ScaleR 25 関数での探索](https://docs.microsoft.com/machine-learning-server/r/tutorial-r-to-revoscaler): このコレクションの高パフォーマンスとスケーリング R ソリューションを提供する再頒布可能の分析関数を調査します。 最も一般的な R モデリング パッケージ (K-平均法クラスタリング、デシジョン ツリー、デシジョン フォレストなど) の並列化可能なバージョンの多くと、データ操作のツールを含みます。

- [MicrosoftML](https://msdn.microsoft.com/library/mt790482.aspx)

    MicrosoftML パッケージは、新しいした機械学習アルゴリズムと Microsoft で開発された高速かつスケーラブルな変換のセットです。 R または Python のいずれかで使用することができます。 詳細については、次を参照してください。 [for Python MicrosoftML](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package)と[R の MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package)です。

## <a name="see-also"></a>参照

[SQL Server コンピューターのサービスの学習の概要](../../advanced-analytics/r/getting-started-with-sql-server-r-services.md)