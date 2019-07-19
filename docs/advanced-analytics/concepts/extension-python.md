---
title: Python プログラミング言語の拡張機能 - SQL Server Machine Learning
description: Python コードが実行され、SQL Server 2017 Machine Learning Services での組み込みの Python ライブラリについて説明します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/05/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: abf7028c8b55f4f97770586f2a678a538f01b29a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67963038"
---
# <a name="python-language-extension-in-sql-server"></a>SQL Server での Python 言語の拡張機能
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Python 拡張機能は、SQL Server Machine Learning サービスにアドオンをリレーショナル データベース エンジンの一部です。 Python 実行環境、python、Python 3.5 ランタイムとインタープリター、標準ライブラリとツール、および Microsoft 製品のライブラリでの Anaconda ディストリビューションを追加します: [revoscalepy](../python/ref-py-revoscalepy.md)スケールと分析[microsoftml](../python/ref-py-microsoftml.md)マシン学習アルゴリズムです。 

として Python 統合がインストールされている[SQL Server Machine Learning Services](../what-is-sql-server-machine-learning.md)します。

Python 3.5 ランタイムおよびインタープリターのインストールでは、標準の Python ソリューションとのほぼ完全な互換性を確保します。 Python は、データベース操作が損なわれないことを保証するために、SQL Server から別のプロセスで実行されます。

## <a name="python-components"></a>Python コンポーネント

SQL Server には、オープン ソースの独自のパッケージが含まれています。 セットアップによってインストールされている Python ランタイムでは、Python 3.5 では、Anaconda 4.2 です。 Python ランタイムでは、SQL ツールとは別にインストールされているし、機能拡張フレームワークのコア エンジン プロセスの外部で実行されます。 Python を使用した Machine Learning サービスのインストールの一環として、GNU Public License の条項に同意する必要があります。 

