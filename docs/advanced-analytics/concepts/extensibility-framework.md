---
title: R 言語と Python スクリプト - SQL Server Machine Learning の機能拡張アーキテクチャ
description: デュアル アーキテクチャ リレーショナル データを R と Python スクリプトを実行するために、SQL Server データベース エンジンの外部コードのサポート。
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/17/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 3d4d8108fda500d48425abfb52fd9f72c6faa147
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67963058"
---
# <a name="extensibility-architecture-in-sql-server-machine-learning-services"></a>SQL Server Machine Learning Services で拡張可能アーキテクチャ 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server では、サーバー上の R や Python などの外部のスクリプトを実行するため、機能拡張フレームワークがあります。 スクリプトは、中核となるデータベース エンジンの拡張機能としては、言語のランタイム環境で実行されます。 

## <a name="background"></a>背景情報

機能拡張フレームワークは、R ランタイムをサポートするために SQL Server 2016 で導入されました。 SQL Server 2017 には、Python のサポートが追加されます。

機能拡張フレームワークの目的は、SQL Server と R、Python、移動のデータ サイエンス ソリューションを運用環境とデータの保護には、開発中に公開されている場合は、摩擦を軽減などのデータ サイエンスの言語間のインターフェイスを提供するにはプロセスです。 SQL Server によって管理されるセキュリティで保護されたフレームワーク内で信頼できるスクリプト言語を実行することによって、データベース管理者はデータ サイエンティストのエンタープライズ データへのアクセスを許可するときにセキュリティを維持できます。

次の図は、視覚的に、営業案件と拡張可能なアーキテクチャの利点について説明します。

  ![SQL Server との統合の目標](../media/ml-service-value-add.png "Machine Learning サービスの値の追加")

ストアド プロシージャを呼び出すことによって、R または Python スクリプトを実行することができ、結果が表形式の結果として、SQL Server に直接簡単に生成または SQL クエリを送信し、結果を処理する任意のアプリケーションからの machine learning を使用します。

+ 外部スクリプトの実行が SQL Server データのセキュリティの対象外部スクリプトを実行しているユーザーが同じように、SQL クエリで使用できるデータにのみアクセスことができます。 クエリでは、十分なアクセス許可のため失敗した場合、同じユーザーによって実行されるスクリプトも同じ理由で失敗します。 テーブル、データベース、およびインスタンス レベルでは、SQL Server のセキュリティが適用されます。 データベース管理者は、ユーザーのアクセス、外部のスクリプトで使用されるリソースと外部コード ライブラリが追加されたサーバーを管理できます。  

+ スケールと最適化の機会が 2 つのベースを準備: データベース プラットフォームの向上 (列ストア インデックス、[リソース ガバナンス](../../advanced-analytics/r/resource-governance-for-r-services.md))、およびデータを R および Python 用の Microsoft ライブラリを使用する場合、拡張機能に固有の向上サイエンス モデル。 R では、シングル スレッド、RevoScaleR 関数はマルチ スレッド、複数のコアにワークロードを分散することです。

+ 配置で SQL Server の方法論を使用して: 外部スクリプトをラップするストアド プロシージャ、埋め込まれた SQL、または T-SQL クエリなどをサーバーで予測モデルの結果の保存を返す予測関数を呼び出す。

+ R と Python の開発者には、特定のツールと Ide のスキルがこれらのツールでコードを記述し、SQL Server にコードを移植が確立されています。

## <a name="architecture-diagram"></a>アーキテクチャ図

アーキテクチャでは、外部スクリプトは、データと SQL Server での操作の要求のチェーンを内部的に管理するコンポーネントでは、SQL Server から別のプロセスで実行するよう設計されています。 R と Python、SQL Server のバージョンによってサポートされている言語の拡張機能が含まれます。 

  ![コンポーネント アーキテクチャ](../media/generic-architecture.png "コンポーネント アーキテクチャ")

