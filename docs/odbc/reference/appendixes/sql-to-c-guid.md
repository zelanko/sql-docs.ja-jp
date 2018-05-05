---
title: 'SQL には、c: GUID |Microsoft ドキュメント'
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
- converting data from SQL to C types [ODBC], GUID
- data conversions from SQL to C types [ODBC], guid
- GUID data type [ODBC]
ms.assetid: cf56c684-c261-4b89-994a-db14ab2241d6
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bff530732652d76d04ec6c0088b4563f38ea5877
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sql-to-c-guid"></a>SQL には、c: GUID
GUID の ODBC SQL データ型の識別子です。  
  
 SQL_GUID  
  
 次の表は、ODBC C データ型の GUID の SQL データを変換することがありますを示します。 列とテーブルの用語の詳細については、次を参照してください。[に変換するデータを SQL から C データ型に](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)です。  
  
|C 型識別子|テスト|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|*BufferLength* > バイトの長さを文字|Data|36|n/a|  
||*BufferLength* < 37|未定義。|未定義。|22003|  
|SQL_C_WCHAR|*BufferLength* > 文字長|Data|36|n/a|  
||*BufferLength* < 37|未定義。|未定義。|22003|  
|SQL_C_BINARY|データのバイト長\< =  *BufferLength*|Data|バイト単位でデータの長さ|n/a|  
||データのバイト長 > *BufferLength*|未定義。|未定義。|22003|  
|SQL_C_GUID|[A] [なし]|Data|16 [b]|n/a|  
  
 [a] の値*BufferLength*この変換では無視されます。 ドライバーでのサイズ **TargetValuePtr* C データ型のサイズです。  
  
 [b] これは、対応する C データ型のサイズです。
