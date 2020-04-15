---
title: SQL キャンセル |マイクロソフトドキュメント
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2db2c4b66940a81dd65064ee730cd683e2206a58
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302645"
---
# <a name="sqlcancel"></a>SQLCancel
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  [SQLCancel](https://go.microsoft.com/fwlink/?LinkId=203516)トピックでは、ODBC 2.x では、アプリケーションがステートメントで処理が行われていないときに**SQLCancel**を呼び出すと **、SQLCancel**は**SQL_CLOSE**オプションを指定した**SQLFreeStmt**と同じ効果を持ちます。この動作は完全性のために定義され、アプリケーションはカーソルをクローズするために**SQLFreeStmt**または**SQLCloseCursor**を呼び出す必要があります。 ただし、ネイティブ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアント アプリケーションで ODBC API バージョンを 3.5.x 以降に設定した場合でも **、SQLCancel**関数は ODBC 2.x の動作を使用します。  
  
## <a name="see-also"></a>参照  
 [キャンセル](https://go.microsoft.com/fwlink/?LinkId=203516)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
