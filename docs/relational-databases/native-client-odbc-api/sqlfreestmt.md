---
title: SQLFreeStmt |Microsoft Docs
ms.custom: ''
ms.date: 11/23/2015
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLFreeStmt function
ms.assetid: d9666d0b-3446-480e-bf1a-10b01213e411
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b985db3cb58a7029a3b5ec489d2e23b0c1292919
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2019
ms.locfileid: "73786732"
---
# <a name="sqlfreestmt"></a>SQLFreeStmt
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  一般的に   
      **SQLFreeStmt**は、ODBC 3.0 以降では推奨されません。 ただし、アプリケーションでステートメントを再利用する必要がある場合でも、 **SQL_RESET_PARAMS**と**SQL_UNBIND**のオプションを指定して**SQLFreeStmt**を使用する必要があります。 [SQLCloseCursor](../../relational-databases/native-client-odbc-api/sqlclosecursor.md)、[SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md)、[SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md)、[SQLSetDescField](../../relational-databases/native-client-odbc-api/sqlsetdescfield.md)、および[SQLFreeHandle](../../relational-databases/native-client-odbc-api/sqlfreehandle.md)を使用して、 **SQLFreeStmt**の関数を置き換えたり複製したりすることもできます。代わりに、これらの関数を使用する必要があります。  
  
 一般に、ステートメントを再利用して新しいステートメントを割り当てるよりも効率的です。 ただし、ステートメントを再利用する場合のように、SQLFreeStmt を使用する必要がある場合もあります。  
  
## <a name="see-also"></a>参照  
 [SQLFreeStmt 関数](https://go.microsoft.com/fwlink/?LinkId=59346)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
