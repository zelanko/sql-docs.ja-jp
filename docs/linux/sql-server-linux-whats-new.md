---
title: "SQL Server 2017 on Linux の新機能 |Microsoft ドキュメント"
description: "このトピックでは、Linux 上の SQL Server 2017 の新機能が強調表示されます。"
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 10/24/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: 456b6f31-6b97-4e31-80ab-b40151ec4868
ms.workload: On Demand
ms.openlocfilehash: 49381b5980d5114f7d22e53ef70542bd03ecf289
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="whats-new-for-sql-server-2017-on-linux"></a>Linux 上の SQL Server 2017 の新機能します。

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

この記事では、Linux で実行されている SQL Server 2017 の主要な機能と使用可能なサービスについて説明します。

> [!NOTE]
> この記事でこれらの機能だけでなく累積的更新プログラムは、GA リリース後に一定の間隔で解放されます。 これらの累積的な更新プログラムは、多くの機能強化と修正を提供します。 最新の CU リリースについては、次を参照してください。 [http://aka.ms/sql2017cu](http://aka.ms/sql2017cu)です。 パッケージのダウンロードと既知の問題は、次を参照してください。、[リリース ノート](sql-server-linux-release-notes.md)です。

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
- [SUSE Linux Enterprise Server をインストールします。](quickstart-install-connect-suse.md)
- [Ubuntu をインストールします。](quickstart-install-connect-ubuntu.md)
- [Docker で実行します。](quickstart-install-connect-docker.md)
- [Azure での SQL VM プロビジョニング](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=%2fsql%2flinux%2ftoc.json)

その他の情報に関する SQL Server on Linux を参照してください、[概要](sql-server-linux-overview.md)です。 パッケージのダウンロードとサポートされない機能と既知の問題の一覧は、次を参照してください。、[リリース ノート](sql-server-linux-release-notes.md)です。

SQL Server 2017 に導入されたその他の改善を表示するには、次を参照してください。[の SQL Server 2017 新](../sql-server/what-s-new-in-sql-server-2017.md)です。

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]
