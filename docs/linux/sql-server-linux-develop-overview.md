---
title: "SQL Server on Linux のアプリケーションを開発 |Microsoft ドキュメント"
description: 
author: sanagama
ms.author: sanagama
manager: jhubbard
ms.date: 07/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 758cb738-b018-465b-9ab0-59a24b892e66
ms.custom: H1Hack27Feb2017
ms.translationtype: MT
ms.sourcegitcommit: ea75391663eb4d509c10fb785fcf321558ff0b6e
ms.openlocfilehash: 7fcd3350796d88d02011f0d45e666851d69cfd78
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="how-to-get-started-developing-applications-for-sql-server-on-linux"></a>SQL Server on Linux 用のアプリケーションの開発を開始する方法

[!INCLUDE[tsql-appliesto-sslinux-only](../../docs/includes/tsql-appliesto-sslinux-only.md)]

接続し、c#、Java、Node.js、PHP、Python、Ruby、および C++ などのプログラミング言語のさまざまな Linux に SQL Server 2017 RC2 を使用するアプリケーションを作成することができます。 一般的な web フレームワーク、およびオブジェクト リレーショナル マッピング (ORM) フレームワークを使用することもできます。

> [!TIP]
> これらと同じ開発オプションでは、他のプラットフォームでは、SQL Server を対象することもできます。 アプリケーションがオンプレミスで実行して SQL Server を対象またはクラウドでは、Linux、Windows、または Docker で macos です。 または、Azure SQL Database と Azure SQL Data Warehouse を対象にできます。

## <a name="try-the-tutorials"></a>チュートリアルを実行してください。

作業を開始し、SQL Server とアプリケーションを構築する最善の方法では、ご自分で試してみてください。

- 参照[入門チュートリアル](http://aka.ms/sqldev)です。
- 言語および開発プラットフォームを選択します。
- コード サンプルを実行してください。

> [!TIP]
> Docker での SQL Server 2017 RC2 を開発する場合を見て、 **macOS**チュートリアルです。

## <a name="create-new-applications"></a>新しいアプリケーションを作成する

新しいアプリケーションを作成する場合を見ての一覧、[接続ライブラリ](sql-server-linux-develop-connectivity-libraries.md)コネクタとさまざまなプログラミング言語の使用可能な一般的なフレームワークの概要についてはします。

## <a name="use-existing-applications"></a>既存のアプリケーションを使用します。

既存のデータベース アプリケーションがあれば、Linux 上の SQL Server 2017 RC2 をターゲットに単にその接続文字列を変更できます。 についての情報を確認してください、[既知の問題](sql-server-linux-release-notes.md)Linux 上の SQL Server 2017 RC2 でできます。

## <a name="use-existing-sql-tools-on-windows-with-sql-server-on-linux"></a>SQL Server on Linux での Windows で既存の SQL ツールを使用します。

SSMS、SSDT では、PowerShell などの Windows で現在実行しているツールは、Linux 上の SQL Server 2017 RC2 と併用することもできます。 実行していないネイティブ on Linux では、Linux 上のリモートの SQL Server インスタンスを管理することができます。 

詳細については、次のトピックを参照してください。

- [SQL Server Management Studio (SSMS)](sql-server-linux-develop-use-ssms.md)
- [SQL Server Data Tools (SSDT)](sql-server-linux-develop-use-ssdt.md)
- [SQL PowerShell](sql-server-linux-manage-powershell.md)

> [!Note] 
> 最良の結果、これらのツールの最新バージョンを使用していることを確認します。

## <a name="use-new-sql-tools-for-linux"></a>新しい SQL ツールを使用して、Linux 用

新しいを使用することができます[mssql 拡張子](https://aka.ms/mssql-marketplace)の[Visual Studio Code](https://code.visualstudio.com) Linux、macOS、および Windows。 ステップ バイ ステップ チュートリアルでは、以下のチュートリアルを参照してください。

- [Visual Studio のコードを使用します。](sql-server-linux-develop-use-vscode.md)

Linux のネイティブな新しいコマンド ライン ツールを使用することもできます。 これらのツールは次のとおりです。

- [sqlcmd](../tools/sqlcmd-utility.md)
- [bcp](sql-server-linux-migrate-bcp.md)
- [mssql conf](sql-server-linux-configure-mssql-conf.md)

## <a name="next-steps"></a>次の手順

、作業を開始するには、次のクイック スタート チュートリアルのいずれかを使用して Linux に SQL Server をインストールします。

- [Red Hat Enterprise Linux にインストールします。](quickstart-install-connect-red-hat.md)
- [SUSE Linux Enterprise Server をインストールします。](quickstart-install-connect-suse.md)
- [Ubuntu をインストールします。](quickstart-install-connect-ubuntu.md)
- [Docker で実行します。](quickstart-install-connect-ubuntu.md)

