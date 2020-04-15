---
title: アプリケーションの宣言&#39;ODBC バージョン |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ba346ed7f7a261446110c5513026d20a86fd3a19
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285232"
---
# <a name="declaring-the-application39s-odbc-version"></a>アプリケーションの宣言&#39;ODBC バージョン
アプリケーションは、接続を割り当てる前に、SQL_ATTR_ODBC_VERSION環境属性を設定する必要があります。 この属性は、次の項目を使用する場合、アプリケーションが ODBC *2.x*または ODBC *3.x*仕様に従っていることを示します。  
  
-   **SQLSTATE .** ODBC *2.x*と ODBC *3.x*では、多くの SQLSTATE 値が異なります。  
  
-   **日付、時刻、およびタイムスタンプの種類の識別子**。 次の表は、ODBC *2.x*および ODBC *3.x*の日付、時刻、およびタイムスタンプデータの型識別子を示しています。  
  
    |ODBC *2.x*|ODBC *3.x*|  
    |----------------|----------------|  
    |**SQL の型識別子**||  
    |SQL_DATE|SQL_TYPE_DATE|  
    |SQL_TIME|SQL_TYPE_TIME|  
    |SQL_TIMESTAMP|SQL_TYPE_TIMESTAMP|  
    |**C 型識別子**||  
    |SQL_C_DATE|SQL_C_TYPE_DATE|  
    |SQL_C_TIME|SQL_C_TYPE_TIME|  
    |SQL_C_TIMESTAMP|SQL_C_TYPE_TIMESTAMP|  
  
-   _SQLTables のカタログ名_  **引数**。 ODBC *2.x*では、*引数 CatalogName*のワイルドカード文字 ("%" と "_") は、文字どおり扱われます。 ODBC *3.x*では、ワイルドカード文字として扱われます。 したがって、ODBC *2.x*仕様に従うアプリケーションでは、これらをワイルドカード文字として使用することはできず、リテラルとして使用する場合はエスケープされません。 ODBC *3.x*仕様に従うアプリケーションでは、これらをワイルドカード文字として使用するか、エスケープしてリテラルとして使用できます。 詳細については、「[カタログ関数の引数](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md)」を参照してください。  
  
 ODBC *3.x*ドライバー マネージャーと ODBC *3.x*ドライバーは、アプリケーションが書き込まれる ODBC 仕様のバージョンを確認し、それに応じて応答します。 たとえば、アプリケーションが ODBC *2.x*仕様に従い **、SQLPrepare**を呼び出す前に**SQLExecute**を呼び出すと、ODBC *3.x*ドライバー マネージャーは SQLSTATE S1010 (関数シーケンス エラー) を返します。 アプリケーションが ODBC *3.x*仕様に従っている場合、ドライバー マネージャーは SQLSTATE HY010 (関数シーケンス エラー) を返します。 詳細については、「[下位互換性と標準準拠](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md)」を参照してください。  
  
> [!IMPORTANT]  
>  ODBC *3.x*仕様に従うアプリケーションでは、ODBC *2.x*ドライバーを操作するときに、ODBC *3.x*の新機能を使用しないように、条件付きコードを使用する必要があります。 ODBC *2.x*ドライバは、ODBC *3.x*仕様に従うことをアプリケーションが宣言したため、ODBC *3.x*の新機能をサポートしていません。 さらに、ODBC 3.x ドライバは、ODBC *2.x*仕様に従うことをアプリケーションが宣言したからといって、ODBC *3.x*の新機能をサポートすることを停止しません。 *2.x*
