---
title: In-database Python analytics SQL 開発者向けの |Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 26703f73312b5531490afc7d01319d4ac290bebe
ms.sourcegitcommit: 70e47a008b713ea30182aa22b575b5484375b041
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49806762"
---
# <a name="in-database-python-analytics-for-sql-developers"></a>SQL 開発者向けの In-database Python 分析
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

このチュートリアルの目的は、machine learning の SQL Server で実行されている Python を使用してソリューションをビルドする実践的な経験のある SQL プログラマを提供することです。 このチュートリアルでは、ストアド プロシージャに Python コードを追加してビルドし、モデルから予測するストアド プロシージャを実行する方法を学習します。

> [!NOTE]
> R こともできます。 参照してください[このチュートリアル](sqldev-in-database-r-for-sql-developers.md)、同様のソリューションを提供しますが、R を使用し、SQL Server 2016 または SQL Server 2017 のいずれかで実行できます。

## <a name="overview"></a>概要

Machine learning ソリューションを構築するプロセスをいくつかのフェーズの間で複数のツール、および領域の専門家の調整を伴う複雑なものを示します。

+ 取得して、データのクリーニング
+ データの探索とモデリングの便利な機能の作成
+ トレーニング セットと、モデルの調整
+ 運用環境へのデプロイ

**このチュートリアルの焦点はのビルドと SQL Server を使用してソリューションを展開します。**

データは、よく知られている NYC タクシー データ セットからです。 このチュートリアルを迅速かつ簡単にするには、データのサンプリングします。 かどうか、特定の乗車か、ヒントを取得する日の時刻、距離、乗車場所などの列に基づいて予測する二項分類モデルを作成します。

すべてのタスクを行うことができますを使用して[!INCLUDE[tsql](../../includes/tsql-md.md)]の使い慣れた環境でのストアド プロシージャ [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]


- [探索し、Python を使用してデータを視覚化します。](sqldev-py3-explore-and-visualize-the-data.md)

    基本的なデータ探索とビジュアル化から Python を呼び出し元によって、実行[!INCLUDE[tsql](../../includes/tsql-md.md)]ストアド プロシージャ。

- [T-SQL で Python を使用してデータ機能を作成します。](sqldev-py5-train-and-save-a-model-using-t-sql.md)

    カスタム SQL 関数を使用して新しいデータ機能を作成します。
  
- [トレーニングし、T-SQL を使用して Python モデルの保存](sqldev-py5-train-and-save-a-model-using-t-sql.md)

    構築し、ストアド プロシージャで Python を使用して、機械学習モデルを保存します。
  
    このチュートリアルは、二項分類タスクを実行する方法を示します回帰または多クラス分類モデルを構築するのにデータを使用することもできます。

  
-  [ Python モデルを運用します。](sqldev-py6-operationalize-the-model.md)

    モデルをデータベースに保存した後は、予測を使用するため、モデルを呼び出す[!INCLUDE[tsql](../../includes/tsql-md.md)]します。

## <a name="requirements"></a>要件

### <a name="prerequisites"></a>前提条件

+ Machine Learning サービスと Python が有効になっているは、SQL Server 2017 のインスタンスをインストールします。 詳細については、次を参照してください。[インストール SQL Server 2017 Machine Learning Services (In-database)](../install/sql-machine-learning-services-windows-install.md)します。
+ このチュートリアルで使用するログインでは、データベースやその他のオブジェクトを作成し、データをアップロードし、データを選択し、ストアド プロシージャを実行するためのアクセス許可が付与されている必要があります。

### <a name="experience-level"></a>経験レベル

データベースとテーブルを作成、テーブルにデータをインポートする SQL クエリの作成などの基本的なデータベース操作する必要があります。

経験豊富な SQL プログラマーであれば、 [!INCLUDE[tsql](../../includes/tsql-md.md)] の [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用するか、提供されている PowerShell スクリプトを実行して、このチュートリアルを完了することができます。

Python: 基本的な知識は、便利ですが、必須ではありません。 すべての Python コードが提供されます。

PowerShell の知識をお勧めします。

### <a name="tools"></a>ツール

このチュートリアルでは、展開の段階に達したかと思います。 データのクリーンアップが与えられている、機能エンジニア リング、および Python コードの操作の T-SQL コードを完了するとします。 そのため、SQL Server Management Studio、または実行中の SQL ステートメントをサポートするその他のツールを使用して、このチュートリアルを行うことができます。

+ [SQL Server ツールの概要](https://docs.microsoft.com/sql/tools/overview-sql-tools) 

開発し、独自の Python コードをテストするまたは、Python のソリューションをデバッグする場合は、専用の開発環境を使用してお勧めします。

+ **Visual Studio 2017**両方 R をサポートしていると[Python](https://blogs.msdn.microsoft.com/visualstudio/2017/05/12/a-lap-around-python-in-visual-studio-2017/)します。 お勧め、[データ サイエンス ワークロード](https://blogs.msdn.microsoft.com/visualstudio/2016/11/18/data-science-workloads-in-visual-studio-2017-rc/)R、f# もサポートします。
+ Visual Studio の以前のバージョンがあれば[for Visual Studio の Python 拡張機能](https://docs.microsoft.com/visualstudio/python/python-in-visual-studio)簡単に複数の Python 環境を管理することです。
+ PyCharm は Python 開発者の間での一般的な IDE です。

    > [!NOTE]
    > 一般に、書き込みや新しい Python コードのテストを避ける[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]します。 ストアド プロシージャに埋め込むことがコードに問題がある場合は、ストアド プロシージャから返される情報は、エラーの原因を解明するすれば十分ではありません。

計画および成功した machine learning のプロジェクトを実行するためには、次のリソースを使用します。

+ [Team Data Science Process](https://docs.microsoft.com/azure/machine-learning/team-data-science-process/overview)

### <a name="estimated-time-required"></a>推定所要時間

|手順| 時間 (時間)|
|----|----|
|サンプル データをダウンロードします。| 0:15|
|PowerShell を使用して SQL server のデータをインポートします。|0:15|
|探索し、データの視覚化|0:20|
|T-SQL を使用してデータ機能を作成します。|0:30|
|トレーニングし、T-SQL を使用してモデルを保存|0:15|
|モデルを運用する|0:40|

## <a name="get-started"></a>作業開始

  [手順 1: サンプル データのダウンロード](demo-data-nyctaxi-in-sql.md)
