---
title: "SQL Server on Linux の概要 |Microsoft ドキュメント"
description: "ここでは、SQL Server on Linux を実行する方法の詳細について説明します。"
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: 9dcc6a90-0add-42c2-815b-862e4e2a21ac
ms.workload: Active
ms.openlocfilehash: b598357bb8ebe17ad15fb10e1d74c21c169c1da8
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2017
---
# <a name="sql-server-on-linux"></a>SQL Server on Linux

SQL Server 2017 を Linux で実行することができます。 多くの機能とサービスを、オペレーティング システムに関係なく、同じ SQL Server データベース エンジンで使用することができます。

## <a name="install"></a>Install

作業を開始するには、次のクイック スタート チュートリアルのいずれかを使用して Linux に SQL Server をインストールします。

- [Red Hat Enterprise Linux にインストールします](quickstart-install-connect-red-hat.md)
- [SUSE Linux Enterprise Server にインストールします](quickstart-install-connect-suse.md)
- [Ubuntu にインストールします](quickstart-install-connect-ubuntu.md)
- [Docker で実行します](quickstart-install-connect-docker.md)
- [Azure での SQL VM プロビジョニング](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=%2fsql%2flinux%2ftoc.json)

> [!NOTE]
> Docker は、Linux、Mac、および Windows で Docker イメージを実行することができ、複数のプラットフォームで実行することができます。

## <a name="connect"></a>Connect

インストール後に、Linux コンピューター上の SQL Server インスタンスに接続します。 ローカルまたはリモートで、さまざまなツールとドライバーで接続することができます。 クイック スタート チュートリアルは、 [sqlcmd](sql-server-linux-setup-tools.md) コマンド ライン ツールを使用するためのデモンストレーションとなっています。 その他のツールは次のとおりです。

| ツール | チュートリアル |
|-----|-----|
| Visual Studio Code (VS Code) | [SQL Server on Linux で VS コードを使用します](sql-server-linux-develop-use-vscode.md) |
| SQL Server Management Studio (SSMS) | [Windows で SSMS を使用して Linux 上の SQL Server に接続するには](sql-server-linux-develop-use-ssms.md) |
| SQL Server Data Tools (SSDT) | [SSDT で SQL Server on Linux を使用します](sql-server-linux-develop-use-ssdt.md) |

## <a name="explore"></a>探索

SQL Server 2017 では、Linux を含む、サポートされているすべてのプラットフォームで同じベースとなるデータベース エンジンを使用しています。 非常に多くの既存の機能と操作は、Linux でも同じように動作します。 このドキュメントでは、Linux の観点からこれらの機能のいくつかを公開しています。 これは、Linux 固有の要件がある領域についても触れています。

SQL Server を使い慣れている場合は、[リリース ノート](sql-server-linux-release-notes.md)で、このリリースの既知の問題と、一般的なガイドラインを確認してください。 [SQL Server on Linux の新機能](sql-server-linux-whats-new.md)と、[SQL Server 2017 の新機能](../sql-server/what-s-new-in-sql-server-2017.md) について解説しています。

##  <a name="infotipmediageneralinfotippng-engage-with-the-sql-server-engineering-team"></a>![info_tip](./media/general/info_tip.png) SQL Server エンジニアリング チームと連携する

- [DBA スタック Exchange](https://dba.stackexchange.com/questions/tagged/sql-server): データベースの管理の質問
- [スタックのオーバーフロー](http://stackoverflow.com/questions/tagged/sql-server): 開発の質問
- [MSDN フォーラム](https://social.msdn.microsoft.com/Forums/en-US/home?category=sqlserver): 技術的な質問
- [Microsoft Connect](https://connect.microsoft.com/SQLServer/Feedback): バグ、および要求機能の報告
- [Reddit](https://www.reddit.com/r/SQLServer/): SQL Server の説明
