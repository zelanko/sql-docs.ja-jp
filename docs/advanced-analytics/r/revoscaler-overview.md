---
title: SQL Server の Machine Learning で RevoScaleR パッケージ |Microsoft ドキュメント
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: ecca127e3b929772c465ae7e1f694b525cc7dd00
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="revoscaler"></a>RevoScaleR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

RevoScaleR は、規模でデータ サイエンスをサポートするには、Microsoft によって提供される、machine learning 関数のパッケージです。

+ 関数は、データのインポート、データ変換、要約、ビジュアル化、および分析をサポートします。

+ _一度に_ファイル システムの操作の並列の非常に大規模なデータセットに対して実行され配布のことを意味します。 アルゴリズムは、チャンクを使用して、操作が完了した場合、戻した結果によって、メモリに収まり切らないデータセットを操作できます。

+ RevoScaleR は、オープン ソースの R 関数より多くの機能強化を提供します。 最も人気のある基本 R 関数の多くに対応する RevoScaleR 関数があります。 RevoScaleR 関数が示されて、 **rx**または**Rx**プレフィックスを識別しやすいようにします。

+ RevoScaleR は、分散データ サイエンス用のプラットフォームとして機能します。 最新のアルゴリズムでな RevoScaleR 計算コンテキストと変換を使用するなど、 [MicrosoftML](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-the-microsoftml-package)です。 使用することも[rxExec](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxexec)ベースの R 関数を並列に実行します。

アクションで RevoScaleR の例は、これらのブログを参照してください。 

+ [ビルドおよび R と SQL Server を使用して、予測モデルの配置](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction/)

+ [Machine Learning のサーバーで 1 秒あたりの 100万予測](https://blogs.msdn.microsoft.com/mlserver/2017/10/15/1-million-predictionssec-with-machine-learning-server-web-service/)

+ [MicrosoftML を使用してタクシー ヒントを予測します。](https://blogs.msdn.microsoft.com/microsoftrservertigerteam/2017/01/17/predicting-nyc-taxi-tips-using-microsoftml/)

+ [RxExec によるパフォーマンスの最適化](https://blogs.msdn.microsoft.com/microsoftrservertigerteam/2016/11/14/performance-optimization-when-using-rxexec-to-parallelize-algorithms/)

## <a name="how-to-get-revoscaler"></a>RevoScaleR を取得する方法

R の RevoScaleR パッケージは、Microsoft R クライアントに無料でインストールされます。 Machine Learning のサーバーまたは SQL Server で R を使用した場合は、既定では RevoScaleR が含まれています。

Python を使用している場合、 [revoscalepy](../python/what-is-revoscalepy.md)パッケージは同等の機能を提供します。

> [!IMPORTANT]
> RevoScaleR パッケージをダウンロードまたは製品およびそれを提供するサービスとは無関係に使用されることはできません。

## <a name="use-revoscaler-in-sql-server"></a>RevoScaleR を SQL Server を使用します。

これらのチュートリアルとサンプルは、RevoScaleR 関数を使用して、SQL Server からデータを取得、モデルを構築およびスコアリングのためデータベースにモデルを保存する方法をデモンストレーションします。

+ [コンピューティング コンテキストを使用する方法を学習します。](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)
+ [SQL 開発者のための R: トレーニング モデルを使用できるように、](../tutorials/sqldev-in-database-r-for-sql-developers.md)
+ [GitHub の Microsoft の製品サンプル](https://github.com/Microsoft/SQL-Server-R-Services-Samples)

## <a name="learn-more-about-revoscaler"></a>RevoScaleR に関する詳細します。

これらのチュートリアルでサポートされている他のコンピューティング コンテキストで RevoScaleR の使用例を示します[Machine Learning サーバー](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server)、Hadoop などです。

+ [RevoScaleR とは何ですか。](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-revoscaler)

+ [関数が 25 で RevoScaleR を調べる](https://docs.microsoft.com/machine-learning-server/r/tutorial-r-to-revoscaler)

+ [RevoScaleR パッケージの参照](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler)

