---
title: 'C から SQL へ: 年-月間隔 |Microsoft ドキュメント'
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
- converting data from c to SQL types [ODBC], year-month intervals
- intervals [ODBC], converting
- year-month intervals [ODBC]
- data conversions from C to SQL types [ODBC], year-month intervals
ms.assetid: a0eb7b55-9db0-4375-9210-bddec4593880
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 26645ddb4e27335a33aec88f002764d20da3d936
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="c-to-sql-year-month-intervals"></a>C から SQL へ: 年-月間隔
年、月間隔 ODBC C データ型の識別子は次のとおりです。  
  
 SQL_C_INTERVAL_MONTH SQL_C_INTERVAL_YEAR SQL_C_INTERVAL_YEAR_TO_MONTH  
  
 次の表は、ODBC SQL データ型の年-月する間隔 C データに変換することがありますを示します。 列とテーブルの用語の詳細については、次を参照してください。[に変換するデータを C から SQL データ型を](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md)です。  
  
|SQL 型の識別子|テスト|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR [a]<br /><br /> [A] SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR [a]|列のバイト長 > 文字バイトの長さを =<br /><br /> 列のバイト長 < 文字バイト長 [a]<br /><br /> データ値はリテラルの有効な間隔ではありません。|n/a<br /><br /> 22001<br /><br /> 22015|  
|[A] の SQL_WCHAR<br /><br /> SQL_WVARCHAR [a]<br /><br /> [A] SQL_WLONGVARCHAR|列の文字の長さ > データの文字の長さを =<br /><br /> 列の文字の長さ < [a] のデータの長さを文字<br /><br /> データ値はリテラルの有効な間隔ではありません。|n/a<br /><br /> 22001<br /><br /> 22015|  
|SQL_TINYINT [b]<br /><br /> SQL_SMALLINT [b]<br /><br /> SQL_INTEGER [b]<br /><br /> SQL_BIGINT [b]<br /><br /> SQL_NUMERIC [b]<br /><br /> SQL_DECIMAL [b]|単一フィールド間隔の変換は、全体の桁数の切り捨てを実行できませんでした。<br /><br /> 変換の結果が全体の桁数の切り捨て|n/a<br /><br /> 22003|  
|SQL_INTERVAL_MONTH<br /><br /> SQL_INTERVAL_YEAR<br /><br /> SQL_INTERVAL_YEAR_TO_MONTH|データ値がすべてのフィールドが切り詰めなしに変換されました<br /><br /> 変換中にデータ値の 1 つまたは複数のフィールドが切り詰められました|n/a<br /><br /> 22015|  
  
 [a] のすべての C interval データ型は、文字データ型に変換できます。  
  
 [b] 間隔構造体の型のフィールドが、間隔が 1 つのフィールド (SQL_YEAR または SQL_MONTH) の場合、C の間隔の種類が、正確な numeric (SQL_TINYINT、SQL_SMALLINT、SQL_INTEGER、SQL_BIGINT、SQL_DECIMAL、または SQL_NUMERIC) に変換できます。  
  
 C 型の間隔の既定の変換は、対応する年-月間隔 SQL 型にです。  
  
 ドライバーは、間隔 C データ型からデータを変換するときに長さ/インジケーター値を無視し、データ バッファーのサイズが間隔 C データ型のサイズであると見なされます。 長さ/インジケーター値に渡されます、 *StrLen_or_Ind*引数**SQLPutData**とで指定したバッファー内の*StrLen_or_IndPtr* で引数**SQLBindParameter**です。 データ バッファーを指定した、 *DataPtr*引数**SQLPutData**と*ParameterValuePtr*引数**SQLBindParameter**.
