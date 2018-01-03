---
title: "SQL ツール、および SQL Server、Azure SQL データベース、および Azure SQL Data Warehouse ユーティリティ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/15/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: misc
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
caps.latest.revision: "0"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 792d80357f62fcc76576dad24105edead20dac44
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="sql-tools-and-utilities-for-sql-server-azure-sql-database-and-azure-sql-data-warehouse"></a>SQL ツールとユーティリティの SQL Server、Azure SQL データベース、および Azure SQL Data Warehouse
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]


## <a name="tools-to-run-queries-and-manage-databases"></a>クエリを実行し、データベースの管理ツール  

| ツール | Description |
|:--|:--|
| [[!INCLUDE[name-sos](../includes/name-sos.md)]](../sql-operations-studio/download.md) | [!INCLUDE[name-sos](../includes/name-sos-short.md)]実行されている場所にデータベースを管理するための無料で軽量のツールです。 このプレビュー リリースでは、拡張 TRANSACT-SQL エディターと、データベースの操作状態のカスタマイズ可能な洞察など、データベースの管理機能を提供します。 **[!INCLUDE[name-sos](../includes/name-sos-short.md)]Windows、macOS、および Linux で実行される**です。|
| [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md) | クエリ、設計、および SQL Server、Azure SQL データベース、および Azure SQL Data Warehouse を管理するには、SQL Server Management Studio (SSMS) を使用します。 **Windows で SSMS を実行**です。|
| [SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md) | SQL Server、Azure SQL データベース、および Azure SQL Data Warehouse の強力な開発環境に Visual Studio を有効にします。 **SSDT は、Windows で実行**です。|
| [Visual Studio Code](https://code.visualstudio.com/)| Visual Studio のコードをインストールすると、インストール、 [mssql 拡張子](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql)Microsoft SQL Server、Azure SQL データベース、および SQL Data Warehouse を開発するためです。 **Visual Studio のコードは、Windows、macOS、および Linux で実行**です。|

## <a name="which-tool-should-i-choose"></a>どのツールを選択する必要がありますか。

- SQL Server インスタンスまたはデータベースで、Windows、Linux または Mac 上の軽量なエディターで管理しますか? 選択します。[[!INCLUDE[name-sos](../includes/name-sos.md)]](../sql-operations-studio/download.md) | [!INCLUDE[name-sos](../includes/name-sos-short.md)] 
- SQL Server インスタンスまたは完全な GUI サポートと Windows 上のデータベースを管理しますか? 選択[SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md)
- 作成またはコンパイル時の検証を含む、データベースのコードを保守する、Windows 上でのリファクタリングおよびデザイナー サポートしますか。 選択[SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md)
- Windows、Linux または Mac で軽量なエディターで T-SQL スクリプトを記述しますか。 選択[Visual Studio Code](https://code.visualstudio.com/)と[mssql 拡張機能](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql)

## <a name="additional-tools"></a>その他のツール

| ツール | Description |
|:--|:--|
| [構成マネージャー](../tools/configuration-manager/sql-server-configuration-manager-help.md) | SQL Server 構成マネージャーを使用して SQL Server サービスを構成し、ネットワーク接続を構成します。|
| [SQL Server Migration Assistant](../ssma/sql-server-migration-assistant.md) | Microsoft Access、DB2、MySQL、Oracle、および Sybase から SQL Server にデータベースの移行を自動化するのにには、SQL Server Migration Assistant を使用します。|
| [分散再生](../tools/distributed-replay/install-distributed-replay-overview.md) | SQL Server の将来のアップグレードの影響を評価するためには、分散再生の機能を使用します。 また Distributed Replay を使用して、ハードウェアとオペレーティング システムのアップグレード、および SQL Server のチューニングの影響を評価します。 |
| [ssbdiagnose](../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md) | Ssbdiagnose ユーティリティは、Service Broker メッセージ交換または Service Broker サービスの構成に関する問題を報告します。 |


## <a name="command-line-utilities"></a>コマンド ライン ユーティリティ

  コマンド ライン ユーティリティを使用するスクリプトと[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]操作します。 次の表は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]に付属するコマンド プロンプト ユーティリティの一覧です。  
  
|**Utility**|**Description**|**インストール先**|  
|-----------------|---------------------|----------------------|  
|[bcp ユーティリティ](../tools/bcp-utility.md)|ユーザー指定の形式で、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスとデータ ファイルとの間でデータをコピーします。|\<*ドライブ*: > \Program Files\\[!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]\Client SDK\ODBC\110\Tools\Binn|  
|[dta ユーティリティ](../tools/dta/dta-utility.md)|作業負荷の分析、およびその作業負荷に対してサーバー パフォーマンスを最適化するための推奨物理デザイン構造の分析を行います。|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[dtexec ユーティリティ](../integration-services/packages/dtexec-utility.md)|[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージを構成および実行します。 このコマンド プロンプト ユーティリティのユーザー インターフェイス バージョンは **DTExecUI**と呼ばれ、パッケージ実行ユーティリティが表示されます。|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]DTS\Binn|  
|[dtutil ユーティリティ](../integration-services/dtutil-utility.md)|SSIS パッケージを管理します。|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]DTS\Binn|  
|[配置ユーティリティを使用したモデル ソリューションの配置](../analysis-services/multidimensional-models/deploy-model-solutions-with-the-deployment-utility.md)|[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] プロジェクトを [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]のインスタンスに配置します。|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn\VShell\Common7\IDE|  
|[mssql scripter (パブリック プレビュー)](https://blogs.technet.microsoft.com/dataplatforminsider/2017/05/17/try-new-sql-server-command-line-tools-to-generate-t-sql-scripts-and-monitor-dynamic-management-views/)|SQL Server、Azure SQL データベース、および Azure SQL Data Warehouse でのデータベース オブジェクトの作成と挿入の T-SQL スクリプトを生成するために使用します。|参照してください、 [GitHub リポジトリの](https://github.com/Microsoft/sql-xplat-cli)ダウンロードと使用状況情報についてはします。| 
|[osql ユーティリティ](../tools/osql-utility.md)|[!INCLUDE[tsql](../includes/tsql-md.md)] ステートメント、システム プロシージャ、およびスクリプト ファイルをコマンド プロンプトで入力できるようになります。|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[profiler ユーティリティ](../tools/profiler-utility.md)|コマンド プロンプトから [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] を起動します。|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[RS.exe ユーティリティ &#40;SSRS&#41;](../reporting-services/tools/rs-exe-utility-ssrs.md)|[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] レポート サーバーを管理するために作成されたスクリプトを実行します。|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[rsconfig ユーティリティ &#40;SSRS&#41;](../reporting-services/tools/rsconfig-utility-ssrs.md)|レポート サーバー接続を構成します。|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[rskeymgmt ユーティリティ &#40;SSRS&#41;](../reporting-services/tools/rskeymgmt-utility-ssrs.md)|レポート サーバー上の暗号化キーを管理します。|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[sqlagent90 アプリケーション](../tools/sqlagent90-application.md)|コマンド プロンプトから [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェントを開始します。|\<ドライブ >: \Program Files\Microsoft SQL Server\\<*instance_name*> \MSSQL\Binn|  
|[sqlcmd Utility](../tools/sqlcmd-utility.md)|[!INCLUDE[tsql](../includes/tsql-md.md)] ステートメント、システム プロシージャ、およびスクリプト ファイルをコマンド プロンプトで入力できるようになります。|\<*ドライブ*: > \Program Files\\[!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]\Client SDK\ODBC\110\Tools\Binn|  
|[SQLdiag ユーティリティ](../tools/sqldiag-utility.md)|[!INCLUDE[msCoName](../includes/msconame-md.md)] カスタマー サポート サービス用の診断情報を収集します。|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[sqllogship アプリケーション](../tools/sqllogship-application.md)|バックアップ、コピー、および復元ジョブを実行することなく、ログ配布構成のバックアップ、コピー、復元操作、および関連するクリーンアップ作業を行うために使用されます。|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[SqlLocalDB ユーティリティ](../tools/sqllocaldb-utility.md)|プログラムの開発者を対象とした [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の実行モードです。|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn\|  
|[sqlmaint ユーティリティ](../tools/sqlmaint-utility.md)|以前のバージョンの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]で作成されたデータベース メンテナンス プランを実行します。|\<ドライブ >: \Program Files\Microsoft SQL Server\MSSQL13 です。MSSQLSERVER\MSSQL\Binn|  
|[sqlps ユーティリティ](../tools/sqlps-utility.md)|PowerShell コマンドおよびスクリプトを実行します。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell プロバイダーおよびコマンドレットの読み込みと登録を行います。|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[sqlservr アプリケーション](../tools/sqlservr-application.md)|トラブルシューティングを行うために、コマンド プロンプトから [!INCLUDE[ssDE](../includes/ssde-md.md)] インスタンスを開始および停止します。|\<ドライブ >: \Program Files\Microsoft SQL Server\MSSQL13 です。MSSQLSERVER\MSSQL\Binn|  
|[Ssms ユーティリティ](../tools/sql-server-management-studio/ssms-utility.md)|コマンド プロンプトから [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] を起動します。|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn\VSShell\Common7\IDE|  
|[tablediff ユーティリティ](../tools/tablediff-utility.md)|2 つのテーブルのデータを比較し、非収束について調査します。これは、レプリケーション トポロジのトラブルシューティングを行う場合に便利です。|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]COM (COM)|  

## <a name="sql-command-prompt-utilities-syntax-conventions"></a>SQL コマンド プロンプト ユーティリティの構文規則  
  
|**表記**|**使用目的**|  
|--------------------|------------------|  
|大文字|オペレーティング システム レベルで使用するステートメントと用語|  
|`monospace`|サンプルのコマンドとプログラム コード|  
|*斜体*|ユーザーが指定するパラメーター|  
|**太字**|示されたとおりに入力する必要があるコマンド、パラメーター、およびその他の構文|  


