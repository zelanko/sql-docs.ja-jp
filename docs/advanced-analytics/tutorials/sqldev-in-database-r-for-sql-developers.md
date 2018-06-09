---
title: SQL Server の Machine Learning の開発者向けの埋め込みの R analytics チュートリアル |Microsoft ドキュメント
description: SQL Server で R を埋め込む方法を示すチュートリアル ストアド プロシージャと T-SQL 関数
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/07/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 3d2b77d73bb1b8f5d4c507b884d0a09f4647012b
ms.sourcegitcommit: b52b5d972b1a180e575dccfc4abce49af1a6b230
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2018
ms.locfileid: "35250025"
---
# <a name="tutorial-embedded-r-in-stored-procedures-and-t-sql-functions"></a>チュートリアル: ストアド プロシージャおよび T-SQL 関数で R を埋め込む
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

このチュートリアルの目的は、SQL プログラマ環境に提供する実践的な機械学習で SQL Server ソリューションの構築です。 このチュートリアルでは、ストアド プロシージャで R コードをラップすることによって、アプリケーションまたは BI ソリューションに R を組み込む方法を学習します。

> [!NOTE]
> 
> 同じソリューションは、Python で使用できます。 SQL Server 2017 が必要です。 参照してください[データベース内分析 Python 開発者向け](../tutorials/sqldev-in-database-python-for-sql-developers.md)

## <a name="overview"></a>概要

エンド ツー エンド ソリューションを構築するプロセスは、通常、データの取得とクリーニング、データ探索およびデータ機能のエンジニアリング、モデルのトレーニングおよびチューニング、実稼働環境へのモデルの展開によって構成されます。 実際のコードの開発とテストが最適な実行専用の開発環境を使用します。 R、RStudio を意味する可能性がありますまたは[!INCLUDE[rtvs-short](../../includes/rtvs-short-md.md)]です。

ただし、ソリューションの作成後は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の使い慣れた環境で [!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャを使用して、ソリューションを [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]に容易に展開することができます。

このチュートリアルでは、ソリューション、およびフォーカスのビルドおよび SQL Server を使用してソリューションを展開するのに必要なすべての R コードが与えられている想定しています。

- [レッスン 1: サンプル データとスクリプトをダウンロードします。](../tutorials/sqldev-download-the-sample-data.md)

- [レッスン 2: チュートリアルの環境を設定します。](../r/sqldev-import-data-to-sql-server-using-powershell.md)

- [レッスン 3: 探索し、ストアド プロシージャで R 関数を呼び出すことによってデータの整形と分布を視覚化します。](../tutorials/sqldev-explore-and-visualize-the-data.md)

- [レッスン 4: T-SQL 関数で R を使用してデータ機能を作成します。](../tutorials/sqldev-create-data-features-using-t-sql.md)
  
- [レッスン 5: トレーニングおよび関数とストアド プロシージャを使用して R モデルを保存します。](../r/sqldev-train-and-save-a-model-using-t-sql.md)
  
- [レッスン 6: ラップ R コード操作運用のストアド プロシージャで](../tutorials/sqldev-operationalize-the-model.md)です。 
  データベースにモデルが保存されたら、ストアド プロシージャを使用して [!INCLUDE[tsql](../../includes/tsql-md.md)] から予測モデルを呼び出します。

## <a name="scenario"></a>シナリオ

このチュートリアルでは、ニューヨーク タクシーでトリップに基づいて、よく知られているパブリック データセットを使用します。 サンプル コードをすばやく実行するためには、データの代表的な 1% のサンプリングを作成しました。 このデータを使用して、かどうか特定トリップもそうでない、ヒントを取得する可能性の高い、時刻、距離、および収集場所などの列に基づいて予測する二項分類モデルを作成します。

## <a name="requirements"></a>要件

このチュートリアルは、データベースとテーブルを作成し、データをインポートして、SQL クエリを記述などの基本的なデータベース操作に関する知識を前提とします。 R. を把握することを想定しませんそのため、すべての R コードを提供します。 スキルを持つ SQL プログラマが提供されている PowerShell スクリプトでは、github、サンプル データを使用し、[!INCLUDE[tsql](../../includes/tsql-md.md)]で[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]をこの例を完了します。 

このチュートリアルを開始: する前に

- インスタンスを構成があることを確認[SQL Server 2016 の R Services](../install/sql-r-services-windows-install.md#verify-installation)または[有効になっている R で SQL Server 2017 マシン ラーニング サービス](../install/sql-machine-learning-services-windows-install.md#verify-installation)です。 さらに、 [R ライブラリを用意することを確認](../r/determine-which-packages-are-installed-on-sql-server.md#get-the-r-library-location)です。
- このチュートリアルで使用するログインがデータベースを作成するアクセス許可を持っていると、データをアップロードする他のオブジェクトが、データを選択し、ストアド プロシージャを実行します。

> [!NOTE]
> 実行することをお勧め**いない**使用[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]R コードを記述またはテストします。 ストアド プロシージャに埋め込まれたコードに問題がある場合は、ストアド プロシージャから返される情報は、エラーの原因を理解すれば十分ではありません。
> 
> デバッグは、ことをお勧めなどのツールを使用する[!INCLUDE[rtvs-short](../../includes/rtvs-short-md.md)]、または RStudio です。 このチュートリアルで示す R スクリプトは、従来の R ツールを使用して既に開発およびデバッグされています。

## <a name="next-lesson"></a>次のレッスン

[レッスン 1: サンプル データをダウンロードします。](../tutorials/sqldev-download-the-sample-data.md)
