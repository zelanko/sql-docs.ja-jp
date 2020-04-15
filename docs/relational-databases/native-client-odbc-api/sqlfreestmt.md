---
title: をクリックして |マイクロソフトドキュメント
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3eb86f9b7b1076fa3a01135b5780637ee9857f90
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298460"
---
# <a name="sqlfreestmt"></a>SQLFreeStmt
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  一般的に   
      ODBC 3.0 以降では **、SQLFreeStmt**は推奨されません。 ただし、アプリケーションがステートメントを再利用する必要がある場合は**SQL_UNBIND****、sqlFreeStmt**を**SQL_RESET_PARAMS**および SQL_UNBIND オプションと共に使用する必要があります。 また[、SQLCloseCursor](../../relational-databases/native-client-odbc-api/sqlclosecursor.md)、SQLBindParameter、SQLBindCol、SQLSetDescField 、および[SQLFreeHandle](../../relational-databases/native-client-odbc-api/sqlfreehandle.md)を使用して **、SQLFreeStmt**の関数を置き換えるか複製し、代わりにそれらを使用する必要があります。 [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md) [SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md) [SQLSetDescField](../../relational-databases/native-client-odbc-api/sqlsetdescfield.md)  
  
 一般に、ステートメントを削除して新しいステートメントを割り当てるよりも、ステートメントを再利用する方が効率的です。 ただし、文の再利用など、状況によっては、SQLFreeStmt を使用する必要があります。  
  
## <a name="see-also"></a>参照  
 [関数](https://go.microsoft.com/fwlink/?LinkId=59346)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
