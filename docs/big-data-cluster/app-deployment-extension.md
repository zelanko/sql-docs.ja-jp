---
title: アプリ展開の拡張機能
titleSuffix: SQL Server big data clusters
description: SQL Server 2019 ビッグ データ クラスター (プレビュー) に、Python または R スクリプトをアプリケーションとして展開します。
author: jeroenterheerdt
ms.author: jterh
ms.reviewer: mikeray
ms.date: 02/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 1e5ab6364437432c803a364abd50ef5b1af4f8f6
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/25/2019
ms.locfileid: "67958910"
---
# <a name="how-to-use-vs-code-to-deploy-applications-to-sql-server-big-data-clusters"></a>VS Code を使用して SQL Server ビッグ データ クラスターにアプリケーションを展開する方法

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

この記事では、Visual Studio Code とアプリ展開拡張機能を使用して SQL Server ビッグ データ クラスターにアプリケーションを展開する方法について説明します。 この機能は CTP 2.3 で導入されました。 

## <a name="prerequisites"></a>Prerequisites

- [Visual Studio Code](https://code.visualstudio.com/)。
- [SQL Server ビッグ データ クラスター](big-data-cluster-overview.md) CTP 2.3 以降。

## <a name="capabilities"></a>Capabilities

この拡張機能では、Visual Studio Code での次のタスクがサポートされます。

- SQL Server ビッグ データ クラスターを使用して認証する。
- サポートされているランタイムの展開用に、GitHub リポジトリからアプリケーション テンプレートを取得する。
- ユーザーのワークスペースで現在開かれているアプリケーション テンプレートを管理する。
- YAML 形式の仕様を使用してアプリケーションを展開する。
- 展開したアプリを SQL Server ビッグ データ クラスター内で管理する。
- 展開したすべてのアプリと追加情報をサイド バーに表示する。
- 実行仕様を生成してアプリを使用するか、クラスターからアプリを削除する。
- 展開したアプリを YAML の実行仕様を通じて使用する。

以下のセクションでは、インストール プロセスについて説明し、拡張機能の動作の概要を示します。 

### <a name="install"></a>インストール

まず、VS Code にアプリ展開の拡張機能をインストールします。

1. [アプリ展開の拡張機能](https://aka.ms/app-deploy-vscode)をダウンロードし、VS Code の一部として拡張機能をインストールします。

1. VS Code を起動し、[拡張機能] サイド バーに移動します。

1. サイド バーの上部にある [`…`] コンテキスト メニューをクリックし、[`Install from vsix`]\(vsix からのインストール\) を選択します。

   ![VSIX のインストール](media/vs-extension/install_vsix.png)

1. ダウンロードした `sqlservbdc-app-deploy.vsix` ファイルを検索し、それを選択してインストールします。

SQL Server ビッグ データ クラスターのアプリ展開拡張機能がインストールされると、VS Code の再読み込みを求めるメッセージが表示されます。 VS Code サイド バーに SQL Server BDC アプリ エクスプローラーが表示されます。

### <a name="app-explorer"></a>アプリ エクスプローラー

サイド バーの拡張機能をクリックして、アプリ エクスプローラーが表示されているサイド パネルを読み込みます。 次のアプリ エクスプローラーのサンプル スクリーンショットは、利用できるアプリやアプリの仕様がないことを示しています。

<img src="media/vs-extension/app_explorer.png" width=350px></img>
<!--![App Explorer](media/vs-extension/app_explorer.png)-->

#### <a name="new-connection"></a>新しい接続

クラスター エンドポイントに接続するには、次のいずれかの方法を使用します。

- 下部にある、[`SQL Server BDC Disconnected`]\(SQL Server BDC が切断されました\) と示されているステータス バーをクリックします。
- または、上部にある、出口をさす矢印の付いた `New Connection` [新しい接続] ボタンをクリックします。

   ![新しい接続](media/vs-extension/connect_to_cluster.png)

VS Code、適切なエンドポイント、ユーザー名、およびパスワードの入力を求められます。 正しい資格情報とアプリ エンドポイントが指定された場合、クラスターに接続されたことが VS Code によって通知され、展開されたアプリがサイド バーに表示されます。 正常に接続すると、エンドポイントとユーザー名がユーザー プロファイルの一部として `./sqldbc` に保存されます。 パスワードやトークンは保存されません。 もう一度ログインすると、保存されているホストとユーザー名がプロンプトに事前に入力されますが、パスワードは常に入力する必要があります。 別のクラスター エンドポイントに接続する場合は、`New Connection` [新しい接続] をもう一度クリックします。 VS Code を閉じた場合、または別のワークスペースを開いた場合、接続は自動的に閉じられ。再接続する必要があります。

### <a name="app-template"></a>アプリ テンプレート

いずれかのテンプレートから新しいアプリを展開するには、[`App Specifications`]\(アプリの仕様\) ウィンドウの [`New App Template`]\(新しいアプリ テンプレート\) ボタンをクリックします。このボタンをクリックすると、名前、ランタイム、およびローカル コンピューターで新しいアプリを配置する場所を入力するように求められます。 拡張機能のすべての機能を使用できるように、現在の VS Code ワークスペースに配置することをお勧めしますが、ローカル ファイル システムの任意の場所に配置できます。

![新しいアプリ テンプレート](media/vs-extension/new_app_template.png)

完了すると、指定した場所に新しいアプリケーションテンプレートがスキャフォールディングされ、ワークスペースに `spec.yaml` の展開が開きます。 選択したディレクトリがワークスペース内にある場合は、それが [`App Specifications`]\(アプリの仕様\) ウィンドウにも表示されます。

![読み込まれたアプリ テンプレート](media/vs-extension/loading_app_template.png)

このテンプレートは、次のようにレイアウトされるシンプルな `Hello World` アプリです。

- **spec. yaml**
   - アプリの展開方法をクラスターに指示します
- **run-spec.yaml**
   - アプリの呼び出し方法をクラスターに指示します
- **handler.py**
   - これは、`spec.yaml` で `src` に指定されているソース コード ファイルです。
   - `spec.yaml` に示されているように、アプリの `entrypoint` と見なされる `handler` という 1 つの関数があります。 `msg` という文字列の入力を受け取り、`out` という文字列の出力を返します。 これらは `spec.yaml` の `inputs` と `outputs` で指定されます。

スキャフォールディング テンプレートが不要で、既に作成済みのアプリの展開用に `spec.yaml` を優先する場合は、[`New App Template`]\(新しいアプリ テンプレート\) ボタンの横にある [`New Deploy Spec`]\(新しい展開の仕様\) ボタンをクリックして同じプロセスを実行しますが、`spec.yaml` が表示されるだけです。それにより選択方法を変更できます。

### <a name="deploy-app"></a>アプリを展開

このアプリは、`spec.yaml` 内の [`Deploy App`]\(アプリの展開\) の CodeLens によってすぐに展開することも、[App Specifications]\(アプリの仕様\) メニューで `spec.yaml` ファイルの横にある稲妻フォルダーのボタンを押すこともできます。 拡張機能により、`spec.yaml` を配置したディレクトリ内のすべてのファイルが zip 圧縮され、アプリがクラスターに展開されます。 

>[!NOTE]
>すべてのアプリ ファイルが確実に `spec.yaml` と同じディレクトリにあるようにします。 `spec.yaml` は、アプリのソース コード ディレクトリのルート レベルにある必要があります。 

![アプリの展開のボタン](media/vs-extension/deploy_app_lightning.png)

![アプリの展開の CodeLens](media/vs-extension/deploy_app_codelens.png)

サイド バーのアプリの状態に基づいてアプリの使用準備が整うと、通知が表示されます。

![展開済みアプリ](media/vs-extension/app_deploy.png)

![アプリ準備完了のサイド バー](media/vs-extension/app_ready_side_bar.png)

![アプリ準備完了通知](media/vs-extension/app_ready_notification.png)

サイド ウィンドウでは、次のものが使用可能なことを確認できます。

展開したすべてのアプリを次の情報と共にサイド バーで確認できます。

- 状態
- version
- 入力パラメーター
- 出力パラメーター
- リンク
  - Swagger
  - 詳細

`Links` をクリックすると、展開されたアプリの `swagger.json` にアクセスできることがわかります。これにより、アプリを呼び出す独自のクライアントを作成できます。

![Swagger](media/vs-extension/swagger.png)

詳細については、「[ビッグ データ クラスターでアプリケーションを使用する](big-data-cluster-consume-apps.md)」を参照してください。

### <a name="app-run"></a>アプリ実行

アプリの準備ができたら、アプリ テンプレートの一部として指定された `run-spec.yaml` を使用して、アプリを呼び出します。

![実行仕様](media/vs-extension/run_spec.png)

`hello` の代わりに任意の文字列を指定してから、CodeLens リンクまたは `run-spec.yaml` の横にあるサイド バーの稲妻ボタンを使用して、もう一度実行します。 何らかの理由で実行仕様がない場合は、クラスター内の展開済みアプリから生成します。

![実行仕様の取得](media/vs-extension/get_run_spec.png)

それを手に入れて満足するまで編集したら、実行します。 アプリの実行が完了すると、VS Code によって適切なフィードバックが返されます。

![アプリの出力](media/vs-extension/app_output.png)

上記からわかるように、出力はワークスペース内の一時的な `.json` ファイルで提供されます。 この出力を保持する場合は、保存してください。そうしないと、終了時に削除されます。 アプリにファイルに書き込む出力がない場合、[`Successful App Run`]\(アプリの正常な実行\) 通知のみが下部に表示されます。 正常に実行されなかった場合は、問題を特定するのに役立つ適切なエラー メッセージが表示されます。

アプリを実行するときは、さまざまな方法でパラメーターを渡すことができます。

`.json` を使用して、要求されるすべての入力を指定できます。これは次のとおりです。

- `inputs: ./example.json`

展開されたアプリを呼び出すときに、入力パラメーターがアプリに本来備わっているかユーザーが指定したものである場合、または入力パラメーターがプリミティブ以外のもの (配列、ベクター、データフレーム、複雑な JSON など) である場合、アプリを呼び出すときにパラメーターの型を行に直接指定します。次のようになります。

- ベクター
    - `inputs:`
        - `x: [1, 2, 3]`
- マトリックス
    - `inputs:`
        - `x: [[A,B,C],[1,2,3]]`
- Object
    - `inputs:`
        - `x: {A: 1, B: 2, C: 3}`

または、必須の入力をアプリに必要な形式で指定した `.txt`、`.json`、`.csv` に対する相対ファイル パスまたは絶対ファイル パスとして文字列を指定します。 ファイルの解析は、`Node.js Path library` に基づきます。ここでは、ファイル パスは`string that contains a / or \ character` / または \ 文字を含む文字列として定義されています。

必要に応じた入力パラメーターが指定されていない場合、正しくないファイル パス (文字列ファイルのパスが指定されていた場合) またはパラメーターが無効であったことを示す適切なエラー メッセージが表示されます。 アプリの作成者には、定義しているパラメーターを確実に理解する責任があります。

アプリを削除するには、[`Deployed Apps`]\(展開済みアプリ\) サイド ウィンドウでアプリの横にあるごみ箱ボタンをクリックするだけです。

## <a name="next-steps"></a>次の手順

SQL Server ビッグ データ クラスターに展開されているアプリを独自のアプリケーションに統合する方法の詳細については、「[ビッグ データ クラスター上でアプリケーションを使用する](big-data-cluster-consume-apps.md)」を参照してください。 「[アプリ展開のサンプル](https://aka.ms/sql-app-deploy)」にある追加のサンプルを参照して、拡張機能を試してみることもできます。

SQL Server ビッグ データ クラスターの詳細については、「[SQL Server 2019 ビッグ データ クラスターとは](big-data-cluster-overview.md)」を参照してください。


私たちの目標は、この拡張機能をお客様にとって有益なものにすることです。フィードバックをお待ちしております。 [[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] チーム](https://aka.ms/sqlfeedback)までお送りください。
