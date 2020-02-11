---
title: SQL 準拠レベル (ODBC Driver for Oracle) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- conformance levels [ODBC], SQL
- SQL conformance levels [ODBC]
- ODBC driver for Oracle [ODBC], conformance levels
ms.assetid: 077a6c6a-2c57-42c9-a4fd-4cf0e65cf7e2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 241f4f3da12f63c15d917a0e47cb13ad0e96e6e3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68063355"
---
# <a name="sql-conformance-levels-odbc-driver-for-oracle"></a>SQL への準拠レベル (ODBC Driver for Oracle)
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows では削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用してください。  
  
 ODBC Driver for Oracle では、sql の構文とコアの SQL 文法がサポートされています。また、次の ODBC 拡張機能もサポートされています。  
  
-   日付、時刻、およびタイムスタンプデータ  
  
-   左外部結合と右外部結合  
  
-   数値関数:  
  
    |||||  
    |-|-|-|-|  
    |Abs|ログ|round|tan|  
    |Ceiling|Log10|second|切捨て|  
    |Cos|Mod|署名||  
    |Exp|Pi|sin||  
    |床|累乗|sqrt||  
  
-   日付関数:   
  
    |||||  
    |-|-|-|-|  
    |Curdate|Dayofweek|monthname|second|  
    |Curtime|Dayofyear|minute|week|  
    |Dayname|時|now|year|  
    |Dayofmonth|月|quarter||  
  
-   文字列関数:   
  
    |||||  
    |-|-|-|-|  
    |Ascii|Left|right|ucase|  
    |Char|Length|rtrim||  
    |Concat|Ltrim|soundex||  
    |Lcase|Replace|substring||  
  
-   型変換関数:  
  
    ||  
    |-|  
    |Convert|  
  
-   システム関数:  
  
    ||  
    |-|  
    |Ifnull|  
    |User|
