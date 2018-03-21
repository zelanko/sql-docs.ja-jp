---
title: "SQL Server 2016 R Server (スタンドアロン) のインストール |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2018
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
caps.latest.revision: 
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.workload: On Demand
ms.openlocfilehash: 48f28b7a8d357e80e7defb6d6a8d446041380fbf
ms.sourcegitcommit: 8e897b44a98943dce0f7129b1c7c0e695949cc3b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/21/2018
---
# <a name="install-sql-server-2016-r-server-standalone"></a>SQL Server 2016 R Server (スタンドアロン) のインストールします。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server 2016 セットアップを使用して、スタンドアロン バージョンをインストールする方法について説明**SQL Server 2016 R サーバー**です。 Enterprise Edition またはソフトウェア アシュアランスがある場合、実稼働サーバーでスタンドアロン R Server をインストールするは無料です。

## <a name="bkmk_prereqs"> </a> インストール前のチェックリスト

SQL Server 2016 が必要です。 SQL Server 2017 があればをインストールしてください[SQL Server 2017 Machine Learning サーバー (スタンドアロン)](sql-machine-learning-standalone-windows-install.md)代わりにします。

以前のバージョンの Revolution Analytics ツールまたはパッケージをインストールした場合は、最初にアンインストールする必要があります。 

## <a name="get-the-installation-media"></a>インストール メディアを入手する

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]

 ###  <a name="bkmk_ga_instalpatch"></a> インストールのパッチ要件 

