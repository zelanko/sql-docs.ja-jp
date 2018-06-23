---
title: カーソルのトランザクション分離レベル |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- isolation levels [ODBC]
- ODBC applications, row versioning
- cursors [ODBC], isolation levels
- ODBC cursors, isolation levels
- row versioning [SQL Server], ODBC
ms.assetid: 0c6663a4-5a25-44aa-8fe4-e35af9bf4a83
caps.latest.revision: 31
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 83c5195598eb28ad8bcbe219d7cda0de327973cc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36084115"
---
# <a name="cursor-transaction-isolation-level"></a>カーソルのトランザクション分離レベル
  カーソルのロック動作全体は、同時実行属性とクライアントが設定したトランザクション分離レベルの相互作用の影響を受けます。 トランザクション分離レベルを使用して、ODBC クライアントの設定、 [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) SQL_ATTR_TXN_ISOLATION または SQL_COPT_SS_TXN_ISOLATION 属性。 特定のカーソル環境のロック動作は、同時実行のロック動作とトランザクション分離レベルのオプションを組み合わせることによって決まります。  
  
 次のカーソルのトランザクション分離レベルがサポートされている、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバー。  
  
-   READ COMMITTED (SQL_TXN_READ_COMMITTED)  
  
-   READ UNCOMMITTED (SQL_TXN_READ_UNCOMMITTED)  
  
-   REPEATABLE READ (SQL_TXN_REPEATABLE_READ)  
  
-   SERIALIZABLE (SQL_TXN_SERIALIZABLE)  
  
-   SNAPSHOT (SQL_TXN_SS_SNAPSHOT)  
  
 ODBC API を別のトランザクション分離レベルを指定しますではサポートされていません[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]または[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client ODBC ドライバー。  
  
## <a name="see-also"></a>参照  
 [カーソルのプロパティ](cursor-properties.md)  
  
  