---
title: "SQL には、データの変換例については C |Microsoft ドキュメント"
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
- data conversions from SQL to C types [ODBC], examples
- converting data from SQL to C types [ODBC], examples
ms.assetid: 0190c76c-7f9b-42f4-be9d-cef7284840fd
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c7dd7b514ce4788a035e6f230f3d0a87a94440f2
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sql-to-c-data-conversion-examples"></a>SQL には、C データ変換の例
次の表に示す例については、ドライバーが SQL データを C データに変換する方法を示しています。  
  
|SQL 型<br /><br /> 識別子 (identifier)|SQL data<br /><br /> value|C 型<br /><br /> 識別子 (identifier)|バッファー<br /><br /> length|**TargetValuePtr*|SQLSTATE|  
|-----------------------------|------------------------|---------------------------|-----------------------|------------------------|--------------|  
|SQL_CHAR|abcdef|SQL_C_CHAR|7|abcdef\0 [a]|n/a|  
|SQL_CHAR|abcdef|SQL_C_CHAR|6|abcde\0 [a]|01004|  
|SQL_DECIMAL|1234.56|SQL_C_CHAR|8|1234.56\0 [a]|n/a|  
|SQL_DECIMAL|1234.56|SQL_C_CHAR|5|1234\0 [a]|01004|  
|SQL_DECIMAL|1234.56|SQL_C_CHAR|4|----|22003|  
|SQL_DECIMAL|1234.56|SQL_C_FLOAT|無視されます。|1234.56|n/a|  
|SQL_DECIMAL|1234.56|SQL_C_SSHORT|無視されます。|1234|01S07|  
|SQL_DECIMAL|1234.56|SQL_C_STINYINT|無視されます。|----|22003|  
SQL_DOUBLE|1.2345678|SQL_C_DOUBLE|無視されます。|1.2345678|n/a|  
|SQL_DOUBLE|1.2345678|SQL_C_FLOAT|無視されます。|1.234567|n/a|  
|SQL_DOUBLE|1.2345678|SQL_C_STINYINT|無視されます。|1|n/a|  
|SQL_TYPE_DATE|1992-12-31|SQL_C_CHAR|11|1992-12-31\0 [a]|n/a|  
|SQL_TYPE_DATE|1992-12-31|SQL_C_CHAR|10|-----|22003|  
|SQL_TYPE_DATE|1992-12-31|SQL_C_TIMESTAMP|無視されます。|1992,12,31、0,0,0,0 [b]|n/a|  
|SQL_TYPE_TIMESTAMP|1992-12-31 23:45:55.12|SQL_C_CHAR|23|1992-12-31 23:45:55.12\0 [a]|n/a|  
SQL_TYPE_TIMESTAMP|1992-12-31 23:45:55.12|SQL_C_CHAR|22|1992-12-31 23:45:55.1\0 [a]|01004|  
|SQL_TYPE_TIMESTAMP|1992-12-31 23:45:55.12|SQL_C_CHAR|18|----|22003|  
  
 [a]「\0」では、null 終了バイトを表します。 ドライバー常に null で終端の SQL_C_CHAR データ。  
  
 [この一覧に b] の数値は、TIMESTAMP_STRUCT 構造体のフィールドに格納されている番号です。

