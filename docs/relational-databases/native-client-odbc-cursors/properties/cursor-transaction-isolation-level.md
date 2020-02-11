---
title: カーソルトランザクション分離レベル |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- isolation levels [ODBC]
- ODBC applications, row versioning
- cursors [ODBC], isolation levels
- ODBC cursors, isolation levels
- row versioning [SQL Server], ODBC
ms.assetid: 0c6663a4-5a25-44aa-8fe4-e35af9bf4a83
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 92d9eb8bb09065290c99f3cb9894208a7613b984
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "73784097"
---
# <a name="cursor-transaction-isolation-level"></a>カーソルのトランザクション分離レベル
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  カーソルのロック動作全体は、コンカレンシー属性とクライアントが設定したトランザクション分離レベルの相互作用の影響を受けます。 ODBC クライアントでは、 [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) SQL_ATTR_TXN_ISOLATION または SQL_COPT_SS_TXN_ISOLATION 属性を使用してトランザクション分離レベルを設定します。 特定のカーソル環境のロック動作は、コンカレンシーのロック動作とトランザクション分離レベルのオプションを組み合わせることによって決まります。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] NATIVE Client ODBC ドライバーでは、次のカーソルトランザクション分離レベルがサポートされています。  
  
-   READ COMMITTED (SQL_TXN_READ_COMMITTED)  
  
-   READ UNCOMMITTED (SQL_TXN_READ_UNCOMMITTED)  
  
-   REPEATABLE READ (SQL_TXN_REPEATABLE_READ)  
  
-   SERIALIZABLE (SQL_TXN_SERIALIZABLE)  
  
-   SNAPSHOT (SQL_TXN_SS_SNAPSHOT)  
  
 ODBC API では、追加のトランザクション分離レベルが指定されています[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]が、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]または Native Client ODBC ドライバーではサポートされていないことに注意してください。  
  
## <a name="see-also"></a>参照  
 [カーソルのプロパティ](../../../relational-databases/native-client-odbc-cursors/properties/cursor-properties.md)  
  
  
