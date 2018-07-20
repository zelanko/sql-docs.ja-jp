---
title: T-SQL (SQL Server Machine Learning) の"Hello World"基本的な R コード実行のクイック スタート |Microsoft Docs
description: SQL Server で R スクリプトのこのクイック スタートでは、hello world の演習で sp_execute_external_script システム ストアド プロシージャの基本を学習します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 07/15/2018
ms.topic: quickstart
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: e738289b39f6d390bc4d6196606d242fa4803865
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39086885"
---
# <a name="quickstart-hello-world-r-script-in-sql-server"></a>SQL Server のクイック スタート:"Hello world"の R スクリプト 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server には、データベース内分析が常駐している SQL Server のデータでの R 言語機能のサポートが含まれています。 スケールで予測分析用のオープン ソース R 関数、サード パーティ製のパッケージおよび Microsoft R の組み込みパッケージを使用できます。

このクイック スタートでを"Hello World"R を実行して、主要な概念スクリプト inT SQL の概要を学習します、 **sp_execute_external_script**システム ストアド プロシージャ。 R スクリプトの実行では、ストアド プロシージャを使用します。 使用するか、 [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)ストアド プロシージャと R のパスでこのクイック スタートのとおり、入力パラメーターとしてスクリプトを作成またはで R スクリプトをラップする[カスタム ストアド プロシージャ](sqldev-in-database-r-for-sql-developers.md)します。 

## <a name="prerequisites"></a>前提条件

この演習では、既にインストールされている、次のいずれかの SQL Server のインスタンスへのアクセスが必要です。

+ [SQL Server 2017 Machine Learning Services](../install/sql-machine-learning-services-windows-install.md)、R 言語がインストールされています。
+ [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md)

  SQL Server インスタンスは、Azure の仮想マシンまたはオンプレミスにできます。 注意する必要がありますので、既定で外部のスクリプト機能は無効にされる[外部スクリプトを有効に](../install/sql-machine-learning-services-windows-install.md#bkmk_enableFeature)ことを確認します**SQL Server スタート パッド サービス**が実行されているは、開始する前にします。

+ SQL クエリを実行するためのツールです。 SQL Server データベースに接続して、T-SQL コードを実行できる任意のアプリケーションを使用することができます。 SQL のプロフェッショナルには、SQL Server Management Studio (SSMS) または Visual Studio を使用できます。

このチュートリアルで、SQL Server 内で R を実行するがいかに簡単かを表示したを使用して、新しい**Visual Studio Code 用 mssql 拡張機能**します。 VS Code は、Linux、macOS、または Windows を実行できる無料の開発環境です。 **Mssql**拡張子は、T-SQL クエリを実行するための軽量の拡張子。 Visual Studio Code を取得するには、[Visual Studio Code のダウンロードとインストール](https://code.visualstudio.com/Download)に関するページをご覧ください。 追加する、 **mssql**拡張機能では、この記事を参照してください: [Visual Studio Code 用 mssql 拡張機能を使用して](https://docs.microsoft.com/sql/linux/sql-server-linux-develop-use-vscode)します。

## <a name="connect-to-a-database-and-run-a-hello-world-test-script"></a>データベースに接続して Hello World テスト スクリプトを実行する

1. Visual Studio Code で新しいテキスト ファイルを作成し、BasicRSQL.sql という名前を付けます。

2. このファイルを開いているときに、Ctrl + Shift + P (macOS では COMMAND + P) を押し、「**sql**」と入力して SQL コマンドを一覧表示し、**[CONNECT]** を選択します。 Visual Studio Code では、特定のデータベースに接続するときに使用するプロファイルを作成するように求められます。 これは、省略可能ですが、データベースとログインの間の切り替えを簡単します。
    + サーバーまたは SQL Server で R がインストールされているインスタンスを選択します。
    + 新しいデータベースを作成する権限があるアカウントを使用し、SELECT ステートメントを実行して、テーブルの定義を表示します。

2. 接続が成功した場合は、サーバーとデータベース名が、現在の資格情報と共にステータス バーに表示されます。 接続に失敗した場合は、コンピューター名とサーバー名が正しいかどうかをご確認ください。

3. 次のステートメントを貼り付けて実行します。

    ```sql
    EXEC sp_execute_external_script
      @language =N'R',
      @script=N'OutputDataSet<-InputDataSet',
      @input_data_1 =N'SELECT 1 AS hello'
      WITH RESULT SETS (([Hello World] int));
    GO
    ```

このストアド プロシージャへの入力は次のとおりです。

+ *@language* パラメーターは、ここでは、R. を呼び出す言語拡張機能を定義します。
+ *@script* パラメーターは、R ランタイムに渡されるコマンドを定義します。 Unicode テキストとして、この引数で R スクリプト全体を囲む必要があります。 **nvarchar** 型の変数にテキストを追加して、その変数を呼び出すこともできます。
+ *@input_data_1* データ フレームとして SQL Server へデータを返す R ランタイムに渡される、クエリによってデータが返されます。
+ 句の結果セット列名として"Hello World"を追加する、SQL Server の返されたデータ テーブルのスキーマを定義します**int**データ型。

**結果**

![rsql_basictut_hello1](media/rsql-basictut-hello1.PNG)

このクエリからすべてのエラーが発生した場合のインストール問題を排除します。 インストール後の構成は、外部コード ライブラリの使用を有効にする必要があります。 参照してください[SQL Server 2017 の Machine Learning サービスをインストール](../install/sql-machine-learning-services-windows-install.md)または[SQL Server 2016 R Services のインストール](../install/sql-r-services-windows-install.md)します。同様に、スタート パッド サービスが実行されていることを確認します。 

環境によっては、SQL Server に接続するための R ワーカー アカウントの有効化、追加のネットワーク ライブラリのインストール、リモートでのコード実行の有効化、すべてを構成した後のインスタンスの再起動が必要な場合があります。 詳細については、次を参照してください[R Services のインストールとアップグレードに関する FAQ。](../r/upgrade-and-installation-faq-sql-server-r-services.md)

> [!TIP]
> Visual Studio Code で、実行するコードをハイライト表示し、Ctrl + Shift + E を押すことができます。 覚えにくい場合は変更できます。 [ショートカット キー バインディングのカスタマイズ](https://github.com/Microsoft/vscode-mssql/wiki/customize-shortcuts)に関する記事をご覧ください。
> 
> ![rsql-basictut_hello1code](media/rsql-basictut-hello1code.PNG)
> 

## <a name="next-steps"></a>次のステップ

インスタンスが R を使用する準備が確認した後、これで、詳しく見て入力と出力を構成します。

> [!div class="nextstepaction"]
> [クイック スタート: 入力と出力を処理します。](rtsql-working-with-inputs-and-outputs.md)
