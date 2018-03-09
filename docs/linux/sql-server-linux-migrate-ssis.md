---
title: "抽出、変換、および SSIS Linux でのデータを読み込む |Microsoft ドキュメント"
description: "この記事では、Linux コンピューターの SQL Server Integration Services (SSIS) がについて説明します"
author: leolimsft
ms.author: lle
ms.reviewer: douglasl
manager: craigg
ms.date: 01/09/2018
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: 
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.workload: On Demand
ms.openlocfilehash: 87c28ec845a59ea13acce0585bc9b249f100a4a5
ms.sourcegitcommit: 9d0467265e052b925547aafaca51e5a5e93b7e38
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/02/2018
---
# <a name="extract-transform-and-load-data-on-linux-with-ssis"></a>抽出、変換、および SSIS Linux でのデータを読み込む

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

この記事では、Linux 上の SQL Server Integration Services (SSIS) パッケージを実行する方法について説明します。 SSIS は、複数のソースと形式からデータを抽出することで複雑なデータ統合の問題を解決し、データをクレンジング データ変換および読み込み、複数の送信先にします。 

Linux で実行されている SSIS パッケージは、Windows、オンプレミスまたはクラウドでは、Linux では、または Docker で実行されている Microsoft SQL Server に接続できます。 Azure SQL Database、Azure SQL Data Warehouse、ODBC データ ソース、フラット ファイル、および ADO.NET ソース、XML ファイル、および OData サービスを含む他のデータ ソースに接続することもできます。

SSIS の機能に関する詳細については、次を参照してください。 [SQL Server Integration Services](../integration-services/sql-server-integration-services.md)です。

## <a name="prerequisites"></a>前提条件

最初を Linux コンピューターで SSIS パッケージを実行するには、SQL Server Integration Services をインストールする必要があります。 SSIS は、Linux コンピューターの SQL Server のインストールには含まれません。 インストール手順については、次を参照してください。 [SQL Server Integration Services のインストール](sql-server-linux-setup-ssis.md)です。

さらに、作成およびパッケージを管理する Windows コンピューターをいなければなりません。 SSIS のデザインおよび管理ツールは、現在は使用できませんの Linux コンピューターを Windows アプリケーションです。 

## <a name="run-an-ssis-package"></a>SSIS パッケージを実行します。

Linux コンピューターで、SSIS パッケージを実行するには、次の作業を行います。

1.  SSIS パッケージを Linux コンピューターにコピーします。
2.  次のコマンドを実行します。
    ```
    $ dtexec /F \<package name \> /DE <protection password>
    ```

## <a name="run-an-encrypted-password-protected-package"></a>暗号化された (パスワードで保護された) パッケージを実行します。
これには、パスワードで暗号化されている SSIS パッケージを実行する 3 つの方法があります。

1.  環境変数の値を設定`SSIS_PACKAGE_DECRYPT`次の例のように。

    ```
    SSIS_PACKAGE_DECRYPT=test /opt/ssis/bin/dtexec /f package.dtsx
    ```

2.  指定して、`/de[crypt]`対話形式で、次の例で示すように、パスワードを入力するオプション。

    ```
    /opt/ssis/bin/dtexec /f package.dtsx /de
    
    Enter decryption password:
    ```

3.  指定して、`/de`次の例のように、コマンド ラインで、パスワードを提供するオプションです。 このメソッドは、コマンド履歴にコマンドを使用して復号化パスワードを格納するためには推奨されません。

    ```
    opt/ssis/bin/dtexec /f package.dtsx /de test
    
    Warning: Using /De[crypt] <password> may store decryption password in command history.
    
    You can use /De[crypt] instead to enter interactive mode,
    or use environment variable SSIS_PACKAGE_DECRYPT to set decryption password.
    ```

## <a name="design-packages"></a>パッケージの設計

**ODBC データ ソースに接続**です。 Linux CTP 2.1 の更新以降、SSIS で SSIS パッケージは、Linux の ODBC 接続を使用できます。 この機能は、SQL Server および MySQL の ODBC ドライバーでテスト済みですはまた、ODBC 仕様に従うすべての Unicode ODBC ドライバーを使用する必要があります。 、デザイン時に、ODBC データに接続する DSN または接続文字列を指定できますWindows 認証を使用することもできます。 詳細については、次を参照してください。、 [Linux 上のブログの投稿 announcing ODBC サポート](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/)です。

