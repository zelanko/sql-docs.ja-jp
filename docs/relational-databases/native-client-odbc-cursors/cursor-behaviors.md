---
title: "カーソルの動作 |Microsoft ドキュメント"
ms.custom: 
ms.date: 10/24/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-cursors
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- scrollable cursors [SQL Server]
- SQL Server Native Client ODBC driver, cursors
- version-based optimistic concurrency
- cursors [ODBC], cursor behaviors
- ODBC applications, cursors
- SQL_ATTR_CURSOR_SENSITIVITY option
- SQL_ATTR_CURSOR_SCROLLABLE option
- sensitivity behavior of cursor
- ODBC cursors, cursor behaviors
ms.assetid: 742ddcd2-232b-4aa1-9212-027df120ad35
caps.latest.revision: "32"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0870e8ae32d958437eb55cd01664ce05188bfc7d
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="cursor-behaviors"></a>カーソルの動作
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  ODBC では、カーソルのスクロールの可否と感度を設定することでカーソル動作を指定する、ISO オプションがサポートされます。 これらの動作への呼び出しで SQL_ATTR_CURSOR_SCROLLABLE と SQL_ATTR_CURSOR_SENSITIVITY オプションの設定で指定された[SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでは、次の特性を持つサーバー カーソルを要求して、これらのオプションを実装します。  
  
|カーソル動作の設定|要求されるサーバー カーソルの特性|  
|------------------------------|---------------------------------------------|  
|SQL_SCROLLABLE と SQL_SENSITIVE|キーセット ドリブン カーソルとバージョンに基づくオプティミスティック同時実行制御|  
|SQL_SCROLLABLE と SQL_INSENSITIVE|静的カーソルと読み取り専用同時実行|  
|SQL_SCROLLABLE と SQL_UNSPECIFIED|静的カーソルと読み取り専用同時実行|  
|SQL_NONSCROLLABLE と SQL_SENSITIVE|順方向専用カーソルとバージョンに基づくオプティミスティック同時実行制御|  
|SQL_NONSCROLLABLE と SQL_INSENSITIVE|既定の結果セット (順方向専用、読み取り専用)|  
|SQL_NONSCROLLABLE と SQL_UNSPECIFIED|既定の結果セット (順方向専用、読み取り専用)|  
  
 バージョンに基づくオプティミスティック同時実行制御が必要です、**タイムスタンプ**基になるテーブル内の列です。 バージョンに基づくオプティミスティック同時実行制御がないテーブルで要求されている場合、**タイムスタンプ**列で、サーバーは値に基づくオプティミスティック同時実行制御。  
  
## <a name="scrollability"></a>スクロール可能  
 カーソルがすべて別の値をサポートする SQL_ATTR_CURSOR_SCROLLABLE が SQL_SCROLLABLE に設定されている場合、 *FetchOrientation*のパラメーター [SQLFetchScroll](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md)です。 SQL_ATTR_CURSOR_SCROLLABLE が SQL_NONSCROLLABLE に設定されている場合、カーソルのみをサポートする*FetchOrientation* SQL_FETCH_NEXT の値。  
  
## <a name="sensitivity"></a>感度  
 SQL_ATTR_CURSOR_SENSITIVITY が SQL_SENSITIVE に設定されているとき、現在のユーザーが行ったデータ変更または他のユーザーがコミットしたデータ変更がカーソルに反映されます。 SQL_ATTR_CURSOR_SENSITIVITY が SQL_INSENSITIVE に設定されているときは、データ変更がカーソルに反映されません。  
  
## <a name="see-also"></a>参照  
 [カーソル (ODBC) を使用して](../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md)[カーソル プロパティ](properties/cursor-properties.md) 
  
  
