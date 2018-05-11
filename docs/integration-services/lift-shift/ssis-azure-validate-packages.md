---
title: Azure にデプロイされた SSIS パッケージの検証 | Microsoft Docs
ms.date: 11/27/2017
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
ms.openlocfilehash: 09086d0f4ff9c5a3f69a922e0c17c046c84001fb
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="validate-ssis-packages-deployed-to-azure"></a>Azure にデプロイされた SSIS パッケージの検証
SQL Server Integration Services (SSIS) プロジェクトを Azure サーバーの SSIS カタログ データベース (SSISDB) にデプロイすると、パッケージの配置ウィザードにより、**[確認]** ページの後に検証手順が追加されます。 この検証手順では、Azure SSIS Integration Runtime で予定されているパッケージ実行を妨げる既知の問題がないか、プロジェクトのパッケージが調べられます。 その後、**[検証]** ページに該当する警告が表示されます。

> [!IMPORTANT]
> この記事で説明する検証は、SQL Server Data Tools (SSDT) バージョン 17.4 以降でプロジェクトをデプロイするときに行われます。 最新版の SSDT を入手する方法については、「[SQL Server Data Tools (SSDT) のダウンロード](../../ssdt/download-sql-server-data-tools-ssdt.md)」をご覧ください。

パッケージの配置ウィザードの詳細については、「[Integration Services (SSIS) プロジェクトとパッケージの配置](../packages/deploy-integration-services-ssis-projects-and-packages.md)」を参照してください。

## <a name="validate-connection-managers"></a>接続マネージャーを検証する

ウィザードでは、接続を失敗させる可能性がある次の問題がないか、特定の接続マネージャーが確認されます。
- **Windows 認証**。 接続文字列で Windows 認証を使用する場合、検証で警告が表示されます。 Windows 認証は、追加の構成手順を要求します。 詳細については、「[Connect to on-premises data sources with Windows Authentication](ssis-azure-connect-with-windows-auth.md)」 (Windows 認証でオンプレミス データ ソースに接続する) を参照してください。
- **ファイル パス**。 接続文字列に `C:\\...` のようなハードコーディングされたローカル ファイル パスが含まれる場合、検証で警告が表示されます。 絶対パスを含むパッケージは失敗することがあります。
- **UNC パス**。 接続文字列に UNC パスが含まれる場合、検証で警告が表示されます。 UNC パスを含むパッケージは失敗することがあります。一般的に、UNC パスはアクセスに Windows 認証を要求するためです。
- **ホスト名**。 サーバー プロパティに IP アドレスではなくホスト名が含まれる場合、検証で警告が表示されます。 ホスト名を含むパッケージは失敗することがあります。一般的に、Azure 仮想ネットワークは DNS 名前解決のために正しい DNS 構成を必要とするためです。
- **プロバイダーまたはドライバー**。 プロバイダーまたはドライバーがサポートされていない場合、検証で警告が表示されます。 現時点では、ごく少数の組み込みプロバイダー/ドライバーがサポートされています。

このウィザードでは、一覧の接続マネージャーに対して次の検証が行われます。

| 接続マネージャー | Windows 認証 | [ファイル パス] | UNC パス | ホスト名 | プロバイダーまたはドライバー |
|--------------------|----------|-----------|-----|-----------|-------------------|
| Ado                | ✓        |           |     | ✓         | ✓                 |
| AdoNet             | ✓        |           |     | ✓         | ✓                 |
| Cache              |          | ✓         | ✓   |           |                   |
| [エクスポート]              |          | ✓         | ✓   |           |                   |
| ファイル               |          | ✓         | ✓   |           |                   |
| FlatFile           |          | ✓         | ✓   |           |                   |
| Ftp                |          |           |     | ✓         |                   |
| MsOLAP100          |          |           |     | ✓         | ✓                 |
| MultiFile          |          | ✓         | ✓   |           |                   |
| MultiFlatFile      |          | ✓         | ✓   |           |                   |
| OData              | ✓        |           |     | ✓         |                   |
| Odbc               | ✓        |           |     | ✓         | ✓                 |
| OleDb              | ✓        |           |     | ✓         | ✓                 |
| SmoServer          | ✓        |           |     | ✓         |                   |
| Smtp               | ✓        |           |     | ✓         |                   |
| SqlMobile          |          | ✓         | ✓   |           |                   |
| Wmi                | ✓        |           |     |           |                   |
|||||||

## <a name="validate-sources-and-destinations"></a>ソースとターゲットの検証
次のサードパーティ ソース/ターゲットはサポートされていません。

-   Attunity Oracle ソース/ターゲット
-   Attunity Teradata ソース/ターゲット
-   SAP BI ソース/ターゲット

## <a name="validate-tasks-and-components"></a>タスクとコンポーネントの検証

### <a name="execute-process-task"></a>プロセス実行タスク

絶対パスを持つローカル ファイルか UNC パスを持つファイルをコマンドが指す場合、検証で警告が表示されます。 このようなパスでは、Azure 上の実行が失敗することがあります。

### <a name="script-task-and-script-component"></a>スクリプト タスクとスクリプト コンポーネント

サポートされていないアセンブリを参照したり、呼び出したりする可能性があるスクリプト タスクまたはスクリプト コンポーネントがパッケージに含まれる場合、検証で警告が表示されます。 このような参照や呼び出しが原因で実行に失敗することがあります。

### <a name="other-components"></a>その他のコンポーネント

Orc 形式は HDFS ターゲットと Azure Data Lake Store ターゲットでサポートされていません。

## <a name="next-steps"></a>次の手順
Azure でパッケージ実行をスケジュールする方法については、「[Schedule the execution of an SSIS package on Azure](ssis-azure-schedule-packages.md)」 (Azure で SSIS パッケージの実行をスケジュールする) を参照してください。