---
title: SQL への準拠レベル (ODBC Driver for Oracle) |Microsoft ドキュメント
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
- conformance levels [ODBC], SQL
- SQL conformance levels [ODBC]
- ODBC driver for Oracle [ODBC], conformance levels
ms.assetid: 077a6c6a-2c57-42c9-a4fd-4cf0e65cf7e2
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6f5937271f1a3e4f42b5c2f3105eadbecd0dc87c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sql-conformance-levels-odbc-driver-for-oracle"></a>SQL への準拠レベル (ODBC Driver for Oracle)
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 ODBC Driver for Oracle では、Minimum SQL 文法と Core SQL 文法をサポートし、SQL に次の ODBC 拡張機能をサポートします。  
  
-   日付、時刻、およびタイムスタンプのデータ  
  
-   左と右外部結合  
  
-   数値関数の場合:  
  
    |||||  
    |-|-|-|-|  
    |Abs|Log|round|tan|  
    |Ceiling|log10 関数|second|truncate|  
    |Cos|Mod|サインイン||  
    |Exp|pi|sin||  
    |floor|Power|sqrt||  
  
-   日付関数:  
  
    |||||  
    |-|-|-|-|  
    |Curdate|dayofweek|monthname|second|  
    |Curtime|Dayofyear|minute|week|  
    |Dayname|Hour|今|year|  
    |dayofmonth|Month|四半期||  
  
-   文字列関数。  
  
    |||||  
    |-|-|-|-|  
    |ascii|Left|right|ucase|  
    |Char|長さ|rtrim||  
    |Concat|Ltrim|soundex||  
    |Lcase|[置換]|substring||  
  
-   型変換関数。  
  
    ||  
    |-|  
    |[変換]|  
  
-   システム関数:  
  
    ||  
    |-|  
    |見つかれば|  
    |ユーザー|
