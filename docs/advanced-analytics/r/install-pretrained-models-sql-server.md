---
title: "事前トレーニング済みの機械学習モデルを SQL Server のインストール |Microsoft ドキュメント"
ms.date: 03/14/2018
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21456462-e58a-44c3-9d3a-68b4263575d7
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: fd02766e4020e6f522d50bbd471c5f84c66a998b
ms.sourcegitcommit: 0d904c23663cebafc48609671156c5ccd8521315
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2018
---
# <a name="install-pretrained-machine-learning-models-on-sql-server"></a>事前トレーニング済みの機械学習の SQL Server 上のモデルをインストールします。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、事前トレーニング済みモデルを SQL Server のインスタンスに追加済みの R Services または Machine Learning のサービスのインストール方法について説明します。

センチメント分析またはイメージの特性付けなどのタスクを実行する必要があり、大規模なデータセットを取得するか、複雑なモデルをトレーニングするためのリソースは持っていないユーザーを支援する MicrosoftML に含まれる事前トレーニング済みのモデルを作成しました。 Machine Learning サーバー チームが作成され、テキストおよびイメージの処理を効率的に作業を開始するため、これらのモデルをトレーニングします。 詳細については、次を参照してください。、[リソース](#bkmk_resources)この記事のセクションです。

SQL Server のデータを事前トレーニング済みモデルを使用する方法の例は、SQL Server の Machine Learning チームによってこのブログを参照してください。

+ [SQL Server の Machine Learning のサービスでの Python のセンチメント分析](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2017/11/01/sentiment-analysis-with-python-in-sql-server-machine-learning-services/)

## <a name="install-the-pre-trained-models"></a>事前トレーニング済みモデルをインストールします。

事前トレーニング済みモデルは、次の製品で使用できます。

+ SQL Server 2016 R Services (In-database)
+ SQL Server 2017 Machine Learning Services (In-database)
+ Machine Learning Server (スタンドアロン)

インストール プロセスは、SQL Server のバージョンによって若干異なります。 各バージョンの詳細については、次のセクションを参照してください。

> [!NOTE]
> パフォーマンスを向上させるために、ネイティブ形式を使用して圧縮されているために、読み取り、または事前トレーニング済みのモデルを変更することはありません。

### <a name="obtain-files-for-an-offline-installation"></a>オフライン インストール用のファイルを取得します。

インターネット アクセスが許可されていないサーバー上の事前トレーニング済みモデルをインストールするには、事前に適切なインストーラーをダウンロードして、インストーラーをサーバー上のローカル フォルダーにコピーします。 

R Server と Machine Learning のサーバーのすべてのインストーラーのダウンロード リンクについては、このページを参照してください:[オフライン インストール](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-offline)

### <a name="install-pretrained-models-with-sql-server-2016-r-services"></a>事前トレーニング済みモデルを SQL Server 2016 の R Services のインストールします。

SQL Server 2016 には、インストールして、機械学習と呼ばれるプロセス内のコンポーネントを最初にアップグレードする場合にのみ事前トレーニング済みの R モデルを使用することができます**バインディング**です。 

Microsoft R Server または Machine Learning のサーバーの別の Windows インストーラーを実行しているインスタンスまたはインスタンスを選択し、これを行う**バインド**です。 R. に頻繁に更新を許可するサポート ポリシーは、インスタンスに関連付けられているインスタンスと、バインドが変更されました。 

1. いずれかの Windows ベースの独立したインストーラーを起動して[R Server](https://docs.microsoft.com/machine-learning-server/rebranding-microsoft-r-server)または[Machine Learning サーバー](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install)です。

2. をアップグレードするインスタンスを選択し、事前トレーニング済みモデルを取得するためのオプションを選択します。

    詳細については、次を参照してください。 [SQL Server で使用されるマシン ラーニング コンポーネントをアップグレード](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)です。

    前のすべての選択のままにして以前の R コンポーネントを更新し、事前トレーニング済みモデルを追加するバインディングを実行した場合**は**、事前トレーニング済みモデル オプションを選択します。 
    
    以前に選択したオプションです。 選択を解除できません。これを行う場合、インストーラーは、コンポーネントを削除します。

3. モデルの場所の既定の設定をそのまま使用することをお勧めします。

4. 使用許諾契約書を含む、他のすべてのメッセージをそのまま使用します。

バインディングが完了したら、R バージョンおよびインスタンスに関連付けられているライブラリが R サーバーまたは Machine Learning のサーバーで提供される新しいバージョンに置き換えられます。 

SQL Server 2016 では、SQL Server 2016 インスタンス ライブラリでモデルを登録する追加の手順を行う必要があります。 事前トレーニング済みモデルがインストールされているインスタンスごとに次の手順を繰り返します。

1. Windows コマンド プロンプトを開き**管理者として**です。

2. Microsoft R インストーラーが含まれる SQL Server のセットアップ ブートス トラップ フォルダーに移動します。 SQL Server 2016 の既定のインスタンスで、フォルダーになります。
    
    `C:\Program Files\Microsoft SQL Server\130\Setup Bootstrap\SQL2017\x64\`

3. 実行`RSetup.exe`し、インストールするコンポーネント、バージョン、およびこの構文を使用して、モデルのソース ファイルを含むフォルダーを指定します。

    `RSetup.exe /install /component MLM /version <version> /language 1033 /destdir "<SQL_DB_instance_folder>\R_SERVICES\library\MicrosoftML\mxLibs\x64"`」を参照してください。 

    バージョン パラメーターは、次の値がサポートされています。

    + リリース候補 0:**されていた 9.1.0.0**
    + リリース候補 1: **9.2.0.22**
    + RTM: **9.2.0.100**
    + 累積更新プログラム 1: **9.2.0.24**
    + 累積更新プログラム 4: **9.3.0**

    > [!NOTE]
    > 対応する SQL Server のリリースは、更新プログラムが発行された時点の概要を把握することを一覧表示されます。 SQL Server と共にインストールされるバージョンの確信できない場合、インスタンスの R_SERVICES フォルダーを開き、RGui を開きます (`~\R_SERVICES\bin\x64`)。 開始画面には、Microsoft R Open のバージョンと Machine Learning のサーバーのバージョンが一覧表示します。 

    たとえば、事前トレーニング済みの R の使い方をモデル化の既定のインスタンスに**R_SERVICES**はこのコマンドを実行します。

    `RSetup.exe /install /component MLM /version 9.2.0.24 /language 1033 /destdir "C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library\MicrosoftML\mxLibs\x64"`

    名前付きインスタンスのコマンドは、ようになります次のような

    `RSetup.exe /install /component MLM /version 9.2.0.24 /language 1033 /destdir "C:\Program Files\Microsoft SQL Server\MSSQL13.MyInstanceName\R_SERVICES\library\MicrosoftML\mxLibs\x64"`

4. 次のモデルを追加する必要がありますのインストールが成功した場合、`R_SERVICES`フォルダー。

    + AlexNet\_Updated.model
    + ImageNet1K\_mean.xml
    + pretrained.model
    + ResNet\_101\_Updated.model
    + ResNet\_18\_Updated.model
    + ResNet\_50\_Updated.model

### <a name="install-pretrained-models-on-sql-server-2017"></a>SQL Server 2017 に事前トレーニング済みモデルをインストールします。

SQL Server 2017 をすでにインストールした場合は、2 つの方法で、事前トレーニング済みモデルを取得できます。

+ バインドを使用して、Python と R コンポーネントをアップグレードし、事前トレーニング済みモデルを同時にインストール
+ 事前トレーニング済みモデルだけをインストールします。

次の手順では、machine learning のコンポーネントをアップグレードして、同時に、事前トレーニング済みモデルを取得するためのプロセスについて説明します。

1. Machine Learning のサーバーの Windows ベースのインストーラーを実行します。 このページのリンクからインストーラーをダウンロードすることができます: [machine Learning の Windows サーバーをインストール](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install)です。

2. インターネット アクセスが許可されていないサーバーにモデルをインストールする場合もこのページから事前トレーニング済みモデル用のインストーラーをダウンロードしてください: [Machine Learning のサーバーのオフライン インストール](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-offline)です。

3. インストーラーを実行します。

4. 同時に、R または Python コンポーネントをアップグレードするには、更新する (R、Python、またはその両方) の言語を選択します。

    前のすべての選択のままにして以前に Machine Learning のサーバーをインストールおよび更新されたバインド オプションを使用して R または Python のコンポーネントが場合、**は**、事前トレーニング済みモデルのオプションを選択します。 以前に選択したオプションです。 選択を解除できません。これを行う場合、インストーラーは、コンポーネントを削除します。

5. 使用許諾契約書を含む、他のすべてのメッセージをそのまま使用します。

SQL Server 2017 で追加の構成は必要ありません。

> [!NOTE]
> 
> Python のモデルでは Python コードから、モデル ファイルを呼び出すときにエラーが表示する可能性があります。 これは、現在の Python 実装の制限により、モデル ファイルへのパスの長さを制限します。 この問題は修正されており、今後のサービス リリースで提供されます。

### <a name="installing-pretrained-models-with-r-server-standalone"></a>R Server (スタンドアロン) の事前トレーニング済みモデルをインストールします。

SQL Server 2016 セットアップを使用して R Server (スタンドアロン) の初期のバージョンをインストールした場合は、新しい Windows ベースのインストーラーを使用して R サーバーをアップグレードすることで、事前トレーニング済みモデルを使用する機能を追加できます。 

事前トレーニング済みモデルが最初にオプションとして利用可能になった[Microsoft R Server 9.1](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/introducing-microsoft-r-server-9-1-release/)アップグレードがリリースされるたびに追加されました。 可能であれば、最新バージョンを取得することをお勧めが以前のリリースが紹介[R Server のリリース](https://docs.microsoft.com/machine-learning-server/install/r-server-install)

次の手順では、R コンポーネントをアップグレードし、同時に、事前トレーニング済みモデルを追加する方法について説明します。

1. いずれかの Windows ベースの独立したインストーラーを起動して[R Server](https://docs.microsoft.com/machine-learning-server/rebranding-microsoft-r-server)または[Machine Learning サーバー](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install)です。

2. 更新、および選択する言語を選択して、 **Pre-trained モデル**オプション。

    > [!TIP]
    > 以前を R Server (スタンドアロン) を更新して、事前トレーニング済みモデルを追加するだけのインストーラーを実行した場合は、前のすべての選択のままに**は**、プレだけを選択し、**-モデルをトレーニング**オプション. **そうしない**以前選択したオプションの選択を解除; インストーラーが、コンポーネントを削除してこれを行う場合。

    モデルの場所の既定の設定をそのまま使用することをお勧めします。

3. **[続行]**をクリックします。 

4. 使用許諾契約書を含む、他のすべてのメッセージをそのまま使用します。

インストールが完了したら、事前トレーニング済みモデルを登録する追加の手順を実行する必要があります。

1. Windows コマンド プロンプトを開き**管理者として**です。

2. Microsoft R インストーラーが含まれる R Server (スタンドアロン) のセットアップ ブートス トラップ フォルダーに移動します。 

3. 実行`RSetup.exe`し、インストールするコンポーネント、バージョン、およびこの構文を使用して、モデルのソース ファイルを含むフォルダーを指定します。

    `RSetup.exe /install /component MLM /version <version> /language 1033 /destdir "~\R_SERVER\library\MicrosoftML\mxLibs\x64"`

    バージョン パラメーターは、次の値がサポートされています。

    + リリース候補 0:**されていた 9.1.0.0**
    + リリース候補 1: **9.2.0.22**
    + RTM: **9.2.0.100**
    + 累積更新プログラム 1: **9.2.0.24**
    + 累積更新プログラム 4: **9.3.0**

    たとえば、R Server (スタンドアロン) の既定のインストールでの R の事前トレーニング済みモデルの最新バージョンの使用を有効にするには、このステートメントを実行します。

    `RSetup.exe /install /component MLM /version 9.3.0 /language 1033 /destdir "C:\Program Files\Microsoft SQL Server\130\R_SERVER\library\MicrosoftML\mxLibs\"`

### <a name="installing-pretrained-models-with-machine-learning-server-standalone"></a>Machine Learning Server (スタンドアロン) を事前トレーニング済みモデルをインストールします。

SQL Server 2017 セットアップを使用して、マシン学習サーバーをインストールした場合は、Windows ベースのインストーラーを実行して事前トレーニング済みモデルを追加します。 R または Python のコンポーネントをアップグレードするオプションを選択し、同時に、事前トレーニング済みのモデルを追加できます。 

追加の構成は必要ありませんインストールが完了した後です。

## <a name="bkmk_resources"></a> 調査およびリソース

現在使用できるモデルは深層ニューラル ネットワーク (DNN) センチメント分析とイメージ分類モデルです。 Microsoft を使用してすべての事前トレーニング済みモデル トレーニングを受けた[計算ネットワーク Toolkit](https://cntk.ai/Features/Index.html)、または**CNTK**です。

各ネットワークの構成が次の参照の実装に基づいています。

+ ResNet-18
+ ResNet-50
+ ResNet-101
+ AlexNet

これらの deep モデル、および ere 実装および方法 CNTK を使用してトレーニングの学習に使用されるアルゴリズムの詳細については、次の記事を参照してください。

+ [Microsoft の調査担当者のアルゴリズム ImageNet チャレンジ マイルス トーンを設定します。](https://www.microsoft.com/research/blog/microsoft-researchers-algorithm-sets-imagenet-challenge-milestone/)

+ [Microsoft 計算ネットワーク Toolkit には、計算パフォーマンスを学習、最も効率的な分散深いが提供しています](https://www.microsoft.com/research/blog/microsoft-computational-network-toolkit-offers-most-efficient-distributed-deep-learning-computational-performance/)

### <a name="how-to-use-pre-trained-models-for-text-analysis"></a>テキスト分析の事前トレーニング済みモデルを使用する方法

事前トレーニング済みのテキストの特性付けのモデルを使用してテキスト分類する方法の例については、次の例を参照してください。

[テキスト フィーチャライザーを使用してセンチメント分析](https://github.com/Microsoft/microsoft-r/tree/master/microsoft-ml/Samples/101/BinaryClassification/SimpleSentimentAnalysis)

### <a name="how-to-use-pretrained-models-for-image-detection"></a>イメージの検出の事前トレーニング済みモデルを使用する方法

イメージの事前トレーニング済みモデルには、指定したイメージの特徴化がサポートされています。 使用するには、モデルを呼び出す、 **featurizeImage**を変換します。 イメージが読み込まれた、サイズ変更、およびトレーニング済みモデルでの特徴です。 DNN featurizer の出力はイメージ分類の線形のモデルのトレーニングに使用されます。

このモデルを使用するのには、すべてのイメージをトレーニング済みモデルの要件を満たす必要がありますサイズ変更。 たとえば、AlexNet モデルを使用する場合、イメージのサイズをする 227 x 227 px します。

詳細については、次を参照してください[センチメント分析やイメージの検出の事前トレーニング済みモデル。](https://docs.microsoft.com/machine-learning-server/install/microsoftml-install-pretrained-models)
