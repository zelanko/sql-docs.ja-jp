---
title: R コードを使用して、transact-sql (SQL のクイック スタートで R) |Microsoft ドキュメント
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: c11e2bba73cef8a8b6f59d5a92de22cddb19ccd9
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="using-r-code-in-transact-sql-r-in-sql-quickstart"></a>TRANSACT-SQL (SQL のクイック スタートで R) での R コードの使用
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

このチュートリアルでは、T-SQL ストアド プロシージャから R スクリプトを呼び出すための基本的なしくみを説明します。

**学習する内容**

+ T-SQL 関数に R を埋め込む方法
+ R と SQL データ型とデータの各オブジェクトを操作するためのヒント
+ 単純なモデルを作成し、SQL Server に保存する方法
+ 予測やモデルを使用して R プロットを作成する方法

**推定所要時間**

30 分 (セットアップを含まない)

## <a name="prerequisites"></a>前提条件

既にインストールされている、次のいずれかの SQL Server のインスタンスへのアクセスが必要です。

+ SQL Server 2017 マシン ラーニング サービス、インストールされている R 言語を使用
+ SQL Server 2016 R サービス

SQL Server のインスタンスは、Azure の仮想マシンまたは内部設置型にできます。 だけ、外部のスクリプト機能が無効である既定では、正常に動作させるための追加手順を実行する必要がありますので注意してください。

R スクリプトを含む SQL クエリを実行するには、データベースへの接続および T-SQL コードを実行できるその他のアプリケーションを使用できます。 SQL の専門家には、SQL Server Management Studio (SSMS) または Visual Studio を使用できます。

このチュートリアルでは、SQL Server の内部の R を実行するは簡単な方法を表示したを使用して、新しい**Visual Studio Code の mssql 拡張子**です。 VS Code は、Linux、macOS、または Windows を実行できる無料の開発環境です。 **Mssql**拡張子は、T-SQL クエリを実行するための軽量な拡張子です。 これをインストールするには、[Visual Studio Code 用の mssql 拡張機能の使用](https://docs.microsoft.com/sql/linux/sql-server-linux-develop-use-vscode)に関する記事をご覧ください。

## <a name="connect-to-a-database-and-run-a-hello-world-test-script"></a>データベースに接続して Hello World テスト スクリプトを実行する

1. Visual Studio Code で新しいテキスト ファイルを作成し、BasicRSQL.sql という名前を付けます。
2. このファイルを開いているときに、Ctrl + Shift + P (macOS では COMMAND + P) を押し、「**sql**」と入力して SQL コマンドを一覧表示し、**[CONNECT]** を選択します。 Visual Studio のコードでは、特定のデータベースに接続するときに使用するプロファイルを作成するように求められます。 これは、オプションですが、データベースとログインの間で切り替えるやすくなります。
    + サーバーまたは SQL Server で R がインストールされているインスタンスを選択します。
    + 新しいデータベースを作成する権限があるアカウントを使用し、SELECT ステートメントを実行して、テーブルの定義を表示します。
2. 接続が成功した場合は、サーバーとデータベース名が、現在の資格情報と共にステータス バーに表示されます。 接続に失敗した場合は、コンピューター名とサーバー名が正しいかどうかをご確認ください。
3. 次のステートメントを貼り付けて実行します。

    ```sql
    EXEC sp_execute_external_script
      @language =N'R',
      @script=N'OutputDataSet<-InputDataSet',
      @input_data_1 =N'SELECT 1 AS hello'
      WITH RESULT SETS (([hello] int not null));
    GO
    ```

    Visual Studio Code で、実行するコードをハイライト表示し、Ctrl + Shift + E を押すことができます。 覚えにくい場合は変更できます。 [ショートカット キー バインディングのカスタマイズ](https://github.com/Microsoft/vscode-mssql/wiki/customize-shortcuts)に関する記事をご覧ください。

    ![rsql-basictut_hello1code](media/rsql-basictut-hello1code.PNG)

**結果**

![rsql_basictut_hello1](media/rsql-basictut-hello1.PNG)

## <a name="troubleshooting"></a>トラブルシューティング

+ このクエリからエラーが発生した場合のインストールが完了できない可能性があります。 SQL Server セットアップ ウィザードを使用して機能を追加した後で、いくつかの追加手順を実行して外部コード ライブラリの使用を有効にする必要があります。  参照してください[Services の学習の SQL Server 2017 マシンをインストール](../install/sql-machine-learning-services-windows-install.md)または[SQL Server 2016 の R Services をインストール](../install/sql-r-services-windows-install.md)です。

+ スタート パッド サービスが実行されていることを確認します。 環境によっては、SQL Server に接続するための R ワーカー アカウントの有効化、追加のネットワーク ライブラリのインストール、リモートでのコード実行の有効化、すべてを構成した後のインスタンスの再起動が必要な場合があります。 [R Services のインストールとアップグレードについての FAQ](../r/upgrade-and-installation-faq-sql-server-r-services.md) に関する記事をご覧ください

+ Visual Studio Code を取得するには、[Visual Studio Code のダウンロードとインストール](https://code.visualstudio.com/Download)に関するページをご覧ください。

## <a name="next-lesson"></a>次のレッスン

これで、インスタンスを R を使用する準備ができて、始めましょう。

レッスン 1:[入力と出力の使用](rtsql-working-with-inputs-and-outputs.md)

レッスン 2: [R と SQL のデータ型とデータ オブジェクト](rtsql-r-and-sql-data-types-and-data-objects.md)

レッスン 3: [SQL Server データを R を使用する関数](rtsql-using-r-functions-with-sql-server-data.md)

レッスン 4:[予測モデルの作成](rtsql-create-a-predictive-model-r.md)

レッスン 5:[予測し、モデルからプロット](rtsql-predict-and-plot-from-model.md)
