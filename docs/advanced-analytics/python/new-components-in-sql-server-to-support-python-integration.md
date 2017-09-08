---
title: "SQL Server での Python 統合コンポーネント |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/20/2017
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
ms.openlocfilehash: 07f8e18b4481b2773f3ac16cdea08c27feff1ba3
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="components-in-sql-server-to-support-python-integration"></a>Python の統合をサポートするために SQL Server のコンポーネント

SQL Server 2017 以降は、Machine Learning のサービスは、T-SQL から実行できるまたはリモート計算コンテキストとして SQL Server を使用して実行する外部の言語としての Python をサポートします。

ここでは、一般に拡張性をサポートする SQL Server 2017 および Python 言語でのコンポーネントを具体的に説明します。

## <a name="sql-server-components-and-providers"></a>SQL Server コンポーネントおよびプロバイダー

Python スクリプトの実行を許可する SQL Server 2017 を構成するのにはの複数の手順を実行します。

1. 拡張機能をインストールします。
2. 外部スクリプト実行機能を有効にします。
3. データベース エンジン サービスを再起動します。

追加の手順は、リモート スクリプトの実行をサポートする必要があります。

詳細については、次を参照してください[Machine Learning のサービスの設定。](setup-python-machine-learning-services.md)

### <a name="launchpad"></a>スタート パッド

SQL Server の信頼されたスタート パッドは、サービスを管理し、フルテキスト インデックス作成とクエリ サービスが、フルテキスト クエリを処理するため、独立したホストを起動する場合と同様に、外部のスクリプトを実行する SQL Server 2016 で導入されました。

スタート パッド サービスには、Microsoft によってパブリッシュされているかは Microsoft によってパフォーマンスとリソース管理の要件を満たすとして認定されている信頼されたランチャーのみを開始できます。

+ SQL Server 2017 R および Python 3.5 をサポートしています
+ SQL Server 2016 は、R をサポートしています。

[!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] サービスは、独自のユーザー アカウント下で実行されます。

> [!TIP]
> スタート パッドを実行するアカウントを変更する場合は、関連するファイルに変更が書き込まれることを確認する SQL Server 構成マネージャーを使用してこれを行うに必ずです。

特定のサポートされている言語で、タスクを実行するには、スタート パッドは、プールからワーカーをセキュリティで保護されたアカウントを取得し、外部のランタイムを管理するサテライト プロセスを開始します。

+ R 言語の RLauncher.dll
+ Python 3.5 の Pythonlauncher.dll

各サテライト プロセスは、スタート パッドのユーザー アカウントを継承し、スクリプトの実行中のワーカー アカウントを使用します。 Python スクリプトは、並列処理を使用している場合は、同じ、1 つのワーカー アカウントが作成されます。

スタート パッドのセキュリティ コンテキストの詳細については、次を参照してください。[セキュリティ](security-overview-sql-server-python-services.md)です。

### <a name="bxlserver-and-sql-satellite"></a>BxlServer と SQL サテライト

