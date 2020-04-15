---
title: ODBC での C データ型 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], C data types
- C data types [ODBC], about C data types
- C data types [ODBC]
ms.assetid: c91bef31-3794-4736-966a-d50997b2233c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5e1efba2187e2c1f2d813d43640fc9259ad4f2b3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306297"
---
# <a name="c-data-types-in-odbc"></a>ODBC の C データ型
ODBC は、アプリケーション変数で使用される C データ型と、それに対応する型識別子を定義します。 これらは、結果セット列とステートメント・パラメーターにバインドされたバッファーによって使用されます。 たとえば、アプリケーションが結果セット列から文字形式でデータを取得するとします。 SQLCHAR * データ型の変数を宣言し、SQL_C_CHAR型識別子を持つ結果セット列にこの変数をバインドします。 C データ型と型識別子の完全な一覧については、「[付録 D : データ型](../../../odbc/reference/appendixes/appendix-d-data-types.md)」を参照してください。  
  
 ODBC では、各 SQL データ型から C データ型への既定のマッピングも定義します。 たとえば、データ ソース内の 2 バイト整数は、アプリケーション内の 2 バイト整数にマップされます。 既定のマッピングを使用するには、アプリケーションはSQL_C_DEFAULT型識別子を指定します。 ただし、相互運用上の理由から、この識別子を使用することはお勧めしません。  
  
 ODBC *1.x*で定義されているすべての整数 C データ型が署名されました。 ODBC 2.0 では、符号なし C データ型とそれに対応する型識別子が追加されました。 このため、アプリケーションとドライバーは *、1.x*バージョンを扱う際に特に注意する必要があります。  
  
## <a name="c-data-type-extensibility"></a>C データ型の拡張性  
 ODBC 3.8 では、ドライバー固有の C データ型を指定できます。 これにより、SQLBindCol [、SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)、または[SQLBindParameter](../../../odbc/reference/syntax/sqlbindcol-function.md)を呼び出すときに、ODBC アプリケーションでドライバー固有の C 型として SQL 型をバインド[できます](../../../odbc/reference/syntax/sqlbindparameter-function.md)。 既存の C データ型が新しいサーバーデータ型を正しく表さない可能性があるため、これは新しいサーバー・タイプをサポートする場合に役立ちます。 ドライバー固有の C 型を使用すると、ドライバーが実行できる変換の数が増加する可能性があります。  
  
 たとえば、データベース管理システム (DBMS) が、日付と時刻をタイム ゾーン情報で表す新しい SQL 型**DATETIMEOFFSET**を導入したとします。 ODBC には、**日付時刻オフセット**に対応する特定の C 型はありません。 アプリケーションは、SQL_C_BINARYとして**DATETIMEOFFSET**をバインドし、ユーザー定義データ型にキャストする必要があります。 Odbc 3.8 以降の C データ型の拡張、ドライバーは、新しい対応する C 型を定義できます。 たとえば、新しい SQL 型の DATETIMEOFFSET、ドライバーは、SQL_C_DATETIMEOFFSETなどの新しい対応する C 型を定義できます。 その後、アプリケーションは、ドライバー固有の C 型として新しい SQL の種類をバインドできます。  
  
 C データ型は、ドライバーで次のように定義されます。  
  
-   アプリケーション、ODBC ドライバー、およびドライバー マネージャーの ODBC 準拠レベルは 3.8 (またはそれ以上) です。  
  
-   ドライバー固有の C 型のデータ範囲は、0x4000 から 0x7FFF の間です。  
  
-   ドライバーは、C 型に対応するデータの構造を定義します。  これは、ドライバー固有の SDK で行うことができます。  
  
 ドライバー マネージャーは、0x4000 と 0x7FFF の範囲で定義されている C 型を検証しません。ドライバーは、検証とデータ型の変換を実行します。 ただし、ドライバー マネージャーに渡される C 型のデータ範囲が 0x0000 と 0x3FFF の間、または 0x8000 と 0xFFFF の間である場合、ドライバー マネージャーは C データ型を検証します。  
  
> [!NOTE]  
>  ドライバー固有の C データ型については、ドライバーのドキュメントで説明する必要があります。  
  
 ODBC 準拠レベル 3.8 を指定するには、アプリケーションは[SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md)を呼び出し、SQL_ATTR_ODBC_VERSION属性を**SQL_OV_ODBC3_80**に設定します。 ドライバーのバージョンを確認するには、アプリケーションは、SQL_DRIVER_ODBC_VERを使用して**SQLGetInfo**を呼び出します。  
  
 ODBC 3.8 の詳細については[、「ODBC 3.8 の新機能](../../../odbc/reference/what-s-new-in-odbc-3-8.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [C データ型](../../../odbc/reference/appendixes/c-data-types.md)
