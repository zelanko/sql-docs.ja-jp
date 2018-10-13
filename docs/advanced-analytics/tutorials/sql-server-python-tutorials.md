---
title: SQL Server の Python のチュートリアル |Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 541675c22ddbe347f67119d8cba82f75955382e6
ms.sourcegitcommit: ce4b39bf88c9a423ff240a7e3ac840a532c6fcae
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/09/2018
ms.locfileid: "48877986"
---
# <a name="sql-server-python-tutorials"></a>SQL Server の Python のチュートリアル
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、チュートリアル、SQL Server 2017 での Python の使用を示すサンプルの一覧を示します。 これらのサンプルとデモを学びます。

+ T-SQL から Python を実行する方法
+ リモートとローカルの計算コンテキスト、および SQL Server コンピューターを使用して Python コードを実行する方法とは
+ ストアド プロシージャで Python コードをラップする方法
+ SQL の運用環境用の Python コードの最適化
+ アプリケーションでの機械学習を埋め込むための実際のシナリオ

要件とセットアップについては、次を参照してください。[の前提条件](#bkmk_Prerequisites)します。

## <a name="bkmk_pythontutorials"></a>Python のチュートリアル

+ [T-SQL で Python を実行](run-python-using-t-sql.md)

   SQL Server 2016 で他社に先駆けて機能拡張メカニズムを使用して、T-SQL で Python を呼び出す方法の基本について説明します。

+ [Machine learning で revoscalepy を使用して Python のモデルの作成します。](use-python-revoscalepy-to-create-model.md)

   このレッスンを実行する方法のコード、リモートの Python ターミナルから SQL Server コンピューティング コンテキストを使用してを示します。 Python ツールと環境についての知識があります。 サンプル コードを使用してモデルを作成する提供**rxLinMod**、新しい**revoscalepy**ライブラリ。 

+ [SQL 開発者向けの In-database Python 分析](sqldev-in-database-python-for-sql-developers.md)

    このエンド ツー エンド チュートリアルでは、T-SQL ストアド プロシージャを使用して完全な Python ソリューションを構築するプロセスについて説明します。 すべての Python コードが含まれます。


## <a name="python-samples"></a>Python のサンプル

これらのサンプルとデモの SQL Server 開発チームによって提供されることは、実際のアプリケーションで埋め込み分析を使用する方法を選択します。

+ [Python と SQL Server を使用して予測モデルを構築します。](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/)

  スキー レンタル ビジネスを予測する機械学習、今後のレンタルを今後の需要を満たすためには、ビジネスの計画と人員配置を一層使用方法について説明します。

  > [!TIP]
  > Python のモデルからのネイティブ スコアリングが含まれています。

+ [顧客を実行する Python と SQL Server を使用してクラスタ リング](https://microsoft.github.io/sql-ml-tutorials/python/customerclustering/)

    K-平均法アルゴリズムを使用して、顧客の教師なしのクラスタ リングを実行する方法について説明します。

## <a name="bkmk_Prerequisites"></a>前提条件

これらのチュートリアルを使用するには SQL Server 2017 が必要と明示的にインストールし、機能、Machine Learning サービス (In-database) を有効にする必要があります。 

SQL Server 2017 は、R と Python の両方の言語をサポートしていますが、どちらもインストールされているか、既定で有効になっています。 Python を実行するにはの機能拡張フレームワークを有効にして、Python をインストールする言語として選択することが必要です。 

### <a name="post-installation-configuration-tips"></a>インストール後の構成のヒント

SQL Server セットアップを実行した後は、Python と SQL Server が通信していることを確認する追加の手順を実行する必要があります。

+ 実行して、外部スクリプト実行機能を有効にする`sp_configure 'external scripts enabled', 1`します。
+ サーバーを再起動します。 
+ 開く、**サービス**パネルをスタート パッドが開始されているかどうかを確認します。 
+ 外部ランタイムを呼び出して、サービスに必要なアクセス許可があることを確認します。 詳細については、次を参照してください。[暗黙の認証を有効にする](../security/add-sqlrusergroup-to-database.md)します。
+ SQL server のファイアウォールでポートを開くし、必要なネットワーク プロトコルを有効にします。
+ SQL ログインまたは Windows ユーザー アカウントがデータを読み取ると、このサンプルで必要なすべてのデータベース オブジェクトを作成する、サーバーへの接続に必要なアクセス許可を持つことを確認します。

一般的な問題は、この記事を参照してください: [Machine Learning サービスのトラブルシューティング](../machine-learning-troubleshooting-faq.md)

### <a name="resource-management"></a>リソース管理

同じコンピューターでは、R と Python の両方をインストールすることができますが、両方の操作を実行している多くのリソースを要求できます。 「メモリ不足」エラーが発生した場合、またはサーバーの使用目的をプリンシパルは、machine learning ジョブを実行している場合は、データベース エンジンに割り当てられているメモリの量を減らすことができます。 詳細については、次を参照してください。[の管理と監視の SQL Server での Python](../python/managing-and-monitoring-python-solutions.md)します。

## <a name="see-also"></a>関連項目

[SQL Server の R チュートリアル](sql-server-r-tutorials.md)
