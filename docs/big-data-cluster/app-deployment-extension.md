---
title: アプリ展開の拡張機能
titleSuffix: SQL Server 2019 big data clusters
description: SQL Server 2019 ビッグ データ クラスター (プレビュー) でアプリケーションとしては、Python または R スクリプトを展開します。
author: TheBharath
ms.author: bharaths
manager: craigg
ms.date: 02/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 761818cd83df5db38b3877184b03b7e5d634aa63
ms.sourcegitcommit: 1c1ed8d6aa2fb9fceb6a00c39597578442f7f4e9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/21/2019
ms.locfileid: "58222026"
---
# <a name="how-to-use-vs-code-to-deploy-applications-to-sql-server-big-data-clusters"></a>VS Code を使用してビッグ データの SQL Server クラスターにアプリケーションを展開する方法

この記事では、Visual Studio Code を使用して、アプリのデプロイの拡張機能で SQL Server のビッグ データ クラスターにアプリケーションを展開する方法について説明します。 この機能は、CTP 2.3 で導入されました。 

## <a name="prerequisites"></a>前提条件

- [Visual Studio Code](https://code.visualstudio.com/)します。
- [SQL Server のビッグ データ クラスター](big-data-cluster-overview.md) CTP 2.3 以降。

## <a name="capabilities"></a>Capabilities

この拡張機能は、Visual Studio Code で、次のタスクをサポートします。

- SQL Server のビッグ データ クラスターで認証します。
- サポートされているランタイムの環境のデプロイの GitHub リポジトリからのアプリケーション テンプレートを取得します。
- ユーザーのワークスペースで現在開いているアプリケーション テンプレートを管理します。
- YAML 形式の仕様を使用してアプリケーションをデプロイします。
- SQL Server のビッグ データ クラスター内で展開されたアプリを管理します。
- 追加情報を含む、サイド バーで、展開されているすべてのアプリを表示します。
- アプリを使用またはクラスターから、アプリを削除する実行の仕様を生成します。
- デプロイ済みのアプリ実行の仕様の YAML を使用します。

次のセクションでは、ただし、インストール プロセスを説明し、拡張機能のしくみの概要を説明します。 

### <a name="install"></a>インストール

まず VS Code でアプリのデプロイの拡張機能をインストールします。

1. ダウンロード[アプリのデプロイの拡張機能](https://aka.ms/app-deploy-vscode)VS コードの一部として、拡張機能をインストールします。

1. VS Code を起動し、拡張機能のサイド バーに移動します。

1. をクリックして、`…`クリックし、サイド バーの上部にあるコンテキスト メニュー`Install from vsix`します。

   ![VSIX をインストールします。](media/vs-extension/install_vsix.png)

1. 検索、`sqlservbdc-app-deploy.vsix`ファイルをダウンロードおよびインストールを選択します。

SQL Server のビッグ データ クラスター アプリが展開した後は、拡張機能がインストールされている、VS Code の再読み込みするよう求められます。 VS Code のサイドバーで SQL Server の BDC アプリ エクスプ ローラーが表示されます。

### <a name="app-explorer"></a>アプリのエクスプ ローラー

アプリのエクスプ ローラーを示すサイド パネルの読み込みにサイドバーで、拡張機能をクリックします。 アプリのエクスプ ローラーの次のサンプルのスクリーン ショットには、アプリまたはアプリの仕様が利用可能な表示なし。

<img src="media/vs-extension/app_explorer.png" width=350px></img>
<!--![App Explorer](media/vs-extension/app_explorer.png)-->

#### <a name="new-connection"></a>新しい接続

クラスター エンドポイントに接続するには、次のメソッドのいずれかを使用します。

- 示す下部にあるステータス バーをクリック`SQL Server BDC Disconnected`します。
- をクリックしてまたは、`New Connection`戸口を指す矢印の付いた上部にあるボタンをクリックします。

   ![新しい接続](media/vs-extension/connect_to_cluster.png)

VS Code は、適切なエンドポイント、username、およびパスワードを要求します。 正しい資格情報とアプリ エンドポイントを指定した場合、VS Code は、クラスターに接続したことと、サイドバーに設定される展開済みのアプリが表示されますを通知します。 正常に接続する場合、エンドポイントとユーザー名に保存されます`./sqldbc`ユーザー プロファイルの一部として。 パスワードまたはトークンが保存されません。 ログをもう一度記録するには、ときに、プロンプトが事前入力、保存されているホストとユーザー名が、常にパスワードを入力する必要があります。 別のクラスター エンドポイントに接続する場合は、クリックして、`New Connection`もう一度です。 VS Code を閉じる場合や、別のワークスペースを開き、再接続する必要があります、接続を自動的に閉じます。

### <a name="app-template"></a>アプリ テンプレート

テンプレートのいずれかの新しいアプリを展開するには、をクリックして、`New App Template`のボタンでは、`App Specifications`を求められます名前、ランタイム、およびどのようなウィンドウに、ローカル コンピューター上で新しいアプリを配置する場所。 配置することが VS Code の現在のワークスペースで、拡張機能のすべての機能を使用できますが、ローカル ファイル システムにどこでも配置できるようにすることをお勧めします。

![新しいアプリ テンプレート](media/vs-extension/new_app_template.png)

指定した場所と、展開での新しいアプリ テンプレートがスキャフォールディングされる完了後、`spec.yaml`ワークスペースが開きます。 ワークスペースが選択したディレクトリにある場合も表示が下に表示されること、`App Specifications`ウィンドウ。

![読み込まれたアプリ テンプレート](media/vs-extension/loading_app_template.png)

テンプレートは、単純な`Hello World`次のように配置されるアプリ。

- **spec.yaml**
   - クラスターにアプリをデプロイする方法を示します
- **run-spec.yaml**
   - クラスターの通知、アプリを呼び出してください。
- **handler.py**
   - これは、ソース コード ファイルで指定された`src`で `spec.yaml`
   - 呼ばれる 1 つの関数が`handler`と見なされますが、`entrypoint`ように、アプリの`spec.yaml`します。 という文字列入力にかかる`msg`と呼ばれる文字列の出力を返しますと`out`します。 指定されて`inputs`と`outputs`の`spec.yaml`します。

スキャフォールディング テンプレートを作成したくないと、希望したかどうか、`spec.yaml`を既に作成したアプリのデプロイをクリックして、`New Deploy Spec`横に、`New App Template`ボタンと同じプロセスが説明は、を受け取るだけ`spec.yaml`、選択した方法を変更できます。

### <a name="deploy-app"></a>アプリをデプロイします。

コード レンズからこのアプリを展開する場合はすぐに`Deploy App`で、`spec.yaml`稲妻フォルダー ボタンを横にキーを押すか、`spec.yaml`アプリ仕様メニュー内のファイル。 拡張機能は、ディレクトリ内のすべてのファイルを zip 圧縮場所、`spec.yaml`が配置されていると、クラスターにアプリをデプロイします。 

>[!NOTE]
>同じディレクトリにあるすべてのアプリ ファイルを確認してください、`spec.yaml`します。 `spec.yaml`アプリのソース コード ディレクトリのルート レベルである必要があります。 

![アプリのボタンを配置します。](media/vs-extension/deploy_app_lightning.png)

![CodeLens のアプリをデプロイします。](media/vs-extension/deploy_app_codelens.png)

アプリは、サイドバーで、アプリの状態に基づいて使用可能な状態が通知されます。

![デプロイされたアプリ](media/vs-extension/app_deploy.png)

![アプリの準備完了のサイド バー](media/vs-extension/app_ready_side_bar.png)

![アプリの準備完了の通知](media/vs-extension/app_ready_notification.png)

作業ウィンドウに使用できる、次を参照することになります。

サイド バーに次の情報で展開したすべてのアプリを表示することがあります。

- 状態
- version
- 入力パラメーター
- 出力パラメーター
- リンク
  - Swagger
  - 詳細情報

をクリックすると`Links`にアクセスできることが表示されます、`swagger.json`デプロイされているアプリのアプリを呼び出すクライアントを記述するようにします。

![Swagger](media/vs-extension/swagger.png)

参照してください[ビッグ データ クラスター上でアプリケーションを消費する](big-data-cluster-consume-apps.md)詳細についてはします。

### <a name="app-run"></a>アプリの実行

使用してアプリを呼び出すアプリ準備ができたら、`run-spec.yaml`アプリ テンプレートの一部として指定するされました。

![仕様を実行します。](media/vs-extension/run_spec.png)

代わりにたい任意の文字列を指定`hello`し、もう一度横に実行、コード レンズのリンクまたはサイド バーの [超] ボタン、`run-spec.yaml`します。 なんらかの理由により実行仕様がない場合、は、クラスター内から、デプロイされたアプリを生成します。

![実行の仕様の取得](media/vs-extension/get_run_spec.png)

いずれかであるし、満足のいくように編集が、これを実行します。 VS Code では、アプリが実行を完了すると、適切なフィードバックが返されます。

![アプリの出力](media/vs-extension/app_output.png)

一時領域に、出力が得られる上記からわかる、`.json`ワークスペース内のファイル。 この出力は、自由に保存する場合は、それ以外の場合、削除されますで終了します。 出力ファイルに出力をアプリがない場合は、のみが表示されます、`Successful App Run`下部に通知します。 正常に実行されなかった場合、問題の特定に役立つ適切なエラー メッセージが表示されます。

アプリを実行するときに、さまざまなパラメーターを渡す方法があります。

必要なすべての入力を指定することも、`.json`は。

- `inputs: ./example.json`

すべての入力パラメーターが指定されたユーザー、アプリに組み込み機能と、指定された入力パラメーターが、配列、ベクトル、データ フレームなどのプリミティブ以外のものなど、複雑な JSON を指定する場合は、展開されたアプリを呼び出すときに、パラメーターの型直接内の行します。つまり、アプリの呼び出し。

- ベクター
    - `inputs:`
        - `x: [1, 2, 3]`
- マトリックス
    - `inputs:`
        - `x: [[A,B,C],[1,2,3]]`
- オブジェクト
    - `inputs:`
        - `x: {A: 1, B: 2, C: 3}`

相対パスまたは絶対ファイル パスとして、文字列を指定または、 `.txt`、 `.json`、または`.csv`アプリに必要な形式で必須の入力を提供します。 ファイルの解析がに基づいて`Node.js Path library`としてファイル パスが定義されている場所、`string that contains a / or \ character`します。

必要に応じて、入力パラメーターを指定しない場合、適切なエラー メッセージが表示されます正しくないファイル パスで指定した文字列のファイル パスか、そのパラメーターが無効です。 責任は、それらを定義するパラメーターを理解していることを確認して、アプリの作成者に付与されます。

アプリを削除するには、ごみ箱をクリックするだけで、アプリの横にあるボタンことができます、`Deployed Apps`作業ウィンドウ。

## <a name="next-steps"></a>次のステップ

独自のアプリケーションでのクラスターのビッグ データ、SQL Server に展開されているアプリを統合する方法について説明[ビッグ データ クラスター上でアプリケーションを消費する](big-data-cluster-consume-apps.md)詳細についてはします。 その他のサンプルを参照することもできます。[アプリの展開サンプル](https://aka.ms/sql-app-deploy)に拡張機能でお試しください。

ビッグ データの SQL Server クラスターの詳細については、次を参照してください。 [SQL Server 2019 ビッグ データ クラスターには何ですか?](big-data-cluster-overview.md)します。


当社の目標は、のこの拡張機能を有効に活用するしてフィードバックをいただければさいわいです。 お知らせください[[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]チーム](https://aka.ms/sqlfeedback)します。