実行する場合[プロセス エクスプ ローラー](https://technet.microsoft.com/sysinternals/processexplorer.aspx) Python ジョブの実行中に、BxlServer の 1 つまたは複数のインスタンスを参照してください可能性があります。

**BxlServer**間の通信を管理する Microsoft によって提供される実行可能ファイルは、[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]および Python (R) します。 外部スクリプト セッション、各ジョブの外部のスクリプトの作業フォルダーはセキュリティで保護された規定を格納するための外部のランタイム間のデータ転送を管理する SQL サテライトを使用して Windows ジョブ オブジェクトを作成し、[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]です。

BxlServer で動作する Python に対応するは、実際には、[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]データの転送タスクおよび管理します。 BXL はバイナリ交換言語の略し、SQL Server と外部プロセス間でデータを効率的に移動するためのデータ形式を参照します。 BxlServer も Microsoft R Client および Microsoft R サーバーの重要な部分です。

**SQL サテライト**が外部コードをサポートする、SQL Server 2016 以降で、データベース エンジンに含まれる機能拡張 API または外部のランタイム C または C++ を使用して実装します。

BxlServer は、次のタスクに SQL サテライトを使用します。

+ 入力データの読み取り
+ 出力データの書き込み
+ 入力引数の取得
+ 出力引数の書き込み
+ エラー処理
+ STDOUT と STDERR のクライアントへの書き戻し

SQL サテライト間で高速なデータを転送用に最適化されたカスタム データ形式を使用して[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]と外部のスクリプト言語です。 型変換を実行し、間の通信中に入力と出力データセットのスキーマを定義[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]と外部スクリプトの実行時。

SQL サテライトは、windows の拡張イベント (Xevent) を使用して監視できます。 詳細については、次を参照してください。 [R の拡張イベント](../../advanced-analytics/r/extended-events-for-sql-server-r-services.md)です。

## <a name="communication-channels-between-components"></a>コンポーネント間の通信チャネル

+ **TCP/IP**

  既定では、間の内部通信[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]SQL サテライト TCP/IP を使用するとします。

+ **名前付きパイプ**

  SQL サテライトを通じた BxlServer と [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 間の内部データ転送では、パフォーマンスを強化するために、専用の圧縮データ形式が使用されます。 データは、名前付きパイプを使用して、BXL 形式での Python と BxlServer 間で交換されます。

+ **ODBC**

  外部データ サイエンス クライアント間の通信、および[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]インスタンスは、ODBC を使用します。 スクリプトが送信するアカウントのジョブを[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]インスタンスに接続し、外部スクリプトを実行するには、両方のアクセス許可を持つ必要があります。

  さらに、タスクによっては、アカウントは、これらのアクセス許可を必要があります。

  + ジョブによって使用されるデータの読み取り
  + テーブルにデータを書き込むたとえば、と保存の結果をテーブル。
  + データベース オブジェクトを作成します。 新しいストアド プロシージャの一部として外部スクリプトを保存する場合などです。

  ときに[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]がリモート クライアントから Python スクリプトを実行し、Python の実行可能ファイルは、外部ソースからデータを取得する必要があります、コンピューティング コンテキストとして使用して、ODBC が書き戻しに使用します。 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]現在のインスタンスでは、ユーザーの id に、リモート コマンドを発行するユーザーの id をマップし、そのユーザーの資格情報を使用して、ODBC コマンドを実行します。 この ODBC 呼び出しを実行するために必要な接続文字列は、クライアント コードから取得されます。

## <a name="interaction-of-components"></a>コンポーネントの相互作用

次の図は、Python ランタイムでサポートされるシナリオの各と SQL Server コンポーネントの相互作用を表している: SQL Server のコンピューティング コンテキストを使用して、Python 端末からスクリプトのデータベース内、およびリモートの実行を実行します。

### <a name="python-scripts-executed-in-database"></a>Python スクリプト データベース内の実行

「内部」Python を実行すると[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]、特殊なストアド プロシージャ内の Python スクリプトをカプセル化する必要があります[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)です。

ストアド プロシージャに埋め込まれたスクリプト、ストアド プロシージャを呼び出すと、すべてのアプリケーションは、Python コードの実行を開始できます。  その後[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]の次の図に示すように、コードの実行を管理します。

![スクリプトで db python](../../advanced-analytics/python/media/script-in-db-python.png)

1. Python ランタイムの要求が、パラメーターで示される _@language= 'Python'_ストアド プロシージャに渡されます。 SQL Server では、スタート パッド サービスにこの要求を送信します。
2. スタート パッド サービスの開始、適切なランチャーです。この場合、PythonLauncher です。
3. PythonLauncher は、Python35 の外部プロセスを開始します。
4. BxlServer は、データの交換と作業の結果のストレージを管理する Python ランタイムと連携します。
5. SQL サテライト関連のタスクについての通信を管理および処理し、[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]です。
6. BxlServer が SQL サテライトを使用して状態を通信し、結果を [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] に送信します。
7. [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] が結果を取得し、関連するタスクとプロセスを終了します。

### <a name="python-scripts-executed-from-a-remote-client"></a>リモート クライアントから実行された Python スクリプト

ラップトップなどのリモート コンピューターから Python スクリプトを実行し、これらの条件が満たされる場合がある SQl Server コンピューターのコンテキストで実行したりできます。

+ スクリプトを適切にデザインします。
+ リモート コンピューターには、Machine Learning サービスによって使用されている機能拡張ライブラリがインストールされています。

次の図は、スクリプトがリモート コンピューターから送信されるときに、全体的なワークフローをまとめたものです。

![リモート sqlcc から python](../../advanced-analytics/python/media/remote-sqlcc-from-python2.png)

1. サポートされている関数の**revoscalepy**、Python ランタイムは BxlServer を呼び出し、リンクの関数を呼び出します。
2. BxlServer では、Machine Learning Services (In-database) に含まれてし、Python ランタイムから別のプロセスで実行します。
3. BxlServer では、接続のターゲットを決定し、Python スクリプト内の接続文字列の一部として提供された資格情報を渡して、ODBC を使用して接続を開始します。
4. BxlServer が [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] インスタンスへの接続を開きます。
5. 外部のスクリプトの実行時が呼び出されると、スタート パッド サービスが呼び出され、さらに、適切なランチャーが開始する: この場合、PythonLauncher.dll です。 その後、Python コードの処理は、T-SQL でストアド プロシージャから Python コードが呼び出されたときにするときと同様、ワークフローで処理されます。
6. PythonLauncher にインストールされている Python のインスタンスへの呼び出しを行い、[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]コンピューター。
7. 結果が BxlServer に返されます。
8. SQL サテライトは、[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] との通信と、関連するジョブ オブジェクトのクリーンアップを管理します。
9. [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] がクライアントに結果を返します。

## <a name="next-steps"></a>次の手順

[SQL Server での Python のアーキテクチャの概要](architecture-overview-sql-server-python.md)
