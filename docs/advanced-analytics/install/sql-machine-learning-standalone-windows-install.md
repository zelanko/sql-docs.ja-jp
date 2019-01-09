---
title: 'R Server または SQL Server のセットアップ: SQL Server Machine Learning を使用して Machine Learning Server (スタンドアロンを) インストールします。'
description: RevoScaleR、revoscalepy、MicrosoftML、およびその他のパッケージを使用して、R と Python の開発インスタンス非対応のスタンドアロンの machine learning server をセットアップします。
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/28/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: a00a91564cff37669f92cdfb4cba04fb3ada26fd
ms.sourcegitcommit: 0bb306da5374d726b1e681cd4b5459cb50d4a87a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2018
ms.locfileid: "53732059"
---
# <a name="install-machine-learning-server-standalone-or-r-server-standalone-using-sql-server-setup"></a>Machine Learning Server (スタンドアロン) または SQL Server セットアップを使用して R Server (スタンドアロンを) インストールします。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server セットアップが含まれています、**共有機能**インスタンスに対応していない、インストールするためのオプション SQL Server 外で実行されるスタンドアロン machine learning server。 SQL Server 2016 では、この機能は呼**R Server (スタンドアロン)** します。 SQL Server 2017 で呼び出されます**Machine Learning Server (スタンドアロン)** R と Python が含まれています。 

SQL Server セットアップによってインストールは、スタンドアロン サーバーは機能的には、SQL のブランド化されていないバージョンの[Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server)ケースやシナリオなどを使用して、同じサポートします。

+ リモート実行、同じコンソールで、ローカルおよびリモート セッション間の切り替え
+ Web ノードとコンピューティング ノードの運用化
+ Web サービスの配置: R と Python スクリプトを web サービスにパッケージ化する機能
+ R と Python の関数ライブラリの完全なコレクション

SQL Server から切り離されて独立したサーバーと、R と Python 環境が構成された、セキュリティ保護、および基になるオペレーティング システムと SQL サーバーではなく、スタンドアロン サーバーで提供されるツールを使用してアクセスします。

SQL Server の補助としてスタンドアロン サーバーが高パフォーマンスの機械学習のサポートされているデータ プラットフォームの完全な範囲に、リモート計算コンテキストを使用できるソリューションを開発する必要がある場合に便利です。 Spark クラスターで、または別の SQL Server インスタンスで、リモートの Machine Learning Server にローカル サーバーから実行を切り替えることができます。

<a name="bkmk_prereqs"> </a>

## <a name="pre-install-checklist"></a>インストール前のチェックリスト

SQL Server 2016 R Server (スタンドアロン) または Microsoft R Server などの以前のバージョンをインストールする場合は、続行する前に、既存のインストールをアンインストールします。

一般的な規則としてをスタンドアロン サーバーとデータベース エンジン インスタンスに対応したインストールとして相互に排他的リソースの競合を回避するために扱うことが禁止その両方をインストールする対象がない場合、十分なリソースがある場合は、お勧めの同じ物理コンピューター。

コンピューターのスタンドアロン サーバーがあることができますのみ: SQL Server 2017 Machine Learning Server または SQL Server 2016 R Server (スタンドアロン) のいずれか。 新しいものを追加する前に 1 つのバージョンをアンインストールしてください。

::: moniker range="=sql-server-2016"
<a name="bkmk_ga_instalpatch"></a> 

 ###  <a name="install-patch-requirement"></a>インストールのパッチ要件 

