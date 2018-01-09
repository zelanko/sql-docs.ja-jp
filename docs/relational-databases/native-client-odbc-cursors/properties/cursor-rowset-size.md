---
title: "カーソルの行セット サイズ |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
- cursors [ODBC], rowset size
- ODBC cursors, rowset size
- rowsets [ODBC]
ms.assetid: 2febe2ae-fdc1-490e-a79f-c516bc8e7c3f
caps.latest.revision: "34"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 028dfc5275a5c8a0aa9f7527cd500545dbe6ff81
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="cursor-rowset-size"></a>カーソルの行セット サイズ
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  ODBC カーソルでは、一度にフェッチできる行数は制限されません。 各呼び出しで複数の行を取得する**SQLFetch**または[SQLFetchScroll](../../../relational-databases/native-client-odbc-api/sqlfetchscroll.md)です。 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のようなクライアント/サーバー型のデータベースで作業しているときは、1 回に複数行を取得する方が効率的です。 回のフェッチで返される行の数が行セットのサイズと呼びますの SQL_ATTR_ROW_ARRAY_SIZE を使用して指定[SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)です。  
  
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
  
 [SQLGetData](../../../relational-databases/native-client-odbc-api/sqlgetdata.md)こともできます、ブロック カーソルから列データを取得します。 **SQLGetData** 、一度に 1 つの行を動作**SQLSetPos**を呼び出す前に、現在の行として、行セット内の特定の行を設定するに呼び出せる必要があります**SQLGetData**です。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーには、行セットを使用して、結果セットをすばやく全体を取得する最適化が提供しています。 この最適化を使用する、カーソルの属性を既定値に設定 (順方向専用、読み取り専用の行セット サイズ = 1) 時に**SQLExecDirect**または**SQLExecute**と呼びます。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは、既定の結果セットを設定します。 スクロールを使用しないでクライアントに結果を送信する場合は、既定の結果セットの方がサーバー カーソルよりも効率的です。 ステートメントを実行後、行セット サイズを増やし、列方向のバインドか行方向のバインドを使用します。 これにより、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]を使用して、クライアントに結果の行を効率的に送信する既定の結果を設定中に、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは継続的に、クライアントのネットワーク バッファーから行を取得します。  
  
## <a name="see-also"></a>参照  
 [カーソルのプロパティ](../../../relational-databases/native-client-odbc-cursors/properties/cursor-properties.md)  
  
  
