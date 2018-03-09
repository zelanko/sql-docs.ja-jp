---
title: "データベース内 Python analytics SQL 開発者のため |Microsoft ドキュメント"
ms.custom: 
ms.date: 10/13/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: 
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: tutorial
applies_to:
- SQL Server 2017
dev_langs:
- Python
- TSQL
ms.assetid: 
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.openlocfilehash: c026e09e1fa34b98d1eda43d59097c966051f6d7
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2018
---
# <a name="in-database-python-analytics-for-sql-developers"></a>SQL 開発者のためのデータベースでの Python の分析
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

このチュートリアルの目的は、SQL プログラマ環境に提供する実践的な機械学習の SQL Server で実行されている Python を使用したソリューションの構築です。 このチュートリアルでは、ストアド プロシージャに Python コードを追加してビルドし、モデルから予測するストアド プロシージャを実行する方法を学習します。

> [!NOTE]
> R を使用しますか。 参照してください[このチュートリアル](sqldev-in-database-r-for-sql-developers.md)、同様のソリューションを提供するが、R を使用し、SQL Server 2016 または SQL Server 2017 のいずれかで実行することができます。

## <a name="overview"></a>概要

機械学習ソリューションの構築プロセスでは、いくつかのフェーズの間で複数のツールおよび領域の専門家の調整を含む複雑なものです。

+ 取得して、データのクリーニング
+ データを調査し、モデリングに有用特徴の構築
+ トレーニング セットとモデルの調整
+ 実稼働環境に展開

**このチュートリアルの焦点はビルドと SQL Server を使用してソリューションを展開します。**

データは、よく知られた NYC タクシー データ セットからです。 このチュートリアルを迅速かつ簡単には、データをサンプリングします。 かどうか特定トリップもそうでない、ヒントを取得する可能性の高い、時刻、距離、および収集場所などの列に基づいて予測する二項分類モデルを作成します。

すべてのタスクを行うことができますを使用して[!INCLUDE[tsql](../../includes/tsql-md.md)]の使い慣れた環境でのストアド プロシージャ [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]

- [手順 1: サンプル データのダウンロード](sqldev-py1-download-the-sample-data.md)

    サンプル データセットとすべてのスクリプト ファイルをローカル コンピューターにダウンロードします。

- [手順 2: PowerShell を使用した SQL Server へのデータのインポート](sqldev-py2-import-data-to-sql-server-using-powershell.md)

    指定したインスタンスにデータベースとテーブルを作成し、テーブルにサンプル データを読み込む PowerShell スクリプトを実行します。

- [手順 3: 探索し、Python を使用してデータの視覚化](sqldev-py3-explore-and-visualize-the-data.md)

    基本的なデータ探索およびから呼び出し元の Python での視覚化は、実行[!INCLUDE[tsql](../../includes/tsql-md.md)]ストアド プロシージャです。

- [手順 4: T-SQL で Python を使用したデータ機能を作成します。](sqldev-py5-train-and-save-a-model-using-t-sql.md)

    カスタム SQL 関数を使用して新しいデータ機能を作成します。
  
- [手順 5: トレーニングおよび T-SQL を使用して、Python モデルを保存](sqldev-py5-train-and-save-a-model-using-t-sql.md)

    構築し、ストアド プロシージャで Python を使用して、機械学習モデルを保存します。
  
    このチュートリアルは、二項分類タスクを実行する方法を示します多クラス分類または回帰のモデルを構築するのにデータを使用することもできます。

  
-  [手順 6: 運用 Python モデル](sqldev-py6-operationalize-the-model.md)

    モデルは、データベースに保存されている後、は、予測を使用するため、モデルを呼び出して[!INCLUDE[tsql](../../includes/tsql-md.md)]です。

## <a name="requirements"></a>必要条件

### <a name="prerequisites"></a>前提条件

+ Machine Learning のサービスと有効になっている Python には、SQL Server 2017 のインスタンスをインストールします。 詳細については、次を参照してください。 [Python の SQL Server マシン ラーニング Services セットアップ](../python/setup-python-machine-learning-services.md)です。
+ このチュートリアルで使用するログインでは、データベースやその他のオブジェクトを作成し、データをアップロードし、データを選択し、ストアド プロシージャを実行するためのアクセス許可が付与されている必要があります。

### <a name="experience-level"></a>経験レベル

データベースとテーブルを作成、テーブルにデータをインポートする SQL クエリを作成するなど、基本的なデータベース操作に慣れておく必要があります。

経験豊富な SQL プログラマーであれば、 [!INCLUDE[tsql](../../includes/tsql-md.md)] の [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用するか、提供されている PowerShell スクリプトを実行して、このチュートリアルを完了することができます。

Python: 基本的な知識は役立ちますが、必須ではありません。 すべての Python コードを示します。

PowerShell の知識をお勧めします。

### <a name="tools"></a>ツール

このチュートリアルで、展開段階に到達したことを想定しています。 データのクリーンアップが指定されている、エンジニア リング、および Python コードを操作の機能の T-SQL コードを完了するとします。 そのため、SQL Server Management Studio または SQL ステートメントの実行をサポートするその他のツールを使用してこのチュートリアルを実行することができます。

+ [SQL Server ツールの概要](https://docs.microsoft.com/sql/tools/overview-sql-tools) 

開発および Python コードをテストするまたは Python ソリューションをデバッグする場合は、専用の開発環境を使用してお勧めします。

+ **Visual Studio 2017**両方 R をサポートしていると[Python](https://blogs.msdn.microsoft.com/visualstudio/2017/05/12/a-lap-around-python-in-visual-studio-2017/)です。 お勧め、[データ サイエンス ワークロード](https://blogs.msdn.microsoft.com/visualstudio/2016/11/18/data-science-workloads-in-visual-studio-2017-rc/)R と f# もサポートします。
+ Visual Studio の以前のバージョンがある場合[for Visual Studio 拡張機能を Python](https://docs.microsoft.com/visualstudio/python/python-in-visual-studio)を複数の Python 環境を管理するが容易です。
+ Python 開発者の間での一般的な IDE を PyCharm にです。

    > [!NOTE]
    > 一般に、書き込みまたは新しい Python コードでのテストを避ける[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]です。 ストアド プロシージャに埋め込まれたコードに問題がある場合は、ストアド プロシージャから返される情報は、エラーの原因を理解すれば十分ではありません。

計画およびプロジェクトの学習成功したコンピューターを実行するためには、次のリソースを使用します。

+ [チーム データ サイエンス プロセス](https://docs.microsoft.com/azure/machine-learning/team-data-science-process/overview)

### <a name="estimated-time-required"></a>推定所要時間

|手順| 時間 (時間)|
|----|----|
|サンプル データをダウンロードします。| 0:15|
|PowerShell を使用して SQL server のデータをインポートします。|0:15|
|探索し、データの視覚化|0:20|
|T-SQL を使用してデータ機能を作成します。|0:30|
|トレーニングし、T-SQL を使用してモデルを保存します。|0:15|
|モデルを操作可能します。|0:40|

## <a name="get-started"></a>概要します。

  [手順 1: サンプル データのダウンロード](sqldev-py1-download-the-sample-data.md)
