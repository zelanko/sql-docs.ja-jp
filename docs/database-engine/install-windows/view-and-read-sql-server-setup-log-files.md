---
title: SQL Server セットアップ ログ ファイルの表示と読み取り | Microsoft Docs
ms.custom: ''
ms.date: 09/08/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: install
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- viewing logs
- displaying log files
- Setup [SQL Server], logs
- installation log files [SQL Server]
- installing SQL Server, logs
- errors [SQL Server], Setup
- logs [SQL Server], Setup
ms.assetid: 9d77af64-9084-4375-908a-d90f99535062
caps.latest.revision: 54
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4d3b40219a412b498e891d0550a10a99e23b7adf
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2018
ms.locfileid: "34771458"
---
# <a name="view-and-read-sql-server-setup-log-files"></a>SQL Server セットアップ ログ ファイルの表示と読み取り

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server セットアップでは既定で、%programfiles%\Microsoft SQL Server\\*nnn*\Setup Bootstrap\Log 内にあるタイムスタンプ付きのログ フォルダーにログ ファイルが作成されます。 タイムスタンプ付きのログ フォルダーの名前形式は YYYYMMDD_hhmmss です。 セットアップを自動モードで実行した場合は、%temp%\sqlsetup*.log 内にログが作成されます。 ログ フォルダー内のログ ファイルはすべて、それぞれのログ フォルダー内で Log\*.cab ファイルにアーカイブされます。  

 ![setup-bootstrap-example.png](media/view-and-read-sql-server-setup-log-files/setup-bootstrap-example.png)

 >[!NOTE]
 > パス *nnn* の数字は、インストールされる SQL のバージョンに相当します。 上記の画像では、SQL 2017 がインストールされ、フォルダーは 140 です。 SQL 2016 の場合、フォルダーは 130 になり、SQL 2014 の場合、フォルダーは 120 になります。
  
 SQL Server セットアップでは、3 つの基本的な段階が完了します。 
  
1.  グローバル ルール検証: 基本的なシステム要件を検証します
2.  コンポーネント更新: インストールされているメディアに対して利用できる更新があるかどうかを確認します
3.  ユーザーが要求した操作: ユーザーは機能を選択し、カスタマイズできます
  

このワークフローによって概要ログが 1 つ生成され、RTM インストールの場合、詳細ログが 1 つ生成され、メディアのスリップストリームの場合、詳細ログが 2 つ生成されます。
  
データストア ファイルには、セットアップ プロセスによって追跡記録されるすべての構成オブジェクトの状態を示すスナップショットが含まれており、構成エラーのトラブルシューティングに便利です。 XML ダンプ ファイルが実行段階ごとに作成され、タイムスタンプ付きのログ フォルダー内の Datastore ログ サブフォルダーに保存されます。 

次のセクションでは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップのログ ファイルを説明します。  
  
## <a name="summarytxt-file"></a>Summary.txt ファイル 
  
### <a name="overview"></a>概要  
 このファイルは、セットアップ時に検出された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネント、オペレーティング システム環境、指定されているコマンド ライン パラメーター値、および実行された各 MSI/MSP の全体的な状態を示します。
  
 ログは次の各セクションに整理されています。
  
-   実行全体の要約  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップが実行されたコンピューターのプロパティと構成  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] そのコンピューターに以前にインストールされていた製品の機能  
-   インストールされたバージョンとインストール パッケージのプロパティ
-   インストール時に提供されたランタイム入力設定  
-   構成ファイルの場所  
-   実行結果の詳細  
-   グローバル ルール  
-   そのインストール シナリオ独自のルール  
-   失敗したルール  
-   ルール レポート ファイルの場所


  >[!NOTE]
  > 修正プログラムの適用時、似たような一連のファイルが含まれるサブフォルダーがたくさん存在することがあります (修正プログラムが適用されるインスタンスごとにサブフォルダーが 1 つ、共有機能のために 1 つ) (すなわち、%programfiles%\MicrosoftSQL Server\130\Setup Bootstrap\Log\<YYYYMMDD_HHMM>\MSSQLSERVER)。 
  
