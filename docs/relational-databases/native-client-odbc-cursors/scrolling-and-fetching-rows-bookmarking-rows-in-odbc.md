---
title: ODBC での行のブックマーク |Microsoft Docs
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
- cursors [ODBC], fetching rows
- ODBC cursors, fetching rows
- cursors [ODBC], scrolling rows
- ODBC cursors, scrolling rows
- bookmarks [ODBC]
ms.assetid: 9cfcd243-c9d4-4c2a-abc4-399dbabe5f6b
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 74998eda5e7712d521967e21333f586062daeeec
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39554812"
---
# <a name="scrolling-and-fetching-rows---bookmarking-rows-in-odbc"></a>行のスクロールとフェッチ - ODBC での行のブックマーク
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  ブックマークは、データ行の識別に使われる値です。 ブックマーク値の意味を解釈できるのは、ドライバーまたはデータ ソースのみです。 たとえば、ブックマークは、行番号のような単純な値の場合も、ディスク アドレスのような複雑な値の場合もあります。 ODBC では、アプリケーションが特定の行のブックマークを要求し、これを保存し、カーソルに戻して行に返します。  
  
 持つ行をフェッチするときに[SQLFetchScroll](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md)アプリケーションは、開始行を選択するため、単位としてブックマークを使用することができます。 これは、現在のカーソルの位置に依存しないので、絶対アドレスの形式になります。 アプリケーションの呼び出し、ブックマークが設定された行にスクロールする**SQLFetchScroll**で、 *FetchOrientation* SQL_FETCH_BOOKMARK の。 この操作では、SQL_ATTR_FETCH_BOOKMARK_PTR オプション属性によって示されるブックマークを使用します。 結果として、そのブックマークによって識別される行で始まる行セットが返されます。 アプリケーションでこの操作のオフセットを指定することができます、 *FetchOffset*への呼び出しの引数**SQLFetchScroll**します。 オフセットを指定すると、結果の行セットの最初の行は、ブックマークで識別される行番号に FetchOffset 引数の数を加算した結果によって決まります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでは、静的カーソルとキーセット カーソルに対してのみブックマークがサポートされます。 ブックマークが設定されている場合に動的カーソルが要求されると、代わりにキーセット カーソルが開かれます。  
  
 ブックマークはでも使用できます、 **SQLBulkOperations**ブックマークで始まる行のセットに対して操作を実行する関数。  
  
## <a name="see-also"></a>参照  
 [行のスクロールとフェッチ](../../relational-databases/native-client-odbc-cursors/scrolling-and-fetching-rows.md)  
  
  
