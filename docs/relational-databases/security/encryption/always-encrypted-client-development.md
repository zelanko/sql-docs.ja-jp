---
title: "Always Encrypted (クライアント開発) | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 07/29/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 9595eb66-284c-4474-828f-8961a05ce989
caps.latest.revision: 33
author: stevestein
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 8cb39d4ae3ff02fffe83e7f0e4646ade1545ce72
ms.openlocfilehash: f1ad5de594493c65688d5c1ca2d69ac421661770
ms.contentlocale: ja-jp
ms.lasthandoff: 07/31/2017

---
# <a name="always-encrypted-client-development"></a>Always Encrypted (クライアント開発)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

クライアント側の暗号化テクノロジ [Always Encrypted](../../../relational-databases/security/encryption/always-encrypted-database-engine.md) により、機微なデータ (および関連する暗号化キー) が SQL Server や Azure SQL Database に開示されることはありません。   Always Encrypted では、クライアント ドライバーが、データベース エンジンにデータを渡す前に機微なデータを透過的に暗号化します。同様に、クライアント ドライバーは、暗号化されたデータベース列から取得したデータを透過的に暗号化解除します。

Always Encrypted の保護するデータベースを使用したアプリケーションの開発、および Always Encrypted をサポートするクライアント ドライバーとそのバージョンの詳細については、次を参照してください。

- [Always Encrypted と .NET Framework Data Provider for SQL Server を使用する](../../../relational-databases/security/encryption/develop-using-always-encrypted-with-net-framework-data-provider.md)
- [JDBC ドライバーで Always Encrypted を使用する](../../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md)
- [ODBC ドライバーで Always Encrypted を使用する](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md)



## <a name="see-also"></a>参照

[Always Encrypted (Database Engine) (Always Encrypted (データベース エンジン))](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)


