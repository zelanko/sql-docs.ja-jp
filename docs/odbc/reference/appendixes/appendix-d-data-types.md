---
title: '付録 D: データ型 |マイクロソフトドキュメント'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- C data types [ODBC], defined
- SQL data types [ODBC], defined
- data types [ODBC]
- data types [ODBC], about data types
ms.assetid: 981d49c3-3531-4543-aa75-5bd9e4f67000
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8c1abadb962e3a1ee9327bbb8d84e52d180b4a7e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292462"
---
# <a name="appendix-d-data-types"></a>付録 D: データ型
ODBC では、SQL データ型と C データ型の 2 つのデータ型セットを定義します。 SQL データ型は、データ ソースに格納されているデータのデータ型を示します。 C データ型は、アプリケーション バッファに格納されているデータのデータ型を示します。  
  
 SQL データ型は、SQL-92 標準に従って各 DBMS によって定義されます。 SQL-92 標準で指定されている SQL データ型ごとに、ODBC は型識別子を定義 **#define**します。 ODBC でサポートされていない SQL-92 データ型は、BIT (ODBC SQL_BIT型には特性が異なる)、BIT_VARYING、TIME_WITH_TIMEZONE、TIMESTAMP_WITH_TIMEZONE、およびNATIONAL_CHARACTERだけです。 ドライバーは、ODBC SQL データ型識別子とドライバー固有の SQL データ型識別子にデータ ソース固有の SQL データ型をマップする役割を担います。 SQL データ・タイプは、実装記述子のSQL_DESC_CONCISE_TYPEフィールドで指定されます。  
  
 ODBC は、C データ型とそれに対応する ODBC 型識別子を定義します。 アプリケーションは **、SQLBindCol**または**SQLGetData**の呼び出しで、適切な C 型識別子を*TargetType*引数に渡すことによって、結果セット データを受け取るバッファーの C データ型を指定します。 **SQLBindParameter**の呼び出しで *、ValueType*引数に適切な C 型識別子を渡すことによって、ステートメント パラメーターを含むバッファーの C 型を指定します。 C データ・タイプは、アプリケーション記述子の SQL_DESC_CONCISE_TYPE フィールドで指定されます。  
  
> [!NOTE]  
>  ドライバ固有の C データ型はありません。  
  
 各 SQL データ型は、ODBC C データ型に対応します。 データ ソースからデータを返す前に、ドライバーは、指定された C データ型に変換します。 データ ソースにデータを送信する前に、ドライバーは、指定された C データ型から変換します。  
  
 この付録では、以下のトピックを取り上げます。  
  
-   [データ型識別子の使用](../../../odbc/reference/appendixes/using-data-type-identifiers.md)  
  
-   [SQL データ型](../../../odbc/reference/appendixes/sql-data-types.md)  
  
-   [C データ型](../../../odbc/reference/appendixes/c-data-types.md)  
  
-   [データ型識別子と記述子](../../../odbc/reference/appendixes/data-type-identifiers-and-descriptors.md)  
  
-   [疑似型識別子](../../../odbc/reference/appendixes/pseudo-type-identifiers.md)  
  
-   [バイナリ形式でのデータ転送](../../../odbc/reference/appendixes/transferring-data-in-its-binary-form.md)  
  
-   [間隔と数値データ型のガイドライン](../../../odbc/reference/appendixes/guidelines-for-interval-and-numeric-data-types.md)  
  
-   [グレゴリオ暦カレンダーの制限](../../../odbc/reference/appendixes/constraints-of-the-gregorian-calendar.md)  
  
-   [列サイズ、小数点以下の桁数、転送オクテット長、および表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)  
  
-   [SQL から C データ型へのデータ変換](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)  
  
-   [C から SQL データ型へのデータ変換](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md)  
  
 ODBC データ型の詳細については[、「ODBC でのデータ型](../../../odbc/reference/develop-app/data-types-in-odbc.md)」を参照してください。 ドライバー固有の SQL データ型については、ドライバーのドキュメントを参照してください。
