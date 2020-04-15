---
title: 'SQL から C: タイムスタンプ |マイクロソフトドキュメント'
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- timestamp data type [ODBC]
- converting data from SQL to C types [ODBC], timestamp
- data conversions from SQL to C types [ODBC], timestamp
ms.assetid: 6a0617cf-d8c0-4316-8bb4-e6ddb45d7bf1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 552bab585e4480fd922c9b9a6b112830f5c11ad9
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296352"
---
# <a name="sql-to-c-timestamp"></a>SQL から C へ: Timestamp

タイムスタンプ ODBC SQL データ型の識別子は次のとおりです。

- SQL_TYPE_TIMESTAMP  

次の表は、タイムスタンプ SQL データを変換できる ODBC C データ型を示しています。 表の列と用語の説明については[、SQL から C データ型へのデータの変換を参照してください](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)。  

|C 型識別子|テスト|**ターゲット値Ptr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|*バッファー長>* 文字バイト長<br /><br /> 20 <=*バッファー長*<= 文字バイト長<br /><br /> *バッファ長<* 20|Data<br /><br /> 切り捨てられたデータ[b]<br /><br /> 未定義。|データの長さ (バイト単位)<br /><br /> データの長さ (バイト単位)<br /><br /> 未定義。|該当なし<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|*バッファ長>* 文字長<br /><br /> 20 <=*バッファ長*<= 文字長<br /><br /> *バッファ長<* 20|Data<br /><br /> 切り捨てられたデータ[b]<br /><br /> 未定義。|文字でのデータの長さ<br /><br /> 文字でのデータの長さ<br /><br /> 未定義。|該当なし<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_BINARY|データ長のバイト長<=*バッファ長*<br /><br /> データのバイト長 >*バッファ長*|Data<br /><br /> 未定義。|データの長さ (バイト単位)<br /><br /> 未定義。|該当なし<br /><br /> 22003|  
|SQL_C_TYPE_DATE|タイムスタンプの時間部分はゼロです[a]<br /><br /> タイムスタンプの時間部分が 0 でない場合[a]|Data<br /><br /> 切り捨てられたデータ[c]|6[f]<br /><br /> 6[f]|該当なし<br /><br /> 01S07|  
|SQL_C_TYPE_TIME|タイムスタンプの秒の小数部分はゼロです[a]<br /><br /> タイムスタンプの秒の小数部分が 0 でない[a]|データ [d]<br /><br /> 切り捨てられたデータ [d] , [e]|6[f]<br /><br /> 6[f]|該当なし<br /><br /> 01S07|  
|SQL_C_TYPE_TIMESTAMP|タイムスタンプの秒の小数部分は切り捨てられない[a]<br /><br /> タイムスタンプの秒の小数部分が切り捨てられます[a]|データ[e]<br /><br /> 切り捨てられたデータ[e]|16[f]<br /><br /> 16[f]|該当なし<br /><br /> 01S07|  

 [a] この変換では *、BufferLength*の値は無視されます。 ドライバーは、**ターゲット値Ptr*のサイズは、Cデータ型のサイズであると仮定します。  
  
 [b] タイムスタンプの秒数の小数秒が切り捨てられます。  
  
 [c] タイムスタンプの時間部分が切り捨てられる。  
  
 [d] タイムスタンプの日付部分は無視されます。  
  
 [e] タイムスタンプの秒の小数部分が切り捨てられます。  
  
 [f] これは、対応する C データ型のサイズです。  

タイムスタンプの SQL データが文字 C データに変換されると、結果の文字列は "*yyyy*-*mm*-*dd* *hh*:*mm*:*ss*[ ] に格納されます。*f..*[]小数点以下の秒数に対して最大 9 桁の数字を使用できます。 この形式は、Windows®国の設定の影響を受けません。 (小数点と秒の小数を除き、タイムスタンプの SQL データ・タイプの精度に関係なく、フォーマット全体を使用する必要があります。
