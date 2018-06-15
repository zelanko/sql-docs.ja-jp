---
title: 'SQL には、c: 年-月間隔 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- converting data from SQL to c types [ODBC], about converting
- data conversions from SQL to C types [ODBC], year-month intervals
- intervals [ODBC], converting
- year-month intervals [ODBC]
ms.assetid: 1233634b-8214-420f-b872-3b2630105ba4
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: da1a3378ba16a360ff2e307219ea350fa6ed1efd
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32910017"
---
# <a name="sql-to-c-year-month-intervals"></a>SQL には、c: 年-月間隔
年、月間隔 ODBC SQL データ型の識別子は次のとおりです。  
  
 SQL_INTERVAL_YEAR  
  
 SQL_INTERVAL_MONTH  
  
 SQL_INTERVAL_YEAR_TO_MONTH  
  
 次の表は、ODBC C データ型の年-月には、SQL データの間隔を変換することがありますを示します。 列とテーブルの用語の詳細については、次を参照してください。[に変換するデータを SQL から C データ型に](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)です。  
  
|C 型識別子|テスト|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_INTERVAL_MONTH [a]<br /><br /> SQL_C_INTERVAL_YEAR [a]<br /><br /> SQL_C_INTERVAL_YEAR_TO_MONTH [a]|末尾のフィールドの部分は切り捨てられません<br /><br /> 末尾のフィールド部分が切り捨てられます<br /><br /> ソースからデータを保持するために十分な大きさが先頭のターゲットの有効桁数です。|Data<br /><br /> 切り捨てられたデータ<br /><br /> 未定義。|バイト単位でデータの長さ<br /><br /> バイト単位でデータの長さ<br /><br /> 未定義。|n/a<br /><br /> 01S07<br /><br /> 22015|  
|SQL_C_STINYINT [b]<br /><br /> SQL_C_UTINYINT [b]<br /><br /> SQL_C_USHORT [b]<br /><br /> SQL_C_SHORT [b]<br /><br /> SQL_C_SLONG [b]<br /><br /> SQL_C_ULONG [b]<br /><br /> SQL_C_NUMERIC [b]<br /><br /> SQL_C_BIGINT [b]|間隔の有効桁数が 1 つのフィールドとデータを切り捨てることがなく変換されました<br /><br /> 間隔の有効桁数が 1 つのフィールドおよび全体に切り捨てられました。<br /><br /> 間隔の有効桁数が 1 つのフィールド|Data<br /><br /> 切り捨てられたデータ<br /><br /> 未定義。|C データ型のサイズ<br /><br /> バイト単位でデータの長さ<br /><br /> C データ型のサイズ|n/a<br /><br /> 22003<br /><br /> 22015|  
_C_BINARY|データのバイト長 < = *BufferLength*<br /><br /> データのバイト長 > *BufferLength*|Data<br /><br /> 未定義。|バイト単位でデータの長さ<br /><br /> 未定義。|n/a<br /><br /> 22003|  
|SQL_C_CHAR|バイトの長さを文字 < *BufferLength*<br /><br /> (ではなく小数部) 全体の数字の数 < *BufferLength*<br /><br /> (ではなく小数部) 全体の数字の数 > = *BufferLength*|Data<br /><br /> 切り捨てられたデータ<br /><br /> 未定義。|C データ型のサイズ<br /><br /> C データ型のサイズ<br /><br /> 未定義。|n/a<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|文字長 < *BufferLength*<br /><br /> (ではなく小数部) 全体の数字の数 < *BufferLength*<br /><br /> (ではなく小数部) 全体の数字の数 > = *BufferLength*|Data<br /><br /> 切り捨てられたデータ<br /><br /> 未定義。|C データ型のサイズ<br /><br /> C データ型のサイズ<br /><br /> 未定義。|n/a<br /><br /> 01004<br /><br /> 22003|  
  
 [a] A 年-月間隔 SQL 型は、任意の年-月間隔 C 型に変換できます。  
  
 [b] の間隔の有効桁数が 1 つのフィールド (年、月の 1 つ) の場合、SQL 型の間隔が、正確な numeric (SQL_C_STINYINT、SQL_C_UTINYINT、SQL_C_USHORT、SQL_C_SHORT、SQL_C_SLONG、SQL_C_ULONG、または SQL_C_NUMERIC) に変換できます。  
  
 間隔の SQL 型の既定の変換は、対応する C interval データ型です。 アプリケーション、列またはパラメーターをバインド (または、ARD の適切なレコードで、SQL_DESC_DATA_PTR フィールドを設定)、初期化された SQL_INTERVAL_STRUCT 構造体を指す (または、としてsql_INTERVAL_STRUCT構造体へのポインターを渡す*TargetValuePtr*への呼び出しで引数**SQLGetData**)。
