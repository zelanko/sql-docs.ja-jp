---
title: Always Encrypted (クライアント開発) | Microsoft Docs
ms.custom: ''
ms.date: 07/29/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: security
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 9595eb66-284c-4474-828f-8961a05ce989
caps.latest.revision: 33
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 41a8fc898e6ac92cd5c3db27b3c35e7ad009aa53
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="always-encrypted-client-development"></a>Always Encrypted (クライアント開発)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

クライアント側の暗号化テクノロジ [Always Encrypted](../../../relational-databases/security/encryption/always-encrypted-database-engine.md) により、機微なデータ (および関連する暗号化キー) が SQL Server や Azure SQL Database に開示されることはありません。   Always Encrypted では、クライアント ドライバーが、データベース エンジンにデータを渡す前に機微なデータを透過的に暗号化します。同様に、クライアント ドライバーは、暗号化されたデータベース列から取得したデータを透過的に暗号化解除します。

Always Encrypted の保護するデータベースを使用したアプリケーションの開発、および Always Encrypted をサポートするクライアント ドライバーとそのバージョンの詳細については、次を参照してください。

- [Always Encrypted と .NET Framework Data Provider for SQL Server を使用する](../../../relational-databases/security/encryption/develop-using-always-encrypted-with-net-framework-data-provider.md)
- [JDBC ドライバーで Always Encrypted を使用する](../../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md)
- [ODBC ドライバーで Always Encrypted を使用する](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md)



## <a name="see-also"></a>参照

[Always Encrypted (Database Engine) (Always Encrypted (データベース エンジン))](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)

