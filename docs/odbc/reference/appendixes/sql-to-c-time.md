---
title: 'SQL から C: 時間 |マイクロソフトドキュメント'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from SQL to C types [ODBC], time
- time data type [ODBC]
- data conversions from SQL to C types [ODBC], time
ms.assetid: 6dc59973-7bb5-40f1-87c8-5bf68b3bf2ee
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ebd146abf650861099a40bf91b2641df768b343d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296382"
---
# <a name="sql-to-c-time"></a>SQL から C へ: Time
時刻 ODBC SQL データ型の識別子は次のとおりです。  
  
 SQL_TYPE_TIME  
  
 次の表は、SQL データの変換後の ODBC C データ型を示しています。 表の列と用語の説明については[、SQL から C データ型へのデータの変換を参照してください](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)。  
  
|C 型識別子|テスト|**ターゲット値Ptr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|*バッファー長>* 文字バイト長<br /><br /> *9* <= *バッファ長<* = 文字バイト長<br /><br /> *バッファ長<* 9|Data<br /><br /> 切り捨てられたデータ[a]<br /><br /> 未定義。|データの長さ (バイト単位)<br /><br /> データの長さ (バイト単位)<br /><br /> 未定義。|該当なし<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|*バッファ長>* 文字長<br /><br /> *9* <= *バッファ長<* = 文字長<br /><br /> *バッファ長<* 9|Data<br /><br /> 切り捨てられたデータ[a]<br /><br /> 未定義。|文字でのデータの長さ<br /><br /> 文字でのデータの長さ<br /><br /> 未定義。|該当なし<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_BINARY|データ長のバイト長<=*バッファ長*<br /><br /> データのバイト長 >*バッファ長*|Data<br /><br /> 未定義。|データの長さ (バイト単位)<br /><br /> 未定義。|該当なし<br /><br /> 22003|  
|SQL_C_TYPE_TIME|なし[b]|Data|6 [d]|該当なし|  
|SQL_C_TYPE_TIMESTAMP|なし[b]|データ[c]|16[d]|該当なし|  
  
 [a] 時間の秒数の小数部が切り捨てられます。  
  
 [b] この変換では *、BufferLength*の値は無視されます。 ドライバーは、**ターゲット値Ptr*のサイズは、Cデータ型のサイズであると仮定します。  
  
 [c] タイムスタンプ構造の日付フィールドは現在の日付に設定され、タイムスタンプ構造の秒の小数部フィールドはゼロに設定されます。  
  
 [d] これは、対応する C データ型のサイズです。  
  
 TIME SQL データが文字 C データに変換されるとき、結果の文字列は "*hh*:*mm*:*ss*" 形式になります。 この形式は、Windows®国の設定の影響を受けません。
