---
title: R と Python コンポーネント - SQL Server Machine Learning Services のアップグレードします。
description: R と SQL Server 2016 サービスまたは SQL Server 2017 Machine Learning Services sqlbindr.exe を使用して Machine Learning Server にバインドするでの Python をアップグレードします。
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/30/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: da28d6f0ae423ce9cca0c6d571af944a2d7acd3d
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58512039"
---
# <a name="upgrade-machine-learning-r-and-python-components-in-sql-server-instances"></a>SQL Server インスタンス内のマシン ラーニング (R および Python) コンポーネントをアップグレードします。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server で R と Python の統合には、オープン ソースと Microsoft 独自のパッケージが含まれます。 標準的な SQL Server サービスに、パッケージは、現在のバージョンがないメジャー バージョンのアップグレードで既存のパッケージにはバグ修正で、SQL Server のリリース サイクルに従って更新されます。 

ただし、多くのデータ サイエンティストは、利用可能になる新しいパッケージを使用した作業に慣れています。 SQL Server 2017 の Machine Learning Services (In-database) と SQL Server 2016 R Services (In-database) の両方で取得できます[新しいバージョンの R と Python](#version-map)によって*バインド*に**MicrosoftMachine Learning Server**します。 

## <a name="what-is-binding"></a>バインディングについて

バインディングは、新しい実行可能ファイル、ライブラリ、R_SERVICES と PYTHON_SERVICES フォルダーの内容を入れ替えるし、からツールをインストール プロセス[Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/index)します。

と共に、サービス モデルでのスイッチは、コンポーネントを更新します。 代わりに、 [SQL Server 製品のライフ サイクル](https://support.microsoft.com/lifecycle/search?alpha=SQL%20Server%202017)で[SQL Server の累積的更新プログラム](https://support.microsoft.com/help/4047329/sql-server-2017-build-versions)、サービスの更新が今すぐに準拠している、[コンピューター (&)、Microsoft R Server のサポート タイムラインLearning Server](https://docs.microsoft.com/machine-learning-server/resources-servicing-support)上、[モダン ライフ サイクル](https://support.microsoft.com/help/30881/modern-lifecycle-policy)します。

コンポーネントのバージョンおよび最新のサービスを除くバインドでは、インストールの基礎は変更されません。R と Python の統合は、データベース エンジンのインスタンスの一部ではまだ (しない追加コスト バインドに関連付けられた)、ライセンスが変更されていないし、データベース エンジンの SQL Server サポート ポリシーを引き続き保持します。 この記事の残りの部分では、バインド メカニズムと SQL Server のバージョンごとにそのしくみについて説明します。

> [!NOTE]
> SQL Server インスタンスにバインドされているのみ (データベース) のインスタンスにバインドが適用されます。 バインディングでは、(スタンドアロン) のインストールに関係ありません。

**SQL Server 2017 のバインドに関する考慮事項**

SQL Server 2017 Machine Learning Services では、Microsoft Machine Learning Server は、追加のパッケージの提供を開始するか、経由するどのような新しいバージョンが既にある場合にのみバインドを考慮するとします。

**SQL Server 2016 のバインドに関する考慮事項**

SQL Server 2016 R Services の顧客のバインドが提供更新された R パッケージを新しいパッケージの元のインストールの一部ではない ([MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package))、および[事前トレーニング済みモデル](https://docs.microsoft.com/machine-learning-server/install/microsoftml-install-pretrained-models)、さらには、これらはすべて新しい各メジャーおよびマイナー リリースで更新[Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/index)します。 バインドを提供しません Python のサポートは、SQL Server 2017 の機能です。 

<a name="version-map"></a>

## <a name="version-map"></a>バージョンのマップ

次の表は、潜在的なアップグレード パスを確認するには、Microsoft Machine Learning Server が (旧称 R Server を開始する Python のサポートを追加する前にバインドするようにリリース媒体でパッケージのバージョンを示す、バージョンのマップで MLS 9.2.1)。 

バインディングには、非常に最新のバージョンの R または Anaconda は保証されませんに注意してください。 Microsoft Machine Learning Server (MLS) にバインドすると、ときに、これは、web で入手できる最新バージョンではない可能性があります、セットアップによってインストールされた R または Python のバージョンを取得します。

[**SQL Server 2016 R Services**](../install/sql-r-services-windows-install.md)

コンポーネント |最初のリリース | [R Server 9.0.1](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows) | [R Server 9.1](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows) | [MLS 9.2.1](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) | [MLS 9.3](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) |
----------|----------------|----------------|--------------|---------|-------|
R 経由で Microsoft R Open (MRO) | R 3.2.2     | R 3.3.2   |R 3.3.3   | R 3.4.1  | R 3.4.3 |
[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) | 8.0.3  | 9.0.1 |  9.1 |  9.2.1 |  9.3 |
[MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package)| n.a. | 9.0.1 |  9.1 |  9.2.1 |  9.3 |
[事前トレーニング済みモデル](https://docs.microsoft.com/machine-learning-server/install/microsoftml-install-pretrained-models)| n.a. | 9.0.1 |  9.1 |  9.2.1 |  9.3 |
[sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils)| n.a. | 1.0 |  1.0 |  1.0 |  1.0 |
[olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) | n.a. | 1.0 |  1.0 |  1.0 |  1.0 |


[**SQL Server 2017 の Machine Learning サービス**](../install/sql-machine-learning-services-windows-install.md)

コンポーネント |最初のリリース | MLS 9.3 | | | |
----------|----------------|---------|-|-|-|-|
R 経由で Microsoft R Open (MRO) | R 3.3.3 | R 3.4.3 | | | |
[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) |   9.2 |  9.3 | | | |
[MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package) | 9.2  | 9.3| | | |
[sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils)| 1.0 |  1.0 | | | |
[olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) | 1.0 |  1.0 | | | |
Python 3.5 には、anaconda 4.2  | 4.2/3.5.2 | 4.2/3.5.2 | | | |
[revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) | 9.2  | 9.3| | | |
 [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) | 9.2  | 9.3| | | |
[事前トレーニング済みモデル](https://docs.microsoft.com/machine-learning-server/install/microsoftml-install-pretrained-models) | 9.2 | 9.3| | | |

## <a name="how-component-upgrade-works"></a>コンポーネントのアップグレードのしくみ 

R と Python ライブラリおよび実行可能ファイルは、Machine Learning Server に R と Python の既存のインストールをバインドするときにアップグレードされます。 バインディングがによって実行される、 [Microsoft Machine Learning Server インストーラー](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install)既存 SQL Server データベース エンジンのインスタンスで、2016 または 2017 年のいずれかでセットアップを実行する場合も R または Python の統合。 セットアップでは、既存の機能を検出し、Machine Learning Server に再バインドするように求められます。 

バインドは、C:\Program files \microsoft SQL Server\MSSQL14 の内容中に。MSSQLSERVER\R_SERVICES と \PYTHON_SERVICES は、新しい実行可能ファイルや C:\Program Files\Microsoft\ML Server\R_SERVER と \PYTHON_SERVER のライブラリで上書きされます。

同時に、サービス モデルも反転、SQL Server 更新プログラムのメカニズムからの Microsoft Machine Learning Server より頻繁に、メジャーおよびマイナー リリース サイクルにします。 サポート ポリシーを切り替えると、R より新しい世代を必要とするデータ サイエンス チームの魅力的な選択肢と、ソリューションの Python モジュールです。 

+ バインド、しなくても、SQL Server service pack または累積更新プログラム (CU) をインストールするときに R と Python のパッケージがバグの修正の修正します。 
+ バインディングでは、新しいパッケージのバージョンに適用できる、CU リリース スケジュールとは無関係に、インスタンスで、[モダン ライフ サイクル ポリシー](https://support.microsoft.com/help/30881/modern-lifecycle-policy)およびリリースの Microsoft Machine Learning Server。 モダン ライフ サイクル サポート ポリシーは、短く、1 年間の有効期間をより頻繁に更新プログラムを提供します。 バインド後、Microsoft ダウンロード サイトで提供される R と Python の今後の更新プログラムの MLS インストーラーを使用する続行なります。

バインディングは、R と Python の機能のみに適用されます。 つまり、R と Python 機能 (Microsoft R Open、Anaconda)、および、独自のオープン ソース パッケージには、RevoScaleR revoscalepy、やなどがパッケージ化します。 バインドは、データベース エンジンのインスタンスのサポート モデルは変更されず、SQL Server のバージョンを変更しません。

バインディングは、元に戻すことができます。 SQL Server のサービスに戻すことが[インスタンスをバインド解除](#bkmk_Unbind)と、SQL Server データベース エンジンのインスタンスをされます。

合計、バインディングには次の手順です。

+ SQL Server 2016 R Services (または SQL Server 2017 Machine Learning サービス) の構成されている既存のインストールと開始します。
+ Microsoft Machine Learning Server のバージョンのアップグレードに使用するコンポーネントであることを確認します。
+ ダウンロードし、そのバージョンのセットアップを実行します。 セットアップでは、既存のインスタンスが検出されます、バインディング オプションを追加し、互換性のあるインスタンスの一覧を返します。
+ バインドし、バインディングを実行するセットアップを完了するインスタンスを選択します。

ユーザーのエクスペリエンスの観点から、テクノロジと方法を使用することは変更されません。 唯一の違いは、新しいバージョン管理されたパッケージと SQL Server (SQL Server 2016 R Services のお客様用の MicrosoftML) などからはもともと使用できない可能性がある追加のパッケージが存在します。

## <a name="bkmk_BindWizard"></a>セットアップを使用して MLS にバインドします。

Microsoft Machine Learning のセットアップでは、既存の機能や SQL Server のバージョンを検出し、というバインドを変更する SqlBindR.exe ユーティリティを呼び出します。 内部的には、SqlBindR がセットアップにチェーンされているし、間接的に使用します。 後で、特定のオプションを実行するためのコマンドラインから直接 SqlBindR を呼び出すことができます。

1. SSMS では、次のように実行します。`SELECT @@version`サーバーは、ビルドの最小要件を満たしていることを確認します。 

   SQL Server 2016 R Services では、最小値は[Service Pack 1](https://www.microsoft.com/download/details.aspx?id=54276)と[CU3](https://support.microsoft.com/help/4019916/cumulative-update-3-for-sql-server-2016-sp1)します。

1. 既存のバージョンが置き換えするよりも低いことを確認するには、基本の R と RevoScaleR パッケージのバージョンを確認します。 SQL Server 2016 R Services での R 基本パッケージ 3.2.2、RevoScaleR 8.0.3 します。

    ```sql
    EXECUTE sp_execute_external_script
    @language=N'R'
    ,@script = N'str(OutputDataSet);
    packagematrix <- installed.packages();
    Name <- packagematrix[,1];
    Version <- packagematrix[,3];
    OutputDataSet <- data.frame(Name, Version);'
    , @input_data_1 = N''
    WITH RESULT SETS ((PackageName nvarchar(250), PackageVersion nvarchar(max) ))
    ```

1. SSMS と SQL Server への開いた接続を持つ他のツールを終了します。 バインディングには、プログラム ファイルが上書きされます。 SQL Server は、開いているセッションには、バインド エラー コード 6 でバインドが失敗します。

1. アップグレードするインスタンスがあるコンピューターに Microsoft Machine Learning Server をダウンロードします。 お勧め、[最新バージョン](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install#download-machine-learning-server-installer)します。

1. フォルダーを解凍し、MLSWIN93 の下にある ServerSetup.exe を開始します。

   ![Microsoft Machine Learning Server セットアップ ウィザード](media/mls-921-installer-start.PNG)

1. **、インストールを構成する**でをアップグレードするコンポーネントを確認し、互換性のあるインスタンスの一覧を確認します。 

   この手順は非常に重要です。

   左側で、保持、またはアップグレードするすべての機能を選択します。 一部の機能などをアップグレードすることはできません。 空のチェック ボックスは、現在インストールされていると仮定すると、その機能を削除します。 スクリーン ショットは、SQL Server 2016 R Services (MSSQL13) のインスタンスには、R と R バージョン事前トレーニング済みモデルを選択します。 この構成は、SQL Server 2016 をサポートしていますが、R、Python ではないため無効です。

   SQL Server 2016 R Services のコンポーネントをアップグレードする場合は、Python 機能を選択しないでください。 Python は、SQL Server 2016 R Services を追加できません。

   右側には、インスタンス名の横にあるチェック ボックスを選択します。 インスタンスが表示されない場合、互換性のない組み合わせがあります。 インスタンスを選択しない場合は、Machine Learning Server の新規スタンドアロン インストールが作成され、SQL Server ライブラリは変更されません。 存在しない場合はインスタンスを選択することはできません[SP1 CU3](https://support.microsoft.com/help/4019916/cumulative-update-3-for-sql-server-2016-sp1)します。 

    ![インストール手順を構成します。](media/mls-931-installer-mssql13.png)

1. **使用許諾契約書**] ページで、[**これらの条項に同意**Machine Learning Server のライセンス条項に同意します。 

1. 後続のページでは、Microsoft R Open または Python の Anaconda ディストリビューションなど、選択したオープン ソース コンポーネントの追加のライセンス条件に同意を提供します。

1. **まであと少し** ページで、インストール フォルダーをメモしておきます。 既定のフォルダーは \Program Files\Microsoft\ML サーバーです。

    インストール フォルダーを変更する場合は、クリックして**詳細**ウィザードの最初のページに戻ります。 ただし、前のすべての選択内容を繰り返す必要があります。

インストール プロセス中には、SQL Server で使用される任意の R または Python ライブラリに置換し、新しいコンポーネントを使用するスタート パッドが更新されます。 その結果、インスタンスは、既定の R_SERVICES フォルダーにライブラリを使用した場合、は、アップグレード後にこれらのライブラリが削除され、新しい場所でライブラリを使用するスタート パッド サービスのプロパティが変更されます。

バインディングでは、これらのフォルダーの内容に影響します。C:\Program files \microsoft SQL Server\MSSQL13 します。MSSQLSERVER\R_SERVICES\library は、C:\Program Files\Microsoft\ML Server\R_SERVER の内容に置き換えられます。 2 つ目のフォルダーとその内容は、Microsoft Machine Learning Server セットアップによって作成されます。 

アップグレードに失敗した場合、 [SqlBindR エラーコード](#sqlbindr-error-codes)詳細についてはします。

## <a name="confirm-binding"></a>バインドを確認します。

新しいバージョンがあることを確認するには、R と RevoScaleR のバージョンを再確認します。 パッケージ情報を取得するのにには、データベース エンジンのインスタンスでの R パッケージを使用した分散 R コンソールを使用します。

```sql
EXECUTE sp_execute_external_script
@language=N'R'
,@script = N'str(OutputDataSet);
packagematrix <- installed.packages();
Name <- packagematrix[,1];
Version <- packagematrix[,3];
OutputDataSet <- data.frame(Name, Version);'
, @input_data_1 = N''
WITH RESULT SETS ((PackageName nvarchar(250), PackageVersion nvarchar(max) ))
```

SQL Server 2016 R Services が Machine Learning Server 9.3 にバインドされている、R 基本パッケージ 3.4.3 をする必要があります、RevoScaleR が、9.3 にする必要がありますおよび MicrosoftML 9.3 必要もあります。 

事前トレーニング済みモデルを追加した場合、モデルが MicrosoftML ライブラリに埋め込まれているし、MicrosoftML 関数を使用して、それらを呼び出すことができます。 詳細については、[MicrosoftML の R サンプル](https://docs.microsoft.com/machine-learning-server/r/sample-microsoftml)を参照してください。

## <a name="offline-binding-no-internet-access"></a>オフラインのバインド (インターネット アクセスなし)

インターネット接続のないシステムは、インターネットに接続されたマシンへのインストーラーと .cab ファイルをダウンロードしてから分離されたサーバーにファイルを転送します。 

(ServerSetup.exe) インストーラーには、Microsoft のパッケージ (RevoScaleR、MicrosoftML、olapR、sqlRUtils) が含まれています。 .Cab ファイルは、その他のコア コンポーネントを提供します。 たとえば、"SRO"cab は、R Open、Microsoft の配布はオープン ソース r です。

次の手順では、オフライン インストール用のファイルを配置する方法について説明します。

1. MLS インストーラーをダウンロードします。 これは、1 つの zip ファイルとしてダウンロードします。 お勧め、[最新バージョン](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install#download-machine-learning-server-installer)、インストールすることもできますが、[以前のバージョン](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows-offline#download-required-components)します。

1. .Cab ファイルをダウンロードします。 9.3 のリリースは、次のリンクです。 その他のリンクで見つかる以前のバージョンが必要な場合[R Server 9.1](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows-offline#download-required-components)します。 Anaconda Python/は SQL Server 2017 Machine Learning Services のインスタンスにのみ追加できることを思い出してください。 事前トレーニング済みモデルは、R と Python; の両方の存在します.cab を使用する言語でモデルを提供します。

    | 機能 | ダウンロード |
    |---------|----------|
    | R       | [SRO_3.4.3.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=867186&clcid=1033) |
    | Python  | [SPO_9.3.0.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=859054) | 
    | トレーニング済みモデル | [MLM_9.3.0.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=859053) |

1. .Zip や .cab ファイルをターゲット サーバーに転送します。

1. サーバーで、次のように入力します。 `%temp%` 、temp ディレクトリの物理的な場所を取得して実行 コマンドでします。 物理パスが、コンピューターによって異なりますが、これは通常`C:\Users\<your-user-name>\AppData\Local\Temp`します。

1. .Cab ファイルを %temp% フォルダーに配置します。

1. インストーラーを解凍します。

1. ServerSetup.exe を実行できるほか、画面に表示されるインストールを完了するように求められます。

## <a name="bkmk_BindCmd"></a>コマンドライン操作

Microsoft Machine Learning Server を実行するという SqlBindR.exe コマンド ライン ユーティリティがさらに操作のバインディングの使用になります。 たとえば、バインディングを反転することにした、でしたセットアップを再実行またはコマンド ライン ユーティリティを使用します。 さらに、このツールを使用すると、インスタンスの互換性と可用性を確認します。

> [!TIP]
> SqlBindR が見つかりませんか。 おそらくいないセットアップを実行しています。 SqlBindR は Machine Learning Server セットアップを実行した後にのみ使用できます。

1. 管理者としてコマンド プロンプトを開き、sqlbindr.exe を含むフォルダーに移動します。 既定の場所は C:\Program Files\Microsoft\MLServer\Setup です。

2. 次のコマンドを入力して、使用可能なインスタンスの一覧を表示します。 `SqlBindR.exe /list`
  
   一覧表示されている完全なインスタンス名をメモしておきます。 たとえば、インスタンス名には、MSSQL14 場合があります。MSSQLSERVER の既定のインスタンスまたはサーバー名のようなものです。MYNAMEDINSTANCE します。

3. 実行、 **SqlBindR.exe**コマンドと、 */bind*引数、前の手順で返されたインスタンス名を使用して、アップグレードするインスタンスの名前を指定します。

   たとえば、既定のインスタンスをアップグレードするには、次のように入力します。  `SqlBindR.exe /bind MSSQL14.MSSQLSERVER`

4. アップグレードが完了したら、変更されている任意のインスタンスに関連付けられているスタート パッド サービスを再起動します。

## <a name="bkmk_Unbind"></a>元に戻す、またはインスタンスをバインド解除

SQL Server セットアップによって確立されている R と Python コンポーネントの最初のインストールには、バインド インスタンスを復元できます。 SQL Server のサービスに戻すことに 3 つの部分があります。

+ [ステップ 1: Microsoft Machine Learning Server からバインド解除します。](#step-1-unbind)
+ [手順 2:インスタンスを元の状態に復元します。](#step-2-restore)
+ [ステップ 3:インストールに追加したすべてのパッケージを再インストールします。](#step-3-reinstall-packages)

<a name="step-1-unbind"></a> 

### <a name="step-1-unbind"></a>手順 1:[バインドの解除]

2 つがあるバインディングをロールバックするためのオプション: 再度セットアップを再実行または SqlBindR コマンド ライン ユーティリティを使用します。

#### <a name="bkmk_wizunbind"></a> セットアップを使用してバインド解除します。

1. Machine Learning Server 用のインストーラーを見つけます。 インストーラーを削除した場合は、もう一度、ダウンロード、または別のコンピューターからコピーする必要があります。
2. バインドを解除するインスタンスがあるコンピューターでインストーラーを実行してください。
2. インストーラーは、バインド解除の候補であるローカルのインスタンスを識別します。
3. 元の構成に戻す対象にするインスタンスの横にあるチェック ボックスをオフにします。
4. ライセンス契約に同意します。 インストールする場合は、偶数の使用許諾契約書に同意するを示す必要があります。
5. **[完了]** をクリックします。 プロセスがかかります。

#### <a name="bkmk_cmdunbind"></a> コマンドラインを使用してバインド解除します。

1. コマンド プロンプトを開き、前のセクションで説明したように **sqlbindr.exe** が含まれているフォルダーに移動します。

2. **SqlBindR.exe** コマンドを実行し、"*/unbind*" 引数でインスタンスを指定します。

   たとえば、次のコマンドでは、既定のインスタンスを元に戻します。
   
    `SqlBindR.exe /unbind MSSQL14.MSSQLSERVER`

<a name="step-2-restore"></a> 

###  <a name="step-2-repair-the-sql-server-instance"></a>手順 2:SQL Server インスタンスを修復します。

R と Python の機能を持つデータベース エンジンのインスタンスを修復する SQL Server セットアップを実行します。 既存の更新プログラムは保持されますが、この手順でそれらのパッチが適用されます、SQL Server の R と Python のパッケージの更新をサービスが実行されなかった場合。

また、これより多くの作業も完全にアンインストールし、データベース エンジンのインスタンスを再インストールしし、すべてのサービス更新プログラムの適用可能性があります。

<a name="step-3-reinstall-packages"></a> 

### <a name="step-3-add-any-third-party-packages"></a>手順 3:すべてのサード パーティ製パッケージを追加します。

パッケージ ライブラリに他のオープン ソースまたはサードパーティ製のパッケージを追加した可能性があります。 スイッチの既定のパッケージ ライブラリの場所を逆に、バインドすることがあるために、R と Python を使用して今すぐいるライブラリにパッケージを再インストールする必要があります。 詳細については、[パッケージの既定](installing-and-managing-r-packages.md)、[新しい R パッケージをインストール](install-additional-r-packages-on-sql-server.md)、および[新しい Python パッケージをインストール](../python/install-additional-python-packages-on-sql-server.md)を参照してください。

## <a name="sqlbindrexe-command-syntax"></a>SqlBindR.exe コマンドの構文

### <a name="usage"></a>使用方法

`sqlbindr [/list] [/bind <SQL_instance_ID>] [/unbind <SQL_instance_ID>]`

### <a name="parameters"></a>パラメーター

|名前|説明|
|------|------|
|*list*| 現在のコンピューター上にあるすべての SQL データベース インスタンスの ID を一覧表示します|
|*bind*| 指定された SQL データベース インスタンスを R Server の最新バージョンにアップグレードし、インスタンスが R Server の今後のアップグレードを自動的に取得するようにします|
|*unbind*|R Server の最新バージョンを指定した SQL データベース インスタンスからアンインストールし、R Server の今後のアップグレードがインスタンスに影響を与えないようにします|

<a name="sqlbindr-error-codes"><a/>

## <a name="binding-errors"></a>バインド エラー

MLS インストーラーと SqlBindR は、次のエラー コードとメッセージを返します。

|エラー コード  | メッセージ           | 詳細               |
|------------|-------------------|-----------------------|
|バインド エラー 0 | Ok (成功) | バインディングは、エラーなしで渡されます。 |
|バインド エラー 1 | 引数が無効です。 | 構文エラーです。 |
|バインド エラー 2 | 無効なアクション | 構文エラーです。 |
|バインド エラー 3 | 無効なインスタンス | インスタンスが存在するが、バインドに対して無効です。 |
|バインド エラー 4 | バインドがありません。 | |
|バインド エラー 5 | 既にバインドされてください | *bind* コマンドを実行しましたが、指定したインスタンスは既にバインドされています。 |
|バインド エラー 6 | バインドに失敗しました | インスタンスをバインド解除中にエラーが発生しました。 このエラーは、任意の機能を選択することがなく MLS インストーラーを実行する場合に発生することができます。 バインディングでは、MSSQL インスタンスと R の両方を選択して、インスタンスと仮定すると、Python、SQL Server 2017 のことが必要です。 このエラーは、SqlBindR は Program Files フォルダーに書き込めませんだった場合にも発生します。 SQL Server へのハンドルまたは開いているセッションでは、発生するには、このエラーが発生します。 このエラーが発生する場合は、コンピューターを再起動し、新しいセッションを開始する前に、バインディングの手順を再実行します。|
|バインド エラー 7 | バインドされていません | データベース エンジンのインスタンスでは、R Services または SQL Server Machine Learning サービスがあります。 Microsoft Machine Learning Server には、インスタンスはバインドされていません。 |
|バインド エラー 8 | バインドを解除できませんでした | インスタンスをバインド解除中にエラーが発生しました。 |
|バインド エラー 9 | No instances found (インスタンスが見つかりませんでした) | データベース エンジンのインスタンスがこのコンピューターに見つかりませんでした。 |

## <a name="known-issues"></a>既知の問題

このセクションでは、SqlBindR.exe ユーティリティまたは SQL Server インスタンスに影響を与える可能性があります、Machine Learning Server のアップグレードを使用する特定の既知の問題が一覧表示します。

### <a name="restoring-packages-that-were-previously-installed"></a>以前にインストールされたパッケージの復元

SqlBindR.exe のバージョンのバージョンが元のパッケージの復元に失敗しました Microsoft R Server 9.0.1 にアップグレードする場合または R コンポーネントを完全には、ユーザーがインスタンスで、SQL Server の修復を実行することを必要とするすべてのサービス リリースを適用し、再起動インスタンス。

SqlBindR の以降のバージョンは自動的に R コンポーネントを再インストールする必要がないため、元の R 機能を復元またはサーバーの修正プログラムを再適用します。 ただし、初期インストール後に追加された R パッケージの更新をインストールする必要があります。

このタスクははるかに簡単にインストールし、パッケージの共有パッケージの管理ロールを使用した場合: R コマンドを使用するには、データベースにレコードを使用してファイル システムにインストールされているパッケージを同期する、またはその逆です。 詳細については、[SQL Server の R パッケージ管理](install-additional-r-packages-on-sql-server.md)を参照してください。

### <a name="problems-with-multiple-upgrades-from-sql-server"></a>複数の SQL Server からのアップグレードに関する問題

以前、Microsoft R Server 9.1.0 の新しいインストーラーを実行すると、SQL Server 2016 R Services のインスタンスを 9.0.1 にアップグレードが場合、は、有効なすべてのインスタンスの一覧を表示し、し、既定で以前にバインドされたインスタンスを選択します。 続行する場合、以前にバインドされたインスタンスはバインドではありません。 その結果、以前の 9.0.1 インストールの削除も含めて、パッケージに関連が Microsoft R Server (9.1.0) の新しいバージョンがインストールされていません。

この問題を回避するには、次のように既存の R Server のインストールを変更できます。
1. コントロール パネルで、開く**プログラム追加と削除**します。
2. Microsoft R Server を見つけてクリックして**を変更する**します。
3. インストーラーが起動 9.1.0 にバインドするインスタンスを選択します。

Microsoft Machine Learning Server 9.2.1 および 9.3 には、この問題はありません。

### <a name="binding-or-unbinding-leaves-multiple-temporary-folders"></a>バインドまたはバインド解除のまま複数の一時フォルダー

場合があります、バインディングおよびバインド解除操作の一時フォルダーをクリーンアップに失敗します。
このような名前を持つフォルダーを検索する場合、インストールが完了した後に削除できます。R_SERVICES_<guid>

> [!NOTE]
> インストールが完了するまで待機することを確認します。 1 つのバージョンに関連付けられている R ライブラリを削除し、新しい R ライブラリを追加する長い時間がかかることができます。 操作が完了したら、一時フォルダーは削除されます。

## <a name="see-also"></a>関連項目

+ [Machine Learning Server for Windows (インターネットに接続) をインストールします。](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install)
+ [Machine Learning Server for Windows (オフライン) のインストールします。](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-offline)
+ [Machine Learning Server の既知の問題](https://docs.microsoft.com/machine-learning-server/resources-known-issues)
+ [R Server の以前のリリースから、機能のお知らせ](https://docs.microsoft.com/r-server/whats-new-in-r-server)
+ [非推奨、廃止された、または変更された機能](https://docs.microsoft.com/machine-learning-server/resources-deprecated-features)
