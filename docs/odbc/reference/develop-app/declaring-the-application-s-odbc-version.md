---
title: アプリケーションを宣言する&#39;s ODBC バージョン |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- declaring ODBC version [ODBC]
- data sources [ODBC], declaring ODBC version
- ODBC drivers [ODBC], declaring ODBC version
- connecting to driver [ODBC], declaring ODBC version
- connecting to data source [ODBC], declaring ODBC version
- version declaration [ODBC]
ms.assetid: 083a1ef5-580a-4979-9cf3-50f4549a080a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7c5bb124af74d1fa009a61237edb54a9c8baec74
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63267692"
---
# <a name="declaring-the-application39s-odbc-version"></a>アプリケーションを宣言する&#39;s ODBC のバージョン
アプリケーションが接続によって割り当てられる前に、SQL_ATTR_ODBC_VERSION 環境属性を設定があります。 この属性は、アプリケーションが ODBC 2 に従うことを示しています。*x*または ODBC 3 *。x*仕様、次のものを使用する場合。  
  
-   **SQLSTATEs**します。 多くの SQLSTATE 値は、ODBC 2 で異なります。*x*および ODBC 3 *。x*します。  
  
-   **日付、時刻、および Timestamp 型識別子**します。 次の表は、日付、時刻、および ODBC 2 のタイムスタンプ データの型識別子を示します。*x*および ODBC 3 *。x*します。  
  
    |ODBC 2。*x*|ODBC 3。*x*|  
    |----------------|----------------|  
    |**SQL の型識別子**||  
    |SQL_DATE|SQL_TYPE_DATE|  
    |SQL_TIME|SQL_TYPE_TIME|  
    |SQL_TIMESTAMP|SQL_TYPE_TIMESTAMP|  
    |**C 型識別子**||  
    |SQL_C_DATE|SQL_C_TYPE_DATE|  
    |SQL_C_TIME|SQL_C_TYPE_TIME|  
    |SQL_C_TIMESTAMP|SQL_C_TYPE_TIMESTAMP|  
  
-   _CatalogName_  **SQLTables 引数**します。 ODBC 2。*x*でワイルドカード文字 (「%」および「_」)、 *CatalogName*引数が文字どおり扱われます。 ODBC 3。*x*、ワイルドカード文字として扱われます。 したがって、ODBC 2 に依存するアプリケーション。*x*仕様ワイルドカード文字し、エスケープしないにそれらをリテラルとして使用する場合に使用これらにできません。 ODBC 3 に依存するアプリケーション。*x*仕様はまたはワイルドカード文字として使用して、エスケープする、およびリテラルとして使用します。 詳細については、次を参照してください。[カタログ関数の引数](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md)します。  
  
 ODBC 3 *.x*ドライバー マネージャーと ODBC 3 *.x*ドライバーは、アプリケーションの書き込み先となる、ODBC 仕様のバージョンを確認し、適宜応答します。 たとえば、次のように、アプリケーションには、ODBC 2 が後ろにある場合です。*x*仕様と呼び出し**SQLExecute**呼び出す前に**SQLPrepare**、ODBC 3 *.x*ドライバー マネージャーは、SQLSTATE S1010 (を返します関数シーケンス エラー) です。 アプリケーションが ODBC 3 に従う場合 *.x*仕様、ドライバー マネージャーは、SQLSTATE HY010 を返します (関数のシーケンス エラーです)。 詳細については、次を参照してください。[旧バージョンとの互換性と標準準拠](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md)します。  
  
> [!IMPORTANT]  
>  次の ODBC 3 アプリケーション。*x*仕様で条件付きのコードを使用して ODBC 3 に新しい機能を使用しないようにする必要があります *。x* ODBC 2 を使用する場合 *。x*ドライバー。 ODBC 2。*x*ドライバーは ODBC 3 に新しい機能をサポートしていません *。x*いって、アプリケーションが ODBC 3 に従っていることを宣言します *。x*仕様。 さらに、ODBC 3。*x*ドライバーは ODBC 3 に新しい機能をサポートするためを停止していません *。x*いって、アプリケーションは、ODBC 2 に従っていることを宣言します *。x*仕様。
