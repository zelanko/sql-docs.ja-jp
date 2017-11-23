---
title: "SQL には、c: GUID |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- converting data from SQL to C types [ODBC], GUID
- data conversions from SQL to C types [ODBC], guid
- GUID data type [ODBC]
ms.assetid: cf56c684-c261-4b89-994a-db14ab2241d6
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 070cb29ce9538e6b8d12eac2b8324c581b25bc83
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="sql-to-c-guid"></a>SQL には、c: GUID
GUID の ODBC SQL データ型の識別子です。  
  
 SQL_GUID  
  
 次の表は、ODBC C データ型の GUID の SQL データを変換することがありますを示します。 列とテーブルの用語の詳細については、次を参照してください。[に変換するデータを SQL から C データ型に](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)です。  
  
|C 型識別子|テスト|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|*BufferLength* > バイトの長さを文字|data|36|n/a|  
||*BufferLength* < 37|未定義。|未定義。|22003|  
|SQL_C_WCHAR|*BufferLength* > 文字長|data|36|n/a|  
||*BufferLength* < 37|未定義。|未定義。|22003|  
|SQL_C_BINARY|データのバイト長\< =  *BufferLength*|data|バイト単位でデータの長さ|n/a|  
||データのバイト長 > *BufferLength*|未定義。|未定義。|22003|  
|SQL_C_GUID|[A] [なし]|data|16 [b]|n/a|  
  
 [a] の値*BufferLength*この変換では無視されます。 ドライバーでのサイズ **TargetValuePtr* C データ型のサイズです。  
  
 [b] これは、対応する C データ型のサイズです。
