---
title: "リフトし、SQL Server Integration Services のワークロードをクラウドに移動 |Microsoft ドキュメント"
ms.date: 09/28/2017
ms.topic: article
ms.prod: sql-server-2017
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.translationtype: MT
ms.sourcegitcommit: e76675099ab290d29231d434eb74e92b613185b7
ms.openlocfilehash: a3693b84ed02583cd47921fbfda84c7df9559b68
ms.contentlocale: ja-jp
ms.lasthandoff: 09/29/2017

---
# <a name="lift-and-shift-sql-server-integration-services-workloads-to-the-cloud"></a>クラウドにリフト アンド シフトの SQL Server Integration Services のワークロード
Azure のクラウドに、SQL Server Integration Services (SSIS) パッケージとワークロードを移動できます。
-   格納し、SSIS プロジェクトと Azure SQL データベースで SSIS カタログ データベース (SSISDB) でのパッケージを管理します。
-   Azure Data Factory バージョン 2 の一部として導入された、Azure SSIS の統合のランタイムのインスタンスにパッケージを実行します。
-   これらの一般的なタスクには、SQL Server Management Studio (SSMS) などの使い慣れたツールを使用します。

## <a name="benefits"></a>利点
Azure に、内部設置型の SSIS ワークロードを移動すると、次の潜在的な利点があります。
-   **運用コストを削減**内部設置型インフラストラクチャを減らすことによってです。
-   **高可用性を向上させる**Azure および Azure SQL データベースの高可用性機能と同様に、クラスターあたり複数のノードにします。
-   **スケーラビリティを向上させる**ノード (スケール アップ) ごとの複数のコアとクラスター (スケール アウト) ごとの複数のノードを指定する機能を使用します。
-   **制限を回避する**SSIS を Azure の仮想マシンで実行されているのです。

## <a name="architecture-overview"></a>アーキテクチャの概要
次の表は、内部設置型の SSIS と Azure での SSIS の違いを示しています。 最も重要な違いは、記憶域のコンピューティングからの分離です。

| ストレージ | ランタイム | スケーラビリティ |
|---|---|---|
| 内部設置型 (SQL Server) | SQL Server でホストされている SSIS ランタイム | SSIS スケール アウト (SQL Server 2017 以降で)<br/><br/>(SQL Server の以前のバージョン) でカスタム ソリューション |
| On Azure (SQL データベース) | Azure の SSIS の統合のランタイム、Azure Data Factory バージョン 2 のコンポーネント | 赤外線の SSIS のスケーリングのオプション |
| | | |

Azure Data Factory では、Azure での SSIS パッケージのランタイム エンジンをホストします。 ランタイム エンジンは、Azure の SSIS の統合の実行時 (SSIS IR) と呼ばれます。

SSIS 赤外線をプロビジョニングする際に、スケール アップと、次のオプションの値を指定してスケール アウトできます。
-   ノードのサイズ (コアの数を含む) と、クラスター内のノードの数。
-   SSIS カタログ データベース (SSISDB)、およびデータベース用のサービス層をホストする Azure SQL データベースの既存のインスタンス。
-   ノードごとの最大並列実行します。

のみ、1 回を SSIS IR にプロビジョニングを行う必要があるとします。 その後、SQL Server Data Tools (SSDT) および SQL Server Management Studio (SSMS) を展開する構成、実行、監視、スケジュール、およびパッケージの管理などの使い慣れたツールを使用できます。

データ ファクトリには、統合ランタイムの他の種類もサポートしています。 赤外線の SSIS との統合のランタイムの他の種類の詳細については、次を参照してください。 [Azure Data Factory で統合ランタイム](/azure/data-factory/concepts-integration-runtime.md)です。

