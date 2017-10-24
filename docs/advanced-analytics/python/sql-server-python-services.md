---
title: "SQL Server R Services |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 06/22/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba1dea65-40ea-484a-b767-53680c954934
caps.latest.revision: 38
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 140885b86f0f6fa1a56119246c859f143f596726
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="machine-learning-services-with-python"></a>Machine Learning Python のサービス

Python は、優れた柔軟性とさまざまな機械学習タスクの機能を提供する言語です。 Python のオープン ソース ライブラリには、カスタマイズ可能なニューラル ネットワークでは、いくつかのプラットフォームおよび自然言語処理のための一般的なライブラリが含まれます。 ここで、SQL Server 2017 CTP 2.0 以降で、広く使用されている言語はサポートされています。

Python を統合しているため、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース エンジン、データの近くで分析して、コストとデータの移動に関連付けられているセキュリティ上のリスクを排除します。  Visual Studio などの便利で使い慣れたツールを使用して Python に基づいて machine learning ソリューションを配置することができます。 実稼働アプリケーションは、モデルの予測を取得できます。 または単に T-SQL で呼び出すことによって、Python 3.5 ランタイムからビジュアル ストアド プロシージャです。

このリリースでは、Python と同様の新しい Anaconda ディストリビューション[revoscalepy](../python/what-is-revoscalepy.md)スケールと機械学習のソリューションのパフォーマンスを向上させるために、ライブラリです。

Python の SQL Server 2017 設定を使用して作業を開始するに必要なすべてをインストールすることができます。

+ **Machine Learning Services (In-database):**で R スクリプトの実行をセキュリティで保護を有効にする、SQL Server データベース エンジンと共に、この機能をインストール、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]コンピューター。
  
     Python スクリプトの実行をサポートするために、データベース エンジンの拡張機能がインストールされている、新しいサービスを作成すると、この機能を選択するときに、 [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]Python ランタイム間の通信を管理するには、および[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンス。

+ **Machine Learning Server (スタンドアロン):** SQL Server の統合を必要がない場合は、Microsoft R Server での Python のサポートを受けるには、この機能をインストールします。 これにより、Python を使用してソリューションを使用できるようにする**mrsdeploy**です。
  
     SQL Server の Machine Learning のサービスを実行している同じコンピューターには、この機能をインストールしません。


## <a name="additional-resources"></a>その他のリソース

[Python の機械学習のデータベース内にサービスを設定します。](setup-python-machine-learning-services.md)

[Python のチュートリアル](../tutorials/sql-server-python-tutorials.md)

