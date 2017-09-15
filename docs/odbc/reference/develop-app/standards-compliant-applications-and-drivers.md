---
title: "標準に準拠したアプリケーションやドライバー |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- standards-compliant applications and drivers [ODBC]
- ODBC drivers [ODBC], standards-compliant
- application features are standards-compliant [ODBC]
ms.assetid: a1145c4c-3094-4f3f-8cc2-e6bb1a930ab1
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1aba299d163aaf9ec14d86740e5d8aa91ddb7b3b
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="standards-compliant-applications-and-drivers"></a>標準に準拠したアプリケーションやドライバー
標準に準拠したアプリケーションやドライバーは、オープンなグループ CAE 仕様"データ管理:: SQL 呼び出しレベル インターフェイス (CLI)"と ISO/IEC 9075 に準拠している 1 つの 3:1995 (E) 呼び出しレベルのインターフェイス (SQL/CLI)。  
  
 ODBC 3*.x*次の機能を保証します。  
  
-   Open Group および ISO CLI 仕様に記述されたアプリケーションは、ODBC 3 の使用*.x*ドライバーまたは ODBC 3 では、コンパイル時の標準に準拠したドライバー*.x*ヘッダー ファイルし、リンクODBC 3*.x*ライブラリ、ドライバーは ODBC 3 へのアクセスを得る場合および*.x*ドライバー マネージャー。  
  
-   Open Group および ISO CLI 仕様に記述されたドライバーは ODBC 3 では機能*.x*アプリケーションまたは ODBC 3 では、コンパイル時の標準に準拠したアプリケーション*.x*ヘッダー ファイルし、リンクODBC 3*.x*ライブラリ、ODBC 3 を使用してドライバー、アプリケーションがアクセスおよび*.x*ドライバー マネージャー。  
  
 ODBC_STD コンパイル フラグでは、標準に準拠したアプリケーションやドライバーがコンパイルされます。  
  
 標準に準拠したアプリケーションでは、次の動作が発生します。  
  
-   標準に準拠したアプリケーションを呼び出す場合**SQLAllocEnv** (ために発生する**SQLAllocEnv** Open Group および ISO CLI で有効な関数は、)、呼び出しにマップされて**SQLAllocHandleStd**コンパイル時にします。 その結果、実行時に、アプリケーションが呼び出す**SQLAllocHandleStd**です。 この呼び出しを処理中に、ドライバー マネージャーはまた環境属性を SQL_OV_ODBC3 に設定します。 呼び出し**SQLAllocHandleStd**への呼び出しに相当**SQLAllocHandle**で、 *HandleType* SQL_HANDLE_ENV とへの呼び出しの**SQLSetEnvAttr**またを SQL_OV_ODBC3 に設定します。  
  
-   標準に準拠したアプリケーションを呼び出す場合**SQLBindParam** (ために発生する**SQLBindParam** Open Group および ISO CLI で有効な関数は、)、ODBC 3*.x*ドライバー マネージャーで、同等の呼び出しへの呼び出しをマップする**SQLBindParameter**です。 (を参照してください[SQLBindParam マッピング](../../../odbc/reference/appendixes/sqlbindparam-mapping.md)旧バージョンとの互換性のための付録 g: ドライバーのガイドライン」にします)。  
  
-   ISO CLI、ODBC 3 に合うように*.x*ヘッダー ファイルへの呼び出しで使用される情報の型のエイリアスを含める**SQLGetInfo**です。 標準に準拠したアプリケーションは、これらの別名を使用して、ODBC 3 ではなく*.x*情報の種類。 詳細については、次のトピックを参照してください。[ヘッダー ファイル](../../../odbc/reference/develop-app/header-files.md)です。  
  
-   標準に準拠したアプリケーションでは、サポートするすべての機能は、ドライバーでは動作でサポートされていることを確認してください。 SQL_SCROLLABLE と設定に SQL_ATTR_CURSOR_SCROLLABLE ステートメント属性を設定する SQL_INSENSITIVE または SQL_SENSITIVE SQL_ATTR_CURSOR_SENSITIVITY ステートメント属性は、標準のオプション機能として利用可能な機能ODBC 3 に含まれていませんが、*.x*コア レベルおよび可能性がありますでサポートされていないすべての ODBC 3*.x*ドライバー。 標準に準拠したアプリケーションでは、これらの機能を使用する場合、ドライバーでは動作をサポートしていることを確認する必要があります。
