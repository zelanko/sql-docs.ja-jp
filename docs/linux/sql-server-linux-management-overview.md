---
title: "SQL Server on Linux の管理 |Microsoft ドキュメント"
description: "このトピックは、Linux で実行されている SQL Server の一般的な管理タスクとツールへのリンクを提供します。"
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 6bd8eb0b-593d-467e-87ea-ab1c4dbcd1ea
ms.custom: H1Hack27Feb2017
ms.translationtype: MT
ms.sourcegitcommit: ea75391663eb4d509c10fb785fcf321558ff0b6e
ms.openlocfilehash: b9fc5e53400fb83006d47213c84541dadfb11b38
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="choose-the-right-tool-to-manage-sql-server-on-linux"></a>Linux 上の SQL Server を管理する適切なツールを選択します。

ストアには、Linux 上の SQL Server 2017 RC2 を管理するいくつかの方法があります。 次のセクションでは、別の管理ツールと他のリソースへのポインターの使用方法の簡単な概要を提供します。

## <a name="mssql-conf"></a>mssql conf 
**Mssql conf**ツールは、Linux に SQL Server を構成します。 詳細については、次を参照してください。 [mssql conf Linux での SQL Server の構成](sql-server-linux-configure-mssql-conf.md)です。

## <a name="transact-sql"></a>Transact-SQL

TRANSACT-SQL ステートメントのほとんどのクライアント ツールで行うことができますも実行できます。 SQL Server が提供[動的管理ビュー (Dmv)](https://msdn.microsoft.com/library/ms188754.aspx)状態と SQL Server の構成を照会します。 [TRANSACT-SQL コマンド](https://msdn.microsoft.com/library/bb510741.aspx)データベースの管理タスク。 SQL Server に接続して、TRANSACT-SQL クエリの実行をサポートする任意のクライアント ツールでは、これらのコマンドを実行できます。 例としては、 [sqlcmd](sql-server-linux-setup-tools.md)、 [Visual Studio Code](sql-server-linux-develop-use-vscode.md)、および[SQL Server Management Studio](sql-server-linux-manage-ssms.md)です。

## <a name="sql-server-management-studio-on-windows"></a>Windows 上の SQL Server Management Studio

SQL Server Management Studio (SSMS) は、SQL Server を管理するためのグラフィカル ユーザー インターフェイスを提供する Windows アプリケーションです。 現在 Windows だけで、実行が、Linux の SQL Server インスタンスにリモート接続を使用します。 SSMS を使用して、SQL Server を管理する方法の詳細については、次を参照してください。 [Linux 上の SQL Server の管理を使用して SSMS](sql-server-linux-manage-ssms.md)です。

## <a name="powershell"></a>PowerShell

PowerShell では、Linux 上の SQL Server を管理する機能豊富なコマンドライン環境を提供します。 詳細については、次を参照してください。 [Linux 上の SQL Server の管理に PowerShell を使用して](sql-server-linux-manage-powershell.md)です。

## <a name="next-steps"></a>次の手順

Linux 上の SQL Server に関する詳細については、次を参照してください。 [Linux に SQL Server](sql-server-linux-overview.md)です。
