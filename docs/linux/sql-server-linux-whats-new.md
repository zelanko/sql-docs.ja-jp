---
title: Linux 上の SQL Server 2017 の新 |Microsoft Docs
description: この記事では、Linux 上の SQL Server 2017 の新機能については強調表示されます。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/21/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 456b6f31-6b97-4e31-80ab-b40151ec4868
ms.openlocfilehash: b248578015e8d821c3c76314ecbbabdf75600a52
ms.sourcegitcommit: de8ef246a74c935c5098713f14e9dd06c4733713
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2018
ms.locfileid: "53160530"
---
# <a name="whats-new-for-sql-server-on-linux"></a>Linux 上の SQL Server の新機能については

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

この記事では、Linux で実行されている SQL Server 2017 の主要な機能と使用可能なサービスについて説明します。

SQL Server 2019 プレビューがリリースされました。 この記事では、SQL Server 2019 プレビュー リリースは含まれません。 SQL Server 2019 プレビューについては、[新機能については Linux 用の SQL Server 2019 プレビュー](../sql-server/what-s-new-in-sql-server-ver15.md?view=sql-server-ver15#sqllinux)を参照してください。

> [!NOTE]
> この記事ではこれらの機能だけでなく累積的更新プログラムは、GA リリース後一定の間隔でリリースされます。 これらの累積的な更新プログラムでは、多くの機能強化と修正が提供されます。 最新の CU リリースについては、[ https://aka.ms/sql2017cu](https://aka.ms/sql2017cu)を参照してください。 パッケージのダウンロードと既知の問題は、、[リリース ノート](sql-server-linux-release-notes.md)を参照してください。

## <a name="sql-server-database-engine"></a>SQL Server データベース エンジン

- コアの SQL Server データベース エンジンの機能を有効になります。
- ネイティブ Linux パスのサポート。
- IPV6 をサポートします。
- NFS 上のデータベース ファイルのサポート。
- 有効になっている[トランスポート層セキュリティ](sql-server-linux-encrypted-connections.md)(TLS) 暗号化します。
- 有効になっている[Active Directory 認証](sql-server-linux-active-directory-authentication.md)します。
- [可用性グループ機能](sql-server-linux-availability-group-overview.md)高可用性を実現します。
- [フルテキスト検索](sql-server-linux-setup-full-text-search.md)をサポートします。

## <a name="sql-server-agent"></a>SQL Server エージェント

- 有効になっている[SQL Server エージェント](sql-server-linux-setup-sql-agent.md)次のタスクをサポートします。
  - [TRANSACT-SQL ジョブ](sql-server-linux-run-sql-server-agent-job.md)
  - [データベース メール](sql-server-linux-db-mail-sql-agent.md)
  - [ログ配布](sql-server-linux-use-log-shipping.md)

## <a name="sql-server-integration-services-ssis"></a>SQL Server Integration Services (SSIS)

- Linux で SSIS パッケージを実行する権限です。 詳細については、[ssis conf Linux で SQL Server Integration Services を構成する](sql-server-linux-configure-ssis.md)を参照してください。

## <a name="other-improvements"></a>その他の改善

- コマンドライン構成ツール、 [mssql conf](sql-server-linux-configure-mssql-conf.md)します。
- 無人インストールのサポートと[環境変数](sql-server-linux-configure-environment-variables.md)します。
- クロス プラットフォーム[mssql server の拡張機能を Visual Studio Code](sql-server-linux-develop-use-vscode.md)します。
- クロスプラット フォームでスクリプト ジェネレーター、 [mssql scripter](https://github.com/Microsoft/sql-xplat-cli/blob/dev/doc/usage_guide.md)します。
- クロス プラットフォームの動的管理ビュー (DMV) のモニター、 [DBFS ツール](https://github.com/Microsoft/dbfs)します。

## <a name="next-steps"></a>次の手順

Linux 上の SQL Server をインストールするには、次のチュートリアルのいずれかを使用します。

- [Red Hat Enterprise Linux をインストールします。](quickstart-install-connect-red-hat.md)
- [SUSE Linux Enterprise Server にインストールします](quickstart-install-connect-suse.md)
- [Ubuntu にインストールします](quickstart-install-connect-ubuntu.md)
- [Docker で実行します。](quickstart-install-connect-docker.md)
- [Azure での SQL VM プロビジョニング](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=%2fsql%2flinux%2ftoc.json)

SQL Server 2017 で導入されたその他の改善を表示するには、[SQL Server 2017 の新](../sql-server/what-s-new-in-sql-server-2017.md)を参照してください。

> [!TIP]
> よく寄せられる質問の回答は、、 [SQL Server on Linux の FAQ](sql-server-linux-faq.md)を参照してください。

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]
