---
title: SQL Server on Linux の管理 |Microsoft ドキュメント
description: この記事は、Linux で実行されている SQL Server の一般的な管理タスクとツールへのリンクを提供します。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.component: ''
ms.suite: sql
ms.technology: database-engine
ms.assetid: 6bd8eb0b-593d-467e-87ea-ab1c4dbcd1ea
ms.custom: sql-linux
ms.openlocfilehash: 59af03a8cc4ed1205220420cd2fe27da1cb7c541
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="choose-the-right-tool-to-manage-sql-server-on-linux"></a>Linux 上の SQL Server を管理する適切なツールを選択します。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

ストアには、Linux 上の SQL Server 2017 を管理するいくつかの方法があります。 次のセクションでは、別の管理ツールと他のリソースへのポインターの使用方法の簡単な概要を提供します。

## <a name="mssql-conf"></a>mssql-conf 
**Mssql conf**ツールは、Linux に SQL Server を構成します。 詳細については、次を参照してください。 [mssql conf Linux での SQL Server の構成](sql-server-linux-configure-mssql-conf.md)です。

## <a name="transact-sql"></a>Transact-SQL

TRANSACT-SQL ステートメントのほとんどのクライアント ツールで行うことができますも実行できます。 SQL Server が提供[動的管理ビュー (Dmv)](../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)状態と SQL Server の構成を照会します。 [TRANSACT-SQL コマンド](https://msdn.microsoft.com/library/bb510741.aspx)データベースの管理タスク。 これらのコマンドを実行するには SQL Server に接続して、たとえば、TRANSACT-SQL クエリを実行しているをサポートする任意のクライアント ツールで[sqlcmd](sql-server-linux-setup-tools.md)または[Visual Studio Code](sql-server-linux-develop-use-vscode.md)です。

## <a name="sql-server-operations-studio-preview"></a>SQL Server 操作 Studio (プレビュー)

新しい Microsoft SQL Operations Studio (preview) は、SQL Server を管理するためのクロスプラット フォーム ツールです。 詳細については、次を参照してください。 [Microsoft SQL Operations Studio (preview)](../sql-operations-studio/what-is.md)です。

## <a name="sql-server-management-studio-on-windows"></a>Windows 上の SQL Server Management Studio

SQL Server Management Studio (SSMS) は、SQL Server を管理するためのグラフィカル ユーザー インターフェイスを提供する Windows アプリケーションです。 現在 Windows だけで、実行が、Linux の SQL Server インスタンスにリモート接続を使用します。 SSMS を使用して、SQL Server を管理する方法の詳細については、次を参照してください。 [Linux 上の SQL Server の管理を使用して SSMS](sql-server-linux-manage-ssms.md)です。

## <a name="mssql-cli-preview"></a>mssql cli (プレビュー)

SQL Server のクロス プラットフォームの新しいスクリプト作成ツールをリリースしました[mssql cli](https://blogs.technet.microsoft.com/dataplatforminsider/2017/12/12/try-mssql-cli-a-new-interactive-command-line-tool-for-sql-server/)です。 このツールは現在プレビューされています。

## <a name="powershell"></a>PowerShell

PowerShell では、Linux 上の SQL Server を管理する機能豊富なコマンドライン環境を提供します。 詳細については、次を参照してください。 [Linux 上の SQL Server の管理に PowerShell を使用して](sql-server-linux-manage-powershell.md)です。

## <a name="next-steps"></a>次の手順

Linux 上の SQL Server に関する詳細については、次を参照してください。 [Linux に SQL Server](sql-server-linux-overview.md)です。
