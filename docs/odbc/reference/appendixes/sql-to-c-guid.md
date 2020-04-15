---
title: 'C への SQL: GUID |マイクロソフトドキュメント'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from SQL to C types [ODBC], GUID
- data conversions from SQL to C types [ODBC], guid
- GUID data type [ODBC]
ms.assetid: cf56c684-c261-4b89-994a-db14ab2241d6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f0f247bc4cb411d535050d7c78e0ea42cc144b0e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296462"
---
# <a name="sql-to-c-guid"></a>SQL から C へ: GUID
ODBC SQL データ型の識別子は次のとおりです。  
  
 SQL_GUID  
  
 次の表は、GUID SQL データの変換先となる ODBC C データ型を示しています。 表の列と用語の説明については[、SQL から C データ型へのデータの変換を参照してください](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)。  
  
|C 型識別子|テスト|**ターゲット値Ptr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|*バッファー長>* 文字バイト長|Data|36|該当なし|  
||*バッファ長<* 37|未定義。|未定義。|22003|  
|SQL_C_WCHAR|*バッファ長>* 文字長|Data|36|該当なし|  
||*バッファ長<* 37|未定義。|未定義。|22003|  
|SQL_C_BINARY|データ\<= バッファ長のバイト*長*|Data|データの長さ (バイト単位)|該当なし|  
||データのバイト長 >*バッファ長*|未定義。|未定義。|22003|  
|SQL_C_GUID|なし[a]|Data|16[b]|該当なし|  
  
 [a] この変換では *、BufferLength*の値は無視されます。 ドライバーは、**ターゲット値Ptr*のサイズは、Cデータ型のサイズであると仮定します。  
  
 [b] これは、対応する C データ型のサイズです。
