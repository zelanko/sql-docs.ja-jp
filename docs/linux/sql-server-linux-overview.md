---
title: "SQL Server on Linux の概要 |Microsoft ドキュメント"
description: "このトピックでは、SQL Server が Linux 上でどのように実行されるかを説明し、詳細な知識を得るための情報を提供します。"
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/22/2018
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: 
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: 9dcc6a90-0add-42c2-815b-862e4e2a21ac
ms.workload: Active
ms.openlocfilehash: faa2898017347f59d415f7f5bf5bd6795a3f9de6
ms.sourcegitcommit: f0c5e37c138be5fb2cbb93e9f2ded307665b54ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/24/2018
---
# <a name="sql-server-on-linux"></a>SQL Server on Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

SQL Server 2017 を Linux で実行することができるようになりました。 同じ SQL Server データベース エンジンです。オペレーティング システムに関係なく、類似した多くの機能とサービスを備えています。

## <a name="install"></a>インストール

、作業を開始するには、次のクイック スタートのいずれかを使用して Linux に SQL Server をインストールします。

- [Red Hat Enterprise Linux にインストールします](quickstart-install-connect-red-hat.md)
- [SUSE Linux Enterprise Server にインストールします](quickstart-install-connect-suse.md)
- [Ubuntu にインストールします](quickstart-install-connect-ubuntu.md)
- [Docker で実行します](quickstart-install-connect-docker.md)
- [Azure での SQL VM プロビジョニング](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=%2fsql%2flinux%2ftoc.json)

> [!NOTE]
> Docker 自体は複数のプラットフォームで実行することができます。つまり、Linux、Mac、および Windows で Docker イメージを実行することができます。

## <a name="connect"></a>接続

インストール後に、Linux コンピューター上の SQL Server インスタンスに接続します。 ローカルまたはリモートで、さまざまなツールとドライバーで接続することができます。 クイック スタート チュートリアルでは、 [sqlcmd](sql-server-linux-setup-tools.md) コマンド ライン ツールの使用方法を説明します。 その他のツールは次のとおりです。

| ツール | チュートリアル |
|-----|-----|
| Visual Studio Code (VS Code) | [SQL Server on Linux での VS Code の使用](sql-server-linux-develop-use-vscode.md) |
| SQL Server Management Studio (SSMS) | [Windows で SSMS を使用して Linux 上の SQL Server に接続するには](sql-server-linux-develop-use-ssms.md) |
| SQL Server Data Tools (SSDT) | [SSDT を SQL Server on Linux と共に使用します](sql-server-linux-develop-use-ssdt.md) |

## <a name="explore"></a>探索

SQL Server 2017 では、Linux を含む、サポートされているすべてのプラットフォームで同じベースとなるデータベース エンジンを使用しています。 非常に多くの既存の機能と操作は、Linux でも同じように動作します。 このドキュメントでは、Linux の観点からこれらの機能のいくつかを紹介しています。 また、Linux 固有の要件がある領域についても触れています。

SQL Server を使い慣れている場合は、[リリース ノート](sql-server-linux-release-notes.md)で、このリリースの既知の問題と、一般的なガイドラインを確認してください。 その後、[SQL Server on Linux の新機能](sql-server-linux-whats-new.md) と、[SQL Server 2017 の新機能](../sql-server/what-s-new-in-sql-server-2017.md) をご覧ください。 

> [!TIP]
> よく寄せられる質問に対する回答については、次を参照してください。、 [SQL Server on Linux に関する FAQ](sql-server-linux-faq.md)です。

[!INCLUDE[Get Help Options](../includes/paragraph-content/get-help-options.md)]