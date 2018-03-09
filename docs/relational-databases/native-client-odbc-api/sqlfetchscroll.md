---
title: "SQLFetchScroll |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-api
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLFetchScroll function
ms.assetid: 524a3985-a08d-4445-99e0-bb551a666615
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5ece42f98419e884d5458959112a0089b0c441ae
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2018
---
# <a name="sqlfetchscroll"></a>SQLFetchScroll
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  **SQLFetchScroll**アプリケーションへのデータの 1 つの行セットを返します。 使用して、行セットのサイズを設定[SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは、次の制限付きのすべての定義済みフェッチ命令 (SQL_FETCH_RELATIVE など) をサポートしています。  
  
-   ステートメントに順方向専用カーソルを定義する場合は、SQL_FETCH_NEXT が必要です。他の形式でフェッチを試行すると、エラーが返されます。  
  
-   SQL_FETCH_BOOKMARK がサポートされるのは、静的カーソルとキーセット ドリブン カーソルに対してのみです。  
  
## <a name="sqlfetchscroll-support-for-enhanced-date-and-time-features"></a>SQLFetchScroll による機能強化された日付と時刻のサポート  
 」の説明に従って、日付/時刻型の結果列の値が変換された[SQL から C への変換](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md)です。  
  
 詳細については、次を参照してください。[日付と時刻の強化 &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)です。  
  
## <a name="sqlfetchscroll-support-for-large-clr-udts"></a>SQLFetchScroll による大きな CLR UDT のサポート  
 **SQLFetchScroll**大きなの CLR ユーザー定義型 (Udt) をサポートしています。 詳細については、次を参照してください。 [Large CLR User-Defined 型 &#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md)です。  
  
## <a name="see-also"></a>参照  
 [SQLFetchScroll 関数](http://go.microsoft.com/fwlink/?LinkId=59343)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
