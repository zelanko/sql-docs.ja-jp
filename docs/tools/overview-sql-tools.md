---
title: SQL Server、Azure SQL Database、および Azure SQL Data Warehouse の SQL ツールとユーティリティ |Microsoft Docs
ms.custom: ''
ms.date: 09/24/2018
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: ''
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 1ff16d7a8b2253fc793db00cb46282539415ff86
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47767370"
---
# <a name="sql-tools-and-utilities-for-sql-server-azure-sql-database-and-azure-sql-data-warehouse"></a>SQL Server、Azure SQL Database、および Azure SQL Data Warehouse の SQL ツールとユーティリティ
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

(クエリ、モニターなど) を管理するツールを必要とするデータベース。 クラウド、Windows、または上で、データベースを実行できる中に[Linux](../linux/sql-server-linux-overview.md)ツール、データベースと同じプラットフォーム上で実行する必要はありません。 

ある多くのデータベース ツール、使用可能なので、この記事では、SQL データベースを操作するための説明と使用可能なツールの一部へのポインターを提供します。 表示、かどうかどのツールを決定する必要があります。[どのツールを使用する必要がありますか?](#which-tool-should-i-choose)します。


## <a name="gui-tools-to-manage-databases"></a>データベースを管理する GUI ツール  

以下は、メインのグラフィカル ユーザー インターフェイス (GUI) ツールです。

| ツール | [説明] | 上で実行します。 |
|:--|:--|:--|
| [[!INCLUDE[name-sos](../includes/name-sos.md)]](../sql-operations-studio/download.md) | [!INCLUDE[name-sos](../includes/name-sos-short.md)] 実行されている任意の場所にデータベースを管理するための無料の軽量ツールです。 このプレビュー リリースでは、拡張 TRANSACT-SQL エディターと、データベースの操作状態のカスタマイズ可能な洞察を含む、データベースの管理機能を提供します。 | **[!INCLUDE[name-sos](../includes/name-sos-short.md)] Windows、macOS、Linux で実行される**します。|
| [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md) | クエリ、設計、および SQL Server、Azure SQL Database、Azure SQL Data Warehouse を管理するには、SQL Server Management Studio (SSMS) を使用します。 | **Windows で SSMS を実行**します。|
| [SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md) | SQL Server、Azure SQL Database、および Azure SQL Data Warehouse の強力な開発環境に Visual Studio を有効にします。| **SSDT は、Windows で実行**します。|
| [Visual Studio Code](https://code.visualstudio.com/)| Visual Studio Code をインストールすると、インストール、 [mssql 拡張機能](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql)Microsoft SQL Server、Azure SQL Database、および SQL Data Warehouse を開発するためです。| **Visual Studio Code は、Windows、macOS、Linux で実行される**します。|


## <a name="command-line-tools-to-manage-databases"></a>データベースを管理するコマンド ライン ツール

以下は、主要なコマンド ライン ツールです。

| ツール | [説明] | 上で実行します。 |
|:--|:--|:--|
|[**mssql-cli (プレビュー)**](mssql-cli.md)|**mssql cli**は SQL Server を照会するための対話型コマンド ライン ツールです。 | Windows、macOS、および Linux|
| [**sqlpackage**](sqlpackage.md) |**sqlpackage**はいくつかのデータベース開発タスクを自動化するコマンド ライン ユーティリティです。 macOS および Linux のバージョンの sqlpackage は現在プレビュー段階です。 | Windows、macOS、および Linux|
|[**SQL Server PowerShell**](../powershell/sql-server-powershell.md)| **SQL Server PowerShell** SQL を使用するためのコマンドレットを提供します。| Windows、macOS、および Linux|
| [**sqlcmd**](sqlcmd-utility.md) |**sqlcmd**ユーティリティを使用して、TRANSACT-SQL ステートメント、システム プロシージャ、およびコマンド プロンプトのスクリプト ファイルを入力できます。 | Windows、macOS、および Linux|
|[**bcp**](../2014/tools/bcp-utility.md)|**b**ulk **c**opy **p**rogram ユーティリティ (**bcp**) では、[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスと、ユーザー指定の形式のデータ ファイルとの間でデータの一括コピーを行います。|Windows、macOS、および Linux|
|[**mssql scripter (プレビュー)**](https://github.com/Microsoft/mssql-scripter)|**mssql scripter**は SQL Server データベースのスクリプトを実行して、マルチプラット フォーム コマンドライン エクスペリエンス|Windows、macOS、および Linux|
|[**mssql conf**](../linux/sql-server-linux-configure-mssql-conf.md)|**mssql conf** Linux で実行されている SQL Server を構成します。|Linux|



## <a name="which-tool-should-i-choose"></a>どのツールを選択する必要がありますか。

- SQL Server インスタンスまたはデータベースで、Windows、Linux または Mac で軽量のエディターで管理しますか。 [[!INCLUDE[name-sos](../includes/name-sos.md)]](../sql-operations-studio/download.md) を選択します。
- SQL Server インスタンスまたは完全な GUI サポートを Windows 上のデータベースを管理しますか。 [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md) を選択します。
- 作成またはコンパイル時に検証をなど、データベースのコードを管理する、Windows でのリファクタリングとデザイナーをサポートしますか。 [SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md) を選択します。
- IntelliSense、構文の高照明を紹介するコマンド ライン ツールを使用した SQL Server のクエリを実行するとしますか? 選択[mssql cli](mssql-cli.md)
- Windows、Linux または Mac で軽量のエディターで T-SQL スクリプトを記述しますか。 選択[Visual Studio Code](https://code.visualstudio.com/) 、 [mssql 拡張機能](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql)



## <a name="additional-tools"></a>その他のツール

| ツール | [説明] |
|:--|:--|
| [構成マネージャー](../tools/configuration-manager/sql-server-configuration-manager-help.md) | SQL Server サービスを構成して、ネットワーク接続を構成するは、SQL Server の構成マネージャーを使用します。 Windows 上の configuration Manager の実行|
| [SQL Server Migration Assistant](../ssma/sql-server-migration-assistant.md) | SQL Server Migration Assistant を使用して、Microsoft Access、DB2、MySQL、Oracle、Sybase から SQL Server へのデータベースの移行を自動化します。|
| [分散再生](../tools/distributed-replay/install-distributed-replay-overview.md) | SQL Server の将来のアップグレードの影響を評価するためには、分散再生の機能を使用します。 Distributed Replay を使用してもハードウェアとオペレーティング システムのアップグレード、および SQL Server のチューニングの影響を評価します。 |
| [ssbdiagnose](../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md) | Ssbdiagnose ユーティリティでは、Service Broker メッセージ交換または Service Broker サービスの構成に関する問題を報告します。 |

このページに記載されていないその他のツールを探している場合は、次を参照してください。 [SQL コマンド プロンプト ユーティリティ](command-prompt-utility-reference-database-engine.md)します。

