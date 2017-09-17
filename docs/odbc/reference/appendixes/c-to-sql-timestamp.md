---
title: "C から SQL へ: タイムスタンプ |Microsoft ドキュメント"
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
- data conversions from C to SQL types [ODBC], timestamp
- timestamp data type [ODBC]
- converting data from c to SQL types [ODBC], timestamp
ms.assetid: 0e08bfff-68f9-4648-9558-09b57fea08ad
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: bbb6396dc1a49d984834ec6f105b3a9ba42d95c4
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="c-to-sql-timestamp"></a>C から SQL へ: タイムスタンプ
Timestamp ODBC C データ型の識別子です。  
  
 SQL_C_TYPE_TIMESTAMP  
  
 次の表は、ODBC SQL データ型が C のタイムスタンプ データを変換することがありますを示します。 列とテーブルの用語の詳細については、次を参照してください。[に変換するデータを C から SQL データ型を](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md)です。  
  
|SQL 型の識別子|テスト|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|列のバイト長 > 文字バイトの長さを =<br /><br /> 19 < バイト長の列を = < バイトの長さを文字<br /><br /> 列のバイトの長さ < 19<br /><br /> データ値は有効なタイムスタンプではありません。|n/a<br /><br /> 22001<br /><br /> 22001<br /><br /> 22008|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|列の文字の長さ > データの文字の長さを =<br /><br /> 19 < 列の文字の長さを = < データの長さを文字<br /><br /> 列の長さ < 19 文字します。<br /><br /> データ値は有効なタイムスタンプではありません。|n/a<br /><br /> 22001<br /><br /> 22001<br /><br /> 22008|  
|SQL_TYPE_DATE|時刻フィールドは 0<br /><br /> 時刻フィールドは 0 以外の値<br /><br /> データ値に有効な日付が含まれていません|n/a<br /><br /> 22008<br /><br /> 22007|  
|SQL_TYPE_TIME|秒の小数部のフィールドは 0 を [a]<br /><br /> 秒の小数部のフィールドは、0 以外の値 [a]<br /><br /> データ値は有効な時刻を含んでいません|n/a<br /><br /> 22008<br /><br /> 22007|  
|SQL_TYPE_TIMESTAMP|秒の小数部のフィールドは、切り捨てられません<br /><br /> 秒の小数部のフィールドは切り捨てられます<br /><br /> データ値は有効なタイムスタンプではありません。|n/a<br /><br /> 22008<br /><br /> 22007|  
  
 [a] の日付のタイムスタンプの構造体のフィールドは無視されます。  
  
 SQL_C_TIMESTAMP 構造で有効な値については、次を参照してください。 [C データ型](../../../odbc/reference/appendixes/c-data-types.md)、前述の「します。  
  
 C のタイムスタンプ データが文字 SQL データに変換されると、結果の文字データは、"*yyyy*-*mm*-*dd* *hh*:*mm*:*ss*[.*f.*]"の形式です。  
  
 ドライバーは、タイムスタンプ C データ型からデータを変換するときに長さ/インジケーター値を無視し、データ バッファーのサイズが timestamp C データ型のサイズであると見なされます。 長さ/インジケーター値に渡されます、 *StrLen_or_Ind*引数**SQLPutData**とで指定したバッファー内の*StrLen_or_IndPtr* で引数**SQLBindParameter**です。 データ バッファーを指定した、 *DataPtr*引数**SQLPutData**と*ParameterValuePtr*引数**SQLBindParameter**.
