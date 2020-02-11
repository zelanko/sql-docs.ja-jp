---
title: カーソルトランザクション分離レベル |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: fef68bfdb62527f7b631b8d7433e095eba4d1c88
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63207141"
---
# <a name="cursor-transaction-isolation-level"></a>カーソルのトランザクション分離レベル
  カーソルのロック動作全体は、コンカレンシー属性とクライアントが設定したトランザクション分離レベルの相互作用の影響を受けます。 ODBC クライアントでは、 [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) SQL_ATTR_TXN_ISOLATION または SQL_COPT_SS_TXN_ISOLATION 属性を使用してトランザクション分離レベルを設定します。 特定のカーソル環境のロック動作は、コンカレンシーのロック動作とトランザクション分離レベルのオプションを組み合わせることによって決まります。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] NATIVE Client ODBC ドライバーでは、次のカーソルトランザクション分離レベルがサポートされています。  
  
-   READ COMMITTED (SQL_TXN_READ_COMMITTED)  
  
-   READ UNCOMMITTED (SQL_TXN_READ_UNCOMMITTED)  
  
-   REPEATABLE READ (SQL_TXN_REPEATABLE_READ)  
  
-   SERIALIZABLE (SQL_TXN_SERIALIZABLE)  
  
-   SNAPSHOT (SQL_TXN_SS_SNAPSHOT)  
  
 ODBC API では、追加のトランザクション分離レベルが指定されています[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]が、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]または Native Client ODBC ドライバーではサポートされていないことに注意してください。  
  
## <a name="see-also"></a>参照  
 [カーソルのプロパティ](cursor-properties.md)  
  
  
