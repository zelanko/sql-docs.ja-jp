---
title: データベース内 R analytics SQL 開発者 (チュートリアル) |Microsoft ドキュメント
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: e1ff2799ba37c97f5ff82c1c15cdeb986220a947
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2018
ms.locfileid: "34585274"
---
# <a name="in-database-r-analytics-for-sql-developers-tutorial"></a>データベース内 R analytics SQL 開発者 (チュートリアル)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

このチュートリアルの目的は、SQL プログラマ環境に提供する実践的な機械学習で SQL Server ソリューションの構築です。 このチュートリアルでは、ストアド プロシージャで R コードをラップすることによって、アプリケーションまたは BI ソリューションに R を組み込む方法を学習します。

> [!NOTE]
> 
> 同じソリューションは、Python で使用できます。 SQL Server 2017 が必要です。 参照してください[データベース内分析 Python 開発者向け](../tutorials/sqldev-in-database-python-for-sql-developers.md)

## <a name="overview"></a>概要

エンド ツー エンド ソリューションを構築するプロセスは、通常、データの取得とクリーニング、データ探索およびデータ機能のエンジニアリング、モデルのトレーニングおよびチューニング、実稼働環境へのモデルの展開によって構成されます。 実際のコードの開発とテストが最適な実行専用の開発環境を使用します。 R、RStudio を意味する可能性がありますまたは[!INCLUDE[rtvs-short](../../includes/rtvs-short-md.md)]です。

ただし、ソリューションの作成後は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の使い慣れた環境で [!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャを使用して、ソリューションを [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]に容易に展開することができます。

このチュートリアルでは、ソリューション、およびフォーカスのビルドおよび SQL Server を使用してソリューションを展開するのに必要なすべての R コードが与えられている想定しています。

- [レッスン 1: サンプル データをダウンロードします。](../tutorials/sqldev-download-the-sample-data.md)

    サンプル データセットとサンプル SQL スクリプト ファイルをローカル コンピューターにダウンロードします。

- [レッスン 2: PowerShell を使用して SQL server のデータをインポートします。](../r/sqldev-import-data-to-sql-server-using-powershell.md)

    [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] インスタンス上でデータベースとテーブルを作成し、テーブルにサンプル データを読み込むための PowerShell スクリプトを実行します。

- [レッスン 3: 探索し、データの視覚化](../tutorials/sqldev-explore-and-visualize-the-data.md)

    R パッケージおよび関数を [!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャから呼び出して、基本的なデータの探索および視覚化を実行します。

- [レッスン 4: T-SQL を使用してデータ機能を作成します。](../tutorials/sqldev-create-data-features-using-t-sql.md)

    カスタム SQL 関数を使用して新しいデータ機能を作成します。
  
-   [レッスン 5: トレーニングおよび T-SQL を使用して R モデルを保存します。](../r/sqldev-train-and-save-a-model-using-t-sql.md)

    ストアド プロシージャで R を使用して、機械学習モデルを構築します。 SQL Server テーブルに、モデルを保存します。
  
-   [レッスン 6: 運用モデル](../tutorials/sqldev-operationalize-the-model.md)

    データベースにモデルが保存されたら、ストアド プロシージャを使用して [!INCLUDE[tsql](../../includes/tsql-md.md)] から予測モデルを呼び出します。

### <a name="scenario"></a>シナリオ

このチュートリアルでは、ニューヨーク タクシーでトリップに基づいて、よく知られているパブリック データセットを使用します。 サンプル コードをすばやく実行するためには、データの代表的な 1% のサンプリングを作成しました。 このデータを使用して、かどうか特定トリップもそうでない、ヒントを取得する可能性の高い、時刻、距離、および収集場所などの列に基づいて予測する二項分類モデルを作成します。

### <a name="requirements"></a>要件

このチュートリアルでは、データベースとテーブルを作成し、テーブルにデータをインポートして、SQL クエリを記述などの基本的なデータベース操作に精通しているユーザーです。 すべての R コードが提供されるため、R の開発環境は必要ありません。 スキルを持つ SQL プログラマが使用できる [! INCLUDE [tsql] (../..含まれています//tsql md.md)] で [! INCLUDE [ssManStudioFull] (../..含まれています//ssmanstudiofull md.md) し、この例を完了する指定した PowerShell スクリプトを実行します。 ただし、このチュートリアルを開始する前に、次の準備を完了する必要があります。

ただし、このチュートリアルを開始する前にこれらの準備を完了する必要があります。

- Machine Learning のサービスと有効になっている R と SQL Server 2017 R Services の SQL Server 2016 のインスタンスに接続します。
- このチュートリアルで使用するログインがデータベースを作成するアクセス許可を持っていると、データをアップロードする他のオブジェクトが、データを選択し、ストアド プロシージャを実行します。

> [!NOTE]
> 実行することをお勧め**いない**使用[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]R コードを記述またはテストします。 ストアド プロシージャに埋め込まれたコードに問題がある場合は、ストアド プロシージャから返される情報は、エラーの原因を理解すれば十分ではありません。
> 
> デバッグは、ことをお勧めなどのツールを使用する[!INCLUDE[rtvs-short](../../includes/rtvs-short-md.md)]、または RStudio です。 このチュートリアルで示す R スクリプトは、従来の R ツールを使用して既に開発およびデバッグされています。

## <a name="next-lesson"></a>次のレッスン

[レッスン 1: サンプル データをダウンロードします。](../tutorials/sqldev-download-the-sample-data.md)
