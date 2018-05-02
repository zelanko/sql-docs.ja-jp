---
title: SQL Server Integration Services ワークロードをクラウドにリフト アンド シフトする | Microsoft Docs
ms.date: 04/13/2018
ms.topic: article
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: lift-shift
ms.suite: sql
ms.custom: ''
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 10870216c2abc826a72bb16715701a794e651610
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="lift-and-shift-sql-server-integration-services-workloads-to-the-cloud"></a>SQL Server Integration Services ワークロードをクラウドにリフト アンド シフトする
SQL Server Integration Services (SSIS) パッケージとワークロードを Azure クラウドに移動できるようになりました。
-   SSIS プロジェクトとパッケージを Azure SQL Database の SSIS カタログ データベース (SSISDB) または Azure SQL Database マネージ インスタンス (プレビュー) に格納して管理します。
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
| Azure (SQL Database または Azure SQL Database マネージ インスタンス (プレビュー)) | Azure SSIS Integration Runtime、Azure Data Factory バージョン 2 のコンポーネント | SSIS IR のスケーリング オプション |
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

## <a name="version-info"></a>バージョン情報

SSIS の任意のバージョンで作成されたパッケージを Azure にデプロイすることができます。 Azure にパッケージをデプロイするときに、検証エラーがなければ、パッケージは最新のパッケージ形式に自動的にアップグレードされます。 つまり、常に SSIS の最新バージョンにアップグレードされます。

デプロイ プロセスでは、パッケージが Azure SSIS Integration Runtime で実行できることを確認するための検証が行われます。 詳細については、「[Azure にデプロイされた SSIS パッケージの検証](ssis-azure-validate-packages.md)」を参照してください。

## <a name="prerequisites"></a>Prerequisites

この記事で説明した機能には、次のバージョンの SQL Server Data Tools (SSDT) が必要です。
-   Visual Studio 2017 の場合、バージョン 15.3 (プレビュー) 以降。
-   Visual Studio 2015 の場合、バージョン 17.2 以降。

Azure での前提条件の詳細については、「[Azure Data Factory UI を使用した Azure SSIS 統合ランタイムのプロビジョニング](https://docs.microsoft.com/azure/data-factory/tutorial-create-azure-ssis-runtime-portal)」を参照してください。

## <a name="provision-ssis-on-azure"></a>Azure での SSIS のプロビジョニング
Azure で SSIS パッケージをデプロイして実行するには、事前に SSIS カタログ データベース (SSISDB) と Azure SSIS Integration Runtime をプロビジョニングする必要があります。 次の記事のプロビジョニングの手順に従ってください: [Azure Data Factory UI を使用した Azure SSIS 統合ランタイムのプロビジョニング](https://docs.microsoft.com/azure/data-factory/tutorial-create-azure-ssis-runtime-portal)

SSISDB をホストする **SQL Database の名前**が、SSDT および SSMS からパッケージを配置して管理する際に使用する 4 つの部分から成る名前の最初の部分になります: `<sql_database_name>.database.windows.net`。

SSIS カタログ データベースに接続する方法の詳細については、「[Azure 上の SSISDB カタログ データベースへの接続](ssis-azure-connect-to-catalog-database.md)」を参照してください。

## <a name="design-packages"></a>パッケージの設計
SSDT のオンプレミス、または SSDT がインストールされた Visual Studio で、**パッケージの設計とビルド**を続行します。

**Windows 認証**を使用してクラウドからオンプレミスのデータ ソースに接続する方法については、「[Windows 認証でオンプレミス データ ソースと Azure ファイル共有に接続する](ssis-azure-connect-with-windows-auth.md)」を参照してください。

ファイルとファイル共有に接続する方法については、「[オンプレミスおよび Azure のファイル共有のファイルを格納および取得する](ssis-azure-files-file-shares.md)」を参照してください。

SSISDB をホストする SQL Database のインスタンスをプロビジョニングする際に、SSIS 用 Azure Feature Pack と Access Redistributable もインストールされます。 これらのコンポーネントは、組み込みのコンポーネントでサポートされるデータ ソースの他に、さまざまな **Azure** データ ソース、および **Excel ファイルと Access ファイル**への接続を提供します。

追加のコンポーネントをインストールすることもできます。 詳細については、「[Custom setup for the Azure-SSIS integration runtime](/azure/articles/data-factory/how-to-configure-azure-ssis-ir-custom-setup.md)」(Azure-SSIS 統合ランタイムのカスタム設定) を参照してください。

## <a name="deploy-and-run-packages"></a>パッケージの配置と実行
Azure の SSISDB にプロジェクトをデプロイする場合には、パッケージ配置モデルではなく、**プロジェクト配置モデル**を使用する必要があります。

Azure でプロジェクトをデプロイしてパッケージを実行するには、次の使い慣れたツールやスクリプト作成オプションのいずれかを使用して行えます。
-   SQL Server Management Studio (SSMS)
-   Transact-SQL (SSMS、Visual Studio Code、または別のツールから)
-   コマンドライン ツール
-   PowerShell
-   C# と SSIS の管理オブジェクト モデル

作業を開始する場合は、「[Azure で SSIS パッケージを配置、実行、および監視する](ssis-azure-deploy-run-monitor-tutorial.md)」を参照してください。

## <a name="monitor-packages"></a>パッケージの監視
SSMS での実行中のパッケージを監視するには、SSMS で次のレポート作成ツールのいずれかを使用できます。
-   **[SSISDB]** を右クリックし、**[アクティブな操作]** を選択して、**[アクティブな操作]** ダイアログ ボックスを開きます。
-   オブジェクト エクスプローラーでパッケージを選択し、右クリックして **[レポート]** を選択し、**[標準レポート]**、**[すべての実行]** の順に選択します。

## <a name="schedule-packages"></a>パッケージのスケジュール設定
SQL Database に格納されたパッケージの実行をスケジュール設定するには、次のツールを使用できます。
-   オンプレミスの SQL Server エージェント
-   Data Factory SQL Server ストアド プロシージャ アクティビティ

詳細については、「[Azure で SSIS パッケージの実行をスケジュールする](ssis-azure-schedule-packages.md)」を参照してください。

## <a name="next-steps"></a>次の手順
Azure で SSIS ワークロードの使用を開始するには、次の記事を参照してください。
-   [Azure Data Factory UI を使用した Azure SSIS 統合ランタイムのプロビジョニング](https://docs.microsoft.com/azure/data-factory/tutorial-create-azure-ssis-runtime-portal)
-   [Azure で SSIS パッケージを配置、実行、および監視する](ssis-azure-deploy-run-monitor-tutorial.md)
