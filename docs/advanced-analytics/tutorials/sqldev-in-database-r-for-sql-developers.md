---
title: R で SQL Server Machine Learning を使用してデータベース内分析のチュートリアル
description: R プログラミング言語のコードでは、SQL Server のストアド プロシージャおよび T-SQL 関数を埋め込む方法について説明します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: tutorial
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 4f0930e3f7f9d037ebb3033cc947f243657a1480
ms.sourcegitcommit: a91c3f4fe2587d474cd4d470bda93239ba2693bb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/14/2019
ms.locfileid: "67140761"
---
# <a name="tutorial-r-data-analytics-for-sql-developers"></a>チュートリアル:SQL 開発者向けの R データの分析
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

構築し、R ベースの machine learning を使用してソリューションを展開する R の統合について説明します SQL プログラマ向けのこのチュートリアルでは、 [NYCTaxi_sample](demo-data-nyctaxi-in-sql.md) SQL Server データベース。 T-SQL、SQL Server Management Studio、および [Machine Learning のサービス] で、データベース エンジンのインスタンスを使用します ([Machine Learning サービス](../install/sql-machine-learning-services-windows-install.md)と R 言語のサポート

このチュートリアルでは、ワークフローをモデル化データで使用される R 関数を紹介します。 手順には、データの探索、ビルドして二項分類モデルとモデルのデプロイが含まれます。 ビルドがモデルでは、乗車の日の時刻、距離、乗車場所に基づいてヒントに可能性があるかどうかを予測します。 

このチュートリアルで使用する R コードのすべては、作成して、Management Studio で実行するストアド プロシージャにラップされます。

## <a name="background-for-sql-developers"></a>SQL 開発者向けの背景

Machine learning ソリューションを構築するプロセスをいくつかのフェーズの間で複数のツール、および領域の専門家の調整を伴う複雑なものを示します。

+ 取得して、データのクリーニング
+ データの探索とモデリングの便利な機能の作成
+ トレーニング セットと、モデルの調整
+ 運用環境へのデプロイ

実際のコードの開発およびテストに専用の R 開発環境を使用してを実行が最適です。 ただし、スクリプトを完全にテストした後に簡単にデプロイできますを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を使用して[!INCLUDE[tsql](../../includes/tsql-md.md)]の使い慣れた環境でのストアド プロシージャ[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]します。

このマルチパート チュートリアルの目的は、「完成した R コードの移行」SQL Server への一般的なワークフローの概要です。 

- [レッスン 1:探索し、ストアド プロシージャで R 関数を呼び出すことによってデータのシェイプと配布を視覚化します。](../tutorials/sqldev-explore-and-visualize-the-data.md)

- [レッスン 2:T-SQL 関数で R を使用してデータ機能を作成します。](sqldev-create-data-features-using-t-sql.md)
  
- [レッスン 3:トレーニングし、関数およびストアド プロシージャを使用して R モデルの保存](sqldev-train-and-save-a-model-using-t-sql.md)
  
- [レッスン 4:ストアド プロシージャで R モデルを使用して潜在的な結果を予測します。](../tutorials/sqldev-operationalize-the-model.md)

モデルをデータベースに保存した後から予測モデルを呼び出す[!INCLUDE[tsql](../../includes/tsql-md.md)]ストアド プロシージャを使用します。

## <a name="prerequisites"></a>前提条件

すべてのタスクを行うことができますを使用して[!INCLUDE[tsql](../../includes/tsql-md.md)]ストアド プロシージャを[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]します。

このチュートリアルは、データベースとテーブルを作成、データをインポートする SQL クエリの記述などの基本的なデータベース操作に関する知識を前提とします。 R. を把握することを想定しませんそのため、すべての R コードが提供されます。 

+ [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md#verify-installation)または[有効になっている R を使用した SQL Server 2017 Machine Learning サービス](../install/sql-machine-learning-services-windows-install.md#verify-installation)

+ [R ライブラリ](../package-management/installed-package-information.md)

+ [権限](../security/user-permission.md)

+ [NYC タクシー デモ データベース](demo-data-nyctaxi-in-sql.md)


## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [探索し、ストアド プロシージャで R 関数を使用してデータを視覚化します。](../tutorials/sqldev-explore-and-visualize-the-data.md)
