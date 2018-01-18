---
title: "SQL Server on Linux のセキュリティの制限事項 |Microsoft ドキュメント"
description: "このトピックでは、Linux の制限の SQL Server がについて説明します。"
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: 64da74cc-14bf-4636-a55e-8cc1fce2aaff
ms.workload: Inactive
ms.openlocfilehash: a120ed0cf8de077c3d1de6d695554b2585a7d9da
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="security-limitations-for-sql-server-on-linux"></a>SQL Server on Linux のセキュリティの制限

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

現在、SQL Server on Linux には、次の制限があります。

* 標準のパスワード ポリシーを指定します。 MUST_CHANGE が、唯一のオプションを構成することがあります。  
* 拡張キー管理はサポートされていません。 
* Azure Key Vault に格納されたキーを使用することはサポートされていません。
* SQL Server では、接続を暗号化するため、独自の自己署名証明書を生成します。 TLS 証明書に指定されたユーザーを使用する SQL Server を構成することができます。 

SQL Server で使用できるセキュリティ機能の詳細については、次を参照してください。、 [SQL Server データベース エンジンと Azure SQL Database のセキュリティ センター](../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)です。

## <a name="next-steps"></a>次の手順

一般的なセキュリティ タスクでは、次を参照してください。 [Linux に SQL Server のセキュリティ機能の概要](sql-server-linux-security-get-started.md)です。   
TCP を変更するスクリプトのポート番号、SQL Server のディレクトリ、トレース フラグまたは照合順序を構成しを参照してください[mssql conf Linux での SQL Server の構成](sql-server-linux-configure-mssql-conf.md)です。
