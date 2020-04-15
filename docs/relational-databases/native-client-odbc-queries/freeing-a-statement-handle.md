---
title: ステートメントハンドルを解放する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- reusing statement handles
- freeing statement handles
- statements [ODBC], statement handles
- SQLFreeStmt function
- ODBC applications, statements
- statement handles [ODBC]
ms.assetid: 96fdff84-0ca7-460a-a240-94ee826ea41c
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7e954773f85afc434d1e5bd18f7ffb76e28a1438
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297897"
---
# <a name="freeing-a-statement-handle"></a>ステートメント ハンドルの解放
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  ステートメント ハンドルは、削除して新しいハンドルを割り当てるよりも、再利用する方が効率的です。 アプリケーションでは、任意のステートメント ハンドルで新しい SQL ステートメントを実行する前に、現在のステートメント設定が適切であることを確認する必要があります。 確認する設定には、ステートメント属性、パラメーター バインド、結果セットのバインドがあります。 一般に、古い SQL ステートメントのパラメーターと結果セットは[、sqlFreeStmt](../../relational-databases/native-client-odbc-api/sqlfreestmt.md)を SQL_RESET_PARAMS およびSQL_UNBIND オプションで呼び出し、新しい SQL ステートメントに再バインドすることによってバインドを解除する必要があります。  
  
 アプリケーションは、ステートメントの使用を終了すると、ステートメントを解放する[SQLFreeHandle](../../relational-databases/native-client-odbc-api/sqlfreehandle.md)を呼び出します。 **SQLDisconnect**は、接続上のすべてのステートメントを自動的に解放します。  
  
## <a name="see-also"></a>参照  
 [ODBC&#41;&#40;クエリの実行](../../relational-databases/native-client-odbc-queries/executing-queries-odbc.md)  
  
  
