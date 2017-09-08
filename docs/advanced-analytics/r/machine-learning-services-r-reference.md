---
title: "SQL Server の Machine Learning のサービスの API リファレンス |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/31/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1c776c43d66d01a2f721b5d3d8bc540741bf8b13
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---

# <a name="api-reference-for-sql-server-machine-learning-services"></a>SQL Server の Machine Learning のサービスの API リファレンス

この記事では、機械学習の SQL Server で使用される Api に関するリファレンス ドキュメントへのリンクを提供します。 

**適用されます:** SQL Server 2016 の R Services、SQL Server 2017 機械学習のサービス

ほとんどの場合、SQL Server は、Microsoft R Server と Microsoft Machine Learning のサーバーに用意されている同じ R、Python ライブラリを使用します。 

> [!NOTE]
> すべての Api のドキュメントでは、ソース コードからは派生し、編集した後ではありません。

## <a name="r"></a>R

+ [RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler)

    リモート計算コンテキストと複数のデータ ソースをサポートするスケーラブルなアルゴリズムです。

+ [MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package)

    アルゴリズムと変換の学習 R. 必要 RevoScaleR の高速でスケーラブルなマシンです。

+ [olapR](https://docs.microsoft.com/r-server/r-reference/olapr/olapr)

   OLAP データ ソースのスキーマを読み込んで、MDX クエリを実行します。

+ [sqlrutils](https://docs.microsoft.com/r-server/r-reference/sqlrutils/sqlrutils)

    R コードから適切な形式のストアド プロシージャを生成するためのヘルパー関数です。

+ [mrsdeploy](https://docs.microsoft.com/r-server/r-reference/mrsdeploy/mrsdeploy-package)

   コンソール アプリケーションでリモート セッションを確立するため、発行および R または Python コードを使用する web サービスを管理する機能です。

## <a name="python"></a>Python

+ [revoscalepy](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package)

    RevoScaleR パッケージを R 言語用の Python と同じです。 同じ計算コンテキストとデータ ソースをサポートしています。

+ [Python の Microsoftml](https://docs.microsoft.com/r-server/python-reference/microsoftml/microsoftml-package)

    MicrosoftML の Python と同等では、R. サポート用パッケージの同じ計算コンテキストと、データ ソースと、高速、スケーラブルなアルゴリズムと Microsoft からの変換が含まれています。

## <a name="related-apis"></a>関連する Api

+ [RevoPEMAR 関数リファレンス](https://docs.microsoft.com/r-server/r-reference/revopemar/pemar)

    並列アルゴリズムの開発をサポートしています

+ [RevoUtils](https://docs.microsoft.com/r-server/r-reference/revoutils/revoutils)

    RevoScaleR 環境で使用するためのユーティリティ関数

## <a name="other"></a>その他

「方法」トピック、およびこれらの R または SQL Server での Python Api を使用する特定の概要を参照してください。

+ [SQL Server を使用するための scaleR 関数](scaler-functions-for-working-with-sql-server-data.md)
+ [Sqlrutils を使用してストアド プロシージャを生成します。](generating-an-r-stored-procedure-for-r-code-using-the-sqlrutils-package.md)
+ [OlapR を使用して R に MDX データの読み取り](how-to-create-mdx-queries-using-olapr.md)

