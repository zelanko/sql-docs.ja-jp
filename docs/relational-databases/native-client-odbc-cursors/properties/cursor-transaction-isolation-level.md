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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 07f3ecf2ad42824e8b9098e4ad4567b7cb8be7c6
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85774387"
---
# <a name="cursor-transaction-isolation-level"></a>カーソルのトランザクション分離レベル
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  カーソルのロック動作全体は、コンカレンシー属性とクライアントが設定したトランザクション分離レベルの相互作用の影響を受けます。 ODBC クライアントでは、 [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) SQL_ATTR_TXN_ISOLATION または SQL_COPT_SS_TXN_ISOLATION 属性を使用してトランザクション分離レベルを設定します。 特定のカーソル環境のロック動作は、コンカレンシーのロック動作とトランザクション分離レベルのオプションを組み合わせることによって決まります。  
  
 Native Client ODBC ドライバーでは、次のカーソルトランザクション分離レベルがサポートされてい [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ます。  
  
-   READ COMMITTED (SQL_TXN_READ_COMMITTED)  
  
-   READ UNCOMMITTED (SQL_TXN_READ_UNCOMMITTED)  
  
-   REPEATABLE READ (SQL_TXN_REPEATABLE_READ)  
  
-   SERIALIZABLE (SQL_TXN_SERIALIZABLE)  
  
-   SNAPSHOT (SQL_TXN_SS_SNAPSHOT)  
  
 ODBC API では、追加のトランザクション分離レベルが指定されていますが、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] または Native CLIENT ODBC ドライバーではサポートされていないことに注意して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ください。  
  
## <a name="see-also"></a>関連項目  
 [カーソルのプロパティ](../../../relational-databases/native-client-odbc-cursors/properties/cursor-properties.md)  
  
  
