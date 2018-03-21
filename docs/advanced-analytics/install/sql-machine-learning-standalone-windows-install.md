---
title: "SQL Server 2017 Machine Learning サーバー (スタンドアロン) のインストール |Microsoft ドキュメント"
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
ms.openlocfilehash: 5dcc5ee16f39ac8612106f40f98c4f85a060ec4d
ms.sourcegitcommit: 8e897b44a98943dce0f7129b1c7c0e695949cc3b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/21/2018
---
# <a name="install-sql-server-2017-machine-learning-server-standalone-on-windows"></a>Windows Server (スタンドアロン) を学習の SQL Server 2017 マシンをインストールします。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server セットアップには、機械学習の SQL Server の外部で実行しているサーバーをインストールするオプションが含まれています。 このオプションは、高パフォーマンス マシン計算コンテキストをリモートで使用できるソリューションを学習、ローカル サーバーとリモート マシン ラーニング サーバーまたは別の SQL Server 上の Spark クラスター上の同じ意味で切り替えを開発する必要がある場合に役立ちます。インスタンス。
  
SQL Server セットアップを使用して、スタンドアロン バージョンをインストールする方法について説明**SQL Server 2017 Machine Learning サーバー**です。 Enterprise Edition またはソフトウェア アシュアランスがある場合、機械学習のスタンドアロン サーバーをインストールするは無料です。

## <a name="bkmk_prereqs"> </a> インストール前のチェックリスト

SQL Server 2017 が必要です。 SQL Server 2016 があればをインストールしてください[SQL Server 2016 R Server (スタンドアロン)](sql-r-standalone-windows-install.md)代わりにします。

SQL Server 2016 R Server (スタンドアロン) または Microsoft R Server などの以前のバージョンをインストールする場合は、続行する前に、既存のインストールをアンインストールします。

## <a name="get-the-installation-media"></a>インストール メディアを入手する

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]

## <a name="run-setup"></a>セットアップの実行

ローカル インストールの場合は、セットアップを管理者として実行する必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をリモート共有からインストールする場合は、そのリモート共有に対する読み取り権限と実行権限を持つドメイン アカウントを使用する必要があります。

1. SQL Server 2017 のセットアップ ウィザードを起動します。

2. クリックして、**インストール**タブをクリックし、選択**Machine Learning Server (スタンドアロン) の新規インストール**です。
    
     ![Machine Learning サーバーをスタンドアロンでインストール](media/2017setup-installation-page-mlsvr.png "の Machine Learning Server のスタンドアロン インストールを開始")

3. ルールのチェックが完了したら、SQL Server のライセンス条項に同意し、新規インストールを選択します。

4. **機能の選択**ページで、次のオプションは既に選択されている必要があります。

    - マイクロソフトの機械学習のサーバー (スタンドアロン)

    - R と Python 既定で選択します。 いずれかの言語の選択を解除することができますが、サポートされている言語の少なくとも 1 つをインストールすることをお勧めします。

     ![Machine Learning サーバーをスタンドアロンでインストール](media/2017setup-features-page-mlsvr-rpy.png "の Machine Learning Server のスタンドアロン インストールを開始")
    
    その他のオプションはすべて無視します。 
    
    > [!NOTE]
    > インストールしないように、**共有機能**コンピューターで既に Machine Learning サービスが SQL Server データベース内の分析用にインストールされたかどうか。 これには、重複するライブラリが作成されます。
    > 
    > SQL Server で実行される R または Python スクリプトは、その他のデータベース エンジン サービスで使用されるメモリの競合にならないように SQL Server で管理されて、一方はスタンドアロンの machine learning サーバーこのような制約を持たないまた、他のデータベース操作に干渉することができます. 最後に、操作運用のよく使用されている RDP セッション経由でリモート アクセスは、通常データベース管理者によってブロックされます。
    > 
    > これらの理由から、SQL Server の Machine Learning のサービスから別のコンピューターには、Machine Learning Server (スタンドアロン) をインストールすることを一般にお勧めします。

5.  ダウンロードし、機械学習のコンポーネントをインストールするためのライセンス条項に同意します。 両方の言語をインストールする場合は別のライセンス契約は Microsoft R および Python の必要です。
    
     ![Python の使用許諾契約書](media/2017setup-python-license.png "Python 使用許諾契約書")
    
    これらのコンポーネントと、必要な前提条件のインストール時間がかかる可能性があります。 **[同意する]** ボタンが使用できない状態になっている場合は、**[次へ]** をクリックします。

6.  **[インストールの準備完了]** ページで、選択内容を確認し、**[インストール]** をクリックします。

### <a name="default-installation-folders"></a>既定のインストール フォルダー

R Server をインストールするときにまたは Machine Learning サーバーは SQL Server セットアップを使用して、R ライブラリは、セットアップを使用して SQL Server のバージョンに関連付けられたフォルダーにインストールされます。 このフォルダーには、また、サンプル データ、R 基本パッケージのドキュメントおよびドキュメントの R ツールとランタイムを検索するされます。

ただし、別の Windows インストーラーを使用してインストールする場合、または別の Windows インストーラーを使用してアップグレードする場合は、R ライブラリは、別のフォルダーにインストールされます。

だけリファレンスについては、R Services (In-database) または Machine Learning Services (In-database)、SQL Server のインスタンスがインストールし、そのインスタンスが、同じコンピューターで、R ライブラリとツールは既定でインストール別のフォルダーにします。

次の表は、各インストール パスを一覧表示します。

|バージョン| インストール方法 | 既定のフォルダー|
|----|----|----|
|SQL Server 2017 Machine Learning サーバー (スタンドアロン) |  SQL Server 2017 セットアップ ウィザード |`C:\Program Files\Microsoft SQL Server\140\R_SERVER` <br/>`C:\Program Files\Microsoft SQL Server\140\PYTHON_SERVER`|
|マイクロソフトの機械学習のサーバー (スタンドアロン) |  Windows スタンドアロン インストーラー |`C:\Program Files\Microsoft\ML Server\R_SERVER`<br/>`C:\Program Files\Microsoft\ML Server\PYTHON_SERVER`|
|SQL Server 2017 Machine Learning Services (In-database) |R 言語のオプションを使用して、SQL Server 2017 セットアップ ウィザード|`C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\R_SERVICES`  <br/>`C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\PYTHON_SERVICES` |
|SQL Server 2016 R Server (スタンドアロン) |  SQL Server 2016 セットアップ ウィザード |`C:\Program Files\Microsoft SQL Server\130\R_SERVER`|
|SQL Server 2016 R Services (In-database) |SQL Server 2016 セットアップ ウィザード|`C:\Program Files\Microsoft SQL Server\MSSQL13.<instance_name>\R_SERVICES`|

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

+ [チュートリアル: T-SQL で R を実行します。](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [R 開発者向けチュートリアル: データベース内の分析](../tutorials/sqldev-in-database-r-for-sql-developers.md)

Python 開発者は、これらのチュートリアルに従って SQL Server で Python を使用する方法を学習できます。

+ [チュートリアル: T-SQL で Python を実行します。](../tutorials/run-python-using-t-sql.md)
+ [Python 開発者のためのチュートリアル: データベース内の分析](../tutorials/sqldev-in-database-python-for-sql-developers.md)

実際のシナリオに基づく機械学習の例を表示するを参照してください。[機械学習のチュートリアル](../tutorials/machine-learning-services-tutorials.md)です。