SQL server 2016 ののみ。SQL Server の前提条件としてインストールされる特定のバージョンの Microsoft VC++ 2013 ランタイム バイナリに問題が見つかりました。 VC ランタイム バイナリに対するこの更新プログラムをインストールしないと、特定のシナリオにおいて、SQL Server で安定性の問題が発生する可能性があります。 SQL Server をインストールする前に、「[SQL Server リリース ノート](../../sql-server/sql-server-2016-release-notes.md#bkmk_ga_instalpatch)」にある手順に従って、ご使用のコンピューターに VC ランタイム バイナリのパッチが必要かどうかを確認してください。  
::: moniker-end

## <a name="get-the-installation-media"></a>インストール メディアを入手する

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
## <a name="run-setup"></a>セットアップの実行

ローカル インストールの場合は、セットアップを管理者として実行する必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をリモート共有からインストールする場合は、そのリモート共有に対する読み取り権限と実行権限を持つドメイン アカウントを使用する必要があります。

1. インストール ウィザードを起動します。

2. をクリックして、**インストール**タブをクリックし、選択**Machine Learning Server (スタンドアロン) の新規インストール**します。
    
     ![Machine Learning Server スタンドアロン インストール](media/2017setup-installation-page-mlsvr.png "Machine Learning Server スタンドアロンのインストールを開始")

3. ルールのチェックが完了した後は、SQL Server のライセンス条項に同意し、新しいインストールを選択します。

4. **機能の選択**ページで、次のオプションは既に選択されている必要があります。

    - Microsoft Machine Learning Server (スタンドアロン)

    - R と Python 既定で選択します。 いずれかの言語の選択を解除することができますが、少なくとも 1 つのサポートされている言語をインストールすることをお勧めします。

     ![R または Python の機能の選択](media/2017setup-features-page-mlsvr-rpy.png "Machine Learning Server スタンドアロンのインストールを開始")
    
    その他のオプションはすべて無視します。 
    
    > [!NOTE]
    > インストールしないように、**共有機能**コンピューターで既に Machine Learning サービスが SQL Server データベース内分析用にインストールされたかどうか。 これには、重複するライブラリが作成されます。
    > 
    > また、他のデータベース エンジン サービスで使用されるメモリと競合にならないように SQL Server で、SQL Server で実行されている R または Python スクリプトの管理はスタンドアロンの machine learning server、このような制約がないと他のデータベース操作に干渉することができます. 最後に、運用化のよく使用されている RDP セッションを介したリモート アクセスはデータベース管理者によって通常ブロックされます。
    > 
    > これらの理由から、一般的な推奨 SQL Server Machine Learning サービスから別のコンピューターには、Machine Learning Server (スタンドアロン) をインストールすることです。

5.  ダウンロードとインストール ベース言語のディストリビューションに関するライセンス条項に同意します。 **[同意する]** ボタンが使用できない状態になっている場合は、**[次へ]** をクリックします。 

     ![Python の使用許諾契約書](media/2017setup-python-license.png "Python の使用許諾契約書")

6.  **[インストールの準備完了]** ページで、選択内容を確認し、**[インストール]** をクリックします。

インストールが完了したらを参照してください。 [for SQL Server R Services のカスタム レポート](../r/monitor-r-services-using-custom-reports-in-management-studio.md)エラーまたは警告については、次を参照してください。[アップグレードとインストールに関する FAQ - Machine Learning サービス](../r/upgrade-and-installation-faq-sql-server-r-services.md)します。
::: moniker-end

::: moniker range="=sql-server-2016"
## <a name="run-setup"></a>セットアップの実行

ローカル インストールの場合は、セットアップを管理者として実行する必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をリモート共有からインストールする場合は、そのリモート共有に対する読み取り権限と実行権限を持つドメイン アカウントを使用する必要があります。

1. インストール ウィザードを起動します。

2. **インストール**] タブで [ **R Server (スタンドアロン) の新規インストール**します。
    
     ![スタンドアロンの R Server のセットアップを開始](media/2016-setup-installation-rsvr.png "スタンドアロンの R Server のセットアップを開始")

3. ルールのチェックが完了した後は、SQL Server のライセンス条項に同意し、新しいインストールを選択します。

4.  **[機能の選択]** ページで、次のオプションが既に選択されています。
    
    **R Server (スタンドアロン)**  
    
    ![機能の選択を R Server のスタンドアロン](media/2016setup-rserver-features.png "機能のスタンドアロンの R Server の選択")
    
    その他のすべてのオプションは無視できます。 
    
    > [!NOTE]
    > インストールしないように、**共有機能**SQL Server データベース内分析に R Services が既にインストールされているコンピューターでセットアップを実行している場合。 これには、重複するライブラリが作成されます。
    > 
    > 他のデータベース エンジン サービスで使用されるメモリと競合にならないように SQL Server で、SQL Server で実行されている R スクリプトの管理は、スタンドアロン R Server は、このような制約がないので、他のデータベース操作に干渉することができます。
    > 
    > 一般的な推奨 R Server (スタンドアロン) をインストールする別のコンピューターから SQL Server R Services (In-database)。

5.  ダウンロードとインストール ベース言語のディストリビューションに関するライセンス条項に同意します。 **[同意する]** ボタンが使用できない状態になっている場合は、**[次へ]** をクリックします。 

6.  **[インストールの準備完了]** ページで、選択内容を確認し、**[インストール]** をクリックします。

インストールが完了したらを参照してください。 [for SQL Server R Services のカスタム レポート](../r/monitor-r-services-using-custom-reports-in-management-studio.md)エラーまたは警告については、次を参照してください。[アップグレードとインストールに関する FAQ - Machine Learning サービス](../r/upgrade-and-installation-faq-sql-server-r-services.md)します。
::: moniker-end

## <a name="set-environment-variables"></a>環境変数な設定

R の機能統合のみに設定する必要があります、 **MKL_CBWR**環境変数を[出力を一貫性のある](https://software.intel.com/articles/introduction-to-the-conditional-numerical-reproducibility-cnr)Intel 数値演算ライブラリ (MKL) 計算から。

1. コントロール パネルで、次のようにクリックします**システムとセキュリティ** > **システム** > **システムの詳細設定** >   **。環境変数**します。

2. 新しいユーザーまたはシステム変数を作成します。 

  + セットを変数名を指定 `MKL_CBWR`
  + 変数の値に設定します。 `AUTO`

3. サーバーを再起動します。

<a name="install-path"></a>

### <a name="default-installation-folders"></a>既定のインストール フォルダー

R と Python の開発では、同じコンピューター上の複数のバージョンが一般的なります。 SQL Server セットアップによってインストール、ベースの配布は、セットアップに使用した SQL Server のバージョンに関連付けられているフォルダーにインストールされます。

次の表では、Microsoft インストーラーによって作成された R および Python のディストリビューションのパスを示します。 完全を期すため、テーブルには、Microsoft Machine Learning Server のスタンドアロンのインストーラーと同様に SQL Server セットアップによって生成されたパスが含まれます。

|バージョン| インストール方法 | 既定のフォルダー|
|----|----|----|
|SQL Server 2017 Machine Learning Server (スタンドアロン) |  SQL Server 2017 セットアップ ウィザード |`C:\Program Files\Microsoft SQL Server\140\R_SERVER` <br/>`C:\Program Files\Microsoft SQL Server\140\PYTHON_SERVER`|
|Microsoft Machine Learning Server (スタンドアロン) |  Windows スタンドアロン インストーラー |`C:\Program Files\Microsoft\ML Server\R_SERVER`<br/>`C:\Program Files\Microsoft\ML Server\PYTHON_SERVER`|
|SQL Server 2017 Machine Learning サービス (データベース) |R 言語のオプションを使用して、SQL Server 2017 セットアップ ウィザード|`C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\R_SERVICES`  <br/>`C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\PYTHON_SERVICES` |
|SQL Server 2016 R Server (スタンドアロン) |  SQL Server 2016 セットアップ ウィザード |`C:\Program Files\Microsoft SQL Server\130\R_SERVER`|
|SQL Server 2016 R Services (In-database) |SQL Server 2016 セットアップ ウィザード|`C:\Program Files\Microsoft SQL Server\MSSQL13.<instance_name>\R_SERVICES`|

<a name="apply-cu"></a>

## <a name="apply-updates"></a>更新プログラムを適用します。

データベース エンジンと machine learning のコンポーネントの両方に、最新の累積的な更新プログラムを適用することをお勧めします。 累積的更新プログラムは、セットアップ プログラムを通じてインストールされます。 

インターネットに接続されたデバイスでは、自己解凍実行可能ファイルをダウンロードできます。 データベース エンジンの更新プログラムを自動的に適用することで既存の R と Python の機能の累積的更新プログラムを取得します。 

切断されたサーバーは、追加の手順が必要です。 データベース エンジンの累積更新プログラムおよび machine learning 機能用の CAB ファイルを取得する必要があります。 すべてのファイルは、分離されたサーバーに転送し、手動で適用する必要があります。

1. ベースラインのインスタンスを起動します。 累積的更新プログラムは、既存のインストールにのみ適用できます。

  + SQL Server 2017 の最初のリリースからの machine Learning Server (スタンドアロン)
  + 最初のリリースの SQL Server 2016、SQL Server 2016 SP 1、または SQL Server 2016 SP 2 からの R Server (スタンドアロン)

2. R または Python の開いているセッションを閉じ、システムで実行されているプロセスを停止します。

3. Web ノードと web サービスのデプロイ用のコンピューティング ノードとして実行する運用化を有効にした場合のバックアップ、 **AppSettings.json**念のためのファイル。 SQL Server 2017 CU13 またはこのファイルは、後で revises を適用するため、元のバージョンを保持するためにバックアップ コピーを作成する場合があります。

4. インターネット接続されているデバイスには、SQL Server のバージョンの累積更新プログラムのリンクをクリックします。

  + [SQL Server 2017 更新プログラム](https://sqlserverupdates.com/sql-server-2017-updates/)
  + [SQL Server 2016 更新プログラム](https://sqlserverupdates.com/sql-server-2016-updates/)

5. 最新の累積的な更新プログラムをダウンロードします。 実行可能ファイルになります。

6. インターネットに接続されたデバイスで、ライセンス条項に同意し、影響を受ける機能を確認し、完了するまでの進行状況の監視ウィザードでセットアップを実行する .exe をダブルクリックします。

7. インターネット接続のないサーバー。

   + R と Python の対応する CAB ファイルを取得します。 ダウンロード リンクは、次を参照してください。[インスタンス SQL Server データベース内分析に累積的更新プログラム用 CAB のダウンロード](sql-ml-cab-downloads.md)します。

   + すべてのファイル、メイン実行可能ファイルと、オフラインのコンピューター上のフォルダーに、CAB ファイルを転送します。

   + セットアップを実行する .exe をダブルクリックします。 インターネット接続のないをサーバーに累積更新プログラムをインストールする場合は、R と Python の .cab ファイルの場所を選択するように求められます。

8. Web ノードとコンピューティング ノードの運用化が有効にするサーバー上のインストール後の編集**AppSettings.json**、"MMLNativePath"のすぐ下の"MMLResourcePath"エントリを追加します。

    ```json
    "ScorerParameters": {
        "MMLNativePath": "C:\Program Files\Microsoft SQL Server\140\R_SERVER\library\MicrosoftML\mxLibs\x64\",
        "MMLResourcePath": "C:\Program Files\Microsoft SQL Server\140\R_SERVER\library\MicrosoftML\mxLibs\x64\"
    }
    ```

9. [管理者の CLI ユーティリティを実行して](https://docs.microsoft.com/machine-learning-server/operationalize/configure-admin-cli-launch)web を再起動し、コンピューティング ノード。 手順と構文は、次を参照してください。[モニター、開始、および web およびコンピューティング ノードを停止](https://docs.microsoft.com/machine-learning-server/operationalize/configure-admin-cli-stop-start)します。

## <a name="development-tools"></a>開発ツール

開発 IDE はセットアップの一部としてインストールされていません。 開発環境を構成する方法の詳細については、次を参照してください。 [R tools セットアップ](../r/set-up-a-data-science-client.md)と[Python ツールのセットアップ](../python/setup-python-client-tools-sql.md)します。

## <a name="next-steps"></a>次の手順

R 開発者は、簡単な例で作業を開始し、SQL Server での R の動作の基本を学習します。 次の手順で、次のリンクを参照してください。

+ [チュートリアル:T-SQL での R を実行します。](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [チュートリアル:R の開発者向けのデータベース内分析](../tutorials/sqldev-in-database-r-for-sql-developers.md)

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
Python の開発者は、これらのチュートリアルに従って、SQL Server で Python を使用する方法を学ぶことができます。

+ [チュートリアル:T-SQL での Python を実行します。](../tutorials/run-python-using-t-sql.md)
+ [チュートリアル:Python 開発者向けのデータベース内分析](../tutorials/sqldev-in-database-python-for-sql-developers.md)
::: moniker-end

実際のシナリオに基づく機械学習の例を表示するを参照してください。 [Machine learning のチュートリアル](../tutorials/machine-learning-services-tutorials.md)します。
