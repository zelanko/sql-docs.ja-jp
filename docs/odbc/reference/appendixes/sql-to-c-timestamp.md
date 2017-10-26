---
title: "SQL には、c: タイムスタンプ |Microsoft ドキュメント"
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
- timestamp data type [ODBC]
- converting data from SQL to C types [ODBC], timestamp
- data conversions from SQL to C types [ODBC], timestamp
ms.assetid: 6a0617cf-d8c0-4316-8bb4-e6ddb45d7bf1
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a551d51a434d17162a5f5bcf0091e593d25f283a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sql-to-c-timestamp"></a>SQL から c: Timestamp へ
ODBC SQL データ型 timestamp の識別子です。  
  
 SQL_TYPE_TIMESTAMP  
  
 次の表は、ODBC C SQL のタイムスタンプ データを変換できるデータ型を示します。 列とテーブルの用語の詳細については、次を参照してください。[に変換するデータを SQL から C データ型に](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)です。  
  
|C 型識別子|テスト|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|*BufferLength* > バイトの長さを文字<br /><br /> 20 < = *BufferLength* < 文字バイトの長さを =<br /><br /> *BufferLength* < 20|data<br /><br /> 切り捨てられたデータ [b]<br /><br /> 未定義。|バイト単位でデータの長さ<br /><br /> バイト単位でデータの長さ<br /><br /> 未定義。|n/a<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|*BufferLength* > 文字長<br /><br /> 20 < = *BufferLength* < 文字の長さを =<br /><br /> *BufferLength* < 20|data<br /><br /> 切り捨てられたデータ [b]<br /><br /> 未定義。|データの文字の長さ<br /><br /> データの文字の長さ<br /><br /> 未定義。|n/a<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_BINARY|データのバイト長 < = *BufferLength*<br /><br /> データのバイト長 > *BufferLength*|data<br /><br /> 未定義。|バイト単位でデータの長さ<br /><br /> 未定義。|n/a<br /><br /> 22003|  
|SQL_C_TYPE_DATE|タイムスタンプの時刻部分は 0 を [a]<br /><br /> タイムスタンプの時刻部分が 0 以外の値 [a]|data<br /><br /> 切り捨てられたデータ [c]|6 [f]<br /><br /> 6 [f]|n/a<br /><br /> 01S07|  
|SQL_C_TYPE_TIME|タイムスタンプの秒の小数部の部分は、0 を [a]<br /><br /> タイムスタンプの秒の小数部の部分では 0 以外の値 [a]|データ [d]<br /><br /> 切り捨てられたデータ [d]、[電子メール]|6 [f]<br /><br /> 6 [f]|n/a<br /><br /> 01S07|  
_C_TYPE_TIMESTAMP|タイムスタンプの秒部分の切り捨て [a]<br /><br /> タイムスタンプの秒部分の切り捨て [a]|データ [e]<br /><br /> 切り捨てられたデータ [e]|16 [f]<br /><br /> 16 [f]|n/a<br /><br /> 01S07|  
  
 [a] の値*BufferLength*この変換では無視されます。 ドライバーでのサイズ **TargetValuePtr* C データ型のサイズです。  
  
 [b] のタイムスタンプの秒の小数部が切り捨てられます。  
  
 [c]、タイムスタンプの時刻部分が切り詰められています。  
  
 [タイムスタンプの d] で、日付部分は無視されます。  
  
 [電子メール] タイムスタンプの秒部分は切り捨てられます。  
  
 [f] これは、対応する C データ型のサイズです。  
  
 SQL のタイムスタンプ データが文字データに変換されると、結果の文字列は、"*yyyy*-*mm*-*dd* *hh*:*mm*:*ss*[.*f.*]"形式、秒の小数部の最大 9 桁の数字を使用できます。 この形式は Windows® 国設定の影響を受けません。 (、小数点と秒の小数部を除く全体の書式設定する必要があります使用、timestamp SQL データ型の有効桁数に関係なく)。

