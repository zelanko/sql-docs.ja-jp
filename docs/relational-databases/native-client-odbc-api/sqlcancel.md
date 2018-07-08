---
title: SQLCancel |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQLCancel function
ms.assetid: d4c965ae-c1ac-4e9d-b4b9-32b561401106
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 37b8219ea52340fa05278e5592b5adc5fc433c96
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37424371"
---
# <a name="sqlcancel"></a>SQLCancel
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [SQLCancel](http://go.microsoft.com/fwlink/?LinkId=203516)トピックでは、ことを示す ODBC では、アプリケーションから呼び出す場合は 2.x **SQLCancel**場合、ステートメントの処理は行われません**SQLCancel** と同じ効果があります**SQLFreeStmt**で、 **SQL_CLOSE**オプションですこの動作は完全を期すためだけ定義され、アプリケーションを呼び出す必要があります**SQLFreeStmt**または **。SQLCloseCursor**カーソルを閉じます。 たとえ、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント アプリケーションは、ODBC の API バージョンを 3.5.x を設定またはそれ以降、 **SQLCancel**関数、ODBC 2.x の動作が使用されます。  
  
## <a name="see-also"></a>参照  
 [SQLCancel](http://go.microsoft.com/fwlink/?LinkId=203516)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
