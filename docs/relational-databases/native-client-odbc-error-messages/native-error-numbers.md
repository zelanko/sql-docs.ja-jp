---
title: "ネイティブ エラー番号 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-error-messages
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- ODBC error handling, native error numbers
- SQL Server Native Client ODBC driver, errors
- native error numbers [SQL Server Native Client]
- messages [ODBC], native error numbers
- errors [ODBC], native error numbers
ms.assetid: 77cbc826-f47f-4803-8e7a-223d6df069b1
caps.latest.revision: "35"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 49fbc1ffedf678170bf08306220a7389cf1ed3f4
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="native-error-numbers"></a>ネイティブ エラー番号
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  データ ソースで発生するエラー (によって返される[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]) では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーがによって返されたネイティブ エラー番号を返します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 ドライバーで検出されたエラーを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client ODBC ドライバーが 0 のネイティブ エラー番号を返します。 ネイティブ エラー番号の一覧の詳細については、のエラー列を参照して、 **sysmessages**システム テーブルに、**マスター**データベース[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
 状態エラー コードについては、次を参照してください。 [SQLSTATE &#40;です。 ODBC エラー コード&#41;](../../relational-databases/native-client-odbc-error-messages/sqlstate-odbc-error-codes.md)です。 Net-Library から返されたエラーについては、ネイティブ エラー番号は基になるネットワーク ソフトウェアから返されます。  
  
## <a name="see-also"></a>参照  
 [エラーとメッセージの処理](../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  
