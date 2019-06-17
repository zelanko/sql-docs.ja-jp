---
title: 発生。マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLCancel function
ms.assetid: d4c965ae-c1ac-4e9d-b4b9-32b561401106
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1758088319a712564fe2f11a136f5833b12111f2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63014704"
---
# <a name="sqlcancel"></a>SQLCancel
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [SQLCancel](https://go.microsoft.com/fwlink/?LinkId=203516)トピックでは、ことを示す ODBC では、アプリケーションから呼び出す場合は 2.x **SQLCancel**場合、ステートメントの処理は行われません**SQLCancel** と同じ効果があります**SQLFreeStmt**で、 **SQL_CLOSE**オプションですこの動作は完全を期すためだけ定義され、アプリケーションを呼び出す必要があります**SQLFreeStmt**または **。SQLCloseCursor**カーソルを閉じます。 であっても、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント アプリケーションは、ODBC API のバージョン 3.5.x であるためを設定またはそれ以降、**発生**ODBC 2.x の動作を使用します。  
  
## <a name="see-also"></a>関連項目  
 [SQLCancel](https://go.microsoft.com/fwlink/?LinkId=203516)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
