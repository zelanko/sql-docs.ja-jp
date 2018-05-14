---
title: SQL Server R インスタンス (Machine Learning サービス) で R、Python のコンポーネントのアップグレード |Microsoft ドキュメント
description: R と SQL Server 2016 の R Services または SQL Server 2017 Machine Learning サービス sqlbindr.exe を使用して、Machine Learning のサーバーにバインドする Python をアップグレードします。
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/05/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 716fbd8a105164d40bfa6b3e67d126067174dc5a
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="upgrade-machine-learning-r-and-python-components-in-sql-server-instances"></a>SQL Server インスタンスでマシン ラーニング (R と Python) コンポーネントをアップグレードします。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server で R、Python の統合には、オープン ソースと Microsoft 独自のパッケージが含まれます。 標準的な SQL Server サービスで R、Python のパッケージは、現在のバージョンで既存のパッケージへのバグ修正が、SQL Server リリース サイクルに従って更新されます。 

ほとんどのデータ サイエンティストは、利用可能になる新しいパッケージの操作に慣れています。 SQL Server 2017 Machine Learning Services (In-database) と SQL Server 2016 R Services (In-database) の両方では、変更することで R、Python の新しいバージョンを取得できます、*バインディング*に SQL Server のサービスから[Microsoft機械学習サーバー](https://docs.microsoft.com/en-us/machine-learning-server/index)と[の最新のライフ サイクルのサポート ポリシー](https://support.microsoft.com/help/30881/modern-lifecycle-policy)です。

バインディングには、インストールの基礎は変わりません: R と Python の統合は、データベース エンジンのインスタンスの一部ではまだ (追加コストなしのバインドに関連付けられている)、ライセンスが変更されていないと、データベースの SQL Server サポート ポリシーをまだ保持。エンジン。 R、Python のパッケージの処理方法変更の再バインドします。 この記事の残りの部分は、関連付けの機構と SQL Server のバージョンごとにそのしくみについて説明します。

> [!NOTE]
> バインディングは、(In-database) のインスタンスのみに適用されます。 バインド (スタンドアロン) のインストールは無効です。

**SQL Server 2017**

SQL Server 2017 Machine Learning サービスでは、Microsoft Machine Learning のサーバーがその他のパッケージの提供を開始するか、内容を新しいバージョンが既にある場合にのみバインドを考慮するとします。

**SQL Server 2016**

新規および更新を取得するための 2 つのパスがある SQL Server 2016 の R Services のユーザーにとって、R パッケージです。 1 つは、SQL Server 2017; へのアップグレード2 番目の Microsoft Machine Learning のサーバーへのバインドします。

SQL Server 2017 へのアップグレードを取得する R パッケージそのリリースと Python 機能に含まれているバージョンにします。 または、バインディングを取得する更新 R パッケージは、Microsoft Machine Learning のサーバーの新しい各メジャーおよびマイナー リリースでさらに更新できます。 

バインドを提供しませんは SQL Server 2017 機能である、Python をサポートします。 

**Microsoft Machine Learning Server を介して使用可能なコンポーネントのアップグレード**

次の表は、Microsoft Machine Learning サーバー (以前の R サーバーとして以降 MLS 9.2.1 で Python サポートを追加する前に) にバインドする場合の可能なアップグレードの SQL Server と共にインストールされるバージョンを示す、バージョン マップです。 

バインディングには、R または Anaconda の最新バージョンは保証されませんに注意してください。 Microsoft Machine Learning のサーバーにバインドすると、web で利用可能な最新のバージョンではない可能性がありますセットアップによってインストールされた R または Python のバージョンを取得します。

[**SQL Server 2016 R サービス**](../install/sql-r-services-windows-install.md)

コンポーネント |最初のリリース | R Server 9.0.1 | R Server 9.1 | MLS 9.2.1 | MLS 9.3 |
----------|----------------|----------------|--------------|---------|-------|
R 経由で Microsoft R Open (MRO) | R 3.2.2     | R 3.3.2   |R 3.3.3   | R 3.4.1  | R 3.4.3 |
[RevoScaleR](https://docs.microsoft.com/achine-learning-server/r-reference/revoscaler/revoscaler) | 8.0.3  | 9.0.1 |  9.1 |  9.2.1 |  9.3 |
[MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package)| n.a. | 9.0.1 |  9.1 |  9.2.1 |  9.3 |
[事前トレーニング済みモデル](https://docs.microsoft.com/machine-learning-server/install/microsoftml-install-pretrained-models)| n.a. | 9.0.1 |  9.1 |  9.2.1 |  9.3 |
[sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils)| n.a. | 1.0 |  1.0 |  1.0 |  1.0 |
[olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) | n.a. | 1.0 |  1.0 |  1.0 |  1.0 |


[**SQL Server 2017 マシンがサービスの学習**](../install/sql-machine-learning-services-windows-install.md)

コンポーネント |最初のリリース | MLS 9.3 | | | |
----------|----------------|---------|-|-|-|-|
R 経由で Microsoft R Open (MRO) | R 3.3.3 | R 3.4.3 | | | |
[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) |   9.2 |  9.3 | | | |
[MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package) | 9.2  | 9.3| | | |
[sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils)| 1.0 |  1.0 | | | |
[olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) | 1.0 |  1.0 | | | |
Python 3.5 経由で anaconda 4.2  | 4.2/3.5.2 | 4.2/3.5.2 | | | |
[revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) | 9.2  | 9.3| | | |
 [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) | 9.2  | 9.3| | | |
[事前トレーニング済みモデル](https://docs.microsoft.com/machine-learning-server/install/microsoftml-install-pretrained-models) | 9.2 | 9.3| | | |

## <a name="how-component-upgrade-works"></a>コンポーネントのアップグレードのしくみ

コンポーネントのアップグレードは、*バインディング*に SQL Server 2016 の R Services のインスタンス (または SQL Server 2017 Machine Learning サービス インスタンス) [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/index)です。 

Microsoft Machine Learning のサーバーは、オンプレミス サーバー製品インタープリターとパッケージが同じでは、SQL Server から分離します。 R、Python パッケージ Microsoft Machine Learning サーバーと配布の方が新しい SQL Server がインストールされているものよりも多くの場合、これを使用できるように、SQL Server サービスの更新機構をスワップをバインドします。 ポリシー サポートの切り替えは、新世代 R を必要とするデータ サイエンス チームの魅力的なオプションとその解決策の Python モジュール。 

バインディングがによって実行される、 [MLS インストーラー](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install)です。 インストーラー、R と Python で特定のパッケージを更新しますが、スタンドアロンの切断されたサーバーのインストールでは、SQL Server データベース内のインスタンスは置き換えられません。

+ SQL Server service pack または累積更新プログラム (CU) をインストールするときに、バインド、せずにバグの修正の R、Python のパッケージがパッチです。 
+ バインディングでは、新しいパッケージのバージョンに適用できる CU リリース スケジュールとは無関係には、インスタンスで、[現代のライフ サイクル ポリシー](https://support.microsoft.com/help/30881/modern-lifecycle-policy)およびリリースの Microsoft Machine Learning Server です。 最新のライフ サイクルのサポート ポリシーは、短く、1 年間の有効期間をより頻繁に更新プログラムを提供します。 バインド後は引き続き Microsoft Machine Learning のサーバーで利用可能になった R、Python の今後の更新プログラムの MLS インストーラーを使用できます。

バインディングは、R、Python の機能のみに適用されます。 つまり、R、Python の機能 (Microsoft R Open、Anaconda)、および、独自のオープン ソース パッケージには、RevoScaleR、revoscalepy などがパッケージ化します。 バインディングを使用して、データベース エンジン インスタンスのサポートのモデルを変更されず、SQL Server のバージョンは変更されません。

バインディングは、元に戻すことです。 SQL Server のサービスに戻すことができます[インスタンスをバインド解除する](#bkmk_Unbind)されます、SQL Server データベース エンジンのインスタンスとします。

合計、バインディングには次の手順です。

+ SQL Server 2016 の R Services (または SQL Server 2017 Machine Learning サービス) の既存の構成済みのインストールと起動します。
+ Microsoft Machine Learning のサーバーのバージョンが使用する場合、アップグレードされたコンポーネントを決定します。
+ ダウンロードし、そのバージョンのセットアップを実行します。 セットアップは、既存のインスタンスが検出、バインド オプションを追加し、互換性のあるインスタンスの一覧を返します。
+ バインドし、バインドを実行するセットアップを完了するインスタンスを選択します。

ユーザー エクスペリエンスの観点から、テクノロジとそれを操作する方法は変更されません。 唯一の違いは、新しいバージョンのパッケージと場合によっては追加 (SQL Server 2016 R サービス向け MicrosoftML) などの SQL Server でない最初の存在します。

## <a name="bkmk_BindWizard"></a>セットアップを使用して MLS へのバインドします。

Microsoft Machine Learning のセットアップは、既存の機能と SQL Server のバージョンを検出し、バインドを変更する SqlBindR.exe というユーティリティを呼び出します。 内部的には、SqlBindR セットアップにチェーンは、間接的に使用します。 後で、特定のオプションを実行するためにコマンドラインから直接 SqlBindR を呼び出すことができます。

1. サーバーがビルドの最小要件を満たしていることを確認します。 最小値は、SQL Server 2016 の R Services の[Service Pack 1](https://www.microsoft.com/download/details.aspx?id=54276)と[CU3](https://support.microsoft.com/help/4019916/cumulative-update-3-for-sql-server-2016-sp1)です。 SSMS では、実行`SELECT @@version`サーバー バージョン情報を返します。 

1. 既存のバージョンよりも低いに置き換えを計画することを確認するには、R と RevoScaleR のバージョンを確認します。 SQL Server 2016 の R Services の R 基本パッケージ 3.2.2、RevoScaleR 8.0.3 です。

    + \Program Files\Microsoft SQL Server\MSSQL13 に移動します。MSSQLSERVER\R_SERVICES\bin
    + ダブルクリックして**R**コンソールを開きます。
    + パッケージのバージョンを取得する`library(help="base")`と`library(help="RevoScaleR")`です。 

1. アップグレードするインスタンスがコンピューターには、Microsoft Machine Learning Server をダウンロードします。 お勧め、[最新バージョン](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install#download-machine-learning-server-installer)します。

1. フォルダーに解凍し、MLSWIN93 の下にある ServerSetup.exe を開始します。

   ![Microsoft Machine Learning のサーバーのセットアップ ウィザード](media/mls-921-installer-start.PNG)

1. **、インストールを構成する**をアップグレードするコンポーネントを確認し、互換性のあるインスタンスの一覧を確認します。 

   左側で維持するか、アップグレードするすべての機能を選択します。 一部の機能などをアップグレードすることはできません。 空のチェック ボックスは、現在インストールされていると仮定した場合、その機能を削除します。 スクリーン ショットで指定された SQL Server 2016 R Services (MSSQL13) のインスタンスには、R と事前トレーニング済みモデルの R バージョンを選択します。 SQL Server 2016 をサポートしていますが、R、Python ではないので、この構成は有効です。

   右側で、インスタンス名の横にあるチェック ボックスを選択します。 インスタンスが表示されない場合は、互換性のない組み合わせがあります。 インスタンスを選択しない場合は、Machine Learning のサーバーの新規スタンドアロン インストールを作成すると、および SQL Server ライブラリは変更されていません。 インスタンスを選択できない場合がありますで[SP1 CU3](https://support.microsoft.com/help/4019916/cumulative-update-3-for-sql-server-2016-sp1)です。 

    ![Microsoft Machine Learning のサーバーのセットアップ ウィザード](media/mls-931-installer-mssql13.png)

1. **使用許諾契約書**] ページで、[**これらの条項に同意**Machine Learning のサーバーのライセンス条項に同意します。 

1. 連続するページで、Microsoft R Open または Python Anaconda ディストリビューションなど、選択したすべてのオープン ソース コンポーネントの追加のライセンス条件に同意を提供します。

1. **少し** ページで、インストール フォルダーのメモしておきます。 既定のフォルダーは \Program Files\Microsoft\ML サーバーです。

    インストール フォルダーを変更する場合は、クリックして**詳細**ウィザードの最初のページに戻ります。 ただし、前のすべての選択を行う必要があります。

インストール プロセス中に SQL Server で使用される R または Python のライブラリが置き換えられ、スタート パッドを更新して、新しいコンポーネントを使用します。 その結果、インスタンスは、以前 R_SERVICES の既定のフォルダーでライブラリを使用、アップグレード後にこれらのライブラリとが削除、スタート パッド サービスのプロパティは、ライブラリを使用する、新しい場所に変更されます。

バインディングがこれらのフォルダーの内容に影響します。 C:\Program files \microsoft SQL Server\MSSQL13 です。MSSQLSERVER\R_SERVICES\library は、C:\Program Files\Microsoft\ML Server\R_SERVER の内容に置き換えられます。 2 番目のフォルダーとその内容は、Microsoft Machine Learning Server セットアップによって作成されます。 

アップグレードが失敗した場合、確認[SqlBindR エラーコード](#sqlbindr-error-codes)詳細についてはします。

## <a name="confirm-binding"></a>バインディングを確認します。

バージョンより新しいバージョンであることを確認するには、R と RevoScaleR を再確認します。 データベース エンジンのインスタンスに R パッケージと共に配布 R コンソールを使用して、パッケージ情報を取得します。

+ \Program Files\Microsoft SQL Server\MSSQL13 に移動します。MSSQLSERVER\R_SERVICES\bin
+ ダブルクリックして**R**コンソールを開きます。
+ パッケージのバージョンを取得する`library(help="base")`と`library(help="RevoScaleR")`です。 

SQL Server 2016 R サービスがマシン ラーニング サーバー 9.3 にバインドされている、R 基本パッケージを 3.4.1、RevoScaleR は 9.3、する必要があり、MicrosoftML 9.3 も必要です。 

事前トレーニング済みモデルを追加した場合は、MicrosoftML ライブラリに埋め込まれているモデルおよび MicrosoftML 関数を使用して、それらを呼び出すことができます。 詳細については、次を参照してください。 [MicrosoftML の R サンプル](https://docs.microsoft.com/machine-learning-server/r/sample-microsoftml)です。

## <a name="offline-no-internet-access"></a>オフライン (インターネットにアクセスできない)

システムのインターネット接続がない場合、インターネットに接続されたコンピューターにインストーラーと .cab ファイルをダウンロードし、分離されたサーバーにファイルを転送できます。 

インストーラー (ServerSetup.exe) には、マイクロソフトのパッケージ (RevoScaleR MicrosoftML、olapR sqlRUtils) が含まれています。 .Cab ファイルでは、その他のコア コンポーネントを提供します。 たとえば、"SRO"cab が R Open、Microsoft の配布はオープン ソース r です。

次の手順では、オフライン インストール用のファイルを配置する方法について説明します。

1. MLS インストーラーをダウンロードします。 1 つの zip ファイルとしてダウンロードします。 お勧め、[最新バージョン](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install#download-machine-learning-server-installer)、インストールすることもできますが、[以前のバージョン](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows-offline#download-required-components)します。

1. .Cab ファイルをダウンロードします。 次のリンクは 9.3 のリリースです。 以前のバージョンを必要とする場合は、その他のリンクは含まれて[R Server 9.1](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows-offline#download-required-components)です。 Python/Anaconda は SQL Server 2017 Machine Learning サービス インスタンスにのみ追加できますに注意してください。 事前トレーニング済みモデルが R、Python; の両方の存在します.cab を使用する言語でモデルを提供します。

    | 機能 | ダウンロード |
    |---------|----------|
    | R       | [SRO_3.4.3.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=867186&clcid=1033) |
    | Python  | [SPO_9.3.0.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=859054) | 
    | 事前トレーニング済みモデル | [MLM_9.3.0.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=859053) |

1. .Zip や .cab ファイルをターゲット サーバーに転送します。

1. サーバーで、次のように入力します。 `%temp%` 、一時ディレクトリの物理的な場所を取得して実行 コマンドでします。 物理パスが、コンピューターによって異なりますが、これは通常、`C:\Users\<your-user-name>\AppData\Local\Temp`です。

1. %Temp% フォルダー内のファイルを Place.cab です。

1. インストーラーに解凍します。

1. ServerSetup.exe を実行し、に従って、インストールを完了する画面に表示されます。

## <a name="bkmk_BindCmd"></a>コマンドライン操作

Microsoft Machine Learning のサーバーを実行した後 SqlBindR.exe と呼ばれるコマンド ライン ユーティリティはさらにバインディング操作を使用することを有効になります。 たとえば、バインディングを反転させることを決定した、またはすることが、セットアップを再実行コマンド ライン ユーティリティを使用します。 さらに、このツールを使用すると、インスタンスの互換性と可用性を確認します。

> [!TIP]
> SqlBindR が見つかりませんか。 可能性がありますいないセットアップを実行しています。 SqlBindR は、Machine Learning Server セットアップを実行した場合にのみ使用可能なです。

1. 管理者としてコマンド プロンプトを開き、sqlbindr.exe を含むフォルダーに移動します。 既定の場所は C:\Program Files\Microsoft\MLServer\Setup です。

2. 次のコマンドを入力して、使用可能なインスタンスの一覧を表示します。 `SqlBindR.exe /list`
  
   一覧表示されている完全なインスタンス名をメモしておきます。 たとえば、インスタンス名では、MSSQL14 可能性があります。既定のインスタンスまたはサーバー名のようなものの MSSQLSERVER です。MYNAMEDINSTANCE です。

3. 実行、 **SqlBindR.exe**コマンドと、 */bind*引数、し、前の手順で返されたインスタンス名を使用して、アップグレードするインスタンスの名前を指定します。

   たとえば、既定のインスタンスをアップグレードするには、次のように入力します。  `SqlBindR.exe /bind MSSQL14.MSSQLSERVER`

4. アップグレードが完了したら、変更されている任意のインスタンスに関連付けられている、スタート パッド サービスを再起動します。

## <a name="bkmk_Unbind"></a>元に戻すまたはインスタンスをバインド解除

SQL Server セットアップによって確立された R、Python コンポーネントの最初のインストールには、バインドのインスタンスを復元できます。 SQL Server サービスに戻すことに 3 つの部分があります。

+ [マイクロソフトの機械学習のサーバーからバインド解除手順 1。](#step-1-unbind)
+ [手順 2: インスタンスを元の状態に復元します。](#step-2-restore)
+ [手順 3: インストールに追加したすべてのパッケージを再インストールします。](#step-3-reinstall-packages)

<a name="step-1-unbind"></a> 

### <a name="step-1-unbind"></a>手順 1: バインド解除

2 つがある場合、バインドをロールバックするためのオプション: 再度セットアップを再実行または SqlBindR コマンド ライン ユーティリティを使用します。

#### <a name="bkmk_wizunbind"></a> セットアップを使用してバインドを解除します。

1. Machine Learning サーバー用のインストーラーを見つけます。 インストーラーを削除した場合は、もう一度、ダウンロードするか、別のコンピューターからコピーする必要があります。
2. バインド解除するインスタンスがコンピューターでインストーラーを実行してください。
2. インストーラーでは、バインドの対象となるローカル インスタンスを識別します。
3. 元の構成に戻すには対象のインスタンスの横にあるチェック ボックスをオフにします。
4. ライセンス契約に同意します。 インストールするときへもライセンス条項の同意を示す必要があります。
5. **[完了]** をクリックします。 プロセスがかかります。

#### <a name="bkmk_cmdunbind"></a> コマンドラインを使用してバインドを解除します。

1. コマンド プロンプトを開き、前のセクションで説明したように **sqlbindr.exe** が含まれているフォルダーに移動します。

2. **SqlBindR.exe** コマンドを実行し、"*/unbind*" 引数でインスタンスを指定します。

   たとえば、次のコマンドでは、既定のインスタンスを元に戻します。
   
    `SqlBindR.exe /unbind MSSQL14.MSSQLSERVER`

<a name="step-2-restore"></a> 

###  <a name="step-2-repair-the-sql-server-instance"></a>手順 2: SQL Server インスタンスを修復します。

R、Python の機能を持つ、データベース エンジンのインスタンスを修復する SQL Server セットアップを実行します。 既存の更新プログラムは保持されますが、この手順がそれらの修正プログラムを適用するには、任意の SQL Server R、Python のパッケージの更新をサービスが実行されなかった場合された場合、。

また、これはより多くの作業も完全にアンインストールし、データベース エンジンのインスタンスを再インストールし、すべてのサービス更新プログラムを適用する可能性があります。

<a name="step-3-reinstall-packages"></a> 

### <a name="step-3-add-any-third-party-packages"></a>手順 3: すべてのサードパーティのパッケージを追加します。

パッケージ ライブラリに他のオープン ソース、またはサード パーティのパッケージを追加する場合があります。 スイッチの既定のパッケージ ライブラリの場所のバインドを反転することから、R と Python で現在使用中、ライブラリにパッケージを再インストールする必要があります。 詳細については、次を参照してください。[既定のパッケージ](installing-and-managing-r-packages.md)、[新しい R パッケージをインストール](install-additional-r-packages-on-sql-server.md)、および[新しい Python パッケージをインストール](../python/install-additional-python-packages-on-sql-server.md)です。

## <a name="known-issues"></a>既知の問題

このセクションでは、SqlBindR.exe ユーティリティまたは SQL Server インスタンスに影響を与える可能性があります Machine Learning のサーバーのアップグレードを使用する特定の既知の問題を一覧表示します。

### <a name="restoring-packages-that-were-previously-installed"></a>以前にインストールされたパッケージを復元します。

そのバージョンの SqlBindR.exe のバージョンが元のパッケージの復元に失敗しました Microsoft R Server 9.0.1 へアップグレードする場合または R コンポーネントを完全には、ユーザーが、インスタンスで SQL Server の修復を実行することが必要なすべてのサービス リリースを適用し、再起動インスタンス。

SqlBindR の以降のバージョンでは、復元元の R 機能は、R コンポーネントを再インストールする必要がなくなるか、サーバーを再度パッチです。 ただし、最初のインストール後に追加された R パッケージの更新をインストールする必要があります。

このタスクがはるかに簡単にインストールし、パッケージの共有パッケージ管理の役割を使用している場合: R コマンドを使用するには、データベース内のレコードを使用して、ファイル システムにインストールされているパッケージを同期して、その逆です。 詳細については、次を参照してください。 [for SQL Server の R パッケージの管理](r-package-management-for-sql-server-r-services.md)です。

### <a name="problems-with-multiple-upgrades-from-sql-server"></a>SQL Server からの複数のアップグレードに関する問題

以前にアップグレードする SQL Server 2016 の R Services のインスタンス 9.0.1、Microsoft R server 9.1.0 新しいインストーラーを実行すると場合、は、そのすべての有効なインスタンスの一覧を表示であり、し、既定では以前にバインドされたインスタンスを選択します。 続行した場合は、以前にバインドされたインスタンスは連結ではありません。 その結果、以前の 9.0.1 のインストールを削除、いずれかの関連するパッケージが新しいバージョンの Microsoft R Server (9.1.0) がインストールされていません。

この問題を回避するには、次のように R Server の既存のインストールを変更できます。
1. コントロール パネルで、開く**プログラム追加と削除**です。
2. Microsoft R Server を見つけてクリックして**変更/変更**です。
3. インストーラーが起動したら、9.1.0 にバインドするインスタンスを選択します。

Machine Learning 9.2.1 および 9.3 のサーバーには、この問題はありません。

### <a name="binding-or-unbinding-leaves-multiple-temporary-folders"></a>バインド、またはバインドは、複数の一時フォルダーを残します

場合があります、バインディングおよびバインド解除操作は、一時フォルダーをクリーンアップに失敗します。
次のように名前を持つフォルダーを検索する場合は、削除できますインストールが完了したら: R_SERVICES_<guid>

> [!NOTE]
> インストールが完了するまで待機することを確認します。 1 つのバージョンに関連付けられた R ライブラリを削除してから、新しい R ライブラリを追加するのに長時間かかることができます。 操作が完了したら、一時フォルダーは削除されます。

## <a name="sqlbindrexe-command-syntax"></a>SqlBindR.exe コマンドの構文

### <a name="usage"></a>使用方法

`sqlbindr [/list] [/bind <SQL_instance_ID>] [/unbind <SQL_instance_ID>]`

### <a name="parameters"></a>パラメーター

|名前|Description|
|------|------|
|*list*| 現在のコンピューター上にあるすべての SQL データベース インスタンスの ID を一覧表示します|
|*bind*| 指定された SQL データベース インスタンスを R Server の最新バージョンにアップグレードし、インスタンスが R Server の今後のアップグレードを自動的に取得するようにします|
|*unbind*|R Server の最新バージョンを指定した SQL データベース インスタンスからアンインストールし、R Server の今後のアップグレードがインスタンスに影響を与えないようにします|

< a name =「sqlbinder エラー コード」<a/>

### <a name="errors"></a>エラー

このツールでは、次のエラー メッセージが返されます。

|エラー コード  | メッセージ           | 詳細               |
|------------|-------------------|-----------------------|
|バインド エラー 0 | Ok (成功) | バインディングは、エラーなしで渡されます。 |
|バインド エラー 1 | 引数が無効です。 | 構文エラーです。 |
|バインド エラー 2 | 無効なアクション | 構文エラーです。 |
|バインド エラー 3 | 無効なインスタンス | インスタンスが、バインドに対して無効です。 |
|バインド エラー 4 | バインドできるされません。 | |
|バインド エラー 5 | 既にバインドされてください | *bind* コマンドを実行しましたが、指定したインスタンスは既にバインドされています。 |
|バインド エラー 6 | バインドに失敗しました | インスタンスをバインド解除中にエラーが発生しました。 |
|バインド エラー 7 | バインドされていません | データベース エンジンのインスタンスには、R Services または SQL Server マシン ラーニング サービスがあります。 インスタンスは、Microsoft Machine Learning のサーバーにバインドされていません。 |
|バインド エラー 8 | バインドを解除できませんでした | インスタンスをバインド解除中にエラーが発生しました。 |
|バインド エラー 9 | No instances found (インスタンスが見つかりませんでした) | インスタンスがこのコンピューターに見つかりませんでした。 |


## <a name="see-also"></a>参照

+ [Machine Learning Server for Windows (インターネットに接続された) のインストールします。](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install)
+ [Machine Learning Server for Windows (オフライン) のインストールします。](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-offline)
+ [Machine Learning のサーバーの既知の問題](https://docs.microsoft.com/machine-learning-server/resources-known-issues)
+ [R Server の以前のリリースから機能の発表内容](https://docs.microsoft.com/r-server/whats-new-in-r-server)
+ [非推奨、廃止された、または変更された機能](https://docs.microsoft.com/machine-learning-server/resources-deprecated-features)