---
title: SQL Server on Linux の概要 |Microsoft Docs
description: このトピックでは、SQL Server が Linux 上でどのように実行されるかを説明し、詳細な知識を得るための情報を提供します。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 09/25/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 9dcc6a90-0add-42c2-815b-862e4e2a21ac
ms.openlocfilehash: 37cd2269d6d8fe413b730a111ad0a5f604ed8994
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2018
ms.locfileid: "52408879"
---
# <a name="sql-server-on-linux"></a>SQL Server on Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

::: moniker range="= sql-server-2017 || = sqlallproducts-allversions"
SQL Server は SQL Server 2017 以降では、Linux で実行されます。 同じ SQL Server データベース エンジンのような多くの機能と、オペレーティング システムに関係なくサービスにすることをお勧めします。
::: moniker-end

::: moniker range=">= sql-server-ver15 || >= sql-server-linux-ver15"
SQL Server 2019 プレビューは、Linux で実行されます。 同じ SQL Server データベース エンジンのような多くの機能と、オペレーティング システムに関係なくサービスにすることをお勧めします。 このリリースに関する詳細については、次を参照してください。[新機能については Linux 用の SQL Server 2019 プレビュー](../sql-server/what-s-new-in-sql-server-ver15.md#sqllinux)します。
::: moniker-end

::: moniker range="= sql-server-2017"
> [!TIP]
> [SQL Server 2019 プレビュー](sql-server-linux-overview.md?view=sql-server-ver15)がリリースされました! 最新のリリースで新しい Linux の新機能についてを参照してください[新機能については Linux 用の SQL Server 2019 プレビュー](../sql-server/what-s-new-in-sql-server-ver15.md?view=sql-server-ver15#sqllinux)します。
::: moniker-end

::: moniker range="= sql-server-linux-2017"
> [!TIP]
> [SQL Server 2019 プレビュー](sql-server-linux-overview.md?view=sql-server-linux-ver15)がリリースされました! 最新のリリースで新しい Linux の新機能についてを参照してください[新機能については Linux 用の SQL Server 2019 プレビュー](../sql-server/what-s-new-in-sql-server-ver15.md?view=sql-server-linux-ver15#sqllinux)します。
::: moniker-end

::: moniker range="= sqlallproducts-allversions"
> [!TIP]
> SQL Server 2019 プレビューがリリースされました! 最新のリリースで新しい Linux の新機能についてを参照してください[新機能については Linux 用の SQL Server 2019 プレビュー](../sql-server/what-s-new-in-sql-server-ver15.md#sqllinux)します。
::: moniker-end

## <a name="install"></a>インストール

開始するには、次のクイック スタートのいずれかを使用して Linux に SQL Server をインストールします。

- [Red Hat Enterprise Linux をインストールします。](quickstart-install-connect-red-hat.md)
- [SUSE Linux Enterprise Server にインストールします](quickstart-install-connect-suse.md)
- [Ubuntu にインストールします](quickstart-install-connect-ubuntu.md)
- [Docker で実行します。](quickstart-install-connect-docker.md)
- [Azure での SQL VM プロビジョニング](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=%2fsql%2flinux%2ftoc.json)

> [!NOTE]
> Docker 自体は複数のプラットフォームで実行することができます。つまり、Linux、Mac、および Windows で Docker イメージを実行することができます。

## <a name="connect"></a>接続

インストール後に、Linux コンピューター上の SQL Server インスタンスに接続します。 ローカルまたはリモートで、さまざまなツールとドライバーで接続することができます。 クイック スタート チュートリアルでは、 [sqlcmd](sql-server-linux-setup-tools.md) コマンド ライン ツールの使用方法を説明します。 その他のツールは次のとおりです。

| ツール | チュートリアル |
|-----|-----|
| Visual Studio Code (VS Code) | [SQL Server on Linux での VS Code の使用](sql-server-linux-develop-use-vscode.md) |
| SQL Server Management Studio (SSMS) | [Windows で SSMS を使用して Linux 上の SQL Server に接続するには](sql-server-linux-manage-ssms.md) |
| SQL Server Data Tools (SSDT) | [SSDT を SQL Server on Linux と共に使用します](sql-server-linux-develop-use-ssdt.md) |

## <a name="explore"></a>探索

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

SQL Server 2017 では、Linux を含む、サポートされているすべてのプラットフォームで同じベースとなるデータベース エンジンを使用しています。 そのため、多くの既存の機能や機能 on Linux で同じように動作します。 このドキュメントでは、Linux の観点からこれらの機能のいくつかを紹介しています。 また、Linux 固有の要件がある領域についても触れています。

SQL Server を使い慣れている場合は、[リリース ノート](sql-server-linux-release-notes.md)で、このリリースの既知の問題と、一般的なガイドラインを確認してください。 その後、[SQL Server on Linux の新機能](sql-server-linux-whats-new.md) と、[SQL Server 2017 の新機能](../sql-server/what-s-new-in-sql-server-2017.md) をご覧ください。

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15"

[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] Linux を含む、サポートされているすべてのプラットフォームで同じ基になるデータベース エンジンが。 そのため、多くの既存の機能や機能 on Linux で同じように動作します。 このドキュメントでは、Linux の観点からこれらの機能のいくつかを紹介しています。 また、Linux 固有の要件がある領域についても触れています。

SQL Server on Linux 理解している場合は、確認、[リリース ノート](sql-server-linux-release-notes-2019.md)の一般的なガイドラインと、このリリースの既知の問題。 見て[Linux 上の SQL Server 2019 プレビューの新](../sql-server/what-s-new-in-sql-server-ver15.md?view=sql-server-ver15)します。

::: moniker-end

<!--SQL Server All Versions-->
::: moniker range="=sqlallproducts-allversions"

SQL Server 2017 と[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)]Linux を含む、サポートされているすべてのプラットフォームで同じ基になるデータベース エンジンがあります。 そのため、多くの既存の機能や機能 on Linux で同じように動作します。 このドキュメントでは、Linux の観点からこれらの機能のいくつかを紹介しています。 また、Linux 固有の要件がある領域についても触れています。

SQL Server on Linux 理解している場合は、リリース ノートを確認します。

- [SQL Server 2017 リリース ノート](sql-server-linux-release-notes.md)
- [SQL Server 2019 preview リリース ノート](sql-server-linux-release-notes-2019.md)

次の新機能になります。

- [SQL Server 2017 の新機能については](sql-server-linux-whats-new.md)
- [Linux 上の SQL Server 2019 プレビューは新機能](../sql-server/what-s-new-in-sql-server-ver15.md#sqllinux)

::: moniker-end

> [!TIP]
> よく寄せられる質問の回答は、次を参照してください。、 [SQL Server on Linux の FAQ](sql-server-linux-faq.md)します。

[!INCLUDE[Get Help Options](../includes/paragraph-content/get-help-options.md)]

[!INCLUDE[contribute-to-content](../includes/paragraph-content/contribute-to-content.md)]
