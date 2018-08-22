---
title: Linux 上の SQL Server の管理 |Microsoft Docs
description: この記事では、Linux で実行されている場合の SQL Server の一般的な管理タスクとツールへのリンクを提供します。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/17/2017
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.technology: linux
ms.assetid: 6bd8eb0b-593d-467e-87ea-ab1c4dbcd1ea
ms.custom: sql-linux
ms.openlocfilehash: d537c4ef2bb84833b4676acebdaf0906ee7a85c9
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/16/2018
ms.locfileid: "40394327"
---
# <a name="choose-the-right-tool-to-manage-sql-server-on-linux"></a>Linux 上の SQL Server を管理するための適切なツールを選択します。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

SQL Server 2017 on Linux を管理するいくつかの方法はあります。 次のセクションでは、さまざまな管理ツールとその他のリソースへのポインターと手法の概要を示します。

## <a name="mssql-conf"></a>mssql-conf 

**Mssql conf**ツール Linux 上の SQL Server を構成します。 詳細については、次を参照してください。 [mssql-conf での Linux 上の SQL Server の構成](sql-server-linux-configure-mssql-conf.md)します。

## <a name="transact-sql"></a>Transact-SQL

TRANSACT-SQL ステートメントでほとんどのクライアント ツールで行うことができますも実現できます。 SQL Server が提供[動的管理ビュー (Dmv)](../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)状態と SQL Server の構成を照会します。 [TRANSACT-SQL コマンド](../t-sql/language-reference.md)データベースの管理タスク。 これらのコマンドを実行するには SQL Server に接続して、たとえば、TRANSACT-SQL クエリを実行しているをサポートする任意のクライアント ツールで[sqlcmd](sql-server-linux-setup-tools.md)または[Visual Studio Code](sql-server-linux-develop-use-vscode.md)します。

## <a name="sql-server-operations-studio-preview"></a>SQL Server Operations Studio (プレビュー)

新しい Microsoft SQL Operations Studio (preview) は、SQL Server を管理するためのクロスプラット フォーム ツールです。 詳細については、次を参照してください。 [Microsoft SQL Operations Studio (preview)](../sql-operations-studio/what-is.md)です。

## <a name="sql-server-management-studio-on-windows"></a>Windows 上の SQL Server Management Studio

SQL Server Management Studio (SSMS) は、SQL Server を管理するためのグラフィカル ユーザー インターフェイスを提供する Windows アプリケーションです。 現在 Windows でしか実行は、Linux の SQL Server インスタンスにリモート接続に使用できます。 SSMS を使用して、SQL Server を管理する方法については、次を参照してください。 [SSMS を使用した Linux 上の SQL Server の管理に](sql-server-linux-manage-ssms.md)します。

## <a name="mssql-cli-preview"></a>mssql cli (プレビュー)

SQL server の新しいクロスプラット フォームでのスクリプト ツールをリリースしました[mssql cli](https://blogs.technet.microsoft.com/dataplatforminsider/2017/12/12/try-mssql-cli-a-new-interactive-command-line-tool-for-sql-server/)します。 このツールは現在プレビュー段階です。

## <a name="powershell"></a>PowerShell

PowerShell では、SQL Server on Linux を管理する場合は、豊富なコマンドライン環境を提供します。 詳細については、次を参照してください。 [Linux 上の SQL Server の管理に PowerShell を使用して](sql-server-linux-manage-powershell.md)します。

## <a name="next-steps"></a>次のステップ

Linux 上の SQL Server に関する詳細については、次を参照してください。 [SQL Server on Linux](sql-server-linux-overview.md)します。
