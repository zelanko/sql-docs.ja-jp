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
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b9555c5fd335abcf4069c4ca9241bbade8f71771
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47844210"
---
# <a name="sqlfreestmt"></a>SQLFreeStmt
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  一般的に   
      **SQLFreeStmt** ODBC 3.0 以降では推奨されません。 ただし、アプリケーションは、ステートメントを再利用する必要がある場合はまだ使用**SQLFreeStmt**で、 **SQL_RESET_PARAMS**と**SQL_UNBIND**オプション)。 使用することも[SQLCloseCursor](../../relational-databases/native-client-odbc-api/sqlclosecursor.md)、 [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md)、 [SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md)、 [SQLSetDescField](../../relational-databases/native-client-odbc-api/sqlsetdescfield.md)、および[SQLFreeHandle](../../relational-databases/native-client-odbc-api/sqlfreehandle.md)を置き換えたりの機能が重複しています**SQLFreeStmt**代わりに使用する必要があります。  
  
 一般よりにドロップし、新しいものを割り当てるステートメントを再利用する方が効率的です。 ただし、状況によっては、ステートメントの再利用するように SQLFreeStmt 依然使用しなければなりません。  
  
## <a name="see-also"></a>関連項目  
 [SQLFreeStmt 関数](http://go.microsoft.com/fwlink/?LinkId=59346)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
