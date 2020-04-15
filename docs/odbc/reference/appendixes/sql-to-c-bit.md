---
title: 'Sql から C: ビット |マイクロソフトドキュメント'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from SQL to c types [ODBC], bit
- bit data type [ODBC]
- data conversions from SQL to C types [ODBC], bit
ms.assetid: 0eeaab8b-ad82-4a36-b464-9a1211d5f72c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 57688f34c504b221f77c1b66792bf9ee9398df27
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296752"
---
# <a name="sql-to-c-bit"></a>SQL から C へ: bit
ビット ODBC SQL データ型の識別子は次のとおりです。  
  
 SQL_BIT  
  
 次の表は、ビット SQL データの変換先となる ODBC C データ型を示しています。 表の列と用語の説明については[、SQL から C データ型へのデータの変換を参照してください](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)。  
  
|C 型識別子|テスト|**ターゲット値Ptr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR<br /><br /> SQL_C_WCHAR|*バッファ長>* 1<br /><br /> *バッファ長<* = 1|Data<br /><br /> 未定義。|1<br /><br /> 未定義。|該当なし<br /><br /> 22003|  
|SQL_C_STINYINT<br /><br /> SQL_C_UTINYINT<br /><br /> SQL_C_TINYINT<br /><br /> SQL_C_SBIGINT<br /><br /> SQL_C_UBIGINT<br /><br /> SQL_C_SSHORT<br /><br /> SQL_C_USHORT<br /><br /> SQL_C_SHORT<br /><br /> SQL_C_SLONG<br /><br /> SQL_C_ULONG<br /><br /> SQL_C_LONG<br /><br /> SQL_C_FLOAT<br /><br /> SQL_C_DOUBLE<br /><br /> SQL_C_NUMERIC|なし[a]|Data|C データ型のサイズ|該当なし|  
|SQL_C_BIT|なし[a]|Data|1[b]|該当なし|  
|SQL_C_BINARY|*バッファ長>* = 1<br /><br /> *バッファ長<* 1|Data<br /><br /> 未定義。|1<br /><br /> 未定義。|該当なし<br /><br /> 22003|  
  
 [a] この変換では *、BufferLength*の値は無視されます。 ドライバーは、**ターゲット値Ptr*のサイズは、Cデータ型のサイズであると仮定します。  
  
 [b] これは、対応する C データ型のサイズです。  
  
 ビット SQL データが文字 C データに変換される場合、可能な値は "0" と "1" です。