## <a name="prerequisites"></a>前提条件
このトピックで説明する機能は、SQL Server Data Tools (SSDT) 17.2 以降のバージョンを必要とは、SQL Server 2017 年 1 または SQL Server 2016 は必要ありません。 Azure にパッケージを配置する場合、パッケージの展開ウィザードは、パッケージを常に最新のパッケージ形式にアップグレードされます。

Azure での前提条件の詳細については、次を参照してください。[を Azure に SQL Server Integration Services (SSIS) パッケージのリフト アンド シフト](/azure/data-factory/quickstart-lift-shift-ssis-packages-powershell.md)です。

## <a name="ssis-features-on-azure"></a>Azure での SSIS 機能

SSISDB をホストする SQL データベースのインスタンスをプロビジョニングする際に、Azure Feature Pack for SSIS をアクセス再頒布可能パッケージがインストールされます。 これらのコンポーネントは、Excel および Access ファイルとさまざまな Azure のデータ ソースへの接続を提供します。 この時点で、SSIS のサード パーティのコンポーネントをインストールできません。

SSISDB をホストする SQL データベースの名前を展開および SSDT および SSMS - からパッケージを管理するときに使用する 4 部構成の名前の最初の部分になります`<sql_database_name>.database.windows.net`です。

Azure SQL データベースで SSISDB に配置するプロジェクトのプロジェクト配置モデルをパッケージ配置モデルではなくを使用する必要があります。

設計し、パッケージ オンプレミス SSDT では、または SSDT のインストールでは Visual Studio でのビルドを続行します。

Windows 認証では、クラウドからオンプレミス データ ソースに接続する方法の詳細については、次を参照してください。 [Windows 認証でオンプレミス データ ソースへの接続](ssis-azure-connect-with-windows-auth.md)です。

## <a name="common-tasks"></a>よく使用するタスク

### <a name="provision"></a>プロビジョニング
展開して、Azure で SSIS パッケージを実行することが、前に SSISDB カタログ データベースと Azure SSIS の統合ランタイムをプロビジョニングする必要があります。 この記事でプロビジョニングの手順に従ってください:[を Azure に SQL Server Integration Services (SSIS) パッケージのリフト アンド シフト](/azure/data-factory/quickstart-lift-shift-ssis-packages-powershell.md)です。

### <a name="deploy-and-run-packages"></a>展開して、パッケージの実行
プロジェクトの配置を SQL データベースでのパッケージの実行は、いくつかの使い慣れたツールやスクリプト作成オプションのいずれかを使用できます。
-   SQL Server Management Studio (SSMS)
-   (SSMS、Visual Studio のコード、または別のツール) から transact SQL
-   コマンド ライン ツール
-   PowerShell
-   C# と SSIS の管理オブジェクト モデル

### <a name="monitor-packages"></a>モニターのパッケージ
SSMS での実行中のパッケージを監視するには SSMS で、次のレポート作成ツールのいずれかを使用できます。
-   右クリック**SSISDB**、し、[ **Active Operations**を開くには、 **Active Operations** ] ダイアログ ボックス。
-   オブジェクト エクスプ ローラーで右クリックし選択パッケージの選択**レポート**、し**標準レポート**、し**すべての実行**です。

### <a name="schedule-packages"></a>パッケージのスケジュール
SQL データベースに格納されたパッケージの実行をスケジュールするには、次のツールを使用できます。
-   SQL Server エージェントで内部設置型
-   データ ファクトリの SQL Server ストアド プロシージャ アクティビティ

詳細については、次を参照してください。[スケジュール SSIS パッケージを Azure で実行](ssis-azure-schedule-packages.md)です。

## <a name="next-steps"></a>次の手順
Azure での SSIS ワークロードで開始するには、次の記事を参照してください。
-   [Azure に SQL Server Integration Services (SSIS) パッケージをリフト アンド シフト](/azure/data-factory/quickstart-lift-shift-ssis-packages-powershell.md)
-   [配置、実行、および Azure で SSIS パッケージの監視](ssis-azure-deploy-run-monitor-tutorial.md)

