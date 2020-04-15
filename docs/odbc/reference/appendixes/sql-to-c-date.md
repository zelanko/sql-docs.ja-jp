---
title: 'SQL から C: 日付 |マイクロソフトドキュメント'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from SQL to C types [ODBC], date
- date data type [ODBC]
- data conversions from SQL to C types [ODBC], date
ms.assetid: 703c7960-9cf4-4d7a-9920-53b29c184f97
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fe9656c0c02c0ff5a10029525da3d38280530cc3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296532"
---
# <a name="sql-to-c-date"></a>SQL から C へ: Date
日付 ODBC SQL データ型の識別子は次のとおりです。  
  
 SQL_TYPE_DATE  
  
 次の表は、SQL データを変換できる日付の ODBC C データ型を示しています。 表の列と用語の説明については[、SQL から C データ型へのデータの変換を参照してください](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)。  
  
|C 型識別子|テスト|**ターゲット値Ptr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|*バッファー長>* 文字バイト長<br /><br /> 11 <=*バッファ長*<= 文字バイト長<br /><br /> *バッファー長<* 11|Data<br /><br /> 切り捨てられたデータ<br /><br /> 未定義。|10<br /><br /> データの長さ (バイト単位)<br /><br /> 未定義。|該当なし<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|*バッファ長>* 文字長<br /><br /> 11 <=*バッファー長*<= 文字長<br /><br /> *バッファー長<* 11|Data<br /><br /> 切り捨てられたデータ<br /><br /> 未定義。|10<br /><br /> 文字でのデータの長さ<br /><br /> 未定義。|該当なし<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_BINARY|データ長のバイト長<=*バッファ長*<br /><br /> データのバイト長 >*バッファ長*|Data<br /><br /> 未定義。|データの長さ (バイト単位)<br /><br /> 未定義。|該当なし<br /><br /> 22003|  
|SQL_C_TYPE_DATE|なし[a]|Data|6[c]|該当なし|  
|SQL_C_TYPE_TIMESTAMP|なし[a]|データ[b]|16[c]|該当なし|  
  
 [a] この変換では *、BufferLength*の値は無視されます。 ドライバーは、**ターゲット値Ptr*のサイズは、Cデータ型のサイズであると仮定します。  
  
 [b] タイムスタンプ構造体の時間フィールドがゼロに設定されている。  
  
 [c] これは、対応する C データ型のサイズです。  
  
 日付 SQL データが文字 C データに変換されると、結果の文字列は "*yyyy*-*mm*-*dd*" 形式になります。 この形式は、Windows®国の設定の影響を受けません。