SQL Server の前提条件としてインストールされる特定のバージョンの Microsoft VC++ 2013 ランタイム バイナリに問題が見つかりました。 VC ランタイム バイナリに対するこの更新プログラムをインストールしないと、特定のシナリオにおいて、SQL Server で安定性の問題が発生する可能性があります。 SQL Server をインストールする前に、「[SQL Server リリース ノート](../../sql-server/sql-server-2016-release-notes.md#bkmk_ga_instalpatch)」にある手順に従って、ご使用のコンピューターに VC ランタイム バイナリのパッチが必要かどうかを確認してください。  

## <a name="run-setup"></a>セットアップの実行

ローカル インストールの場合は、セットアップを管理者として実行する必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をリモート共有からインストールする場合は、そのリモート共有に対する読み取り権限と実行権限を持つドメイン アカウントを使用する必要があります。

1. SQL Server 2016 のセットアップ ウィザードを起動します。 Service Pack 1 以降をインストールすることをお勧めします。

2. **インストール** タブで、をクリックして**R Server (スタンドアロン) の新規インストール**です。
    
     ![R Server のスタンドアロンのセットアップを開始](media/2016-setup-installation-rsvr.png "R Server のスタンドアロンのセットアップを開始")
    
3.  **[機能の選択]** ページで、次のオプションが既に選択されています。
    
    **R Server (スタンドアロン)**  
    
    ![機能の選択 R Server のスタンドアロンの](media/2016setup-rserver-features.png "機能の R Server のスタンドアロンの選択")
    
    その他のすべてのオプションは無視できます。 
    
    > [!NOTE]
    > インストールしないように、**共有機能**SQL Server データベース内の分析の R サービスが既にインストールされているコンピューターでセットアップを実行している場合。 これには、重複するライブラリが作成されます。
    > 
    > SQL Server で実行されている R スクリプトは、その他のデータベース エンジン サービスで使用されるメモリの競合にならないように SQL Server で管理されて、一方、スタンドアロン R Server はこのような制約がないので、他のデータベース操作に干渉することができます。
    > 
    > 一般的な推奨 R Server (スタンドアロン) をインストールする別のコンピューターに SQL Server R Services (In-database) からです。

4.  Microsoft R Open のダウンロードとインストールに関するライセンス条項に同意します。 **[同意する]** ボタンが使用できない状態になっている場合は、**[次へ]** をクリックします。
    
    これらのコンポーネントと、必要な前提条件のインストール時間がかかる可能性があります。
    
5.  **[インストールの準備完了]** ページで、選択内容を確認し、**[インストール]** をクリックします。

## <a name="default-installation-folders"></a>既定のインストール フォルダー

SQL Server セットアップを使用して R Server をインストールするときに、R ライブラリは、セットアップを使用して SQL Server のバージョンに関連付けられているフォルダーにインストールされます。 このフォルダーには、また、サンプル データ、R 基本パッケージのドキュメントおよびドキュメントの R ツールとランタイムを検索するされます。

ただし、別の Windows インストーラー (SQL セットアップされていません) を使用して Microsoft R Server をインストールした場合、または別の Windows インストーラーを使用してアップグレードする場合は、R ライブラリは、別のフォルダーにインストールされます。

推奨しますが、それに対しても、同じコンピューター上の SQL Server R Services (In-database) のインスタンスをインストールした場合、R ライブラリとツールの 2 番目のコピーが別のフォルダーにインストールされます。

次の表は、各インストール パスを一覧表示します。

|バージョン| インストール方法 | 既定のフォルダー|
|----|----|----|
|R Server (スタンドアロン) |SQL Server 2016 セットアップ ウィザード|`C:\Program Files\Microsoft SQL Server\130\R_SERVER`|
|R Server (スタンドアロン) |Windows スタンドアロン インストーラー|`C:\Program Files\Microsoft\R Server\R_SERVER`|
|Machine Learning Server (スタンドアロン) |  R 言語のオプションを使用して、SQL Server 2017 セットアップ ウィザード |`C:\Program Files\Microsoft SQL Server\140\R_SERVER`|
|Machine Learning Server (スタンドアロン) |  Python 言語オプションと、SQL Server 2017 セットアップ ウィザード |`C:\Program Files\Microsoft SQL Server\140\PYTHON_SERVER`|
|Machine Learning Server (スタンドアロン) |  Windows スタンドアロン インストーラー |`C:\Program Files\Microsoft\R Server\R_SERVER`|
|R Services (データベース内) |SQL Server 2016 セットアップ ウィザード|`C:\Program Files\Microsoft SQL Server\MSSQL13.<instance_name>\R_SERVICES`|
|Machine Learning Services (データベース内) |R 言語のオプションを使用して、SQL Server 2017 セットアップ ウィザード|`C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\R_SERVICES`  |
|Machine Learning Services (データベース内) |Python 言語オプションと、SQL Server 2017 セットアップ ウィザード| `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\PYTHON_SERVICES` |

## <a name="development-tools"></a>開発ツール

開発 IDE はセットアップの一部としてインストールされていません。 その他のツールは必要ありませんに R または Python の分布を使用して指定するようにすべての標準的なツールが含まれます。

新しいリリースを試してみることをお勧め[!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)]または[for Visual Studio の Python](https://docs.microsoft.com/en-us/visualstudio/python/installing-python-support-in-visual-studio)です。 Visual Studio では、R と、Python と両方ともデータベース開発ツール、SQL Server との接続および BI ツールをサポートします。 ただし、RStudio を含む、任意の希望する開発環境を使用することができます。
  
## <a name="get-help"></a>ヘルプの参照

ヘルプをインストールまたはアップグレードが必要ですか。 よく寄せられる質問と既知の問題への回答は、次の記事を参照してください。

* [アップグレードとインストールに関する FAQ - Machine Learning サービス](../r/upgrade-and-installation-faq-sql-server-r-services.md)

インスタンスのインストール状態をチェックして、一般的な問題を修正、これらのカスタム レポートを実行してください。

* [SQL Server R Services のカスタム レポート](../r/monitor-r-services-using-custom-reports-in-management-studio.md)

## <a name="next-steps"></a>次の手順

R の開発者は、単純な例についてで始めることができ、SQL Server での R の動作の基礎を学習します。 次の手順は、次のリンクを参照してください。

+ [チュートリアル: T-SQL で R を実行する](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)です。
+ [R 開発者向けチュートリアル: データベース内の分析](../tutorials/sqldev-in-database-r-for-sql-developers.md)

実際のシナリオに基づく機械学習の例を表示するを参照してください。[機械学習のチュートリアル](../tutorials/machine-learning-services-tutorials.md)です。

