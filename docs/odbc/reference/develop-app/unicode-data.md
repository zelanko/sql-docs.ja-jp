---
title: "Unicode データ |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Unicode [ODBC], data
- data types [ODBC], Unicode
- C data types [ODBC], Unicode
- SQL data types [ODBC], Unicode
ms.assetid: abc28718-e6d9-49fb-97ff-402d50c3c375
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 31122122cdb7a6f940dd1ba91eeb8caef8ac9d0c
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="unicode-data"></a>Unicode データ
SQL の Unicode データ型は、Unicode、DBMS にネイティブで存在するデータを記述する提供されます。 C の Unicode データ型は、Unicode のバッファーにデータをバインドするアプリケーションを許可するものです。 ドライバー マネージャーは、Unicode C 型にするには、(SQL_C_WCHAR) からデータを変換できる関数、ANSI ドライバーを使用します。  
  
 ODBC 3.0 または 2 です。*x*アプリケーションは、必ず ANSI データ型にバインドします。 最適なパフォーマンスは、ODBC 3.5 (またはそれ以降) アプリケーションする必要があります、ANSI データ型にバインド C 場合は SQL 列の型は ansi、および SQL 列の型が Unicode の場合、Unicode の C データ型にバインドする必要があります。  
  
 SQL Unicode 型インジケーターは、SQL_WCHAR、SQL_WVARCHAR、SQL_WLONGVARCHAR です。 SQL_WCHAR データに、固定文字列の長さ、SQL_WVARCHAR、宣言された最大の可変長があり、SQL_WLONGVARCHAR データ ソースに依存している最大の可変長があります。  
  
 C Unicode 型インジケーターは、SQL_C_WCHAR です。 これは、それぞれの SQL Unicode 型インジケーターの既定値です。 すべての SQL 型は、SQL_C_WCHAR に変換できる SQL_C_WCHAR は、すべての SQL 型に変換することができます。 アプリケーションでは、3 つの方法のいずれかでデータを取得できます。  
  
-   SQL_C_CHAR としてデータを取得します。  
  
-   SQL_C_WCHAR としてデータを取得します。  
  
-   SQL_C_TCHAR としてデータを宣言します。 これは、アプリケーションの場合、Unicode アプリケーションとしてコンパイルや、ANSI アプリケーションとしてコンパイルされている場合、SQL_C_CHAR を挿入、SQL_C_WCHAR を挿入するマクロです。  
  
 SQL_C_TCHAR が次の関数の宣言は。  
  
```  
SQLBindParameter(StatementHandle, 1, SQL_PARAM_INPUT, SQL_C_TCHAR, SQL_WCHAR, NameLen, 0, Name, 0, &Name)  
```  
  
 Unicode アプリケーションとして、アプリケーションがコンパイルされるときに、 *ValueType* SQL_C_WCHAR に SQL_C_TCHAR から引数に変更します。 アプリケーションが、ANSI アプリケーションとしてコンパイルされるときに、 *ValueType* SQL_C_CHAR に引数が変更されます。  
  
 Unicode のドライバーでは、SQL_CHAR を含む、ANSI データ型はサポートもする必要があります。 Unicode ドライバーで動作するアプリケーションは、SQL_CHAR にバインドした場合、ドライバー マネージャーは SQL_WCHAR に SQL_CHAR データをマップされません。 Unicode ドライバーでは、SQL_CHAR データを受け取る必要があります。  
  
 ドライバー マネージャーは、Unicode でドライバーおよび DSN 名を格納し、必要に応じて、ANSI にマッピングします。 文字を変換できませんでしたが既定の文字 sup によって表される場合は、Unicode 文字は、ANSI 文字 (ように、コンピューターのネイティブ コード ページではないコード ページから文字ドライバーと DSN 名で使用する場合に発生することができます) にマップすることはできません、システムによって plied です。
