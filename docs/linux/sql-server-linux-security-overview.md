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
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 74357e2741e01e44f0f9d504456fca10f29f78e7
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="security-limitations-for-sql-server-on-linux"></a>SQL Server on Linux のセキュリティの制限

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

現在、SQL Server on Linux には、次の制限があります。

* 標準のパスワード ポリシーを指定します。 MUST_CHANGE が、唯一のオプションを構成することがあります。  
* 拡張キー管理はサポートされていません。 
* Azure Key Vault に格納されたキーを使用することはサポートされていません。
* SQL Server では、接続を暗号化するため、独自の自己署名証明書を生成します。 現時点では、SSL または TLS 証明書に指定されたユーザーを使用する SQL サーバーを構成することはできません。 

SQL Server で使用できるセキュリティ機能の詳細については、次を参照してください。、 [SQL Server データベース エンジンと Azure SQL Database のセキュリティ センター](https://msdn.microsoft.com/library/bb510589.aspx)です。

## <a name="next-steps"></a>次の手順

一般的なセキュリティ タスクでは、次を参照してください。 [Linux に SQL Server のセキュリティ機能の概要](sql-server-linux-security-get-started.md)です。   
TCP を変更するスクリプトのポート番号、SQL Server のディレクトリ、トレース フラグまたは照合順序を構成しを参照してください[mssql conf Linux での SQL Server の構成](sql-server-linux-configure-mssql-conf.md)です。

