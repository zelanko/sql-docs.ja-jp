---
title: SQL 準拠レベル (Oracle 用 ODBC ドライバ) |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e283bbc13f0d0dda055b047b027f7b9816502df5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300682"
---
# <a name="sql-conformance-levels-odbc-driver-for-oracle"></a>SQL への準拠レベル (ODBC Driver for Oracle)
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 Oracle 用 ODBC ドライバーは、最小 SQL 文法とコア SQL 文法をサポートし、SQL に次の ODBC 拡張機能もサポートします。  
  
-   日付、時刻、およびタイムスタンプのデータ  
  
-   左と右の外部結合  
  
-   数値関数:  
  
    |||||  
    |-|-|-|-|  
    |Abs|ログ|round|tan|  
    |Ceiling|Log10|second|切り捨て|  
    |Cos|Mod|署名||  
    |Exp|Pi|sin||  
    |床|Power|sqrt||  
  
-   日付関数:   
  
    |||||  
    |-|-|-|-|  
    |カーデート|Dayofweek|月名|second|  
    |キュタイム|Dayofyear|minute|week|  
    |日名|時|now|year|  
    |デイオブマンス|月|quarter||  
  
-   文字列関数:   
  
    |||||  
    |-|-|-|-|  
    |Ascii|Left|right|ウケース|  
    |Char|長さ|rtrim||  
    |Concat|Ltrim|Soundex||  
    |Lcase|Replace|substring||  
  
-   型変換関数:  
  
    ||  
    |-|  
    |Convert|  
  
-   システム機能:  
  
    ||  
    |-|  
    |ifnull|  
    |User|