コンポーネントが含まれます、**スタート パッド**言語固有のランチャー (R または Python) の言語およびインタープリターとライブラリを読み込むためのライブラリに固有のロジックを呼び出すために使用するサービス。 起動プログラムには、言語の実行時間と、独自のモジュールが読み込まれます。 たとえば、コードには、RevoScaleR 関数が含まれている場合 RevoScaleR インタープリターが読み込まれます。 **BxlServer**と**SQL サテライト**SQL Server との通信やデータの転送を管理します。

<a name="launchpad"></a>

## <a name="launchpad"></a>スタート パッド

[!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]は管理し、フルテキスト インデックス作成とクエリ サービスが、フルテキスト クエリを処理するための別のホストを起動するのと同様に、外部のスクリプトを実行するサービスです。 スタート パッド サービスには、信頼済みのランチャーには、Microsoft によって公開されているか、パフォーマンスとリソース管理の要件を満たすとしてマイクロソフトによって認定されたを開始できます。

| 信頼済みランチャー | 拡張子 | SQL Server のバージョン |
|-------------------|-----------|---------------------|
| R 言語の RLauncher.dll | [R の拡張機能](extension-r.md) | SQL Server 2016、SQL Server 2017 |
| Python 3.5 用 Pythonlauncher.dll | [Python 拡張機能](extension-python.md) | SQL Server 2017 |

[!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] サービスは、独自のユーザー アカウント下で実行されます。 スタート パッドを実行するアカウントを変更する場合は、そのファイルへの変更を書き込むことを確認する SQL Server 構成マネージャーを使用して関連するために必ず。

個別の[!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]SQL Server Machine Learning サービスを追加した各データベース エンジン インスタンスのサービスを作成します。 1 つのスタート パッドがあるため、それぞれのスタート パッド サービスがある外部スクリプトのサポートの複数のインスタンスがあれば、各データベース エンジン インスタンスのサービスです。 データベース エンジンのインスタンスは、スタート パッド サービスの作成にバインドされます。 ストアド プロシージャの外部のスクリプトまたは SQL Server サービスが、同じインスタンスに対して作成されたスタート パッド サービスの呼び出しで T-SQL の結果のすべての呼び出し。

サポートされている特定の言語でタスクを実行するには、は、スタート パッドは、プールからセキュリティで保護されたワーカー アカウントを取得し、外部ランタイムを管理するサテライト プロセスを開始します。 各サテライト プロセスは、スタート パッドのユーザー アカウントを継承し、スクリプトの実行時間のワーカー アカウントを使用します。 スクリプトは、並列処理を使用している場合は、同じ、1 つのワーカー アカウントが作成されます。

## <a name="bxlserver-and-sql-satellite"></a>BxlServer と SQL サテライト