**パス**です。 SSIS パッケージ内の Windows スタイル パスを提供します。 Linux 上の SSIS では、Linux スタイルのパスをサポートしていませんが、実行時に、Windows 形式のパスを Linux スタイル パスにマップします。 次に、たとえば、Linux 上の SSIS マップ Windows 形式のパス`C:\test`Linux スタイルのパスに`/test`です。

## <a name="deploy-packages"></a>パッケージを展開します。
パッケージは、このリリースでは、Linux 上のファイル システムにのみ保存できます。 SSIS カタログ データベースと、レガシ SSIS サービスでは、パッケージの配置とストレージの Linux で使用できません。

## <a name="schedule-packages"></a>パッケージのスケジュール設定
スケジューリング ツールなど、Linux システムを使用する`cron`パッケージをスケジュールします。 このリリースでは、パッケージの実行をスケジュールするのに Linux で SQL エージェントを使用することはできません。 詳細については、次を参照してください。 [cron を Linux 上のスケジュールの SSIS パッケージ](sql-server-linux-schedule-ssis-packages.md)です。

## <a name="limitations-and-known-issues"></a>制限事項と既知の問題

制限事項と Linux の SSIS の既知の問題に関する詳細情報は、次を参照してください。[制限事項と既知の問題 Linux 上の SSIS](sql-server-linux-ssis-known-issues.md)です。

## <a name="more-info-about-ssis-on-linux"></a>詳細については、Linux 上の SSIS

Linux 上の SSIS の詳細については、次のブログの投稿を参照してください。

-   [Linux 上の SSIS では、SQL Server 2017 CTP2.1 で使用できます。](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/)
-   [ODBC は (SQL Server 2017 CTP 2.1 更新) を Linux 上の SSIS でサポートされています。](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/)

## <a name="more-info-about-ssis"></a>詳細については、SSIS

Microsoft SQL Server Integration Services (SSIS) は、抽出、変換、およびデータ ウェアハウスの読み込み (ETL) のパッケージを含む、パフォーマンスの高いデータ統合ソリューションを構築するためのプラットフォームです。 詳細については、「[SQL Server Integration Services](/sql/integration-services/sql-server-integration-services)」を参照してください。

SSIS では、次の機能があります。
- グラフィカル ツールとのビルドと Windows 上のパッケージをデバッグするためのウィザード
- さまざまな SQL ステートメントの実行、電子メール メッセージを送信する FTP 操作などのワークフロー機能を実行するタスク
- さまざまなデータ ソースおよび変換先を抽出およびデータの読み込みを行う
- さまざまなクリーニング、集計、マージ、およびデータのコピーの変換
- 独自のカスタム スクリプトおよびコンポーネントと SSIS を拡張するためのアプリケーション プログラミング インターフェイス (Api)

最新バージョンをダウンロード、SSIS で作業を開始する[SQL Server Data Tools (SSDT)](../integration-services/ssis-how-to-create-an-etl-package.md)です。

SSIS に関する詳細については、次の記事を参照してください。
- [SQL Server Integration Services の詳細を表示します](../integration-services/sql-server-integration-services.md)
- [SQL Server Integration Services (SSIS) の開発および管理ツール](../integration-services/integration-services-ssis-development-and-management-tools.md)
- [SQL Server Integration Services のチュートリアル](../integration-services/integration-services-tutorials.md)

## <a name="related-content-about-ssis-on-linux"></a>Linux 上の SSIS についての関連コンテンツ
-   [Linux 上の SQL Server Integration Services (SSIS) のインストールします。](sql-server-linux-setup-ssis.md)
-   [Ssis conf で Linux 上の SQL Server Integration Services を構成します。](sql-server-linux-configure-ssis.md)
-   [制限事項と Linux の SSIS の既知の問題](sql-server-linux-ssis-known-issues.md)
-   [スケジュール SQL Server Integration Services パッケージの cron と Linux の実行](sql-server-linux-schedule-ssis-packages.md)
