---
title: カーソルの動作 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 10/24/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f2e3400e52cd0b7574c07a3cf813b4cbca317df2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305491"
---
# <a name="cursor-behaviors"></a>カーソル動作
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  ODBC では、カーソルのスクロールの可否と感度を設定することでカーソル動作を指定する、ISO オプションがサポートされます。 これらの動作は、 [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)の呼び出しでSQL_ATTR_CURSOR_SCROLLABLEオプションとSQL_ATTR_CURSOR_SENSITIVITYオプションを設定することによって指定されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでは、次の特性を持つサーバー カーソルを要求して、これらのオプションを実装します。  
  
|カーソル動作の設定|要求されるサーバー カーソルの特性|  
|------------------------------|---------------------------------------------|  
|SQL_SCROLLABLE と SQL_SENSITIVE|キーセット ドリブン カーソルとバージョンに基づくオプティミスティック コンカレンシー|  
|SQL_SCROLLABLE と SQL_INSENSITIVE|静的カーソルと読み取り専用コンカレンシー|  
|SQL_SCROLLABLE と SQL_UNSPECIFIED|静的カーソルと読み取り専用コンカレンシー|  
|SQL_NONSCROLLABLE と SQL_SENSITIVE|順方向専用カーソルとバージョンに基づくオプティミスティック コンカレンシー|  
|SQL_NONSCROLLABLE と SQL_INSENSITIVE|既定の結果セット (順方向専用、読み取り専用)|  
|SQL_NONSCROLLABLE と SQL_UNSPECIFIED|既定の結果セット (順方向専用、読み取り専用)|  
  
 バージョン ベースのオプティミスティック同時実行制御では、基になるテーブルに**タイムスタンプ**列が必要です。 **timestamp**列がないテーブルでバージョンベースのオプティミスティック同時実行制御が要求された場合、サーバーは値ベースのオプティミスティック同時実行制御を使用します。  
  
## <a name="scrollability"></a>スクロール可能  
 SQL_ATTR_CURSOR_SCROLLABLEをSQL_SCROLLABLE に設定すると、カーソルは[SQLFetchScroll](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md)の*フェッチオリエンテーション*パラメーターのすべての異なる値をサポートします。 SQL_ATTR_CURSOR_SCROLLABLEがSQL_NONSCROLLABLEに設定されている場合、カーソルは SQL_FETCH_NEXT の*FetchOrientation*値のみをサポートします。  
  
## <a name="sensitivity"></a>感度  
 SQL_ATTR_CURSOR_SENSITIVITY が SQL_SENSITIVE に設定されているとき、現在のユーザーが行ったデータ変更または他のユーザーがコミットしたデータ変更がカーソルに反映されます。 SQL_ATTR_CURSOR_SENSITIVITY が SQL_INSENSITIVE に設定されているときは、データ変更がカーソルに反映されません。  
  
## <a name="see-also"></a>参照  
 [カーソルの使用 (ODBC)](../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md) [カーソルプロパティ](properties/cursor-properties.md) 
  
  
