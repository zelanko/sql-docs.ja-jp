---
title: SQL Server、Azure SQL Database、および Azure SQL Data Warehouse 用の SQL ツールとユーティリティ |Microsoft Docs
ms.custom: ''
ms.date: 11/19/2018
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: ''
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: fe249e4df9c33fcbb292fc93f218e16ae111b0bb
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68105658"
---
# <a name="sql-tools-and-utilities-for-sql-server-azure-sql-database-and-azure-sql-data-warehouse"></a>SQL Server、Azure SQL Database、および Azure SQL Data Warehouse 用の SQL ツールとユーティリティ
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

データベースの管理 (クエリ、監視など) を行うには、ツールが必要です。 データベースはクラウド、Windows、または[Linux](../linux/sql-server-linux-overview.md)で実行できますが、ツールをデータベースと同じプラットフォームで実行する必要はありません。 

使用できるデータベースツールは多数あります。この記事では、SQL データベースを操作するために使用できるツールについて説明します。 必要なツールを決定する際には、[どのツールを使用すればよいでしょうか](#which-tool-should-i-choose)。

## <a name="gui-tools-to-manage-databases"></a>データベースを管理するための GUI ツール  

次に、グラフィカルユーザーインターフェイス (GUI) の主要なツールを示します。

| ツール | [説明] | 実行 |
|:--|:--|:--|
| [[!INCLUDE[name-sos](../includes/name-sos.md)]](../sql-operations-studio/download.md) | [!INCLUDE[name-sos](../includes/name-sos-short.md)]は、実行されている任意の場所でデータベースを管理するための、無料の軽量ツールです。 このプレビューリリースでは、拡張された Transact-sql エディターや、データベースの運用状態に対するカスタマイズ可能な洞察など、データベース管理機能を利用できます。 | **Windows、macOS、Linux で実行されます。 [!INCLUDE[name-sos](../includes/name-sos-short.md)]**|
| [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md) | SQL Server Management Studio (SSMS) を使用して、SQL Server、Azure SQL Database、および Azure SQL Data Warehouse のクエリ、設計、管理を行います。 | **SSMS は Windows 上で実行**されます。|
| [SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md) | SQL Server、Azure SQL Database、および Azure SQL Data Warehouse のために、Visual Studio を強力な開発環境にします。| **SSDT は Windows 上で実行されます**。|
| [Visual Studio Code](https://code.visualstudio.com/)| Visual Studio Code のインストール後、Microsoft SQL Server、Azure SQL Database、および SQL Data Warehouse を開発するための[mssql 拡張機能](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql)をインストールします。| **Visual Studio Code は、Windows、macOS、Linux で実行**されます。|


## <a name="command-line-tools-to-manage-databases"></a>データベースを管理するためのコマンドラインツール

主なコマンドラインツールを次に示します。

| ツール | [説明] | 実行 |
|:--|:--|:--|
|[**mssql-cli (プレビュー)** ](mssql-cli.md)|**mssql-cli**は、SQL Server クエリを実行するための対話型コマンドラインツールです。 | Windows、macOS、Linux|
| [**sqlpackage**](sqlpackage.md) |**sqlpackage**は、いくつかのデータベース開発タスクを自動化するコマンドラインユーティリティです。 sqlpackage の macOS および Linux バージョンは、現在プレビューの段階です。 | Windows、macOS、Linux|
|[**SQL Server PowerShell**](../powershell/sql-server-powershell.md)| **SQL Server PowerShell**は、SQL を操作するためのコマンドレットを提供します。| Windows、macOS、Linux|
| [**sqlcmd**](sqlcmd-utility.md) |**sqlcmd**ユーティリティを使用すると、transact-sql ステートメント、システムプロシージャ、およびスクリプトファイルをコマンドプロンプトで入力できます。 | Windows、macOS、Linux|
|[**bcp**](https://docs.microsoft.com/sql/tools/bcp-utility?view=sql-server-2014)|**b**ulk **c**opy **p**rogram ユーティリティ (**bcp**) では、[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスと、ユーザー指定の形式のデータ ファイルとの間でデータの一括コピーを行います。|Windows、macOS、Linux|
|[**mssql-scripter (プレビュー)** ](https://github.com/Microsoft/mssql-scripter)|**scripter**は、SQL Server データベースをスクリプト化するためのマルチプラットフォームコマンドラインエクスペリエンスです。|Windows、macOS、Linux|
|[**mssql-conf**](../linux/sql-server-linux-configure-mssql-conf.md)|**mssql は、** Linux で実行されている SQL Server を構成します。|Linux|



## <a name="which-tool-should-i-choose"></a>どのツールを選択すればよいですか?

- Windows、Linux、または Mac で軽量エディターを使用して、SQL Server インスタンスまたはデータベースを管理しますか? [[!INCLUDE[name-sos](../includes/name-sos.md)]](../sql-operations-studio/download.md) を選択します。
- 完全な GUI サポートを使用して、Windows 上の SQL Server インスタンスまたはデータベースを管理しますか? [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md) を選択します。
- Windows でのコンパイル時の検証、リファクタリング、デザイナーのサポートなど、データベースコードを作成または管理しますか? [SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md) を選択します。
- IntelliSense、高光灯などの機能を備えたコマンドラインツールを使用して SQL Server に対してクエリを実行しますか? [Mssql-cli の](mssql-cli.md)選択
- Windows、Linux、または Mac の軽量エディターで T-sql スクリプトを作成しますか? [Visual Studio Code](https://code.visualstudio.com/)と[mssql 拡張機能](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql)を選択します。



## <a name="additional-tools"></a>その他のツール

| ツール | [説明] |
|:--|:--|
| [構成マネージャー](../tools/configuration-manager/sql-server-configuration-manager-help.md) | SQL Server 構成マネージャーを使用して SQL Server サービスを構成し、ネットワーク接続を構成します。 Windows での Configuration Manager の実行|
| [SQL Server Migration Assistant](../ssma/sql-server-migration-assistant.md) | SQL Server Migration Assistant を使用して、Microsoft Access、DB2、MySQL、Oracle、Sybase から SQL Server へのデータベースの移行を自動化します。|
| [Database Experimentation Assistant](../dea/database-experimentation-assistant-overview.md) | Database Experimentation Assistant を使用して、特定のワークロードの対象となる SQL のバージョンを評価します。 |
| [分散再生](../tools/distributed-replay/install-distributed-replay-overview.md) | 分散再生の機能を使用すると、今後の SQL Server アップグレードの影響を評価するのに役立ちます。 また、分散再生を使用して、ハードウェアとオペレーティングシステムのアップグレード、および SQL Server チューニングの影響を評価することもできます。 |
| [ssbdiagnose](../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md) | Ssbdiagnose ユーティリティは、Service Broker メッセージ交換または Service Broker サービスの構成の問題を報告します。 |

このページに記載されていないその他のツールについては、「 [SQL コマンドプロンプトユーティリティ](command-prompt-utility-reference-database-engine.md)」を参照してください。

