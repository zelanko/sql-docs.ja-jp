---
title: 'SQL から c: GUID |Microsoft Docs'
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 21054bdb3f869a0f06349b32e481144b3582de4e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47849000"
---
# <a name="sql-to-c-guid"></a>SQL から C へ: GUID
GUID の ODBC SQL データ型の識別子です。  
  
 SQL_GUID  
  
 次の表は、ODBC C データ型の GUID の SQL データを変換する可能性がありますを示します。 列とテーブルの用語の詳細については、次を参照してください。 [SQL から C データ型への変換データ](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)します。  
  
|C 型識別子|テスト|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|*BufferLength* > バイト長の文字|data|36|n/a|  
||*BufferLength* < 37|未定義。|未定義。|22003|  
|SQL_C_WCHAR|*BufferLength* > 文字長|data|36|n/a|  
||*BufferLength* < 37|未定義。|未定義。|22003|  
|SQL_C_BINARY|データのバイト長\< =  *BufferLength*|data|バイト単位でデータの長さ|n/a|  
||データのバイト長 > *BufferLength*|未定義。|未定義。|22003|  
|SQL_C_GUID|[A] [なし]|data|16 [b]|n/a|  
  
 [a] の値*BufferLength*この変換は無視されます。 ドライバーでのサイズ **TargetValuePtr* C データ型のサイズです。  
  
 [b] これは、対応する C データ型のサイズです。
