---
title: Machine Learning Python のサービス |Microsoft ドキュメント
ms.date: 03/16/2018
ms.reviewer: ''
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: python
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.workload: On Demand
ms.openlocfilehash: 275eedc011367e51e97c6bddae03858cdda932ee
ms.sourcegitcommit: 059fc64ba858ea2adaad2db39f306a8bff9649c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/04/2018
---
# <a name="machine-learning-services-with-python"></a>Machine Learning Python のサービス
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Python は、優れた柔軟性とさまざまな機械学習タスクの機能を提供する言語です。 Python のオープン ソース ライブラリには、カスタマイズ可能なニューラル ネットワークでは、いくつかのプラットフォームおよび自然言語処理のための一般的なライブラリが含まれます。 ここで、この広く使用されている言語は、SQL Server 2017 機械学習でサポートされます。

Python を統合しているため、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース エンジン、データの近くで分析して、コストとデータの移動に関連付けられているセキュリティ上のリスクを排除します。  Visual Studio などの便利で使い慣れたツールを使用して Python に基づいて machine learning ソリューションを配置することができます。 実稼働アプリケーションは、モデルの予測を取得できます。 または単に T-SQL で呼び出すことによって、Python 3.5 ランタイムからビジュアル ストアド プロシージャです。

このリリースでは、Python の Anaconda ディストリビューションだけでなく[revoscalepy](../python/what-is-revoscalepy.md)スケールと機械学習のソリューションのパフォーマンスを向上させるために、ライブラリです。

Python の SQL Server 2017 設定を使用して作業を開始するに必要なすべてをインストールすることができます。

+ [**機械学習 Services (In-database)**](../install/sql-machine-learning-services-windows-install.md): SQL Server データベース エンジンの Python スクリプトのセキュリティで保護された実行を有効にすると共に、この機能をインストール、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]コンピューター。
  
     Python スクリプトの実行をサポートするために、データベース エンジンの拡張機能がインストールされている、新しいサービスを作成すると、この機能を選択するときに、 [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]Python ランタイム間の通信を管理するには、および[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンス。

+ [**機械学習 Server (スタンドアロン)**](../install/sql-machine-learning-standalone-windows-install.md): SQL Server の統合を必要がない場合は、分散の機械学習の Python と R のサポートを取得するには、この機能をインストールします。

## <a name="see-also"></a>参照

+ [SQL Server コンピューターの学習と R Services (In-database)](../r/sql-server-r-services.md)
+ [SQL Server コンピューターの学習と R Server (スタンドアロン)](../r/r-server-standalone.md)
+ [Python のアーキテクチャ](architecture-overview-sql-server-python.md)
+ [Python のチュートリアル](../tutorials/sql-server-python-tutorials.md)
