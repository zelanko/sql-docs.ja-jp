---
title: 抽出、変換、および SSIS を使用した Linux 上のデータの読み込み |Microsoft Docs
description: この記事では、Linux コンピューターの SQL Server Integration Services (SSIS) をについて説明します
author: leolimsft
ms.author: lle
ms.reviewer: douglasl
manager: craigg
ms.date: 01/09/2018
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.openlocfilehash: d01a53524bf03e0ea8318c41b05b9cc59499de33
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2018
ms.locfileid: "46713224"
---
# <a name="extract-transform-and-load-data-on-linux-with-ssis"></a>抽出、変換、および SSIS を使用した Linux 上のデータの読み込み

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

この記事では、Linux 上の SQL Server Integration Services (SSIS) パッケージを実行する方法について説明します。 SSIS から複数のソースや形式、データを抽出することで複雑なデータ統合に関する問題の解決に変換して、データのクレンジングと複数の変換先にデータを読み込みます。 

Linux で実行されている SSIS パッケージは、オンプレミスで Windows または linux では、または Docker では、クラウドで実行されている Microsoft SQL Server に接続できます。 Azure SQL Database、Azure SQL Data Warehouse、ODBC データ ソース、フラット ファイル、および ADO.NET ソース、XML ファイルでは、OData サービスなど、他のデータ ソースに接続することもできます。

SSIS の機能についての詳細については、次を参照してください。 [SQL Server Integration Services](../integration-services/sql-server-integration-services.md)します。

## <a name="prerequisites"></a>前提条件

Linux コンピューターで、SSIS パッケージを実行するには、最初に SQL Server Integration Services をインストールする必要があります。 SSIS は、Linux コンピューターの SQL Server のインストールには含まれません。 インストール手順については、次を参照してください。 [SQL Server Integration Services のインストール](sql-server-linux-setup-ssis.md)します。

作成してパッケージを管理する Windows コンピューターを持つ必要があるとします。 SSIS の設計と管理ツールは、Linux コンピューターの場合は、現在使用可能なない Windows アプリケーションです。 

## <a name="run-an-ssis-package"></a>SSIS パッケージを実行します。

SSIS パッケージを Linux コンピューターで実行するには、次のことを行います。

1.  SSIS パッケージを Linux コンピューターにコピーします。
2.  次のコマンドを実行します。
    ```
    $ dtexec /F \<package name \> /DE <protection password>
    ```

## <a name="run-an-encrypted-password-protected-package"></a>暗号化された (パスワードで保護された) パッケージを実行します。
パスワードで暗号化されている SSIS パッケージを実行する 3 つの方法はあります。

1.  環境変数の値を設定`SSIS_PACKAGE_DECRYPT`次の例のように。

    ```
    SSIS_PACKAGE_DECRYPT=test /opt/ssis/bin/dtexec /f package.dtsx
    ```

2.  指定、`/de[crypt]`対話形式で、次の例に示すように、パスワードを入力するオプション。

    ```
    /opt/ssis/bin/dtexec /f package.dtsx /de
    
    Enter decryption password:
    ```

3.  指定、`/de`の次の例に示すように、コマンドラインでパスワードを指定するオプション。 このメソッドは、コマンド履歴にコマンドを使用して暗号化解除パスワードを格納するためには推奨されません。

    ```
    opt/ssis/bin/dtexec /f package.dtsx /de test
    
    Warning: Using /De[crypt] <password> may store decryption password in command history.
    
    You can use /De[crypt] instead to enter interactive mode,
    or use environment variable SSIS_PACKAGE_DECRYPT to set decryption password.
    ```

## <a name="design-packages"></a>パッケージの設計

**ODBC データ ソースに接続する**します。 SSIS で Linux CTP 2.1 の更新以降では、SSIS パッケージは Linux で ODBC 接続を使用できます。 この機能は、SQL Server および MySQL ODBC ドライバーでテストされているが、ODBC 仕様には任意の Unicode ODBC ドライバーを使用することも必要です。 デザイン時に、DSN または接続文字列は、ODBC データに接続するを指定することができます。Windows 認証を使用することもできます。 詳細については、次を参照してください。、[ブログ Linux に ODBC サポートのお知らせを投稿する](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/)します。

