---
title: "SQL Server on Linux のセキュリティの制限事項 |Microsoft ドキュメント"
description: "この記事では、Linux の制限の SQL Server がについて説明します。"
author: rothja
ms.author: jroth
manager: craigg
ms.date: 01/30/2018
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: 
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: 64da74cc-14bf-4636-a55e-8cc1fce2aaff
ms.workload: Inactive
ms.openlocfilehash: 54e7518c24cb75e5f41f8fc6a4c5a159093ca66a
ms.sourcegitcommit: f02598eb8665a9c2dc01991c36f27943701fdd2d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/13/2018
---
# <a name="security-limitations-for-sql-server-on-linux"></a>SQL Server on Linux のセキュリティの制限

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

現在、SQL Server on Linux には、次の制限があります。

* 標準のパスワード ポリシーを指定します。 MUST_CHANGE が、唯一のオプションを構成することがあります。  
* 拡張キー管理はサポートされていません。 
* Azure Key Vault に格納されたキーを使用することはサポートされていません。
* SQL Server では、接続を暗号化するため、独自の自己署名証明書を生成します。 TLS 証明書に指定されたユーザーを使用する SQL Server を構成することができます。 

SQL Server で使用できるセキュリティ機能の詳細については、次を参照してください。、 [SQL Server データベース エンジンと Azure SQL Database のセキュリティ センター](../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)です。

## <a name="next-steps"></a>次の手順

一般的なセキュリティ タスクでは、次を参照してください。 [Linux に SQL Server のセキュリティ機能の概要](sql-server-linux-security-get-started.md)です。 TCP を変更するスクリプトのポート番号、SQL Server のディレクトリ、トレース フラグまたは照合順序を構成しを参照してください[mssql conf Linux での SQL Server の構成](sql-server-linux-configure-mssql-conf.md)です。
