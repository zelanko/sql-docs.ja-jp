---
title: カーソル行セットサイズ |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], rowset size
- ODBC cursors, rowset size
- rowsets [ODBC]
ms.assetid: 2febe2ae-fdc1-490e-a79f-c516bc8e7c3f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bff145e7e3c6e429ca0877c81c5188b02e428809
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63207166"
---
# <a name="cursor-rowset-size"></a>カーソルの行セット サイズ
  ODBC カーソルでは、一度にフェッチできる行数は制限されません。 **Sqlfetch**または[sqlfetchscroll](../../native-client-odbc-api/sqlfetchscroll.md)を呼び出すたびに、複数の行を取得できます。 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のようなクライアント/サーバー型のデータベースで作業しているときは、1 回に複数行を取得する方が効率的です。 フェッチで返される行の数は行セットサイズと呼ばれ、 [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)の SQL_ATTR_ROW_ARRAY_SIZE を使用して指定されます。  
  
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
  
 列方向または行方向のバインドのいずれかを使用すると、 **Sqlfetch**または**sqlfetchscroll**を呼び出すたびに、バインドされた配列に、取得した行セットのデータが格納されます。  
  
 [SQLGetData](../../native-client-odbc-api/sqlgetdata.md)を使用して、ブロックカーソルから列データを取得することもできます。 **SQLGetData**は一度に1行ずつ動作するため、 **SQLGetData**を呼び出す前に**SQLSetPos**を呼び出して、行セット内の特定の行を現在の行として設定する必要があります。  
  
 Native [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client ODBC ドライバーでは、行セットを使用して結果セット全体をすばやく取得する最適化が提供されます。 この最適化を使用するには、 **SQLExecDirect**または**sqlexecute**が呼び出されたときに、カーソルの属性を既定値 (順方向専用、読み取り専用、行セットサイズ = 1) に設定します。 Native [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client ODBC ドライバーは、既定の結果セットを設定します。 スクロールを使用しないでクライアントに結果を送信する場合は、既定の結果セットの方がサーバー カーソルよりも効率的です。 ステートメントを実行後、行セット サイズを増やし、列方向のバインドか行方向のバインドを使用します。 これに[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]より、既定の結果セットを使用してクライアントに結果行を効率的[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]に送信できます。一方、Native client ODBC ドライバーでは、クライアントのネットワークバッファーから行を継続的にプルします。  
  
## <a name="see-also"></a>参照  
 [カーソルのプロパティ](cursor-properties.md)  
  
  