### <a name="location"></a>場所  
 summary.txt は %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\*nnn*\Setup Bootstrap\Log\\ 内にあります。
  
 概要テキスト ファイル内でエラーを見つけるには、"エラー" や "失敗" をキーワードにして検索できます。
  
## <a name="summarymachinenameyyyymmddhhmmsstxt-file"></a>Summary_\<MachineName>_YYYYMMDD_HHMMss.txt ファイル
  
### <a name="overview"></a>概要  
 summary_engine の基本的なファイルは概要ファイルに似ていますが、メイン ワークフロー内で生成されます。
  
### <a name="location"></a>場所  
 Summary_\<MachineName>_YYYYMMDD_HHMMss.txt ファイルは %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\*nnn*\Setup Bootstrap\Log\\<YYYYMMDD_HHMM>\\ にあります。
  
  
## <a name="detailtxt-file"></a>Detail.txt ファイル
  
### <a name="overview"></a>概要
 Detail.txt はインストールやアップグレードなど、メイン ワークフロー内で生成され、実行の詳細を示します。 ファイル内のログは、インストールの各アクションが呼び出されたときの時刻に基づいて生成されます。 テキスト ファイルには、アクションが実行された順所とその依存関係が示されます。  
  
### <a name="location"></a>場所  
 detail.txt ファイルは %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\*nnn*\Setup Bootstrap\Log\\<YYYYMMDD_HHMM>\Detail.txt 内にあります。  
  
 セットアップ過程でエラーが発生すると、例外やエラーはこのファイルの終わりに記録されます。 このファイル内でエラーを見つけるには、まずファイルの終わりを調べてから、"エラー" や "例外" をキーワードにして検索します。
    
## <a name="msi-log-files"></a>MSI ログ ファイル
  
### <a name="overview"></a>概要  
 MSI ログ ファイルはパッケージ インストール過程の詳細を提供します。 各パッケージのインストール時に、MSIEXEC によって生成されるログ ファイルです。  
  
 MSI ログ ファイルの種類
  
-   \<機能>_\<アーキテクチャ>\_\<相互作用>.log   
-   \<機能>_\<アーキテクチャ>\_\<言語>\_\<相互作用>.log   
-   \<機能>_\<アーキテクチャ>\_\<相互作用>\_\<ワークフロー>.log  
  
### <a name="location"></a>場所  
 MSI ログ ファイルは %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\*nnn*\Setup Bootstrap\Log\\<YYYYMMDD_HHMM>\\<Name\>.log にあります。  
  
 ファイルの終わりに実行の概要があり、成功したかどうかとプロパティを示します。 MSI ファイルのエラーを見つけるには、"value 3" を探し、その前後のテキストを確認します。  
  
## <a name="configurationfileini-file"></a>ConfigurationFile.ini ファイル
  
### <a name="overview"></a>概要  
 構成ファイルにはインストール時に使用される入力の設定が含まれています。 手動で設定を入力しなくてもインストールを再起動できるようにするときに使用できます。 ただし、パスワード、PID、およびパラメーターの一部は構成ファイルには保存されません。 設定はファイルに追加できますが、コマンドラインまたはセットアップのインターフェイスを使って供給することもできます。 詳細については、「 [構成ファイルを使用した SQL Server 2016 のインストール](../../database-engine/install-windows/install-sql-server-2016-using-a-configuration-file.md)」を参照してください。  
  
### <a name="location"></a>場所  
 ConfigurationFile.ini は %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\*nnn*\Setup Bootstrap\Log\\<YYYYMMDD_HHMM>\\ にあります。  
  
## <a name="systemconfigurationcheckreporthtm-file"></a>SystemConfigurationCheck_Report.htm ファイル
  
### <a name="overview"></a>概要  
 システム構成チェッカーのレポートには、実行された各ルールの簡単な記述と、実行ステータスが含まれています。
  
### <a name="location"></a>場所  
SystemConfigurationCheck_Report.htm は %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\*nnn*\Setup Bootstrap\Log\\<YYYYMMDD_HHMM>\\ にあります。
  
## <a name="see-also"></a>参照  
 [SQL Server 2017 のインストール](../../database-engine/install-windows/install-sql-server.md)
