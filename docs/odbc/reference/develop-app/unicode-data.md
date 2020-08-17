---
description: Unicode データ
title: Unicode データ |Microsoft Docs
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
ms.openlocfilehash: f217e6b629936cc835d134c89d972bb1408b9d0b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88339118"
---
# <a name="unicode-data"></a>Unicode データ
SQL Unicode データ型は、DBMS にネイティブで格納されているデータを記述するために用意されています。 アプリケーションで Unicode バッファーにデータをバインドできるようにするために、C Unicode データ型が用意されています。 ドライバーマネージャーは、Unicode C 型 (SQL_C_WCHAR) のデータを変換して、ANSI ドライバーで機能させることができます。  
  
 ODBC 3.0 または2。*x* アプリケーションは、常に ANSI データ型にバインドされます。 最適なパフォーマンスを実現するには、ODBC 3.5 (またはそれ以降) のアプリケーションを ANSI データ C 型にバインドし、SQL 列の型が ANSI である場合は、Unicode の C データ型にバインドする必要があります。  
  
 SQL Unicode の型インジケーターは、SQL_WCHAR、SQL_WVARCHAR、および SQL_WLONGVARCHAR です。 SQL_WCHAR データは固定長の文字列であり、SQL_WVARCHAR の可変長は、宣言された最大値で、SQL_WLONGVARCHAR の可変長はデータソースによって異なります。  
  
 C Unicode 型のインジケーターは SQL_C_WCHAR。 これは、各 SQL Unicode 型インジケーターの既定値です。 すべての SQL 型を SQL_C_WCHAR に変換し、SQL_C_WCHAR をすべての SQL 型に変換できます。 アプリケーションは、次の3つの方法のいずれかでデータを取得できます。  
  
-   データを SQL_C_CHAR として取得します。  
  
-   データを SQL_C_WCHAR として取得します。  
  
-   データを SQL_C_TCHAR として宣言します。 これは、アプリケーションが Unicode アプリケーションとしてコンパイルされている場合は SQL_C_WCHAR を挿入するマクロで、ANSI アプリケーションとしてコンパイルされる場合は SQL_C_CHAR を挿入します。  
  
 SQL_C_TCHAR は、次のように関数で宣言されます。  
  
```  
SQLBindParameter(StatementHandle, 1, SQL_PARAM_INPUT, SQL_C_TCHAR, SQL_WCHAR, NameLen, 0, Name, 0, &Name)  
```  
  
 アプリケーションが Unicode アプリケーションとしてコンパイルされると、 *ValueType* 引数が SQL_C_TCHAR から SQL_C_WCHAR に変更されます。 アプリケーションが ANSI アプリケーションとしてコンパイルされると、 *ValueType* 引数が SQL_C_CHAR に変更されます。  
  
 Unicode ドライバーでは、SQL_CHAR を含む ANSI データ型を引き続きサポートする必要があります。 Unicode ドライバーを使用しているアプリケーションが SQL_CHAR にバインドされている場合、ドライバーマネージャーは、SQL_CHAR データを SQL_WCHAR にマップしません。 Unicode ドライバーは、SQL_CHAR データを受け入れる必要があります。  
  
 ドライバーマネージャーでは、ドライバー名と DSN 名が Unicode で格納され、必要に応じて ANSI にマップされます。 Unicode 文字を ANSI 文字にマップできない場合 (コンピューターのネイティブコードページの文字がドライバーと DSN の名前で使用されていない場合に発生する可能性があります)、変換できなかった文字は、システムによって提供される既定の文字によって表されます。
