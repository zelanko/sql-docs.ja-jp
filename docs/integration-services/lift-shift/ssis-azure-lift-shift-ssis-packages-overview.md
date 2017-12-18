---
title: "SQL Server Integration Services ワークロードをクラウドにリフト アンド シフトする | Microsoft Docs"
ms.date: 10/31/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: lift-shift
ms.suite: sql
ms.custom: 
ms.technology: integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7ddfcca6408a64b2c2875aaa625c275899e8c85f
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="lift-and-shift-sql-server-integration-services-workloads-to-the-cloud"></a>SQL Server Integration Services ワークロードをクラウドにリフト アンド シフトする
SQL Server Integration Services (SSIS) パッケージとワークロードを Azure クラウドに移動できるようになりました。
-   SSIS プロジェクトとパッケージを Azure SQL Database の SSIS カタログ データベース (SSISDB) に格納して管理します。
-   Azure Data Factory バージョン 2 の一部として導入された、Azure SSIS Integration Runtime のインスタンスでパッケージを実行します。
-   これらの一般的なタスクには、SQL Server Management Studio (SSMS) などの使い慣れたツールを使用します。

## <a name="benefits"></a>利点
オンプレミスの SSIS ワークロードを Azure に移動すると、次の潜在的な利点があります。
-   **運用コストを削減**し、SSIS をオンプレミスまたは Azure の仮想マシンで実行するのに必要なインフラストラクチャを管理するための作業負荷を軽減します。
-   クラスターごとの複数のノードを指定する機能と、Azure および Azure SQL Database の高可用性機能により、**高可用性が向上**します。
-   ノード (スケール アップ) ごとに複数のコアとクラスター (スケール アウト) ごとに複数のノードを指定する機能により、**スケーラビリティが向上**します。

## <a name="architecture-overview"></a>アーキテクチャの概要
次の表に、オンプレミスの SSIS と Azure の SSIS の違いを示します。 最も重要な違いは、計算からの記憶域の分離です。

| ストレージ | ランタイム | スケーラビリティ |
|---|---|---|
| オンプレミス (SQL Server) | SQL Server でホストされている SSIS ランタイム | SSIS Scale Out (SQL Server 2017 以降)<br/><br/>カスタム ソリューション (SQL Server の以前のバージョン) |
| Azure (SQL Database) | Azure SSIS Integration Runtime、Azure Data Factory バージョン 2 のコンポーネント | SSIS IR のスケーリング オプション |
| | | |

Azure Data Factory では、Azure で SSIS パッケージのランタイム エンジンをホストします。 ランタイム エンジンは、Azure SSIS Integration Runtime (SSIS IR) と呼ばれます。

SSIS IR をプロビジョニングする際に、次のオプションの値を指定して、スケール アップとスケール アウトができます。
-   ノード サイズ (コアの数を含む) とクラスター内のノードの数。
-   SSIS カタログ データベース (SSISDB) をホストする Azure SQL Database の既存のインスタンス、およびデータベース用のサービス層。
-   ノードごとの最大並列実行。

SSIS IR は 1 回だけプロビジョニングを行う必要があります。 その後は、SQL Server Data Tools (SSDT) や SQL Server Management Studio (SSMS) などの使い慣れたツールを使用して、パッケージの配置、構成、実行、監視、スケジュール、および管理ができます。

