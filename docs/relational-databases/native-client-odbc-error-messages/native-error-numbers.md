---
title: ネイティブ エラー番号 |マイクロソフトのドキュメント
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
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c1a66e011ee5716f92d8b0257ed8424c86244139
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62738718"
---
# <a name="native-error-numbers"></a>ネイティブ エラー番号
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  データ ソースで発生するエラー (によって返される[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーによって返されたネイティブ エラー番号を返します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 ドライバーで検出されたエラー、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは、ネイティブ エラー番号は 0 を返します。 ネイティブ エラー番号の一覧については、のエラー列を参照して、 **sysmessages**システム テーブルに、**マスター**データベース[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。  
  
 状態エラー コードについては、次を参照してください。 [SQLSTATE &#40;ODBC エラー コード&#41;](../../relational-databases/native-client-odbc-error-messages/sqlstate-odbc-error-codes.md)します。 Net-Library から返されたエラーについては、ネイティブ エラー番号は基になるネットワーク ソフトウェアから返されます。  
  
## <a name="see-also"></a>参照  
 [エラーとメッセージの処理](../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  