**パス**します。 SSIS パッケージ内の Windows スタイルのパスを提供します。 Linux 上の SSIS では、Linux 形式のパスをサポートしませんが、実行時に Linux 形式のパスを Windows 形式のパスをマップします。 Windows スタイルのパスにマップなど、Linux 上の SSIS `C:\test` Linux スタイルのパスに`/test`します。

## <a name="deploy-packages"></a>パッケージの配置
パッケージは、このリリースでの Linux ファイル システムにのみ格納できます。 SSIS カタログ データベースとレガシ SSIS サービスでは、パッケージの配置とストレージの Linux では使用できません。

## <a name="schedule-packages"></a>パッケージのスケジュール設定
Linux システムのスケジューリングなどのツールを使用する`cron`パッケージをスケジュールします。 このリリースでは、パッケージの実行をスケジュールするのに Linux 上の SQL エージェントを使用できません。 詳細については、次を参照してください。 [cron で Linux 上のスケジュールの SSIS パッケージ](sql-server-linux-schedule-ssis-packages.md)します。

## <a name="limitations-and-known-issues"></a>制限事項と既知の問題

Linux 上の SSIS の既知の問題と制限事項の詳細については、次を参照してください。[制限事項と既知の問題を Linux 上の SSIS の](sql-server-linux-ssis-known-issues.md)します。

## <a name="more-info-about-ssis-on-linux"></a>Linux 上の SSIS に関する詳細情報

Linux 上の SSIS の詳細については、次のブログの投稿を参照してください。

-   [Linux 上の SSIS は SQL Server CTP2.1 で使用できます。](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/)
-   [(SQL Server CTP 2.1 更新) を Linux 上の SSIS の ODBC がサポートされています。](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/)

## <a name="more-info-about-ssis"></a>SSIS に関する詳細情報

Microsoft SQL Server Integration Services (SSIS) は、抽出、変換、およびデータ ウェアハウジング用パッケージの読み込み (ETL) をなど、パフォーマンスの高いデータ統合ソリューションを構築するためのプラットフォームです。 詳細については、「[SQL Server Integration Services](/sql/integration-services/sql-server-integration-services)」を参照してください。

SSIS には、次の機能が含まれています。
- グラフィカル ツールおよびビルド、および Windows 上のパッケージをデバッグ用のウィザード
- さまざまな FTP 操作などのワークフロー機能を実行する、SQL ステートメント、および電子メール メッセージを送信するためのタスク
- さまざまなデータ ソースと変換を抽出し、データの読み込み
- さまざまなクリーニング、集計、マージ、およびデータのコピーの変換
- 独自のカスタム スクリプトやコンポーネントを SSIS を拡張するためのアプリケーション プログラミング インターフェイス (Api)

SSIS で開始するには、最新バージョンをダウンロード[SQL Server Data Tools (SSDT)](../integration-services/ssis-how-to-create-an-etl-package.md)します。

SSIS についての詳細については、次の記事を参照してください。
- [SQL Server Integration Services を詳細します。](../integration-services/sql-server-integration-services.md)
- [SQL Server Integration Services (SSIS) の開発と管理ツール](../integration-services/integration-services-ssis-development-and-management-tools.md)
- [SQL Server Integration Services のチュートリアル](../integration-services/integration-services-tutorials.md)

## <a name="related-content-about-ssis-on-linux"></a>Linux 上の SSIS に関する関連コンテンツ
-   [Linux 上の SQL Server Integration Services (SSIS) のインストールします。](sql-server-linux-setup-ssis.md)
-   [Ssis conf で Linux 上の SQL Server Integration Services を構成します。](sql-server-linux-configure-ssis.md)
-   [制限事項と Linux での SSIS の既知の問題](sql-server-linux-ssis-known-issues.md)
-   [スケジュールの SQL Server Integration Services パッケージ cron を使用した Linux 上の実行](sql-server-linux-schedule-ssis-packages.md)
