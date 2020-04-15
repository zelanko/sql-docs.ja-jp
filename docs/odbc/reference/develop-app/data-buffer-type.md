---
title: データ バッファタイプ |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], buffers
- data buffers [ODBC], types
- buffers [ODBC], data
- C data types [ODBC], buffers
ms.assetid: 58bea3e9-d552-447f-b3ad-ce1dab213b72
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9b98ed2ab0865b98884f6dfa1ff20142540ff314
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305248"
---
# <a name="data-buffer-type"></a>データ バッファーの種類
バッファーの C データ・タイプは、アプリケーションによって指定されます。 単一の変数では、アプリケーションが変数を割り当てると、この処理が発生します。 汎用メモリ (void 型のポインタが指すメモリ) では、アプリケーションがメモリを特定の型にキャストしたときに発生します。 ドライバーは、2 つの方法でこの型を検出します。  
  
-   **データ バッファー型引数。** パラメーター値と結果セットのデータを転送するために使用されるバッファー **(SQLBindCol**で*TargetValuePtr*でバインドされたバッファーなど) には、通常 **、SQLBindCol**の*TargetType*引数などの関連付けられた型引数があります。 この引数では、アプリケーションは、バッファーの型に対応する C 型の識別子を渡します。 たとえば、次の**SQLBindCol**の呼び出しでは、*値SQL_C_TYPE_DATE、日付*バッファーがSQL_DATE_STRUCTであることをドライバーに通知します。  
  
    ```  
    SQL_DATE_STRUCT Date;  
    SQLINTEGER  DateInd;  
    SQLBindCol(hstmt, 1, SQL_C_TYPE_DATE, &Date, 0, &DateInd);  
    ```  
  
     型識別子の詳細については、後の[「ODBC データ型](../../../odbc/reference/develop-app/data-types-in-odbc.md)」を参照してください。  
  
-   **定義済みの型。** **SQLGetInfo**の*InfoValuePtr*引数が指すバッファーなど、オプションまたは属性の送信および取得に使用されるバッファーは、指定されたオプションに依存する固定型を持ちます。 ドライバーは、データ バッファーがこの型であることを前提としています。このタイプのバッファを割り当てるのはアプリケーションの責任です。 たとえば、次の**SQLGetInfo**の呼び出しでは、ドライバーはバッファーが 32 ビット整数であると仮定SQL_STRING_FUNCTIONS オプションが必要です。  
  
    ```  
    SQLUINTEGER StringFuncs;  
    SQLGetInfo(hdbc, SQL_STRING_FUNCTIONS, (SQLPOINTER) &StringFuncs, 0,  
                NULL);  
    ```  
  
 ドライバーは、バッファー内のデータを解釈するのに C データ型を使用します。
