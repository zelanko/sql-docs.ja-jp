---
title: "SQL Server の Python チュートリアル |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 08/29/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2017
dev_langs:
- Python
caps.latest.revision: 1
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b891cda72d5a69aafe461918674218fd3279c423
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="sql-server-python-tutorials"></a>SQL Server の Python のチュートリアル

この記事では、チュートリアルおよび SQL Server 2017 での Python の使用方法を示すサンプルの一覧を示します。 これらのサンプルとデモでは、学びます。

+ T-SQL から Python を実行する方法
+ リモートおよびローカルの計算コンテキスト、および SQL Server コンピューターを使用する Python コードを実行する方法とは
+ ストアド プロシージャでの Python コードをラップする方法
+ SQL の実稼働環境の Python コードを最適化します。
+ 機械学習をアプリケーションに埋め込むための実際のシナリオ

要件およびセットアップについては、次を参照してください。[の前提条件](#bkmk_Prerequisites)です。

## <a name="bkmk_pythontutorials"></a>Python のチュートリアル

+ [T-SQL で Python を実行しています。](run-python-using-t-sql.md)

   SQL Server 2016 を開拓機能拡張メカニズムを使用して、T-SQL で Python を呼び出す方法の基礎を説明します。

+ [機械学習 revoscalepy を使用して Python でモデルを作成します。](use-python-revoscalepy-to-create-model.md)

   使用してモデルを作成する**rxLinMod**、新しいから**revoscalepy**ライブラリです。 リモート Python ターミナルからのコードを起動しますが、SQL Server のコンピューティング コンテキストで、モデリングが行われます。

+ [Python (GitHub) の予測モデルを構築します。](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/machine-learning-services/python/getting-started/rental-prediction)

  Ski レンタル ビジネスの需要を予測する機械学習モデルを作成し、ストアド プロシージャを使用して日常的な需要予測のためには、そのモデルを使用できるようにします。 すべてのコードとデータが提供されています。

+ [SQL 開発者のためのデータベースでの Python の分析](sqldev-in-database-python-for-sql-developers.md)

  新機能！ T-SQL ストアド プロシージャを使用して完全な Python ソリューションをビルドします。 すべての Python コードが含まれます。

+ [展開および Python モデルを使用します。](..\python\publish-consume-python-code.md)

  Python を Microsoft Machine Learning のサーバーの最新バージョンを使用してモデルを展開する方法を説明します。

## <a name="python-samples"></a>Python のサンプル

これらのサンプルと SQL Server 開発チームによって提供されるデモは、実際のアプリケーションに埋め込まれた分析を使用する方法を選択します。

+ [Python および SQL Server を使用して予測モデルを構築します。](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/)

  Ski レンタル ビジネス可能性がありますの機械学習を将来のレンタルを予測するのに役立つ、今後の要求を満たすには、ビジネス プランとスタッフを使用する方法について説明します。

+ [新機能！顧客を実行する Python と SQL Server を使用してクラスタ リング](https://microsoft.github.io/sql-ml-tutorials/python/customerclustering/)

    Kmeans アルゴリズムを使用して、顧客の監視対象外のクラスタ リングを実行する方法を説明します。

## <a name="bkmk_Prerequisites"></a>前提条件

これらのチュートリアルを使用するには、SQL Server 2017 Machine Learning Services (In-database) をインストールする必要があります。 SQL Server 2017 は、R、または Python をサポートします。 ただし、機械学習をサポートする拡張機能フレームワークをインストールし、Python をインストールする言語として選択する必要があります。 同じコンピューターには、R、Python の両方をインストールできます。

> [!NOTE]
>
> Python のサポートは、SQL Server 2017 の新機能は、CTP 2.0 以降が必要です。 機能はリリース前と実稼働環境のサポートされていませんが、ご協力をお試しくださいフィードバックをお送りください。

**SQL Server 2017**

SQL Server セットアップを実行した後、これらの重要な手順を必ず。

+ 実行して、外部スクリプト実行機能を有効にします。`sp_configure 'external scripts enabled', 1`
+ サーバーの再起動
+ 外部のランタイムを呼び出して、サービスに必要なアクセス許可があることを確認します。
+ SQL ログインまたは Windows ユーザー アカウントが、データを読み取ると、このサンプルで必要なすべてのデータベース オブジェクトを作成するのには、サーバーに接続するために必要な権限を持つことを確認してください。

問題が実行する場合は、いくつかの一般的な問題には、この記事を参照してください: [Machine Learning のサービスのトラブルシューティング](../machine-learning-troubleshooting-faq.md)

## <a name="see-also"></a>参照

[SQL Server R チュートリアル](sql-server-r-tutorials.md)

