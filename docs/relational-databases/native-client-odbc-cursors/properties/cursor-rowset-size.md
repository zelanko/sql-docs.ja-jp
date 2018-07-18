---
title: カーソルの行セットのサイズ |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], rowset size
- ODBC cursors, rowset size
- rowsets [ODBC]
ms.assetid: 2febe2ae-fdc1-490e-a79f-c516bc8e7c3f
caps.latest.revision: 34
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 7d03701d162e38ba0bd06c82cb3a29a00d87ed0c
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37408691"
---
# <a name="cursor-rowset-size"></a>カーソルの行セット サイズ
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  ODBC カーソルでは、一度にフェッチできる行数は制限されません。 呼び出すたびに複数の行を取得する**SQLFetch**または[SQLFetchScroll](../../../relational-databases/native-client-odbc-api/sqlfetchscroll.md)します。 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のようなクライアント/サーバー型のデータベースで作業しているときは、1 回に複数行を取得する方が効率的です。 フェッチで返される行の数が行セットのサイズという名前の SQL_ATTR_ROW_ARRAY_SIZE を使用して指定されて[SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)します。  
  
```  
SQLUINTEGER uwRowsize;  
SQLSetStmtAttr(m_hstmt, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER)uwRowsetSize, SQL_IS_UINTEGER);  
```  
  
 行セット サイズが 2 以上のカーソルをブロック カーソルと呼びます。  
  
 ブロック カーソルの結果セット列は、次の 2 つの方法でバインドできます。  
  
-   列方向のバインド  
  
     各列が変数の配列にバインドされます。 各配列には行セット サイズと同じ数の要素が含まれます。  
  
-   行方向のバインド  
  
     1 行のすべての列のデータとインジケーターが含まれる構造体を使用して配列が構築されます。 この配列には行セット サイズと同じ数の構造体が含まれます。  
  
 列方向または行方向のバインドを使用する場合、呼び出しごとに**SQLFetch**または**SQLFetchScroll**取得した行セットからデータをバインドされた配列に設定します。  
  
 [SQLGetData](../../../relational-databases/native-client-odbc-api/sqlgetdata.md)ブロック カーソルから列データを取得できます。 **SQLGetData** 、一度に 1 つの行を動作**SQLSetPos**行セット内の特定の行を呼び出す前に、現在の行として設定を呼び出す必要がある**SQLGetData**します。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは、行セットを使用して全体の結果がすばやく設定を取得する最適化を提供しています。 この最適化を使用する、カーソルの属性を既定値に設定 (順方向専用、読み取り専用、行セット サイズ = 1) 時に**SQLExecDirect**または**SQLExecute**が呼び出されます。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは、既定の結果セットを設定します。 スクロールを使用しないでクライアントに結果を送信する場合は、既定の結果セットの方がサーバー カーソルよりも効率的です。 ステートメントを実行後、行セット サイズを増やし、列方向のバインドか行方向のバインドを使用します。 これにより、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]結果の行を効率的に、クライアントに送信する既定の結果のセットを使用中に、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは継続的に、クライアントのネットワーク バッファーから行を取得します。  
  
## <a name="see-also"></a>参照  
 [カーソルのプロパティ](../../../relational-databases/native-client-odbc-cursors/properties/cursor-properties.md)  
  
  
