---
title: "Machine Learning Python のサービス |Microsoft ドキュメント"
ms.date: 11/03/2017
ms.prod: sql-non-specified
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
ms.workload: On Demand
ms.openlocfilehash: 665d307f37bca34669de291a2ea0c71d231288a8
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2017
---
# <a name="machine-learning-services-with-python"></a>Machine Learning Python のサービス

Python は、優れた柔軟性とさまざまな機械学習タスクの機能を提供する言語です。 Python のオープン ソース ライブラリには、カスタマイズ可能なニューラル ネットワークでは、いくつかのプラットフォームおよび自然言語処理のための一般的なライブラリが含まれます。 ここで、SQL Server 2017 CTP 2.0 以降で、広く使用されている言語はサポートされています。

Python を統合しているため、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース エンジン、データの近くで分析して、コストとデータの移動に関連付けられているセキュリティ上のリスクを排除します。  Visual Studio などの便利で使い慣れたツールを使用して Python に基づいて machine learning ソリューションを配置することができます。 実稼働アプリケーションは、モデルの予測を取得できます。 または単に T-SQL で呼び出すことによって、Python 3.5 ランタイムからビジュアル ストアド プロシージャです。

このリリースでは、Python と同様の新しい Anaconda ディストリビューション[revoscalepy](../python/what-is-revoscalepy.md)スケールと機械学習のソリューションのパフォーマンスを向上させるために、ライブラリです。

Python の SQL Server 2017 設定を使用して作業を開始するに必要なすべてをインストールすることができます。

+ **Machine Learning Services (In-database):**で Python スクリプトのセキュリティで保護された実行を有効にする、SQL Server データベース エンジンと共に、この機能をインストール、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]コンピューター。
  
     Python スクリプトの実行をサポートするために、データベース エンジンの拡張機能がインストールされている、新しいサービスを作成すると、この機能を選択するときに、 [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]Python ランタイム間の通信を管理するには、および[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンス。

+ **Machine Learning Server (スタンドアロン):** SQL Server の統合を必要がない場合は、分散の機械学習の Python と R のサポートを取得するには、この機能をインストールします。 使用して、web サービスとしての Python ソリューションを配置することもできます**mrsdeploy**です。
  
     SQL Server の Machine Learning のサービスを実行している同じコンピューターには、この機能をインストールしません。


## <a name="additional-resources"></a>その他のリソース

[Python の機械学習のデータベース内にサービスを設定します。](setup-python-machine-learning-services.md)

[Python のチュートリアル](../tutorials/sql-server-python-tutorials.md)
