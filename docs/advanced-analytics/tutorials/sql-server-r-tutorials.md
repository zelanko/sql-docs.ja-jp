---
title: SQL Server R チュートリアルの概要 - SQL Server Machine Learning
description: SQL Server データベース内分析用の R 言語のチュートリアルを紹介します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/18/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 99dc3aa20bd3f31766ed66a6cdabea5cf38553f6
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58510159"
---
# <a name="sql-server-r-language-tutorials"></a>SQL Server の R 言語のチュートリアル
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事でデータベース内分析用の R 言語のチュートリアルを説明します[SQL Server 2016 R Services](../install/sql-r-services-windows-install.md)または[SQL Server 2017 Machine Learning Services](../install/sql-machine-learning-services-windows-install.md)します。

+ ラップして、ストアド プロシージャで R コードを実行する方法について説明します。
+ シリアル化し、r ベースのモデルを SQL Server データベースに保存します。
+ リモートとローカル コンピューティング コンテキストを使用する状況について説明します。
+ データ サイエンスや機械学習タスク用の Microsoft R ライブラリをについて説明します。

<a name="bkmk_sqltutorials"></a>

## <a name="r-quickstarts-and-tutorials"></a>R のクイック スタートとチュートリアル

| リンク | 説明 |
|------|-------------|
| [クイック スタート:T-SQL での R の使用](rtsql-using-r-code-in-transact-sql-quickstart.md) | この 1 つの SQL Server Management Studio などの T-SQL クエリ エディターを使用して、R 関数を呼び出す基本的な構文を示す、いくつかのクイック スタートの最初の数値。 |
| [チュートリアル: データ サイエンティスト向けデータベース内の R 分析について説明します](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md) | R の開発者は新しい SQL Server に、このチュートリアルで説明します共通のデータ サイエンスのタスクでは、SQL Server へ実行する方法。 読み込むとデータを視覚化して、トレーニングし、SQL サーバーにモデルを保存および予測分析モデルを使用します。 |
| [チュートリアル: SQL 開発者向けのデータベース内の R 分析について説明します](../tutorials/sqldev-in-database-r-for-sql-developers.md) | ビルドおよび配置のみを使用して、完全な R ソリューション[!INCLUDE[tsql](../../includes/tsql-md.md)]ツール。 運用環境にソリューションを移動することに注目します。 ストアド プロシージャに R コードをラップし、R モデルを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに保存し、パラメーター化された呼び出しを R モデルに行い、予測を実行する方法について学習します。 |
| [チュートリアル: RevoScalepR deep dive](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) | RevoScaleR パッケージの関数を使用する方法について説明します。 R と SQL Server、およびスイッチ間でデータの移動は、特定のタスクに合わせてコンテキストを計算します。 モデルとプロットを作成し、開発環境とデータベース サーバーの間で移動します。 |

<a name ="bkmk_samples"></a>

## <a name="code-samples"></a>コード サンプル

| リンク | 説明 |
|------|-------------|
| [R と SQL Server を使用して予測モデルを構築します。](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction) | スキー レンタル ビジネスを予測する機械学習、今後のレンタルを今後の需要を満たすためには、ビジネスの計画と人員配置を一層使用方法について説明します。 |
| [顧客を実行する R と SQL Server を使用してクラスタ リング](https://microsoft.github.io/sql-ml-tutorials/R/customerclustering/) | 売上データに基づき顧客をセグメントの教師なし学習を使用します。 |

## <a name="see-also"></a>関連項目

+ [SQL Server に R 拡張機能](../concepts/extension-r.md)
+ [SQL Server Machine Learning Services のチュートリアル](machine-learning-services-tutorials.md)

