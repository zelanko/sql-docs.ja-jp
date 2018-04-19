---
title: 'SQL には、c: 時間 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- converting data from SQL to C types [ODBC], time
- time data type [ODBC]
- data conversions from SQL to C types [ODBC], time
ms.assetid: 6dc59973-7bb5-40f1-87c8-5bf68b3bf2ee
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6f8db10d126eab69546b2d81eaf4d93743a63238
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sql-to-c-time"></a>SQL には、c: 時刻
ODBC SQL データ型は、時間の識別子。  
  
 SQL_TYPE_TIME  
  
 次の表は、ODBC C データ型が time SQL データを変換することがありますを示します。 列とテーブルの用語の詳細については、次を参照してください。[に変換するデータを SQL から C データ型に](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)です。  
  
|C 型識別子|テスト|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|*BufferLength* > バイトの長さを文字<br /><br /> *9* <= *BufferLength* < 文字バイトの長さを =<br /><br /> *BufferLength* < 9|Data<br /><br /> [A] 切り捨てられたデータ<br /><br /> 未定義。|バイト単位でデータの長さ<br /><br /> バイト単位でデータの長さ<br /><br /> 未定義。|n/a<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|*BufferLength* > 文字長<br /><br /> *9* <= *BufferLength* < 文字の長さを =<br /><br /> *BufferLength* < 9|Data<br /><br /> [A] 切り捨てられたデータ<br /><br /> 未定義。|データの文字の長さ<br /><br /> データの文字の長さ<br /><br /> 未定義。|n/a<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_BINARY|データのバイト長 < = *BufferLength*<br /><br /> データのバイト長 > *BufferLength*|Data<br /><br /> 未定義。|バイト単位でデータの長さ<br /><br /> 未定義。|n/a<br /><br /> 22003|  
|SQL_C_TYPE_TIME|[なし]: [b]|Data|6 [d]|n/a|  
|SQL_C_TYPE_TIMESTAMP|[なし]: [b]|データ [c]|16 [d]|n/a|  
  
 [a] の時刻の秒の小数部が切り捨てられます。  
  
 [b] の値*BufferLength*この変換では無視されます。 ドライバーでのサイズ **TargetValuePtr* C データ型のサイズです。  
  
 [タイムスタンプの構造体の場合は、c] の日付フィールドが現在の日付に設定し、タイムスタンプの構造体の秒の小数部のフィールドが 0 に設定します。  
  
 [d] これは、対応する C データ型のサイズです。  
  
 時間 SQL データが文字データに変換されると、結果の文字列は、"*hh*:*mm*:*ss*"の形式です。 この形式は Windows® 国設定の影響を受けません。
