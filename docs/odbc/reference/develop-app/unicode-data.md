---
title: ユニコードデータ |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Unicode [ODBC], data
- data types [ODBC], Unicode
- C data types [ODBC], Unicode
- SQL data types [ODBC], Unicode
ms.assetid: abc28718-e6d9-49fb-97ff-402d50c3c375
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 73ea9035b05f04fec1527ca2aa98531a807db8cf
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307399"
---
# <a name="unicode-data"></a>Unicode データ
SQL Unicode データ型は、DBMS 上でネイティブに Unicode に存在するデータを記述するために用意されています。 アプリケーションがデータを Unicode バッファーにバインドできるようにするために、C Unicode データ型が提供されています。 ドライバー マネージャーは、ANSI ドライバーで機能するように、Unicode C 型 (SQL_C_WCHAR) からデータを変換できます。  
  
 ODBC 3.0 または 2。*x*アプリケーションは、常に ANSI データ型にバインドします。 最適なパフォーマンスを得るためには、ODBC 3.5 (またはそれ以上) のアプリケーションは、SQL 列タイプが ANSI の場合は ANSI データ C 型にバインドし、SQL 列タイプが Unicode の場合は Unicode C データ型にバインドする必要があります。  
  
 SQL ユニコード・タイプ標識は、SQL_WCHAR、SQL_WVARCHAR、およびSQL_WLONGVARCHARです。 SQL_WCHARデータの長さは固定で、SQL_WVARCHARは宣言された最大値の可変長を持ち、SQL_WLONGVARCHARはデータ ソースに依存する最大の可変長を持ちます。  
  
 C ユニコードタイプインジケータがSQL_C_WCHAR。 これは、SQL ユニコードの各タイプのインジケーターのデフォルトです。 すべての SQL 型をSQL_C_WCHARに変換でき、SQL_C_WCHARすべての SQL 型に変換できます。 アプリケーションは、次の 3 つの方法のいずれかでデータを取得できます。  
  
-   データをSQL_C_CHARとして取得します。  
  
-   データをSQL_C_WCHARとして取得します。  
  
-   データをSQL_C_TCHARとして宣言します。 これは、アプリケーションが Unicode アプリケーションとしてコンパイルされた場合にSQL_C_WCHARを挿入するマクロであり、ANSI アプリケーションとしてコンパイルされた場合はSQL_C_CHARを挿入します。  
  
 SQL_C_TCHARは、次のように関数で宣言されます。  
  
```  
SQLBindParameter(StatementHandle, 1, SQL_PARAM_INPUT, SQL_C_TCHAR, SQL_WCHAR, NameLen, 0, Name, 0, &Name)  
```  
  
 アプリケーションが Unicode アプリケーションとしてコンパイルされると *、ValueType*引数はSQL_C_TCHARからSQL_C_WCHARに変更されます。 アプリケーションを ANSI アプリケーションとしてコンパイルすると *、ValueType*引数がSQL_C_CHARに変更されます。  
  
 Unicode ドライバーは、SQL_CHARを含む ANSI データ型をサポートする必要があります。 Unicode ドライバーを使用して動作するアプリケーションがSQL_CHARにバインドする場合、ドライバー マネージャーは、SQL_WCHARにSQL_CHARデータをマップしません。 Unicode ドライバーは、SQL_CHARデータを受け入れる必要があります。  
  
 ドライバー マネージャーは、Unicode でドライバーと DSN 名を格納し、必要に応じて ANSI にマップします。 Unicode 文字を ANSI 文字にマップできない場合 (コンピュータのネイティブ コード ページではないコード ページの文字がドライバ名と DSN 名で使用されている場合など)、変換できなかった文字はシステムによって指定された既定の文字で表されます。
