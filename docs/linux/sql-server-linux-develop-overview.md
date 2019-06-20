---
title: SQL Server on Linux 用アプリケーションの開発 |Microsoft Docs
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 11/17/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 758cb738-b018-465b-9ab0-59a24b892e66
ms.openlocfilehash: 4d3ef46dfbacb1c4cbfe67df555b79fb10ade86d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66705816"
---
# <a name="how-to-get-started-developing-applications-for-sql-server-on-linux"></a>SQL Server on Linux 向けのアプリケーションの開発を開始する方法

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

接続して、c#、Java、Node.js、PHP、Python、Ruby、および C++ などのプログラミング言語のさまざまな Linux 上の SQL Server を使用するアプリケーションを作成することができます。 一般的な web フレームワークやオブジェクト リレーショナル マッピング (ORM) フレームワークを使用することもできます。

> [!VIDEO https://channel9.msdn.com/events/Connect/2017/T153/player]

> [!TIP]
> これらと同じ開発オプションでは、他のプラットフォームでは、SQL Server を対象することもできます。 アプリケーションがオンプレミスで実行されている SQL Server を対象または macOS でクラウド、Linux、Windows、Docker でします。 または、Azure SQL Database と Azure SQL Data Warehouse を対象にできます。

## <a name="try-the-tutorials"></a>チュートリアルをお試しください。

開始して、SQL Server でアプリケーションを構築する最善の方法では、自分でやってみてください。

- 参照する[入門チュートリアル](https://aka.ms/sqldev)します。
- 言語および開発プラットフォームを選択します。
- コード サンプルを実行してください。

> [!TIP]
> SQL Server on Docker 用の開発する場合を見て、 **macOS**チュートリアル。

## <a name="create-new-applications"></a>新しいアプリケーションを作成する

新しいアプリケーションを作成する場合の実行の一覧を見て、[接続ライブラリ](sql-server-linux-develop-connectivity-libraries.md)コネクタとさまざまなプログラミング言語の使用可能な一般的なフレームワークの概要についてはします。

## <a name="use-existing-applications"></a>既存のアプリケーションを使用します。

既存のデータベース アプリケーションがあれば、SQL Server on Linux をターゲットに単にその接続文字列を変更できます。 詳細を閲覧することを確認、[既知の問題](sql-server-linux-release-notes.md)SQL Server on Linux でします。

## <a name="use-existing-sql-tools-on-windows-with-sql-server-on-linux"></a>SQL Server on Linux での Windows で既存の SQL ツールを使用します。

SSMS、SSDT では、PowerShell などの Windows で現在実行しているツールは、SQL Server on Linux でも動作します。 実行していないネイティブ Linux 上では、Linux 上のリモートの SQL Server インスタンスを管理できます。 

詳細については、次のトピックを参照してください。

- [SQL Server Management Studio (SSMS)](sql-server-linux-manage-ssms.md)
- [SQL Server Data Tools (SSDT)](sql-server-linux-develop-use-ssdt.md)
- [SQL PowerShell](sql-server-linux-manage-powershell.md)

> [!Note]
> 最適なエクスペリエンスでこれらのツールの最新バージョンを使用していることを確認します。

## <a name="use-new-sql-tools-for-linux"></a>新しい SQL ツールを使用して、Linux 用

新たに使用することができます[mssql 拡張機能](https://aka.ms/mssql-marketplace)の[Visual Studio Code](https://code.visualstudio.com)で Linux、macOS、および Windows。 ステップ バイ ステップ チュートリアルでは、次のチュートリアルを参照してください。

- [Visual Studio Code の使用](sql-server-linux-develop-use-vscode.md)

Linux のネイティブな新しいコマンド ライン ツールを使用することもできます。 これらのツールを以下に示します。

- [sqlcmd](../tools/sqlcmd-utility.md)
- [bcp](sql-server-linux-migrate-bcp.md)
- [mssql-conf](sql-server-linux-configure-mssql-conf.md)

## <a name="next-steps"></a>次のステップ

開始するには、次のクイック スタートのいずれかを使用して Linux に SQL Server をインストールします。

- [Red Hat Enterprise Linux をインストールします。](quickstart-install-connect-red-hat.md)
- [SUSE Linux Enterprise Server にインストールします](quickstart-install-connect-suse.md)
- [Ubuntu にインストールします](quickstart-install-connect-ubuntu.md)
- [Docker で実行します。](quickstart-install-connect-ubuntu.md)
