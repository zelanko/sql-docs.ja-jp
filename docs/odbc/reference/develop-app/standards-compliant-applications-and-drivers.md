---
title: 標準に準拠したアプリケーションとドライバー |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- standards-compliant applications and drivers [ODBC]
- ODBC drivers [ODBC], standards-compliant
- application features are standards-compliant [ODBC]
ms.assetid: a1145c4c-3094-4f3f-8cc2-e6bb1a930ab1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8937c2b9c80209975d03963acb19ab5da9c99e39
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47811340"
---
# <a name="standards-compliant-applications-and-drivers"></a>標準に準拠したアプリケーションとドライバー
標準に準拠したアプリケーションまたはドライバーが開いているグループ CAE 仕様"のデータ管理:: SQL コールレベル インターフェイス (CLI)、"と ISO/IEC 9075 に準拠している 1 つの 3:1995 (E) コールレベル インターフェイス (SQL/CLI)。  
  
 ODBC 3 *.x*で、次の機能が保証されます。  
  
-   Open Group および ISO CLI 仕様に記述されたアプリケーションは、ODBC 3 *.x*ドライバーまたは ODBC 3 でコンパイルされるときに、標準に準拠したドライバー *.x*ヘッダー ファイルし、リンクされています。ODBC 3 *.x*ライブラリ、ドライバーは ODBC 3 へのアクセスが得られますときと *.x*ドライバー マネージャー。  
  
-   Open Group および ISO CLI 仕様に記述されたドライバーは、ODBC 3 *.x*アプリケーションまたは ODBC 3 でコンパイルされるときに、標準に準拠したアプリケーションを *.x*ヘッダー ファイルし、リンクODBC 3 *.x*ライブラリ、ドライバーは ODBC 3 に、アプリケーションがアクセスおよび *.x*ドライバー マネージャー。  
  
 標準に準拠したアプリケーションとドライバーは、ODBC_STD コンパイル フラグを使用してコンパイルされます。  
  
 標準に準拠したアプリケーションが、次の動作があります。  
  
-   標準に準拠したアプリケーションから呼び出す場合**SQLAllocEnv** (ために発生する**SQLAllocEnv** 、Open Group と ISO CLI の有効な関数は、)、呼び出しにマップされて**SQLAllocHandleStd**コンパイル時にします。 その結果、実行時に、アプリケーション呼び出し**SQLAllocHandleStd**します。 この呼び出しの処理の中には、ドライバー マネージャーは SQL_ATTR_ODBC_VERSION 環境属性を SQL_OV_ODBC3 に設定します。 呼び出し**SQLAllocHandleStd**への呼び出しに相当**SQLAllocHandle**で、 *HandleType* sql_handle_env としてとへの呼び出しの**SQLSetEnvAttr**を SQL_ATTR_ODBC_VERSION を SQL_OV_ODBC3 に設定します。  
  
-   標準に準拠したアプリケーションから呼び出す場合**SQLBindParam** (ために発生する**SQLBindParam**は、Open Group と ISO CLI の有効な関数です)、ODBC 3 *.x*ドライバー マネージャーで同等の呼び出しへの呼び出しをマップする**SQLBindParameter**します。 (を参照してください[SQLBindParam のマッピング](../../../odbc/reference/appendixes/sqlbindparam-mapping.md)付録 g: ドライバーとの下位互換性のためのガイドラインにします)。  
  
-   ISO CLI、ODBC 3 とを連携させる *.x*ヘッダー ファイルへの呼び出しで使用される情報の種類の別名を含む**SQLGetInfo**します。 標準に準拠したアプリケーションは、これらの別名を使用して、ODBC 3 ではなく *.x*情報の種類。 詳細については、次のトピックを参照してください。[ヘッダー ファイル](../../../odbc/reference/develop-app/header-files.md)します。  
  
-   標準に準拠したアプリケーションで動作するドライバーでサポートするすべての機能がサポートされていることを確認してください。 SQL_SCROLLABLE と設定を SQL_ATTR_CURSOR_SCROLLABLE ステートメント属性を設定 SQL_INSENSITIVE または SQL_SENSITIVE SQL_ATTR_CURSOR_SENSITIVITY ステートメント属性は、標準のオプション機能として利用可能な機能ODBC 3 に含まれていない *.x*コア レベルと可能性がありますでサポートされていないすべての ODBC 3 *.x*ドライバー。 標準に準拠したアプリケーションは、これらの機能を使用している場合、ドライバーでは動作をサポートしていることを確認する必要があります。
