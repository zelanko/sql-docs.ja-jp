---
title: SQL Server の Python チュートリアル |Microsoft ドキュメント
titleSuffix: SQL Server
ms.custom: ''
ms.date: 03/06/2018
ms.reviewer: ''
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: tutorial
applies_to:
- SQL Server 2017
dev_langs:
- Python
ms.author: heidist
author: HeidiSteen
manager: cgronlun
ms.openlocfilehash: 690d27faac3fff53c72abc80690899117d8ea9ce
ms.sourcegitcommit: 059fc64ba858ea2adaad2db39f306a8bff9649c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/04/2018
---
# <a name="sql-server-python-tutorials"></a>SQL Server の Python のチュートリアル
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

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

   このレッスンでは、どのようにコードを実行できる、リモートの Python ターミナルから SQL Server のコンピューティング コンテキストを使用してを示しています。 Python tools および環境をある程度理解してください。 サンプル コードを使用してモデルを作成する提供**rxLinMod**、新しいから**revoscalepy**ライブラリです。 

+ [SQL 開発者のためのデータベースでの Python の分析](sqldev-in-database-python-for-sql-developers.md)

    このエンド ツー エンド チュートリアルでは、T-SQL ストアド プロシージャを使用して完全な Python ソリューションを構築するプロセスを示します。 すべての Python コードが含まれます。


## <a name="python-samples"></a>Python のサンプル

これらのサンプルと SQL Server 開発チームによって提供されるデモは、実際のアプリケーションに埋め込まれた分析を使用する方法を選択します。

+ [Python および SQL Server を使用して予測モデルを構築します。](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/)

  Ski レンタル ビジネス可能性がありますの機械学習を将来のレンタルを予測するのに役立つ、今後の要求を満たすには、ビジネス プランとスタッフを使用する方法について説明します。

  > [!TIP]
  > Python モデルからネイティブのスコアが含まれています。

+ [顧客を実行する Python と SQL Server を使用してクラスタ リング](https://microsoft.github.io/sql-ml-tutorials/python/customerclustering/)

    Kmeans アルゴリズムを使用して、顧客の監視対象外のクラスタ リングを実行する方法を説明します。

## <a name="bkmk_Prerequisites"></a>前提条件

これらのチュートリアルを使用する SQL Server の 2017 が必要と明示的にインストールし、Machine Learning Services (In-database)、この機能を有効にする必要があります。 

SQL Server 2017 が R、Python の両方の言語をサポートしますが、どちらをインストールまたは既定で有効にします。 Python を実行するには、extensibility framework を有効にして、Python をインストールする言語として選択する必要があります。 

### <a name="post-installation-configuration-tips"></a>インストール後の構成のヒント

SQL Server セットアップを実行した後は、Python と SQL Server が通信していることを確認する追加の手順を実行する必要があります。

+ 実行して、外部スクリプト実行機能を有効にする`sp_configure 'external scripts enabled', 1`です。
+ サーバーを再起動します。 
+ 開く、 **Services**パネルをスタート パッドが開始されているかどうかを確認します。 
+ 外部のランタイムを呼び出して、サービスが必要な権限を持っていることを確認します。 詳細については、次を参照してください。[黙示的な認証を有効にする](../r/add-sqlrusergroup-to-database.md)です。
+ SQL Server のファイアウォールでポートを開くし、必要なネットワーク プロトコルを有効にします。
+ SQL ログインまたは Windows ユーザー アカウントが、データを読み取ると、このサンプルで必要なすべてのデータベース オブジェクトを作成するのには、サーバーに接続するために必要な権限を持っていることを確認します。

一般的な問題は、この資料を参照してください: [Machine Learning のサービスのトラブルシューティング](../machine-learning-troubleshooting-faq.md)

### <a name="resource-management"></a>リソース管理

同じコンピューターに R、Python の両方をインストールすることができますが、両方の操作を実行している多くのリソースを要求できます。 「メモリ不足」エラーが発生する場合、または、プリンシパル サーバーを使用するためのものでは、machine learning のジョブを実行する場合は、データベース エンジンに割り当てられているメモリの量を減らすことができます。 詳細については、次を参照してください。 [Managing and monitoring SQL Server での Python](../python/managing-and-monitoring-python-solutions.md)です。

## <a name="see-also"></a>参照

[SQL Server の R チュートリアル](sql-server-r-tutorials.md)
