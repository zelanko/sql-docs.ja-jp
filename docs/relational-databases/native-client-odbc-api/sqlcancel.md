---
title: SQLCancel |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client-odbc-api
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQLCancel function
ms.assetid: d4c965ae-c1ac-4e9d-b4b9-32b561401106
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: a0268466df7ee99e1ed770f52423d5b62a90cbdd
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sqlcancel"></a>SQLCancel
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [SQLCancel](http://go.microsoft.com/fwlink/?LinkId=203516)トピックの質問を odbc 2.x、アプリケーションを呼び出す場合**SQLCancel** 、ステートメントの処理が行われない場合に**SQLCancel** 場合と同じ効果**SQLFreeStmt**で、 **SQL_CLOSE**オプションですこの動作は、完全を期すためだけに定義し、アプリケーションを呼び出す必要があります**SQLFreeStmt**または**。SQLCloseCursor**カーソルを閉じます。 たとえ、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント アプリケーションは、ODBC API バージョンを 3.5.x を設定またはそれ以降、 **SQLCancel**関数、ODBC 2.x の動作が使用されます。  
  
## <a name="see-also"></a>参照  
 [SQLCancel](http://go.microsoft.com/fwlink/?LinkId=203516)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
