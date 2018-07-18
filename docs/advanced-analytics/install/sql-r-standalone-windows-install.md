---
title: SQL Server 2016 R Server (スタンドアロン) のインストール |Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: e5457698120536247ad1823b842bb1b8e52b484d
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2018
ms.locfileid: "38979284"
---
# <a name="install-sql-server-2016-r-server-standalone"></a>SQL Server 2016 R Server (スタンドアロン) のインストールします。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、SQL Server 2016 セットアップを使用して、スタンドアロン バージョンをインストールする方法をについて説明します**SQL Server 2016 R Server**します。

## <a name="bkmk_prereqs"> </a> インストール前のチェックリスト

SQL Server 2016 が必要です。 SQL Server 2017 の場合をインストールしてください[SQL Server 2017 の Machine Learning Server (スタンドアロン)](sql-machine-learning-standalone-windows-install.md)代わりにします。

以前のバージョンの Revolution Analytics ツールまたはパッケージをインストールした場合は、最初にアンインストールする必要があります。 

## <a name="get-the-installation-media"></a>インストール メディアを入手する

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]

 ###  <a name="bkmk_ga_instalpatch"></a> インストールのパッチ要件 

SQL Server の前提条件としてインストールされる特定のバージョンの Microsoft VC++ 2013 ランタイム バイナリに問題が見つかりました。 VC ランタイム バイナリに対するこの更新プログラムをインストールしないと、特定のシナリオにおいて、SQL Server で安定性の問題が発生する可能性があります。 SQL Server をインストールする前に、「[SQL Server リリース ノート](../../sql-server/sql-server-2016-release-notes.md#bkmk_ga_instalpatch)」にある手順に従って、ご使用のコンピューターに VC ランタイム バイナリのパッチが必要かどうかを確認してください。  

## <a name="run-setup"></a>セットアップの実行

ローカル インストールの場合は、セットアップを管理者として実行する必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をリモート共有からインストールする場合は、そのリモート共有に対する読み取り権限と実行権限を持つドメイン アカウントを使用する必要があります。

1. SQL Server 2016 のセットアップ ウィザードを起動します。 Service Pack 1 以降をインストールすることをお勧めします。

2. **インストール**] タブで [ **R Server (スタンドアロン) の新規インストール**します。
    
     ![スタンドアロンの R Server のセットアップを開始](media/2016-setup-installation-rsvr.png "スタンドアロンの R Server のセットアップを開始")
    
3.  **[機能の選択]** ページで、次のオプションが既に選択されています。
    
    **R Server (スタンドアロン)**  
    
    ![機能の選択を R Server のスタンドアロン](media/2016setup-rserver-features.png "機能のスタンドアロンの R Server の選択")
    
    その他のすべてのオプションは無視できます。 
    
    > [!NOTE]
    > インストールしないように、**共有機能**SQL Server データベース内分析に R Services が既にインストールされているコンピューターでセットアップを実行している場合。 これには、重複するライブラリが作成されます。
    > 
    > 他のデータベース エンジン サービスで使用されるメモリと競合にならないように SQL Server で、SQL Server で実行されている R スクリプトの管理は、スタンドアロン R Server は、このような制約がないので、他のデータベース操作に干渉することができます。
    > 
    > 一般的な推奨 R Server (スタンドアロン) をインストールする別のコンピューターから SQL Server R Services (In-database)。

4.  Microsoft R Open のダウンロードとインストールに関するライセンス条項に同意します。 **[同意する]** ボタンが使用できない状態になっている場合は、**[次へ]** をクリックします。
    
    これらのコンポーネントと前提条件を必要となる、すべてのインストール時間がかかる場合があります。
    
5.  **[インストールの準備完了]** ページで、選択内容を確認し、**[インストール]** をクリックします。

## <a name="default-installation-folders"></a>既定のインストール フォルダー

SQL Server セットアップを使用して R Server をインストールするときに、R ライブラリは、セットアップに使用した SQL Server のバージョンに関連付けられているフォルダーにインストールされます。 このフォルダー内にサンプル データ、R 基本パッケージのドキュメントおよび R ツールとランタイムのドキュメントを検索することもされます。

ただし、別の Windows インストーラー (SQL セットアップされていません) を使用して Microsoft R Server をインストールした場合、または別の Windows インストーラーを使用してアップグレードする場合は、R ライブラリは、別のフォルダーにインストールされます。

推奨しますが、それに対しても、同じコンピューターに SQL Server R services (In-database) のインスタンスをインストールした場合、R ライブラリとツールの 2 番目のコピーが別のフォルダーにインストールされます。

次の表では、インストールごとにパスを示します。

|バージョン| インストール方法 | 既定のフォルダー|
|----|----|----|
|R Server (スタンドアロン) |SQL Server 2016 セットアップ ウィザード|`C:\Program Files\Microsoft SQL Server\130\R_SERVER`|
|R Server (スタンドアロン) |Windows スタンドアロン インストーラー|`C:\Program Files\Microsoft\R Server\R_SERVER`|
|Machine Learning Server (スタンドアロン) |  R 言語のオプションを使用して、SQL Server 2017 セットアップ ウィザード |`C:\Program Files\Microsoft SQL Server\140\R_SERVER`|
|Machine Learning Server (スタンドアロン) |  Python 言語のオプションを使用して、SQL Server 2017 セットアップ ウィザード |`C:\Program Files\Microsoft SQL Server\140\PYTHON_SERVER`|
|Machine Learning Server (スタンドアロン) |  Windows スタンドアロン インストーラー |`C:\Program Files\Microsoft\R Server\R_SERVER`|
|R Services (データベース内) |SQL Server 2016 セットアップ ウィザード|`C:\Program Files\Microsoft SQL Server\MSSQL13.<instance_name>\R_SERVICES`|
|Machine Learning Services (データベース内) |R 言語のオプションを使用して、SQL Server 2017 セットアップ ウィザード|`C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\R_SERVICES`  |
|Machine Learning Services (データベース内) |Python 言語のオプションを使用して、SQL Server 2017 セットアップ ウィザード| `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\PYTHON_SERVICES` |

## <a name="development-tools"></a>開発ツール

開発 IDE はセットアップの一部としてインストールされていません。 その他のツールは必要ありません、R または Python の分布を使用して提供するすべての標準的なツールが含まれています。

新しいリリースを試してみることをお勧めします。[!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)]または[for Visual Studio の Python](https://docs.microsoft.com/visualstudio/python/installing-python-support-in-visual-studio)します。 Visual Studio では、両方 R、Python と SQL Server との接続のデータベース開発ツールと BI ツールをサポートします。 ただし、RStudio を含む、任意のお好みの開発環境を使用することができます。
  
## <a name="get-help"></a>ヘルプの参照

インストールまたはアップグレードに関するヘルプ よく寄せられる質問と既知の問題への回答は、次の記事を参照してください。

* [アップグレードとインストールに関する FAQ - Machine Learning サービス](../r/upgrade-and-installation-faq-sql-server-r-services.md)

インスタンスのインストール状態を確認し、一般的な問題を修正には、これらのカスタム レポートをお試しください。

* [SQL Server R Services 用のカスタム レポート](../r/monitor-r-services-using-custom-reports-in-management-studio.md)

## <a name="next-steps"></a>次のステップ

R 開発者は、簡単な例で作業を開始し、SQL Server での R の動作の基本を学習します。 次の手順で、次のリンクを参照してください。

+ [チュートリアル: T-SQL で R を実行する](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)します。
+ [R の開発者向けチュートリアル: データベース内分析](../tutorials/sqldev-in-database-r-for-sql-developers.md)

実際のシナリオに基づく機械学習の例を表示するを参照してください。 [Machine learning のチュートリアル](../tutorials/machine-learning-services-tutorials.md)します。

