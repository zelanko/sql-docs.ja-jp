---
title: SQL Server Integration Services ワークロードをクラウドにリフト アンド シフトする | Microsoft Docs
ms.date: 05/22/2018
ms.topic: conceptual
ms.prod: sql
ms.prod_service: integration-services
ms.component: lift-shift
ms.suite: sql
ms.custom: ''
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f62987a7edc2d04f88c3cfe98f04f0bd6043b44a
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34585574"
---
# <a name="lift-and-shift-sql-server-integration-services-workloads-to-the-cloud"></a>SQL Server Integration Services ワークロードをクラウドにリフト アンド シフトする
SQL Server Integration Services (SSIS) パッケージとワークロードを Azure クラウドに移動できるようになりました。
-   SSIS プロジェクトとパッケージを Azure SQL Database の SSIS カタログ データベース (SSISDB) または Azure SQL Database マネージ インスタンス (プレビュー) に格納して管理します。
-   Azure Data Factory のコンポーネントである、Azure SSIS 統合ランタイムのインスタンスでパッケージを実行します。
-   一般的なタスクには、SQL Server Management Studio (SSMS) などの使い慣れたツールを使用します。

## <a name="benefits"></a>利点
オンプレミスの SSIS ワークロードを Azure に移動すると、次の潜在的な利点があります。
-   **運用コストを削減**し、SSIS をオンプレミスまたは Azure の仮想マシンで実行するのに必要なインフラストラクチャを管理するための作業負荷を軽減します。
-   クラスターごとの複数のノードを指定する機能と、Azure および Azure SQL Database の高可用性機能により、**高可用性が向上**します。
-   ノード (スケール アップ) ごとに複数のコアとクラスター (スケール アウト) ごとに複数のノードを指定する機能により、**スケーラビリティが向上**します。

