---
title: データバッファーの種類 |Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 615625ca396e5f2ae094962457cc9e746730ddcf
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68067414"
---
# <a name="data-buffer-type"></a>データ バッファーの種類
バッファーの C データ型は、アプリケーションによって指定されます。 1つの変数を使用すると、アプリケーションによって変数が割り当てられたときに発生します。 汎用メモリ (つまり、void 型のポインターによって参照されるメモリ) では、アプリケーションがメモリを特定の型にキャストするときに、この処理が行われます。 ドライバーは、次の2つの方法でこの型を検出します。  
  
-   **データバッファーの型引数。** **SQLBindCol**の*targetvalueptr*にバインドされたバッファーなど、パラメーター値と結果セットデータを転送するために使用されるバッファーには、通常、 **SQLBindCol**の*TargetType*引数など、関連付けられた型引数があります。 この引数では、アプリケーションは、バッファーの型に対応する C 型の識別子を渡します。 たとえば、次の**SQLBindCol**への呼び出しでは、値 SQL_C_TYPE_DATE によって、*日付*バッファーが SQL_DATE_STRUCT であることがドライバーに通知されます。  
  
    ```  
    SQL_DATE_STRUCT Date;  
    SQLINTEGER  DateInd;  
    SQLBindCol(hstmt, 1, SQL_C_TYPE_DATE, &Date, 0, &DateInd);  
    ```  
  
     型識別子の詳細については、このセクションの後の「 [ODBC のデータ型](../../../odbc/reference/develop-app/data-types-in-odbc.md)」セクションを参照してください。  
  
-   **定義済みの型。** **SQLGetInfo**の*infovalueptr*引数によってポイントされるバッファーなどのオプションまたは属性を送受信するために使用されるバッファーには、指定されたオプションに依存する固定型があります。 ドライバーは、データバッファーがこの種類であることを前提としています。この型のバッファーを割り当てるのは、アプリケーションの役割です。 たとえば、 **SQLGetInfo**の次の呼び出しでは、ドライバーはバッファーが32ビット整数であると想定しています。これは SQL_STRING_FUNCTIONS オプションで必要とされるためです。  
  
    ```  
    SQLUINTEGER StringFuncs;  
    SQLGetInfo(hdbc, SQL_STRING_FUNCTIONS, (SQLPOINTER) &StringFuncs, 0,  
                NULL);  
    ```  
  
 ドライバーは、C データ型を使用して、バッファー内のデータを解釈します。
