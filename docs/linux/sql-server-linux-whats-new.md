---
title: SQL Server 2017 on Linux の新機能 |Microsoft ドキュメント
description: この記事では、Linux 上の SQL Server 2017 の新機能が強調表示されます。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/20/2018
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: 456b6f31-6b97-4e31-80ab-b40151ec4868
ms.openlocfilehash: 3d1f841f2ea2e0169aa27cb8ec7853be2e90665e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="whats-new-for-sql-server-2017-on-linux"></a>Linux 上の SQL Server 2017 の新機能します。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

この記事では、Linux で実行されている SQL Server 2017 の主要な機能と使用可能なサービスについて説明します。

> [!NOTE]
> この記事でこれらの機能だけでなく累積的更新プログラムは、GA リリース後に一定の間隔で解放されます。 これらの累積的な更新プログラムでは、多くの機能強化と修正が提供されます。 最新の CU リリースについては、次を参照してください。 [ http://aka.ms/sql2017cu](http://aka.ms/sql2017cu)です。 パッケージのダウンロードと既知の問題は、次を参照してください。、[リリース ノート](sql-server-linux-release-notes.md)です。

## <a name="sql-server-database-engine"></a>SQL Server データベース エンジン

- コア SQL Server データベース エンジンの機能を有効になります。
- ネイティブの Linux パスをサポートします。
- IPV6 をサポートします。
- NFS 上のデータベース ファイルをサポートします。
- 有効になっている[透過的 Layer Security](sql-server-linux-encrypted-connections.md) (TLS) 暗号化します。
- 有効になっている[Active Directory 認証](sql-server-linux-active-directory-authentication.md)です。
- [可用性グループ機能](sql-server-linux-availability-group-overview.md)高可用性を実現します。
- [フルテキスト検索](sql-server-linux-setup-full-text-search.md)をサポートします。

## <a name="sql-server-agent"></a>SQL Server エージェント

- 有効になっている[SQL Server エージェント](sql-server-linux-setup-sql-agent.md)次のタスクをサポートします。
  - [TRANSACT-SQL ジョブ](sql-server-linux-run-sql-server-agent-job.md)
  - [データベース メール](sql-server-linux-db-mail-sql-agent.md)
  - [ログ配布](sql-server-linux-use-log-shipping.md)

## <a name="sql-server-integration-services-ssis"></a>SQL Server Integration Services (SSIS)

- Linux で SSIS パッケージを実行する権限です。 詳細については、次を参照してください。 [ssis conf Linux で SQL Server Integration Services を構成する](sql-server-linux-configure-ssis.md)です。

## <a name="other-improvements"></a>その他の改善

- コマンドライン構成ツール、 [mssql conf](sql-server-linux-configure-mssql-conf.md)です。
- 無人インストールのサポートと[環境変数](sql-server-linux-configure-environment-variables.md)です。
- クロス プラットフォーム[mssql サーバーの拡張機能を Visual Studio Code](sql-server-linux-develop-use-vscode.md)です。
- クロス プラットフォーム スクリプト ジェネレーター [mssql scripter](https://github.com/Microsoft/sql-xplat-cli/blob/dev/doc/usage_guide.md)です。
- クロス プラットフォームの動的管理ビュー (DMV) のモニター、 [DBFS ツール](https://github.com/Microsoft/dbfs)です。

## <a name="next-steps"></a>次の手順

Linux 上の SQL Server をインストールするには、次のチュートリアルのいずれかを使用します。

- [Red Hat Enterprise Linux にインストールします。](quickstart-install-connect-red-hat.md)
- [SUSE Linux Enterprise Server にインストールします](quickstart-install-connect-suse.md)
- [Ubuntu にインストールします](quickstart-install-connect-ubuntu.md)
- [Docker で実行します。](quickstart-install-connect-docker.md)
- [Azure での SQL VM プロビジョニング](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=%2fsql%2flinux%2ftoc.json)

SQL Server 2017 に導入されたその他の改善を表示するには、次を参照してください。[の SQL Server 2017 新](../sql-server/what-s-new-in-sql-server-2017.md)です。

> [!TIP]
> よく寄せられる質問に対する回答については、次を参照してください。、 [SQL Server on Linux に関する FAQ](sql-server-linux-faq.md)です。

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]
