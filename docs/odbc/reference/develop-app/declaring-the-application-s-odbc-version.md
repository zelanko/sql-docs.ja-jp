---
title: アプリケーションを宣言する&#39;s ODBC のバージョン |Microsoft ドキュメント
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
ms.topic: conceptual
helpviewer_keywords:
- declaring ODBC version [ODBC]
- data sources [ODBC], declaring ODBC version
- ODBC drivers [ODBC], declaring ODBC version
- connecting to driver [ODBC], declaring ODBC version
- connecting to data source [ODBC], declaring ODBC version
- version declaration [ODBC]
ms.assetid: 083a1ef5-580a-4979-9cf3-50f4549a080a
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 89e3363eeefaf85aa81c29266bdf565066c626a3
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="declaring-the-application39s-odbc-version"></a>アプリケーションを宣言する&#39;s ODBC のバージョン
アプリケーションにより、接続を割り当てる前にまた環境属性を設定する必要があります。 この属性は、アプリケーションが、ODBC 2 を準拠していることを示しています。*x*または ODBC 3 *。x*仕様、次の項目を使用する場合。  
  
-   **SQLSTATEs**です。 多くの SQLSTATE 値は、ODBC 2 で異なります。*x*および ODBC 3 *。x*です。  
  
-   **日付、時刻、および Timestamp 型識別子**です。 次の表は、日付、時刻、および ODBC 2 のタイムスタンプ データの型識別子を示します。*x*および ODBC 3 *。x*です。  
  
    |ODBC 2 です。*x*|ODBC 3 です。*x*|  
    |----------------|----------------|  
    |**SQL の型識別子**||  
    |SQL_DATE|SQL_TYPE_DATE|  
    |SQL_TIME|SQL_TYPE_TIME|  
    |SQL_TIMESTAMP|SQL_TYPE_TIMESTAMP|  
    |**C 型識別子**||  
    |SQL_C_DATE|SQL_C_TYPE_DATE|  
    |SQL_C_TIME|SQL_C_TYPE_TIME|  
    |SQL_C_TIMESTAMP|SQL_C_TYPE_TIMESTAMP|  
  
-   *CatalogName***SQLTables 引数**です。 ODBC 2 です。*x*中のワイルドカード文字 (「%」および「_」)、 *CatalogName*引数はリテラル扱われます。 ODBC 3 です。*x*、ワイルドカード文字として扱われます。 したがって、ODBC 2 に依存するアプリケーション。*x*仕様とワイルドカード文字をエスケープしませんにリテラルとして使用するときに使用これらにできません。 ODBC 3 に依存するアプリケーション。*x*仕様はまたはワイルドカード文字として使用して、エスケープする、およびリテラルとして使用します。 詳細については、次を参照してください。[カタログ関数の引数](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md)です。  
  
 ODBC 3 *.x*ドライバー マネージャーと ODBC 3 *.x*ドライバーは、アプリケーションの書き込み先となる、ODBC 仕様のバージョンを確認し、適宜対応します。 たとえば、次のように、アプリケーション、ODBC 2 に従う場合です。*x*仕様と呼び出し**SQLExecute**呼び出す前に**SQLPrepare**、ODBC 3 *.x*ドライバー マネージャーは、SQLSTATE S1010 (を返します関数のシーケンス エラー)。 アプリケーションが ODBC 3 に従う場合 *.x*仕様、ドライバー マネージャーが含む SQLSTATE HY010 を返します (関数のシーケンス エラーです)。 詳細については、次を参照してください。[旧バージョンとの互換性と標準の順守](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md)です。  
  
> [!IMPORTANT]  
>  ODBC 3 に続くアプリケーション。*x*仕様は、ODBC 3 に新しい機能を使用しないように条件付きのコードを使用する必要があります*。x* ODBC 2 を使用する場合*。x*ドライバー。 ODBC 2 です。*x*ドライバーでは、ODBC 3 に新しい機能をサポートしていません*。x*アプリケーションでは、ODBC 3 に従っていることを宣言からといって*。x*仕様です。 さらに、ODBC 3 です。*x*ドライバーは ODBC 3 に新しい機能をサポートするために停止されません*。x*アプリケーションでは、ODBC 2 に従っていることを宣言からといって*。x*仕様です。
