---
title: SQLGetTypeInfo との情報を入力するデータの取得 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL data types [ODBC], identifiers
- SQLGetTypeInfo function [ODBC], retrieving data type information
- retrieving data type information [ODBC]
- type identifiers [ODBC], SQL
- identifiers [ODBC], SQL type
- SQL type identifiers [ODBC]
ms.assetid: d4f8b152-ab9e-4d05-a720-d10a08a6df81
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e0a5377934d3487fcfdc58459e8d08e01c8bd21b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="retrieving-data-type-information-with-sqlgettypeinfo"></a>SQLGetTypeInfo とデータ型情報の取得中
ODBC が関数を提供する ODBC 型識別子を基になる SQL データ型マッピングは概数であるため (**SQLGetTypeInfo**) を介して、ドライバーは完全にデータ ソース内の各 SQL データ型について説明します。 この関数は、各行が名、型識別子、有効桁数、小数点以下桁数、null 値許容属性などの単一のデータ型の特性を記述、結果セットを返します。  
  
 この情報は、通常はユーザーの作成し、変更テーブルに許可する汎用アプリケーションによって使用されます。 このようなアプリケーション呼び出し**SQLGetTypeInfo**データ型情報を取得し、ユーザーの一部またはすべてを表示します。 このようなアプリケーションは、次の 2 つの注意する必要があります。  
  
-   1 つ以上の SQL データ型はを使用するデータ型を決定するが困難に 1 つの型識別子にマップできます。 これを解決するには、結果セットが順序付けにまず型識別子によって、2 つ目の型識別子の定義に近さの程度によってです。 さらに、データ ソース – 定義データ型は、ユーザー定義データ型に優先します。 たとえば、データ ソースが同じにすることを除き、カウンターが自動インクリメント整数とカウンターのデータ型を定義します。 ユーザー定義型 WHOLENUM が整数のシノニムにもあるとします。 これらの型は、SQL_INTEGER にマップされます。 **SQLGetTypeInfo**結果セット、WHOLENUM 続けて整数が最初に、表示され、カウンターです。 WHOLENUM は、ユーザー定義ですが、カウンターの前により厳密に一致するので、SQL_INTEGER の定義の id を入力するために、整数の後に表示されます。  
  
-   ODBC で使用するためのデータ型の名前を定義しません**CREATE TABLE**と**ALTER TABLE**ステートメントです。 代わりに、アプリケーションがによって返される結果セットの TYPE_NAME 列で返される名前を使用する必要があります**SQLGetTypeInfo**です。 この理由は、する SQL のほとんどが一定の Dbms の間で、データ型の名前も異なります大幅です。 ドライバーを SQL ステートメントを解析し、標準的なデータ型の名前を DBMS に固有のデータ型の名前に置き換えるのではなく、ODBC には、まず DBMS 固有の名前を使用するアプリケーションが必要です。  
  
 なお**SQLGetTypeInfo**必ずしもについては説明しませんすべてのデータ型が、アプリケーションが発生することができます。 具体的には、結果セットには、直接サポートされていないデータ ソースのデータ型があります。 たとえば、ODBC カタログ関数によって返される結果セット内の列のデータ型の定義は、およびこれらのデータ型は、データ ソースでサポートされていない可能性があります。 結果セット内のデータ型の特性を判断するには、アプリケーションが呼び出す**SQLColAttribute**です。
