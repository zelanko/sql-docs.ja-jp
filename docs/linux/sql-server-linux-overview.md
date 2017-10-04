---
title: "SQL Server on Linux の概要 |Microsoft ドキュメント"
description: "ここでは、SQL Server on Linux を実行し、方法の詳細について説明します。"
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 9dcc6a90-0add-42c2-815b-862e4e2a21ac
ms.translationtype: MT
ms.sourcegitcommit: 834bba08c90262fd72881ab2890abaaf7b8f7678
ms.openlocfilehash: 6fdb36fbf294ea1f109728a1f304b5a3f3662122
ms.contentlocale: ja-jp
ms.lasthandoff: 10/02/2017

---
# <a name="sql-server-on-linux"></a>SQL Server on Linux

SQL Server 2017 が Linux で実行されます。 ような多くの機能とサービスは、オペレーティング システムに関係なく、同じ SQL Server データベース エンジンを勧めします。

## <a name="install"></a>Install

、作業を開始するには、次のクイック スタート チュートリアルのいずれかを使用して Linux に SQL Server をインストールします。

- [Red Hat Enterprise Linux にインストールします。](quickstart-install-connect-red-hat.md)
- [SUSE Linux Enterprise Server をインストールします。](quickstart-install-connect-suse.md)
- [Ubuntu をインストールします。](quickstart-install-connect-ubuntu.md)
- [Docker で実行します。](quickstart-install-connect-docker.md)

> [!NOTE]
> Docker 自体は、Linux、Mac、および Windows で Docker イメージを実行できることを意味する、複数のプラットフォームで実行されます。

## <a name="connect"></a>Connect

インストール後に、Linux コンピューター上の SQL Server インスタンスに接続します。 ローカルまたはリモートでと、さまざまなツールとドライバーを接続することができます。 クイック スタート チュートリアルが使用する方法をデモンストレーション、 [sqlcmd](sql-server-linux-setup-tools.md)コマンド ライン ツールです。 その他のツールは次のとおりです。

| ツール | チュートリアル |
|-----|-----|
| Visual Studio Code (VS Code) | [SQL Server on Linux で VS コードを使用します。](sql-server-linux-develop-use-vscode.md) |
| SQL Server Management Studio (SSMS) | [Windows で SSMS を使用して Linux 上の SQL Server に接続するには](sql-server-linux-develop-use-ssms.md) |
| SQL Server Data Tools (SSDT) | [SQL Server on Linux で SSDT を使用します。](sql-server-linux-develop-use-ssdt.md) |

## <a name="explore"></a>探索

SQL Server 2017 では、Linux を含む、サポートされているすべてのプラットフォームで同じ基になるデータベース エンジンがあります。 非常に多くの既存の機能と機能は、Linux で同じように動作します。 ドキュメントのこの領域では、Linux の観点からこれらの機能の一部を公開します。 これは、Linux 固有の要件がある領域も呼び出します。

SQL Server を使い慣れている場合は、確認、[リリース ノート](sql-server-linux-release-notes.md)のこのリリースの既知の問題の一般的なガイドラインとします。 見て[SQL Server on Linux の新](sql-server-linux-whats-new.md)だけでなく[新機能の全体的な SQL Server 2017](../sql-server/what-s-new-in-sql-server-2017.md)。

##  <a name="infotipmediageneralinfotippng-engage-with-the-sql-server-engineering-team"></a>![info_tip](./media/general/info_tip.png) SQL Server エンジニアリング チームと連携する

- [DBA スタック Exchange](https://dba.stackexchange.com/questions/tagged/sql-server): データベースの管理の質問
- [スタックのオーバーフロー](http://stackoverflow.com/questions/tagged/sql-server): 開発の質問
- [MSDN フォーラム](https://social.msdn.microsoft.com/Forums/en-US/home?category=sqlserver): 技術的な質問
- [Microsoft Connect](https://connect.microsoft.com/SQLServer/Feedback): バグ、および要求機能の報告
- [Reddit](https://www.reddit.com/r/SQLServer/): SQL Server の説明

