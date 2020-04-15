---
title: SQLSTATE (ODBC エラー コード) |マイクロソフトドキュメント
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81291532"
---
# <a name="sqlstate-odbc-error-codes"></a>SQLSTATE (ODBC エラー コード)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  SQLSTATE は、警告やエラーの原因についての詳細情報を提供します。 によって検出され、返される[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ ソースで発生したエラーの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]場合、ネイティブ クライアント ODBC ドライバーは、返されたネイティブ エラー番号を適切な SQLSTATE にマップします。 ネイティブ エラー番号に対応付ける ODBC エラー コードがない場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント ODBC ドライバは SQLSTATE 42000 (構文エラーまたはアクセス違反) を返します。 ドライバによって検出されたエラーの場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント ODBC ドライバは適切な SQLSTATE を生成します。  
  
 状態エラー コードの詳細については、次のトピックを参照してください。  
  
-   [付録 A: ODBC エラー コード](https://go.microsoft.com/fwlink/?LinkId=89356)  
  
-   [SQLSTATE マッピング](https://go.microsoft.com/fwlink/?LinkId=89355)  
  
## <a name="see-also"></a>参照  
 [エラーとメッセージの処理](../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  
