---
title: "抽出、変換、および SSIS Linux でのデータを読み込む |Microsoft ドキュメント"
description: 
author: sanagama
ms.author: sanagama
manager: jhubbard
ms.date: 07/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 9dab69c7-73af-4340-aef0-de057356b791
ms.translationtype: MT
ms.sourcegitcommit: a6aeda8e785fcaabef253a8256b5f6f7a842a324
ms.openlocfilehash: 736b7e0744a95d859bd25a6c7974dc13e79d4bb7
ms.contentlocale: ja-jp
ms.lasthandoff: 09/21/2017

---
# <a name="extract-transform-and-load-data-on-linux-with-ssis"></a>抽出、変換、および SSIS Linux でのデータを読み込む

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

このトピックでは、Linux 上の SQL Server Integration Services (SSIS) パッケージを実行する方法について説明します。 SSIS は、変換して、データのクレンジングと複数の送信先を更新から複数のソースと形式のデータの読み込みで複雑なデータ統合の問題を解決します。 

Linux で実行されている SSIS パッケージは、Windows、オンプレミスまたはクラウドでは、Linux では、または Docker で実行されている Microsoft SQL Server に接続できます。 Azure SQL Database、Azure SQL Data Warehouse、および ODBC データ ソースに接続することもできます。

SSIS を使用しても作成およびパッケージを管理する Windows コンピューターがあるときに、Linux でパッケージを実行します。 SSIS のデザインおよび管理ツールは、Windows アプリケーションです。 

## <a name="prerequisites"></a>前提条件

最初を Linux コンピューターで SSIS パッケージを実行するには、SQL Server Integration Services をインストールする必要があります。 インストール手順については、次を参照してください。 [SQL Server Integration Services のインストール](sql-server-linux-setup-ssis.md)です。

## <a name="run-an-ssis-package"></a>SSIS パッケージを実行します。

Linux コンピューターで、SSIS パッケージを実行するには、次の作業を行います。

1.  SSIS パッケージを Linux コンピューターにコピーします。
2.  次のコマンドを実行します。
    ```
    $ dtexec /F \<package name \> /DE <protection password>
    ```

## <a name="more-about-ssis-on-linux"></a>Linux 上の SSIS に関する詳細情報

**ODBC 接続**です。 Linux CTP 2.1 の更新以降、SSIS で SSIS パッケージは、Linux の ODBC 接続を使用できます。 この機能は、SQL Server および MySQL の ODBC ドライバーでテスト済みですはまた、ODBC 仕様に従うすべての Unicode ODBC ドライバーを使用する必要があります。 、デザイン時に、ODBC データに接続する DSN または接続文字列を指定できますWindows 認証を使用することもできます。 詳細については、次を参照してください。、 [Linux 上のブログの投稿 announcing ODBC サポート](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/)です。

**パス**です。 Linux 上の SSIS では、Linux スタイルのパスをサポートしていませんが、実行時に、Windows 形式のパスを Linux スタイル パスにマップします。 SSIS パッケージ内の Windows スタイル パスを提供します。 次に、たとえば、Linux 上の SSIS マップ Windows 形式のパス`C:\test`Linux スタイルのパスに`/test`です。

**パッケージの配置**です。 パッケージは、このリリースでは、Linux 上のファイル システムにのみ保存できます。 SSIS カタログ データベースと、レガシ SSIS サービスでは、パッケージの配置とストレージの Linux で使用できません。

**パッケージのスケジュール設定**です。 このリリースでは、パッケージの実行をスケジュールするのに Linux で SQL エージェントを使用することはできません。

**その他の制限事項と既知の問題**です。 Linux で SSIS パッケージを実行すると、このリリースでは、次の機能はサポートされていません。
  - SSIS カタログ データベース
  - SQL エージェントがスケジュールされているパッケージの実行
  - [Windows 認証]
  - サード パーティのコンポーネント
  - 変更データ キャプチャ (CDC)
  - SSIS のスケール アウト
  - SSIS 用 azure Feature Pack
  - Hadoop と HDFS のサポート
  - Microsoft Connector for SAP BW

その他の制限事項と Linux 上の SSIS に関する既知の問題には、次を参照してください。、[リリース ノート](sql-server-linux-release-notes.md#ssis)です。

Linux 上の SSIS の詳細については、次のブログの投稿を参照してください。

-   [Linux 上の SSIS では、SQL Server 2017 CTP2.1 で使用できます。](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/)
-   [ODBC は (SQL Server 2017 CTP 2.1 更新) を Linux 上の SSIS でサポートされています。](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/)

## <a name="more-about-ssis"></a>SSIS に関する詳細情報

Microsoft SQL Server Integration Services (SSIS) は、抽出、変換、およびデータ ウェアハウスの読み込み (ETL) のパッケージを含む、パフォーマンスの高いデータ統合ソリューションを構築するためのプラットフォームです。 詳細については、「[SQL Server Integration Services](/sql/integration-services/sql-server-integration-services.md)」を参照してください。

SSIS では、次の機能があります。
- グラフィカル ツールとのビルドと Windows 上のパッケージをデバッグするためのウィザード
- さまざまな SQL ステートメントの実行、電子メール メッセージを送信する FTP 操作などのワークフロー機能を実行するタスク
- さまざまなデータ ソースおよび変換先を抽出およびデータの読み込みを行う
- さまざまなクリーニング、集計、マージ、およびデータのコピーの変換
- 独自のカスタム スクリプトおよびコンポーネントと SSIS を拡張するためのアプリケーション プログラミング インターフェイス (Api)

最新バージョンをダウンロード、SSIS で作業を開始する[SQL Server Data Tools (SSDT)](/sql-docs/docs/integration-services/ssis-how-to-create-an-etl-package)です。

## <a name="see-also"></a>参照
- [SQL Server Integration Services の詳細を表示します](/sql-docs/docs/integration-services/sql-server-integration-services)
- [SQL Server Integration Services (SSIS) の開発および管理ツール](/sql-docs/docs/integration-services/integration-services-ssis-development-and-management-tools)
- [SQL Server Integration Services のチュートリアル](/sql-docs/docs/integration-services/integration-services-tutorials)

