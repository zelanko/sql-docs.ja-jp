---
title: 事前トレーニング済みの機械学習モデルを SQL Server のインストール |Microsoft ドキュメント
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/31/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: e3abc1b1581216bb0207fbba2d857993b947afae
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34707580"
---
# <a name="install-pre-trained-machine-learning-models-on-sql-server"></a>事前トレーニング済みの機械学習の SQL Server 上のモデルをインストールします。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、事前トレーニング済みの機械学習のセンチメント分析とイメージの特性付け (In-database) SQL Server のインスタンスにモデルを追加済みの R Services または SQL Server マシン学習サービスがインストールされている方法について説明します。 

事前トレーニング済みモデルのために存在する顧客の特性付け、画像のまたはセンチメント分析を実行する必要がありますが、大規模なデータセットを取得するか、複雑なモデルをトレーニングするためのリソースはありません。 Machine Learning サーバー チームが作成され、テキストおよびイメージの処理を効率的に作業を開始するため、これらのモデルをトレーニングします。 詳細については、次を参照してください。、[リソース](#bkmk_resources)この記事のセクションです。

SQL Server のデータを事前トレーニング済みモデルを使用する方法の例を参照してくださいこのブログでは、SQL Server の Machine Learning チーム: [SQL Server の Machine Learning のサービスでの Python のセンチメント分析](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2017/11/01/sentiment-analysis-with-python-in-sql-server-machine-learning-services/)

## <a name="pre-trained-model-availability"></a>事前トレーニング済みモデルの可用性

事前トレーニング済みモデルは、Microsoft Machine Learning のサーバー (または Microsoft R Server、SQL Server 2016 のインストールにモデルを追加する場合) のインストール メディアを使用してインストールされます。 空き Developer edition を使用して、モデルをインストールすることができます。 余分ながないモデルのインストールに関連するコストです。 

事前トレーニング済みモデルは、次の製品と言語を使用します。 セットアップ プログラムは、言語の統合、MicrosoftML または microsoftml ライブラリを検出し、次に、事前トレーニング済みモデルを各自のライブラリに挿入します。 モデルのインストールが完了したら、ライブラリ関数を使用して、モデルにアクセスします。

+ SQL Server 2016 R Services (In-database) にのみ、R と、 [MicrosoftML ライブラリ](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package)
+ SQL Server 2016 R Server (スタンドアロン) にのみ、R と、 [MicrosoftML ライブラリ](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package)
+ SQL Server 2017 マシン ラーニング Services (In-database) の"R"、 [MicrosoftML ライブラリ](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package)、Python と、 [microsoftml ライブラリ](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package)
+ SQL Server 2017 マシン ラーニング サーバー (スタンドアロン) の"R"、 [MicrosoftML ライブラリ](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package)、Python と、 [microsoftml ライブラリ](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package)

インストール プロセスは、SQL Server のバージョンによって若干異なります。 各バージョンの詳細については、次のセクションを参照してください。

> [!NOTE]
> 読み取り、または事前トレーニング済みモデルを変更することはできません。 パフォーマンスを向上させるためにネイティブ形式を使用して、圧縮されています。

## <a name="obtain-files-for-an-offline-installation"></a>オフライン インストール用のファイルを取得します。

インターネット アクセスが許可されていないサーバー上の事前トレーニング済みモデルをインストールするには、事前に適切なインストーラーをダウンロードして、インストーラーをサーバー上のローカル フォルダーにコピーします。 

R Server と Machine Learning のサーバーのすべてのインストーラーのダウンロード リンクについては、このページを参照してください:[オフライン インストール](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-offline)

## <a name="install-pre-trained-models-on-sql-server-2016-r-services"></a>事前トレーニング済みモデルを SQL Server 2016 の R Services のインストールします。

SQL Server 2016 には、インストールして、機械学習と呼ばれるプロセス内のコンポーネントを最初にアップグレードする場合にのみ事前トレーニング済みの R モデルを使用することができます**バインディング**です。 

削除するには Microsoft R Server の Machine Learning のサーバー インスタンスまたはインスタンスを選択して、SQL Server 2016 の R Services のインストールを持つコンピューター上の個別の Windows インストーラーを実行している**バインド**です。 R. に頻繁に更新を許可するサポート ポリシーは、インスタンスに関連付けられているインスタンスと、バインドが変更されました。 

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

    `RSetup.exe /install /component MLM /version <version> /language 1033 /destdir "<SQL_DB_instance_folder>\R_SERVICES\library\MicrosoftML\mxLibs\x64"`。 

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

## <a name="install-pre-trained-models-on-sql-server-2017-machine-learning-services-in-database"></a>事前トレーニング済みモデルを SQL Server 2017 Machine Learning Services (In-database) のインストールします。

SQL Server 2017 をすでにインストールした場合は、2 つの方法で、事前トレーニング済みモデルを取得できます。

+ 事前トレーニング済みモデルだけをインストールします。
+ バインドを使用して、Python と R コンポーネントをアップグレードし、事前トレーニング済みモデルを同時にインストール

### <a name="add-pre-trained-models-only"></a>事前トレーニング済みモデルのみを追加します。

事前トレーニング済みモデルを追加するには、コマンドラインから RSetup.exe を実行できます。

バージョンについては、R モデルの R_SERVICES に MLM コンポーネントをインストールします。

```
RSetup.exe /install /component MLM /version 9.2.0.24 /language 1033 /destdir "C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES"
```

モデルの Python のバージョン、PYTHON_SERVICES に MLM コンポーネントをインストールします。

```
RSetup.exe /install /component MLM /version 9.2.0.24 /language 1033 /destdir "C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES"
```

### <a name="bind-and-install-pre-trained-models"></a>バインドして、事前トレーニング済みモデルのインストール

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

## <a name="install-pre-trained-models-with-sql-server-standalone-r-server"></a>SQL Server のスタンドアロン R サーバーでの事前トレーニング済みモデルをインストールします。

SQL Server 2016 セットアップを使用して R Server (スタンドアロン) の初期のバージョンをインストールした場合は、新しい Windows ベースのインストーラーを使用して R サーバーをアップグレードすることで、事前トレーニング済みモデルを使用する機能を追加できます。 

事前トレーニング済みモデルが最初にオプションとして利用可能になった[Microsoft R Server 9.1](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/introducing-microsoft-r-server-9-1-release/)アップグレードがリリースされるたびに追加されました。 可能であれば、最新バージョンを取得することをお勧めが以前のリリースが紹介[R Server のリリース](https://docs.microsoft.com/machine-learning-server/install/r-server-install)

次の手順では、R コンポーネントをアップグレードし、同時に、事前トレーニング済みモデルを追加する方法について説明します。

1. いずれかの Windows ベースの独立したインストーラーを起動して[R Server](https://docs.microsoft.com/machine-learning-server/rebranding-microsoft-r-server)または[Machine Learning サーバー](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install)です。

2. 更新、および選択する言語を選択して、 **Pre-trained モデル**オプション。

    > [!TIP]
    > 以前を R Server (スタンドアロン) を更新して、事前トレーニング済みモデルを追加するだけのインストーラーを実行した場合は、前のすべての選択のままに**は**、プレだけを選択し、**-モデルをトレーニング**オプション. **そうしない**以前選択したオプションの選択を解除; インストーラーが、コンポーネントを削除してこれを行う場合。

    モデルの場所の既定の設定をそのまま使用することをお勧めします。

3. **[続行]** をクリックします。 

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

## <a name="install-pre-trained-models-with-sql-server-2017-standalone-server"></a>事前トレーニング済みモデルを SQL Server 2017 スタンドアロン サーバーにインストールします。

SQL Server 2017 セットアップを使用して、マシン学習サーバーをインストールした場合は、Windows ベースのインストーラーを実行して事前トレーニング済みモデルを追加します。 R または Python のコンポーネントをアップグレードするオプションを選択し、同時に、事前トレーニング済みのモデルを追加できます。 

追加の構成は必要ありませんインストールが完了した後です。

## <a name="bkmk_resources"></a> 調査およびリソース

現在使用できるモデルは深層ニューラル ネットワーク (DNN) センチメント分析とイメージ分類モデルです。 Microsoft を使用してすべての事前トレーニング済みモデル トレーニングを受けた[計算ネットワーク Toolkit](https://cntk.ai/Features/Index.html)、または**CNTK**です。

各ネットワークの構成が次の参照の実装に基づいています。

+ ResNet-18
+ ResNet 50
+ ResNet 101
+ AlexNet

これらの深層学習モデルでは、その実装方法で使用されるアルゴリズムの詳細については、トレーニング CNTK を使用して、これらの記事を参照してください。

+ [Microsoft の調査担当者のアルゴリズム ImageNet チャレンジ マイルス トーンを設定します。](https://www.microsoft.com/research/blog/microsoft-researchers-algorithm-sets-imagenet-challenge-milestone/)

+ [Microsoft 計算ネットワーク Toolkit には、計算パフォーマンスを学習、最も効率的な分散深いが提供しています](https://www.microsoft.com/research/blog/microsoft-computational-network-toolkit-offers-most-efficient-distributed-deep-learning-computational-performance/)

## <a name="how-to-use-pre-trained-models-for-text-analysis"></a>テキスト分析の事前トレーニング済みモデルを使用する方法

事前トレーニング済みのテキストの特性付けのモデルを使用してテキスト分類する方法の例については、次の例を参照してください。

[テキスト フィーチャライザーを使用してセンチメント分析](https://github.com/Microsoft/microsoft-r/tree/master/microsoft-ml/Samples/101/BinaryClassification/SimpleSentimentAnalysis)

## <a name="how-to-use-pre-trained-models-for-image-detection"></a>イメージの検出の事前トレーニング済みモデルを使用する方法

イメージの事前トレーニング済みモデルには、指定したイメージの特徴化がサポートされています。 使用するには、モデルを呼び出す、 **featurizeImage**を変換します。 イメージが読み込まれた、サイズ変更、およびトレーニング済みモデルでの特徴です。 DNN featurizer の出力はイメージ分類の線形のモデルのトレーニングに使用されます。

このモデルを使用するのには、すべてのイメージをトレーニング済みモデルの要件を満たす必要がありますサイズ変更。 たとえば、AlexNet モデルを使用する場合、イメージのサイズをする 227 x 227 px します。

詳細については、次を参照してください[センチメント分析やイメージの検出の事前トレーニング済みモデル。](https://docs.microsoft.com/machine-learning-server/install/microsoftml-install-pretrained-models)
