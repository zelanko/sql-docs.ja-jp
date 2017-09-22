---
title: "SQL Server on Linux のセキュリティの制限事項 |Microsoft ドキュメント"
description: "このトピックでは、Linux の制限の SQL Server がについて説明します。"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.date: 07/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 64da74cc-14bf-4636-a55e-8cc1fce2aaff
ms.translationtype: MT
ms.sourcegitcommit: a6aeda8e785fcaabef253a8256b5f6f7a842a324
ms.openlocfilehash: 6823b8a9cd3f92781d0fd3518f50b8866ba12d48
ms.contentlocale: ja-jp
ms.lasthandoff: 09/21/2017

---
# <a name="security-limitations-for-sql-server-on-linux"></a>SQL Server on Linux のセキュリティの制限

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

現在、SQL Server on Linux には、次の制限があります。

* 標準のパスワード ポリシーを指定します。 MUST_CHANGE が、唯一のオプションを構成することがあります。  
* 拡張キー管理はサポートされていません。 
* Azure Key Vault に格納されたキーを使用することはサポートされていません。
* SQL Server では、接続を暗号化するため、独自の自己署名証明書を生成します。 現時点では、SSL または TLS 証明書に指定されたユーザーを使用する SQL サーバーを構成することはできません。 

SQL Server で使用できるセキュリティ機能の詳細については、次を参照してください。、 [SQL Server データベース エンジンと Azure SQL Database のセキュリティ センター](/sql-docs/docs/relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database)です。

## <a name="next-steps"></a>次の手順

一般的なセキュリティ タスクでは、次を参照してください。 [Linux に SQL Server のセキュリティ機能の概要](sql-server-linux-security-get-started.md)です。   
TCP を変更するスクリプトのポート番号、SQL Server のディレクトリ、トレース フラグまたは照合順序を構成しを参照してください[mssql conf Linux での SQL Server の構成](sql-server-linux-configure-mssql-conf.md)です。

