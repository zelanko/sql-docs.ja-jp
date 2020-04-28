---
title: SQLSTATE (ODBC エラーコード) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, errors
- ODBC error handling, cause information
- messages [ODBC], cause information
- SQLSTATEs
- errors [ODBC], cause information
ms.assetid: 84cce528-edb0-473f-a85f-3eb87fbe2cf3
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8c7f3fbdf690989830cff2a41028ee0c1e2c9f37
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81291532"
---
# <a name="sqlstate-odbc-error-codes"></a>SQLSTATE (ODBC エラー コード)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  SQLSTATE は、警告やエラーの原因についての詳細情報を提供します。 によって検出され、によって[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]返されるデータソース[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で発生したエラーの場合、native Client ODBC ドライバーは、返されたネイティブエラー番号を適切な SQLSTATE にマップします。 ネイティブエラー番号にマップする ODBC エラーコードがない場合、native Client ODBC ドライバー [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は SQLSTATE 42000 ("構文エラーまたはアクセス違反") を返します。 ドライバーによって検出されたエラーに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ついては、NATIVE Client ODBC ドライバーによって適切な SQLSTATE が生成されます。  
  
 状態エラー コードの詳細については、次のトピックを参照してください。  
  
-   [付録 A: ODBC エラー コード](https://go.microsoft.com/fwlink/?LinkId=89356)  
  
-   [SQLSTATE マッピング](https://go.microsoft.com/fwlink/?LinkId=89355)  
  
## <a name="see-also"></a>参照  
 [エラーとメッセージの処理](../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  
