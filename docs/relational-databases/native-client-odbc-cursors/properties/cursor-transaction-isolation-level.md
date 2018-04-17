---
title: カーソルのトランザクション分離レベル |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client-odbc-cursors
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- isolation levels [ODBC]
- ODBC applications, row versioning
- cursors [ODBC], isolation levels
- ODBC cursors, isolation levels
- row versioning [SQL Server], ODBC
ms.assetid: 0c6663a4-5a25-44aa-8fe4-e35af9bf4a83
caps.latest.revision: 32
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 0050531050be4ab573358140525ca58e67befe1f
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="cursor-transaction-isolation-level"></a>カーソルのトランザクション分離レベル
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  カーソルのロック動作全体は、同時実行属性とクライアントが設定したトランザクション分離レベルの相互作用の影響を受けます。 トランザクション分離レベルを使用して、ODBC クライアントの設定、 [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) SQL_ATTR_TXN_ISOLATION または SQL_COPT_SS_TXN_ISOLATION 属性。 特定のカーソル環境のロック動作は、同時実行のロック動作とトランザクション分離レベルのオプションを組み合わせることによって決まります。  
  
 次のカーソルのトランザクション分離レベルがサポートされている、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバー。  
  
-   READ COMMITTED (SQL_TXN_READ_COMMITTED)  
  
-   READ UNCOMMITTED (SQL_TXN_READ_UNCOMMITTED)  
  
-   REPEATABLE READ (SQL_TXN_REPEATABLE_READ)  
  
-   SERIALIZABLE (SQL_TXN_SERIALIZABLE)  
  
-   SNAPSHOT (SQL_TXN_SS_SNAPSHOT)  
  
 ODBC API を別のトランザクション分離レベルを指定しますではサポートされていません[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]または[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client ODBC ドライバー。  
  
## <a name="see-also"></a>参照  
 [カーソルのプロパティ](../../../relational-databases/native-client-odbc-cursors/properties/cursor-properties.md)  
  
  
