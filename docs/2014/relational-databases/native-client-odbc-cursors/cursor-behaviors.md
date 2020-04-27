---
title: カーソルの動作 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6c5ded9f42da267cfd137f0adfd4465d965d9a06
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "63188564"
---
# <a name="cursor-behaviors"></a>カーソル動作
  ODBC では、カーソルのスクロールの可否と感度を設定することでカーソル動作を指定する、ISO オプションがサポートされます。 これらの動作は、 [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md)の呼び出しで SQL_ATTR_CURSOR_SCROLLABLE オプションと SQL_ATTR_CURSOR_SENSITIVITY オプションを設定することによって指定します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでは、次の特性を持つサーバー カーソルを要求して、これらのオプションを実装します。  
  
|カーソル動作の設定|要求されるサーバー カーソルの特性|  
|------------------------------|---------------------------------------------|  
|SQL_SCROLLABLE と SQL_SENSITIVE|キーセット ドリブン カーソルとバージョンに基づくオプティミスティック コンカレンシー|  
|SQL_SCROLLABLE と SQL_INSENSITIVE|静的カーソルと読み取り専用コンカレンシー|  
|SQL_SCROLLABLE と SQL_UNSPECIFIED|静的カーソルと読み取り専用コンカレンシー|  
|SQL_NONSCROLLABLE と SQL_SENSITIVE|順方向専用カーソルとバージョンに基づくオプティミスティック コンカレンシー|  
|SQL_NONSCROLLABLE と SQL_INSENSITIVE|既定の結果セット (順方向専用、読み取り専用)|  
|SQL_NONSCROLLABLE と SQL_UNSPECIFIED|既定の結果セット (順方向専用、読み取り専用)|  
  
 バージョンベースのオプティミスティック同時実行制御には、基になるテーブルに**timestamp**列が必要です。 **Timestamp**列のないテーブルに対してバージョンベースのオプティミスティック同時実行制御が要求された場合、サーバーは値に基づくオプティミスティック同時実行制御を使用します。  
  
## <a name="scrollability"></a>スクロール可能  
 SQL_ATTR_CURSOR_SCROLLABLE が SQL_SCROLLABLE に設定されている場合、カーソルは[Sqlfetchscroll](../native-client-odbc-api/sqlfetchscroll.md)の*fetchorientation*パラメーターのさまざまな値をすべてサポートします。 SQL_ATTR_CURSOR_SCROLLABLE が SQL_NONSCROLLABLE に設定されている場合、カーソルは SQL_FETCH_NEXT の*Fetchorientation*値のみをサポートします。  
  
## <a name="sensitivity"></a>感度  
 SQL_ATTR_CURSOR_SENSITIVITY が SQL_SENSITIVE に設定されているとき、現在のユーザーが行ったデータ変更または他のユーザーがコミットしたデータ変更がカーソルに反映されます。 SQL_ATTR_CURSOR_SENSITIVITY が SQL_INSENSITIVE に設定されているときは、データ変更がカーソルに反映されません。  
  
## <a name="see-also"></a>参照  
 [ODBC&#41;&#40;カーソルの使用](using-cursors-odbc.md)  
  
  
