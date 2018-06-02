---
title: カーソルを実装する方法 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-odbc-cursors
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, cursors
- ODBC cursors, about ODBC cursors
- ODBC applications, cursors
- cursors [ODBC], about ODBC cursors
ms.assetid: 2b1d7dd4-08a4-43fc-b3eb-70c183d0941f
caps.latest.revision: 32
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 8572f47636729998cf12cff3eb26f07c2061fda1
ms.sourcegitcommit: 2d93cd115f52bf3eff3069f28ea866232b4f9f9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2018
ms.locfileid: "34708530"
---
# <a name="how-cursors-are-implemented"></a>カーソルの実装方法
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  ODBC アプリケーションでは SQL ステートメントを実行する前に、1 つ以上のステートメント属性を設定することにより、カーソルの動作を制御します。 ODBC には、カーソルの特性を指定する方法として、次の 2 つが用意されています。  
  
-   カーソルの種類  
  
     カーソルの種類は、の SQL_ATTR_CURSOR_TYPE 属性を使用して設定された[SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)です。 ODBC カーソルの種類には、順方向専用、静的、キーセット ドリブン、混合、および動的があります。 カーソルの種類を設定することは、カーソルを指定するための ODBC 独自の方法でした。  
  
-   カーソルの動作  
  
     SQL_ATTR_CURSOR_SCROLLABLE と SQL_ATTR_CURSOR_SENSITIVITY 属性を使用してカーソルの動作を設定**SQLSetStmtAttr**です。 これらの属性は、ISO 標準で DECLARE CURSOR ステートメント用に定義されている SCROLL キーワードと SENSITIVE キーワードをモデルにしたものです。 これら 2 つの ISO オプションは、ODBC Version 3.0 で導入されました。  
  
 ODBC カーソルの特性は、これら 2 つの方法のいずれかを使用して指定する必要がありますが、ODBC カーソルの種類を使用することをお勧めします。  
  
 ODBC アプリケーションではカーソルの種類を設定すること以外に、1 回のフェッチで返される行数、同時実行オプション、トランザクション分離レベルなど、他のオプションも設定します。 これらのオプションは、ODBC 形式のカーソル (順方向専用、静的、キーセット ドリブン、混合、および動的) または ISO 形式のカーソル (スクロール機能と感度) に対して設定できます。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは、さまざまな種類のカーソルを物理的に実装するいくつかの方法をサポートしています。 このドライバーでは、いくつかの種類のカーソルは [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の既定の結果セットを使用して実装されます。また ODBC カーソル ライブラリを使用してサーバー カーソルとして実装される場合もあります。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [SQL Server の既定の結果セットの使用](../../../relational-databases/native-client-odbc-cursors/implementation/using-sql-server-default-result-sets.md)  
  
-   [サーバー カーソルの使用](../../../relational-databases/native-client-odbc-cursors/implementation/using-server-cursors.md)  
  
-   [ODBC カーソル ライブラリ](../../../relational-databases/native-client-odbc-cursors/implementation/odbc-cursor-library.md)  
  
## <a name="see-also"></a>参照  
 [カーソルを使用して&#40;ODBC&#41;](../../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md)  
  
  