SQL Server では、Python の実行可能ファイルは変更しませんが、そのバージョンが独自のパッケージをビルドしてテストする 1 つであるために、セットアップによってインストールされている Python のバージョンを使用する必要があります。 Anaconda ディストリビューションでサポートされているパッケージの一覧は、Continuum analytics サイトを参照してください。[パッケージ一覧の anaconda](https://docs.continuum.io/anaconda/packages/pkg-docs)します。

特定のデータベース エンジンのインスタンスに関連付けられた Anaconda ディストリビューションは、インスタンスに関連付けられたフォルダーにあります。 Machine Learning サービスと Python の既定のインスタンスに SQL Server 2017 データベース エンジンをインストールした場合の検索など、`C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES`します。

並列および分散ワークロード用に Microsoft によって追加された Python パッケージには、次のライブラリが含まれます。

| ライブラリ | 説明 |
|---------|-------------|
| [**revoscalepy**](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) | データ ソース オブジェクトとデータの探索、操作、変換、および視覚エフェクトをサポートしています。 など、さまざまなスケーラブルな機械学習モデルと同様に、リモート計算コンテキストの作成をサポート**rxLinMod**します。 詳細については、次を参照してください。 [revoscalepy モジュールは、SQL Server と](../python/ref-py-revoscalepy.md)します。  |
| [**microsoftml**](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) | 場合の速度と精度、最適化されているだけでなく行のテキストとイメージを操作するための変換を機械学習アルゴリズムが含まれています。 詳細については、次を参照してください。 [microsoftml モジュールは、SQL Server と](../python/ref-py-microsoftml.md)します。 |

Microsoftml と revoscalepy を密に結合します。microsoftml で使用されるデータ ソースは、revoscalepy オブジェクトとして定義されます。 Microsoftml の revoscalepy 転送コンテキストの制限事項を計算します。 つまり、すべての機能はローカルの操作に使用できるが、RxInSqlServer リモート コンピューティング コンテキストへの切り替えが必要です。

## <a name="using-python-in-sql-server"></a>SQL Server での Python の使用

インポートする、 **revoscalepy** 、Python コードとし、モジュールからの関数の呼び出しにモジュールなどの他の Python 関数。

サポートされているデータ ソースには、他のソースまたは R ソリューションのデータを交換するには、ODBC データベース、SQL Server、および XDF ファイル形式が含まれます。 Python 用の入力データを表形式にする必要があります。 形式ですべての Python の結果を返す必要がある、 **pandas**データ フレーム。

サポートされているコンピューティング コンテキストには、ローカルまたはリモートの SQL Server 計算コンテキストが含まれます。 1 台のコンピューター、ワークステーションなどで始まるコードが実行するリモート コンピューティング コンテキストがスクリプトのリモート コンピューターに実行し、スイッチです。 コンピューティング コンテキストを切り替えるには、両方のシステムは、同じ revoscalepy ライブラリである必要があります。

ローカル計算コンテキストは、T-SQL 内のコードで、データベース エンジンのインスタンスと同じサーバー上の Python コードの実行が含まれていますご想像のとおり、またはストアド プロシージャに埋め込まれています。 ローカルの Python IDE からコードを実行し、スクリプトが SQL Server コンピューターで実行される、リモートを定義することによって計算コンテキストもできます。

## <a name="execution-architecture"></a>実行のアーキテクチャ

次の図は、SQL Server コンポーネントのサポートされているシナリオでの Python のランタイムとの対話を示しています。 SQL Server のコンピューティング コンテキストを使用して、Python のターミナルからスクリプトでデータベースとリモートの実行を実行します。

### <a name="python-scripts-executed-in-database"></a>Python スクリプトの実行 (データベース内)

SQL Server の「内部」Python を実行すると、特殊なストアド プロシージャ内部での Python スクリプトをカプセル化する必要があります[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)します。

スクリプトは、ストアド プロシージャに埋め込まれたが、ストアド プロシージャを呼び出すと、任意のアプリケーションは、Python コードの実行を開始できます。  その後 SQL Server は、次の図に示すコードが実行を管理します。

![script-in-db-python](../../advanced-analytics/python/media/script-in-db-python2.png)

1. Python ランタイムの要求が、パラメーターで示される`@language='Python'`ストアド プロシージャに渡されます。 SQL Server では、この要求をスタート パッド サービスに送信します。
2. スタート パッド サービスが適切なランチャー; を開始します。この場合、PythonLauncher です。
3. PythonLauncher 外部 Python35 プロセスを開始します。
4. BxlServer は、Python ランタイム、データの交換と作業結果のストレージの管理を調整します。
5. SQL サテライトは、関連するタスクとプロセスを SQL Server の通信を管理します。
6. BxlServer は、SQL サテライトを使用して、状態と SQL Server に結果を通信します。
7. SQL Server では、結果を取得し、関連するタスクとプロセスを閉じます。

### <a name="python-scripts-executed-from-a-remote-client"></a>リモート クライアントから実行される Python スクリプト

ラップトップなどのリモート コンピューターから Python スクリプトを実行し、これらの条件が満たされる場合がある、SQl Server コンピューターのコンテキストで実行できます。

+ スクリプトを適切に設計します。
+ リモート コンピューターには、Machine Learning サービスで使用される拡張機能ライブラリがインストールされているがします。 [Revoscalepy](../python/ref-py-revoscalepy.md)パッケージは、リモート計算コンテキストを使用するために必要です。

次の図は、スクリプトがリモート コンピューターから送信されたときに、全体的なワークフローをまとめたものです。

![remote-sqlcc-from-python](../../advanced-analytics/python/media/remote-sqlcc-from-python3.png)

1. サポートされている関数の**revoscalepy**、Python ランタイムが呼び出すリンク関数が含まれ、よって BxlServer を呼び出します。
2. BxlServer は、Machine Learning サービス (In-database) に含まれているし、Python ランタイムから別のプロセスで実行されます。
3. BxlServer は接続先を決定し、Python スクリプトで接続文字列の一部として提供された資格情報を渡して、ODBC を使用して接続を開始します。
4. BxlServer は、SQL Server インスタンスへの接続を開きます。
5. 外部スクリプトの実行時が呼び出されると、さらに、適切なランチャーを開始するスタート パッド サービスが呼び出されます。: この場合、PythonLauncher.dll します。 その後、Python コードの処理は、Python コードは T-SQL のストアド プロシージャから呼び出されたときにするときと同様のワークフローで処理されます。
6. PythonLauncher では、SQL Server コンピューターにインストールされている Python のインスタンスへの呼び出しを実行します。
7. 結果が BxlServer に返されます。
8. SQL サテライトは、SQL Server と関連するジョブ オブジェクトのクリーンアップとの通信を管理します。
9. SQL Server は、クライアントに結果を渡します。

## <a name="see-also"></a>関連項目

+ [SQL Server で revoscalepy モジュール](../python/ref-py-revoscalepy.md)
+ [revoscalepy 関数リファレンス](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package) 
+ [SQL Server の機能拡張フレームワーク](extensibility-framework.md)
+ [R と SQL Server の拡張機能の学習](extension-r.md)