> [!NOTE]
> このパブリック プレビュー中は、Azure SSIS Integration Runtime は、すべてのリージョンで利用できるわけではありません。 サポートされているリージョンについては、「[リージョン別の利用可能な製品 - Microsoft Azure](https://azure.microsoft.com/regions/services/)」を参照してください。

Data Factory は、他の種類の Integration Runtime もサポートしています。 SSIS IR と他の種類の Integration Runtime の詳細については、「[Azure Data Factory の統合ランタイム](https://docs.microsoft.com/azure/data-factory/concepts-integration-runtime)」を参照してください。

## <a name="prerequisites"></a>前提条件
このトピックで説明されている機能には、SQL Server 2017 または SQL Server 2016 は必要ありません。

これらの機能には、次のバージョンの SQL Server Data Tools (SSDT) が必要です。
-   Visual Studio 2017 の場合、バージョン 15.3 (プレビュー) 以降。
-   Visual Studio 2015 の場合、バージョン 17.2 以降。

> [!NOTE]
> パッケージを Azure に配置すると、常に最新のパッケージ形式となるように、パッケージの配置ウィザードによってパッケージがアップグレードされます。

Azure の前提条件の詳細については、「[SQL Server Integration Services パッケージを Azure にデプロイする](https://docs.microsoft.com/azure/data-factory/tutorial-deploy-ssis-packages-azure)」を参照してください。

## <a name="ssis-features-on-azure"></a>Azure の SSIS 機能

SSISDB をホストする SQL Database のインスタンスをプロビジョニングする際に、SSIS 用 Azure Feature Pack と Access Redistributable もインストールされます。 これらのコンポーネントは、組み込みのコンポーネントでサポートされるデータ ソースの他に、**Excel ファイルと Access ファイル**、およびさまざまな **Azure** データ ソースへの接続を提供します。 この時点では、SSIS 用の**サード パーティ コンポーネント** (Attunity や SAP BI コンポーネントなど、Microsoft が提供するサード パーティ コンポーネントを含む) をインストールすることはできません。

SSISDB をホストする **SQL Database の名前**が、SSDT および SSMS からパッケージを配置して管理する際に使用する 4 つの部分から成る名前の最初の部分になります: `<sql_database_name>.database.windows.net`。

Azure SQL Database の SSISDB に配置するプロジェクトには、パッケージ配置モデルではなく、**プロジェクト配置モデル**を使用する必要があります。

SSDT のオンプレミス、または SSDT がインストールされた Visual Studio で、**パッケージの設計とビルド**を続行します。

Windows 認証を使用してクラウドから**オンプレミスのデータ ソース**に接続する方法については、「[Windows 認証でオンプレミス データ ソースに接続する](ssis-azure-connect-with-windows-auth.md)」を参照してください。

## <a name="common-tasks"></a>よく使用するタスク

### <a name="provision"></a>プロビジョニング
Azure で SSIS パッケージをデプロイして実行するには、事前に SSISDB カタログ データベースと Azure SSIS Integration Runtime をプロビジョニングする必要があります。 「[SQL Server Integration Services パッケージを Azure にデプロイする](https://docs.microsoft.com/azure/data-factory/tutorial-deploy-ssis-packages-azure)」のプロビジョニングの手順に従います。

### <a name="deploy-and-run-packages"></a>パッケージの配置と実行
SQL Database でプロジェクトの配置と実行は、使い慣れたツールやスクリプト作成オプションのいずれかを使用して行えます。
-   SQL Server Management Studio (SSMS)
-   Transact-SQL (SSMS、Visual Studio Code、または別のツールから)
-   コマンドライン ツール
-   PowerShell
-   C# と SSIS の管理オブジェクト モデル

### <a name="monitor-packages"></a>パッケージの監視
SSMS での実行中のパッケージを監視するには、SSMS で次のレポート作成ツールのいずれかを使用できます。
-   **[SSISDB]** を右クリックし、**[アクティブな操作]** を選択して、**[アクティブな操作]** ダイアログ ボックスを開きます。
-   オブジェクト エクスプローラーでパッケージを選択し、右クリックして **[レポート]** を選択し、**[標準レポート]**、**[すべての実行]** の順に選択します。

### <a name="schedule-packages"></a>パッケージのスケジュール設定
SQL Database に格納されたパッケージの実行をスケジュール設定するには、次のツールを使用できます。
-   オンプレミスの SQL Server エージェント
-   Data Factory SQL Server ストアド プロシージャ アクティビティ

詳細については、「[Azure で SSIS パッケージの実行をスケジュールする](ssis-azure-schedule-packages.md)」を参照してください。

## <a name="next-steps"></a>次の手順
Azure で SSIS ワークロードの使用を開始するには、次の記事を参照してください。
-   [SQL Server Integration Services パッケージを Azure にデプロイする](https://docs.microsoft.com/azure/data-factory/tutorial-deploy-ssis-packages-azure)
-   [Azure で SSIS パッケージを配置、実行、および監視する](ssis-azure-deploy-run-monitor-tutorial.md)
