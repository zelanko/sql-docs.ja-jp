---
title: ネイティブエラー番号 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC error handling, native error numbers
- SQL Server Native Client ODBC driver, errors
- native error numbers [SQL Server Native Client]
- messages [ODBC], native error numbers
- errors [ODBC], native error numbers
ms.assetid: 77cbc826-f47f-4803-8e7a-223d6df069b1
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0b5572ee784f47b0444e1d825de1b6dd53db8066
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81291609"
---
# <a name="native-error-numbers"></a>ネイティブ エラー番号
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  データ ソースで発生したエラー ( によって[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]返される[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]) の場合、ネイティブ クライアント ODBC ドライバ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は、そのデータ ソースに返されたネイティブ エラー番号を返します。 ドライバによって検出されたエラーの場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント ODBC ドライバはネイティブ エラー番号 0 を返します。 ネイティブ エラー番号の一覧の詳細については、**の master**データベースの**sysmessages**システム テーブルの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エラー列を参照してください。  
  
 状態エラー コードについては[、SQLSTATE &#40;ODBC エラー コード&#41;](../../relational-databases/native-client-odbc-error-messages/sqlstate-odbc-error-codes.md)を参照してください。 Net-Library から返されたエラーについては、ネイティブ エラー番号は基になるネットワーク ソフトウェアから返されます。  
  
## <a name="see-also"></a>参照  
 [エラーとメッセージの処理](../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  