## <a name="architecture-overview"></a>アーキテクチャの概要
次の表に、オンプレミスの SSIS と Azure の SSIS の違いを示します。 最も重要な違いは、ランタイムからの記憶域の分離です。 Azure Data Factory では、Azure で SSIS パッケージのランタイム エンジンをホストします。 ランタイム エンジンは、Azure SSIS 統合ランタイム (Azure SSIS IR) と呼ばれます。 詳細については、「[Azure SSIS 統合ランタイム](https://docs.microsoft.com/azure/data-factory/concepts-integration-runtime#azure-ssis-integration-runtime)」を参照してください。

| ストレージ | ランタイム | スケーラビリティ |
|---|---|---|
| オンプレミス (SQL Server) | SQL Server でホストされている SSIS ランタイム | SSIS Scale Out (SQL Server 2017 以降)<br/><br/>カスタム ソリューション (SQL Server の以前のバージョン) |
| Azure (SQL Database または Azure SQL Database マネージ インスタンス (プレビュー)) | Azure SSIS 統合ランタイム、Azure Data Factory のコンポーネント | Azure SSIS 統合ランタイムのスケーリング オプション |
| | | |

Azure SSIS IR は 1 回だけプロビジョニングを行う必要があります。 その後は、SQL Server Data Tools (SSDT) や SQL Server Management Studio (SSMS) などの使い慣れたツールを使用して、パッケージの配置、構成、実行、監視、スケジュール、および管理ができます。

## <a name="version-support"></a>バージョンのサポート

SSIS の任意のバージョンで作成されたパッケージを Azure にデプロイすることができます。 Azure にパッケージをデプロイするときに、検証エラーがなければ、パッケージは最新のパッケージ形式に自動的にアップグレードされます。 つまり、常に SSIS の最新バージョンにアップグレードされます。

デプロイ プロセスでは、パッケージが Azure SSIS Integration Runtime で実行できることを確認するための検証が行われます。 詳細については、「[Azure にデプロイされた SSIS パッケージの検証](ssis-azure-validate-packages.md)」を参照してください。

## <a name="prerequisites"></a>Prerequisites

SSIS パッケージを Azure にデプロイするには、次のいずれかのバージョンの SQL Server Data Tools (SSDT) が必要です。
-   Visual Studio 2017 の場合、バージョン 15.3 以降。
-   Visual Studio 2015 の場合、バージョン 17.2 以降。

Azure SSIS 統合ランタイムの前提条件については、「[SQL Server Integration Services パッケージを Azure にデプロイする - 前提条件](https://docs.microsoft.com/azure/data-factory/tutorial-deploy-ssis-packages-azure#prerequisites)」を参照してください。

> [!NOTE]
> このパブリック プレビュー中は、Azure SSIS 統合ランタイムは、すべてのリージョンで利用できるわけではありません。 サポートされているリージョンについては、「[リージョン別の利用可能な製品 - Microsoft Azure](https://azure.microsoft.com/regions/services/)」を参照してください。

## <a name="provision-ssis-on-azure"></a>Azure での SSIS のプロビジョニング

Azure で SSIS パッケージをデプロイして実行するには、事前に SSIS カタログ データベース (SSISDB) と Azure SSIS Integration Runtime をプロビジョニングする必要があります。 「[SQL Server Integration Services パッケージを Azure にデプロイする](https://docs.microsoft.com/azure/data-factory/tutorial-deploy-ssis-packages-azure)」のプロビジョニングの手順に従います。

Azure SSIS IR をプロビジョニングする際に、次のオプションの値を指定して、スケール アップとスケール アウトができます。
-   ノード サイズ (コアの数を含む) とクラスター内のノードの数。
-   SSIS カタログ データベース (SSISDB) をホストする Azure SQL Database の既存のインスタンス、およびデータベース用のサービス層。
-   ノードごとの最大並列実行。

パフォーマンスに関する詳細については、「[Azure-SSIS 統合ランタイムを高パフォーマンス用に構成する](https://docs.microsoft.com/azure/data-factory/configure-azure-ssis-integration-runtime-performance)」を参照してください。

## <a name="design-packages"></a>パッケージの設計

SSDT のオンプレミス、または SSDT がインストールされた Visual Studio で、**パッケージの設計とビルド**を続行します。

### <a name="connect-to-data-sources"></a>データ ソースに接続する

**Windows 認証**を使用してクラウドからオンプレミスのデータ ソースに接続する方法については、「[Windows 認証でオンプレミス データ ソースと Azure ファイル共有に接続する](ssis-azure-connect-with-windows-auth.md)」を参照してください。

ファイルとファイル共有に接続する方法については、「[オンプレミスおよび Azure のファイル共有のファイルを格納および取得する](ssis-azure-files-file-shares.md)」を参照してください。

### <a name="available-ssis-components"></a>使用可能な SSIS コンポーネント

SSISDB をホストする SQL Database のインスタンスをプロビジョニングする際に、SSIS 用 Azure Feature Pack と Access Redistributable もインストールされます。 これらのコンポーネントは、組み込みのコンポーネントでサポートされるデータ ソースの他に、さまざまな **Azure** データ ソース、および **Excel ファイルと Access ファイル**への接続を提供します。

追加のコンポーネントもインストールできます。たとえば、既定ではインストールされないドライバーをインストールできます。 詳細については、「[Custom setup for the Azure-SSIS integration runtime](/azure/articles/data-factory/how-to-configure-azure-ssis-ir-custom-setup.md)」(Azure-SSIS 統合ランタイムのカスタム設定) を参照してください。

ISV は、ライセンスのあるコンポーネントのインストールを Azure で使用できるように更新する必要があります。 詳細については、「[Azure SSIS 統合ランタイムの有料 (ライセンスあり) カスタム コンポーネントを開発する](https://docs.microsoft.com/azure/data-factory/how-to-develop-azure-ssis-ir-licensed-components)」を参照してください。

### <a name="transaction-support"></a>トランザクションのサポート

オンプレミスと Azure 仮想マシンでの SQL Server では、Microsoft 分散トランザクション コーディネーター (MSDTC) トランザクションを使用することができます。 Azure SSIS IR の各ノードで MSDTC を構成するには、カスタム設定の機能を使用します。 詳細については、「[Custom setup for the Azure-SSIS integration runtime](https://docs.microsoft.com/azure/data-factory/how-to-configure-azure-ssis-ir-custom-setup)」(Azure-SSIS 統合ランタイムのカスタム設定) を参照してください。

Azure SQL Database では、エラスティック トランザクションのみを使用できます。 詳細については、「[クラウド データベースにまたがる分散トランザクション](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-transactions-overview)」を参照してください。

## <a name="deploy-and-run-packages"></a>パッケージの配置と実行

作業を開始する場合は、「[Azure で SSIS パッケージを配置、実行、および監視する](ssis-azure-deploy-run-monitor-tutorial.md)」を参照してください。

### <a name="connect-to-ssisdb"></a>SSISDB に接続する

SSISDB をホストする **SQL Database の名前**が、SSDT および SSMS からパッケージを配置して実行する際に使用する 4 つの部分から成る名前の最初の部分になります。次のような形式です: `<sql_database_name>.database.windows.net`。 Azure で SSIS カタログ データベースに接続する方法の詳細については、「[Azure 上の SSISDB カタログ データベースへの接続](ssis-azure-connect-to-catalog-database.md)」を参照してください。

### <a name="deploy-projects-and-packages"></a>プロジェクトとパッケージをデプロイする

Azure の SSISDB にプロジェクトをデプロイする場合には、パッケージ配置モデルではなく、**プロジェクト配置モデル**を使用する必要があります。

Azure でプロジェクトをデプロイするには、次の使い慣れたツールやスクリプト作成オプションのいずれかを使用できます。
-   SQL Server Management Studio (SSMS)
-   Transact-SQL (SSMS、Visual Studio Code、または別のツールから)
-   コマンドライン ツール
-   PowerShell または C# と SSIS の管理オブジェクト モデル

SSMS と Integration Services デプロイ ウィザードを使用するデプロイ例については、[Azure で SSIS パッケージをデプロイし、実行し、監視する](ssis-azure-deploy-run-monitor-tutorial.md)方法に関するページを参照してください。

### <a name="run-packages"></a>パッケージを実行する

Azure にデプロイされている SSIS パッケージの実行に使用できる方法の概要については、[Azure で SSIS パッケージを実行する](ssis-azure-run-packages.md)方法に関するページを参照してください。

## <a name="pass-runtime-values-with-environments"></a>環境を利用してランタイム値を渡す

Azure Data Factory パイプラインの一部として実行するパッケージに 1 つまたは複数のランタイム値を渡すには、SSISDB と SQL Server Management Studio (SSMS) で SSIS 実行環境を作成します。 各環境で変数を作成し、プロジェクトまたはパッケージのパラメーターに対応する値を渡します。 それらの環境変数とプロジェクトまたはパッケージのパラメーターが関連付けられるように、SSMS で SSIS パッケージを構成します。 Data Factory パイプラインでパッケージを実行するときは、SSIS パッケージの実行アクティビティ UI の [設定] タブで異なる環境パスを指定することで環境を切り替えます。

SSIS 環境の詳細については、「[サーバー環境の作成とマップ](../packages/deploy-integration-services-ssis-projects-and-packages.md#create-and-map-a-server-environment)」を参照してください。 Azure Data Factory パイプラインの一部としてパッケージを実行する方法については、[Azure Data Factory で SSIS パッケージの実行アクティビティを使用して SSIS パッケージを実行する](https://docs.microsoft.com/azure/data-factory/how-to-invoke-ssis-package-ssis-activity)方法に関するページを参照してください。

## <a name="monitor-packages"></a>パッケージの監視
SSMS で実行中のパッケージを監視するには、SSMS で次のレポート作成ツールを使用できます。
-   **[SSISDB]** を右クリックし、**[アクティブな操作]** を選択して、**[アクティブな操作]** ダイアログ ボックスを開きます。
-   オブジェクト エクスプローラーでパッケージを選択し、右クリックして **[レポート]** を選択し、**[標準レポート]**、**[すべての実行]** の順に選択します。

Azure SSIS 統合ランタイムを監視するには、[Azure SSIS 統合ランタイムの監視](https://docs.microsoft.com/azure/data-factory/monitor-integration-runtime#azure-ssis-integration-runtime)に関するページを参照してください。

## <a name="schedule-packages"></a>パッケージのスケジュール設定
Azure SQL Database に格納されたパッケージの実行をスケジュール設定するには、さまざまなツールを使用できます。 詳細については、「[Azure で SSIS パッケージの実行をスケジュールする](ssis-azure-schedule-packages.md)」を参照してください。

## <a name="next-steps"></a>次の手順
Azure で SSIS ワークロードの使用を開始するには、次の記事を参照してください。
-   [SQL Server Integration Services パッケージを Azure にデプロイする](https://docs.microsoft.com/azure/data-factory/tutorial-deploy-ssis-packages-azure)
-   [Azure で SSIS パッケージを配置、実行、および監視する](ssis-azure-deploy-run-monitor-tutorial.md)
