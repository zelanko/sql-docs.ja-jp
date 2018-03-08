---
title: "SQL Server 2016 リリース ノート | Microsoft Docs"
ms.date: 02/27/2018
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: sql-non-specified
ms.reviewer: 
ms.suite: sql
ms.custom: 
ms.technology:
- server-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- build notes
- release issues
ms.assetid: c64077a2-bec8-4c87-9def-3dbfb1ea1fb6
caps.latest.revision: 
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 6485ef83b940ab9d04b9406e461517d5254aec7f
ms.sourcegitcommit: 1a3584a60c12521ba5b4b12a18d8cb32b1f2d555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2018
---
# <a name="sql-server-2016-release-notes"></a>SQL Server 2016 リリース ノート
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]
ここでは、SQL Server 2016 リリースでの制限事項と問題について説明します。 新機能については、「 [SQL Server 2016 の新機能](https://docs.microsoft.com/en-us/sql/sql-server/what-s-new-in-sql-server-2016)」をご覧ください。

> [![Evaluation Center からダウンロードする](../includes/media/download2.png)](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016)  **[Evaluation Center](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016)** から SQL Server 2016 をダウンロードする
>
> [![Azure Virtual Machine のアイコン](../includes/media/azure-vm.png)](https://azure.microsoft.com/marketplace/partners/microsoft/sqlserver2016sp1standardwindowsserver2016/) Azure アカウントをすでにお持ちですか?  **[こちら](https://azure.microsoft.com/marketplace/partners/microsoft/sqlserver2016sp1standardwindowsserver2016/)** にアクセスして、SQL Server 2016 SP1 がインストール済みの仮想マシンをすぐにご利用いただけます。
>
> [![SSMS をダウンロードする](../includes/media/download2.png)](../ssms/download-sql-server-management-studio-ssms.md) 最新版の SQL Server Management Studio を入手するには、「**[SQL Server Management Studio (SSMS) のダウンロード](../ssms/download-sql-server-management-studio-ssms.md)**」をご覧ください。

## <a name="bkmk_2016sp1"></a>SQL Server 2016 Service Pack 1 (SP1) を使用できる
![info_tip](../sql-server/media/info-tip.png) SQL Server 2016 SP1 では、SQL Server 2016 のすべてのエディションとサービス レベルを SQL Server 2016 SP1 にアップグレードします。 この記事に記載されている修正プログラムに加えて、SQL Server 2016 SP1 には、SQL Server 2016 Cumulative Update 1 (CU1) から SQL Server 2016 CU3 に含まれていた修正プログラムが含まれています。

- [SQL Server 2016 SP1 ダウンロード ページ](https://www.microsoft.com/download/details.aspx?id=54276)
- [SQL Server 2016 Service Pack 1 リリース情報](https://support.microsoft.com/kb/3182545) SP1 で修正または変更されたバグ番号と問題を一覧します。
 - ![info_tip](../sql-server/media/info-tip.png) のサービス パックを含む、サポートされるすべてのバージョンのリンクと情報については、「[SQL Server Update Center](https://msdn.microsoft.com/library/ff803383.aspx)」を参照してください。 [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] 

##  <a name="bkmk_2016_ga"></a>SQL Server 2016 Release - 一般公開 (GA)
-   [データベース エンジン (GA)](#bkmk_ga_instalpatch) 
-   [Stretch Database (GA)](#bkmk_ga_stretch)
-   [クエリ ストア (GA)](#bkmk_ga_query_store)
-   [製品ドキュメント (GA)](#bkmk_ga_docs)
 
### ![repl_icon_warn](../database-engine/availability-groups/windows/media/repl-icon-warn.gif) <a name="bkmk_ga_instalpatch"></a> Install Patch Requirement (GA) 
**問題およびユーザーへの影響:** SQL Server 2016 の前提条件としてインストールされる Microsoft VC++ 2013 ランタイム バイナリに影響を与える問題が見つかりました。 更新プログラムを利用してこの問題を修正できます。 VC ランタイム バイナリに対するこの更新プログラムをインストールしないと、特定のシナリオにおいて、SQL Server 2016 で安定性の問題が発生する可能性があります。 SQL Server 2016 をインストールする前に、 [KB 3164398](http://support.microsoft.com/kb/3164398)で説明されている修正プログラムがコンピューターに必要かどうかを確認してください。 修正プログラムは、[SQL Server 2016 RTM の累積的な更新プログラム パッケージ 1 (CU1)](https://www.microsoft.com/download/details.aspx?id=53338) にも含まれています。 

**解決方法:** 次の解決策のいずれかを使用します。

- [KB 3138367 - 2013 の Visual C++ および Visual C++ の再頒布可能パッケージ用の更新プログラム](http://support.microsoft.com/kb/3138367)をインストールします。 KB は推奨される解決方法です。 このインストールは、SQL Server 2016 のインストールの前でも後でも実行できます。 

    SQL Server 2016 が既にインストール済みの場合は、次の順序で手順を実行します。

    1.  該当する *vcredist_\*exe* をダウンロードします。
    1.  データベース エンジンのすべてのインスタンスで SQL Server サービスを停止します。
    1.  **KB 3138367**をインストールします。
    1.  コンピューターを再起動します。
 

 - [KB 3164398 - SQL Server 2016 MSVCRT の必須コンポーネントの重要な更新プログラム](http://support.microsoft.com/kb/3164398)をインストールします。  
 
    **KB 3164398**を使用する場合、SQL Server のインストール中、Microsoft Update の実行時、または Microsoft ダウンロード センターからインストールできます。 

    - **SQL Server 2016 のインストール中:** SQL Server セットアップを実行するコンピューターからインターネットにアクセスできる場合、SQL Server セットアップにより、SQL Server インストール全体の一部として更新プログラムが調べられます。 更新を承認すると、インストール中にセットアップによりバイナリがダウンロードされて更新されます。

    - **Microsoft Update:** Microsoft Update から、セキュリティに関連しない重要な SQL Server 2016 更新プログラムとしてこの更新プログラムを入手できます。 SQL Server 2016 のインストール後に Microsoft Update を使用してインストールした場合には、更新後にサーバーの再起動が必要になります。 

    - **ダウンロード センター:** 最後に、Microsoft ダウンロード センターから更新プログラムをダウンロードできます。 更新用のソフトウェアをダウンロードして、SQL Server 2016 がインストール済みのサーバーにインストールできます。 


### <a name="bkmk_ga_stretch"></a>Stretch Database

#### <a name="problem-with-a-specific-character-in-a-database-or-table-name"></a>データベースやテーブルの名前に特定の文字が使用される場合の問題

**問題およびユーザーへの影響:** データベースまたはテーブルで Stretch Database を有効にしようとすると、エラーが発生して失敗します。 この問題は、オブジェクトの名前に、小文字から大文字に変換されるときに別の文字として扱われる文字が含まれている場合に発生します。 この問題が発生する文字の例には、"ƒ" 文字 (ALT+159 を入力すると作成される) があります。

**回避策:** データベースかテーブルに対して Stretch Database を有効にするには、オブジェクトの名前を変更して問題の文字を削除するオプションしかありません。

#### <a name="problem-with-an-index-that-uses-the-include-keyword"></a>INCLUDE キーワードを使用するインデックスの問題

**問題およびユーザーへの影響:** テーブルに対して Stretch Database を有効にしようとする場合に、INCLUDE キーワードを使用して追加の列を組み込んでいるインデックスがそのテーブルにあると、エラーが発生して失敗します。

**回避策:** INCLUDE キーワードを使用しているインデックスを削除し、そのテーブルに対して Stretch Database を有効にしてから、インデックスを再作成します。 その場合には、組織のメンテナンスのプラクティスやポリシーに従っているか確認して、影響を受けるテーブルのユーザーに対する反響をなくすか最小限に抑えるようにしてください。

### <a name="bkmk_ga_query_store"></a>Query Store

#### <a name="problem-with-automatic-data-cleanup-on-editions-other-than-enterprise-and-developer"></a>Enterprise や Developer 以外のエディションでのデータの自動クリーンアップに関する問題

 **問題およびユーザーへの影響:** Enterprise や Developer 以外のエディションでデータの自動クリーンアップが失敗します。 その結果、データを手動で消去しないと、クエリ ストアに使用される領域は構成済みの制限に達するまで時間の経過と共に増えます。 この問題を回避しないと、エラー ログ用に割り当てられたディスク領域もいっぱいになります。クリーンアップを実行しようとするたびにダンプ ファイルが生成されるからです。 クリーンアップをアクティブ化する期間はワークロードの頻度に応じて異なりますが、15 分以内です。

 **回避策:** Enterprise や Developer 以外のエディションでクエリ ストアを使用する計画の場合は、クリーンアップのポリシーを明示的にオフにする必要があります。 この作業は、SQL Server Management Studio ([データベースのプロパティ] ページ) から行うか、Transact SQL スクリプトを使用して行うことができます。

```ALTER DATABASE <database name> SET QUERY_STORE (OPERATION_MODE = READ_WRITE, CLEANUP_POLICY = (STALE_QUERY_THRESHOLD_DAYS = 0), SIZE_BASED_CLEANUP_MODE = OFF)```

また、クエリ ストアが読み取り専用モードに移行しないように、手動クリーンアップのオプションを検討してください。 たとえば、次のクエリを実行して、データ領域全体を定期的にクリーンアップします。

```ALTER DATABASE <database name> SET QUERY_STORE CLEAR```

また、次のクエリ ストアのストアド プロシージャを定期的に実行して、ランタイム統計、特定のクエリ、または計画をクリーンアップします。

- `sp_query_store_reset_exec_stats`

- `sp_query_store_remove_plan`

- `sp_query_store_remove_query`


###  <a name="bkmk_ga_docs"></a> 製品ドキュメント (GA) 
 **問題およびユーザーへの影響:** SQL Server 2016 のドキュメントのダウンロード可能なバージョンはまだありません。 ヘルプ ライブラリ マネージャーを使って **オンラインからコンテンツをインストール**しようとすると、SQL Server 2012 および SQL Sever 2014 のドキュメントは表示されますが、SQL Server 2016 のドキュメントのオプションはありません。    
    
 **回避策:** 次のいずれかの回避策を使用してください。    
    
 ![SQL Server のヘルプ設定の管理](../sql-server/media/docs-sql2016-managehelpsettings.png "SQL Server のヘルプ設定の管理")    
    
-   **[オンラインまたはローカル ヘルプの選択]** オプションを使用し、[オンライン ヘルプを使用する] にヘルプを構成します。    
    
-   **[オンラインからコンテンツをインストール]** オプションを使用し、SQL Server 2014 のコンテンツをダウンロードします。    
    
 **F1 ヘルプ:** 仕様上、[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]で F1 キーを押すと、ブラウザーでオンライン バージョンの F1 ヘルプ記事が表示されます。 この問題は、ブラウザー ベースのヘルプで、ローカル ヘルプのインストールを構成した場合でも発生します。 
     
**コンテンツの更新:**    
SQL Server Management Studio と Visual Studio では、ドキュメントの追加プロセス中に、ヘルプ ビューアーのアプリケーションが凍結 (ハング) することがあります。 この問題を解決するには、次の手順を実行します。 この問題の詳細については、「 [Visual Studio ヘルプ ビューアーがフリーズする](https://msdn.microsoft.com/library/mt654096.aspx)」を参照してください。    
    
* メモ帳で %LOCALAPPDATA%\Microsoft\HelpViewer2.2\HlpViewer_SSMS16_en-US.settings | HlpViewer_VisualStudio14_en-US.settings ファイルを開き、次のコード内の日付を将来の日付に変更します。    
    
     
```    
     Cache LastRefreshed="12/31/2017 00:00:00"    
``` 

## <a name="additional-information"></a>追加情報
+ [SQL Server 2016 のインストール](../database-engine/install-windows/installation-for-sql-server-2016.md)
+ [SQL Server Update Center - サポート対象のすべてのバージョンのリンクと情報](https://msdn.microsoft.com/library/ff803383.aspx)


[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]    

![MS_Logo_X-Small](../sql-server/media/ms-logo-x-small.png "MS_Logo_X-Small")    