**BxlServer**は SQL Server と Python または R. 間の通信を管理する Microsoft によって提供される実行可能ファイル外部スクリプトのセッション、各外部スクリプト ジョブのセキュアな作業フォルダーをプロビジョニングを含めるために使用して、SQL サテライトを使用して、外部のランタイムと SQL Server 間のデータ転送を管理する Windows ジョブ オブジェクトを作成します。 実行する場合[Process Explorer](https://technet.microsoft.com/sysinternals/processexplorer.aspx)ジョブの実行中に、BxlServer の 1 つまたは複数のインスタンスを参照してください可能性があります。

実際には、BxlServer は、実行時環境にタスクを管理するための SQL Server で動作する言語に対応します。 BXL はバイナリ交換言語の意味し、は SQL Server と外部プロセスの間でデータを効率的に移動するために使用するデータ形式を参照します。 BxlServer は、Microsoft R Client と Microsoft R Server などの関連製品の重要な部分もです。

**SQL サテライト**が外部コードをサポートする、SQL Server 2016 以降、データベース エンジンに含まれる、機能拡張 API または外部ランタイムの C または C++ を使用して実装します。

BxlServer は、次のタスクに SQL サテライトを使用します。

+ 入力データの読み取り
+ 出力データの書き込み
+ 入力引数の取得
+ 出力引数の書き込み
+ エラー処理
+ STDOUT と STDERR のクライアントへの書き戻し

SQL サテライトは、SQL Server と外部スクリプト言語間の高速データ転送に最適化されたカスタム データ形式を使用します。 型変換を実行し、SQL Server と外部スクリプトのランタイム間の通信中に入力と出力データセットのスキーマを定義します。

SQL サテライトは、windows の拡張イベント (Xevent) を使用して監視できます。 詳細については、次を参照してください。 [R の拡張イベント](../../advanced-analytics/r/extended-events-for-sql-server-r-services.md)と[Python の拡張イベント](../../advanced-analytics/python/extended-events-for-python.md)します。

## <a name="communication-channels-between-components"></a>コンポーネント間の通信チャネル

コンポーネントおよびデータ プラットフォーム間の通信プロトコルは、このセクションで説明します。

+ **TCP/IP**

  既定では、SQL Server と SQL サテライト間の内部通信は、TCP/IP を使用します。

+ **名前付きパイプ**

  BxlServer と SQL サテライトを通じた SQL Server 間の内部データ転送は、パフォーマンスを強化するために、専用の圧縮データ形式を使用します。 データは、名前付きパイプを使用して、BXL 形式で言語の実行時間と BxlServer 間で交換されます。

+ **ODBC**

  外部データ サイエンス クライアントとリモートの SQL Server インスタンス間の通信は、ODBC を使用します。 SQL server スクリプトのジョブを送信するアカウント インスタンスに接続し、外部スクリプトを実行するには、両方のアクセス許可が必要です。

  さらに、タスクによっては、アカウントは、これらのアクセス許可を必要があります。

  + ジョブで使用されるデータの読み取り
  + テーブルにデータを書き込むたとえば、ときに保存結果をテーブルに。
  + データベース オブジェクトを作成します。 たとえば、新しいストアド プロシージャの一部として外部スクリプトを保存しています。

  スクリプトから実行される、計算コンテキストとして SQL Server が使用される場合は、リモート クライアントの場合は、および実行可能ファイルは、外部ソースからデータを取得する必要があります、ODBC は書き戻しに使用します。 SQL Server では、現在のインスタンス上のユーザーの id に、リモート コマンドを発行したユーザーの id をマップし、そのユーザーの資格情報を使用して ODBC コマンドを実行します。 この ODBC 呼び出しを実行するために必要な接続文字列は、クライアント コードから取得されます。

+ **RODBC (R の場合のみ)** 

  追加の ODBC 呼び出しは、**RODBC** を使用してスクリプト内で実行できます。 RODBC はリレーショナル データベース内のデータにアクセスするための一般的な R パッケージです。ただし、そのパフォーマンスは、一般的に、SQL Server で使用される同等のプロバイダよりも低速です。 多くの R スクリプトでは、分析に使用する "セカンダリ" データセットを取得するために、RODBC への埋め込み呼び出しが使用されます。 たとえば、モデルをトレーニングするストアド プロシージャでは、モデル トレーニング用のデータを取得するために SQL クエリが定義される場合もありますが、追加要素を取得したり、検索を実行したり、テキスト ファイルや Excel などの外部ソースから新しいデータを取得する場合には、埋め込みの RODBC 呼び出しが使用されます。

  次のコードは、R スクリプトに埋め込まれた RODBC 呼び出しを示したものです。

    ```R
    library(RODBC);
    connStr <- paste("Driver=SQL Server;Server=", instance_name, ";Database=", database_name, ";Trusted_Connection=true;", sep="");
    dbhandle <- odbcDriverConnect(connStr)
    OutputDataSet <- sqlQuery(dbhandle, "select * from table_name");
    ```

+ **その他のプロトコル**

  "チャンク"単位で動作するか、リモート クライアントにデータを転送する必要があるプロセスで使用できますも、 [XDF ファイル形式](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-xdf)します。 実際のデータ転送は、エンコードされた blob 経由でです。

## <a name="see-also"></a>参照

+ [SQL Server での R 拡張機能](extension-r.md)
+ [SQL Server での Python 拡張機能](extension-python.md)