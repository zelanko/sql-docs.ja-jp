---
title: SQLFreeStmt |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/23/2015
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-odbc-api
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLFreeStmt function
ms.assetid: d9666d0b-3446-480e-bf1a-10b01213e411
caps.latest.revision: 35
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 13d5dee3d0486e0cbaa07f10d522a16ed918c926
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sqlfreestmt"></a>SQLFreeStmt
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  一般的に   
      **SQLFreeStmt** ODBC 3.0 以降ではお勧めしません。 ただし、アプリケーションは、ステートメントを再利用する必要がある場合を使用してください**SQLFreeStmt**で、 **SQL_RESET_PARAMS**と**SQL_UNBIND**オプション)。 使用することも[SQLCloseCursor](../../relational-databases/native-client-odbc-api/sqlclosecursor.md)、 [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md)、 [SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md)、 [SQLSetDescField](../../relational-databases/native-client-odbc-api/sqlsetdescfield.md)、および[SQLFreeHandle](../../relational-databases/native-client-odbc-api/sqlfreehandle.md)を置き換えるかの機能を複製する**SQLFreeStmt**して代わりに使用する必要があります。  
  
 一般よりにドロップし、新しいものを割り当てるステートメントを再利用する効率的です。 ただし、状況によっては、ステートメントの再利用するように SQLFreeStmt まだは必ず使用します。  
  
## <a name="see-also"></a>参照  
 [SQLFreeStmt 関数](http://go.microsoft.com/fwlink/?LinkId=59346)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
