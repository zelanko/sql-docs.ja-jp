---
title: "付録 d: データの種類 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- C data types [ODBC], defined
- SQL data types [ODBC], defined
- data types [ODBC]
- data types [ODBC], about data types
ms.assetid: 981d49c3-3531-4543-aa75-5bd9e4f67000
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a543430479a33953e087fd50c91f7f2a307fc204
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="appendix-d-data-types"></a>付録 d: データ型
ODBC データ型の 2 つのセットを定義します。 SQL データ型と C データ型。 SQL データ型では、データ ソースに格納されているデータのデータ型を示します。 C データ型では、アプリケーションのバッファーに格納されたデータのデータ型を示します。  
  
 SQL データ型は、sql-92 標準に従って各 DBMS によって定義されます。 Sql-92 標準で指定された各 SQL データ型では、ODBC を定義する型識別子。 これは、 **#define** ODBC 関数の引数として渡したり、結果セットのメタデータで返される値。 唯一の SQL 92 ODBC でサポートされていないデータ型は (ODBC SQL_BIT 型は、異なる特性を持つ) ビット、BIT_VARYING、TIME_WITH_TIMEZONE、TIMESTAMP_WITH_TIMEZONE、および NATIONAL_CHARACTER です。 ドライバーは、ODBC SQL データ型識別子およびドライバー固有の SQL データ型識別子のデータ ソース固有の SQL データ型のマッピングを行います。 SQL データ型は、実装記述子の SQL_DESC_CONCISE_TYPE フィールドで指定されます。  
  
 ODBC C データ型と、対応する ODBC 型識別子を定義します。 アプリケーションの適切な C 型の識別子を渡すことによって結果セットのデータを受け取るバッファーの C データ型を指定する、 *TargetType*への呼び出しで引数**SQLBindCol**または**SQLGetData**です。 C 型の適切な C 型の識別子を渡すことによって、ステートメントのパラメーターを格納するバッファーの指定、 *ValueType*への呼び出しで引数**SQLBindParameter**です。 C データ型は、アプリケーションの記述子の SQL_DESC_CONCISE_TYPE フィールドで指定されます。  
  
> [!NOTE]  
>  ドライバー固有の C データ型はありません。  
  
 各 SQL データ型は、ODBC C データ型に対応します。 データ ソースからデータを返す前に、ドライバーは、それを C データ型が指定に変換します。 データ ソースにデータを送信する前に、ドライバーは、ことを指定の C データ型から変換します。  
  
 この付録の内容には、次のトピックが含まれています。  
  
-   [データ型識別子の使用](../../../odbc/reference/appendixes/using-data-type-identifiers.md)  
  
-   [SQL データ型](../../../odbc/reference/appendixes/sql-data-types.md)  
  
-   [C データ型](../../../odbc/reference/appendixes/c-data-types.md)  
  
-   [データ型識別子と記述子](../../../odbc/reference/appendixes/data-type-identifiers-and-descriptors.md)  
  
-   [疑似型識別子](../../../odbc/reference/appendixes/pseudo-type-identifiers.md)  
  
-   [バイナリ形式のデータを転送します。](../../../odbc/reference/appendixes/transferring-data-in-its-binary-form.md)  
  
-   [間隔の数値データ型のガイドライン](../../../odbc/reference/appendixes/guidelines-for-interval-and-numeric-data-types.md)  
  
-   [構成のグレゴリオ暦カレンダーの制約](../../../odbc/reference/appendixes/constraints-of-the-gregorian-calendar.md)  
  
-   [列のサイズ、小数点以下桁数、転送のオクテットの長さ、および表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)  
  
-   [SQL から C データ型にデータを変換します。](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)  
  
-   [データを C から SQL データ型に変換します。](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md)  
  
 ODBC データ型の詳細については、次を参照してください。 [ODBC でのデータ型](../../../odbc/reference/develop-app/data-types-in-odbc.md)です。 ドライバー固有の SQL データ型については、ドライバーのドキュメントを参照してください。

