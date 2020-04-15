---
title: 標準に準拠したアプリケーションとドライバ |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4b4daf2e777b20b1b84c090757d0d84796a4cae1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299719"
---
# <a name="standards-compliant-applications-and-drivers"></a>標準に準拠したアプリケーションとドライバー
標準に準拠したアプリケーションまたはドライバーは、オープン グループ CAE 仕様「データ管理: SQL コール レベル インターフェイス (CLI)」、および ISO/IEC 9075-3:1995 (E) コール レベル インターフェイス (SQL/CLI) に準拠したアプリケーションまたはドライバーです。  
  
 ODBC *3.x では*、次の機能が保証されます。  
  
-   オープングループおよび ISO CLI 仕様書に記述されたアプリケーションは、ODBC 3.x ヘッダーファイルを使用してコンパイルされ、ODBC *3.x*ライブラリにリンクされ、ODBC 3.x ドライバ マネージャを通じてドライバにアクセスする場合に、ODBC *3.x* *3.x*ドライバまたは標準準拠ドライバで動作します。 *3.x*  
  
-   オープングループおよび ISO CLI 仕様書に書き込まれたドライバーは、ODBC *3.x*ヘッダーファイルを使用してコンパイルされ、ODBC *3.x*ライブラリにリンクされ、ODBC *3.x*ドライバー マネージャーを使用してアプリケーションがドライバーにアクセスできる場合に、ODBC *3.x*アプリケーションまたは標準準拠アプリケーションで動作します。  
  
 標準に準拠したアプリケーションとドライバーは、ODBC_STD コンパイル フラグを使用してコンパイルされます。  
  
 標準に準拠したアプリケーションでは、次の動作が行われます。  
  
-   標準に準拠したアプリケーションが**SQLAllocEnv**を呼び出した場合 **(SQLAllocEnv**はオープン グループおよび ISO CLI の有効な関数であるために発生する可能性があります)、呼び出しはコンパイル時に**SQLAllocHandleStd**にマップされます。 その結果、アプリケーションは実行時に**SQLAllocHandleStd**を呼び出します。 この呼び出しの処理中に、ドライバー マネージャーは、SQL_ATTR_ODBC_VERSION環境属性をSQL_OV_ODBC3に設定します。 **SQLAllocHandleStd**の呼び出しは、*ハンドルのSQL_HANDLE_ENVのハンドル型*を持つ**SQLAllocHandle**の呼び出しと、SQL_OV_ODBC3にSQL_ATTR_ODBC_VERSIONを設定する**SQLSetEnvAttr**の呼び出しと同等です。  
  
-   標準準拠のアプリケーションが**SQLBindParam**を呼び出す場合 **(SQLBindParam**はオープン グループおよび ISO CLI の有効な関数であるために発生する可能性があります)、ODBC *3.x*ドライバー マネージャーは、呼び出しを**SQLBindParameter**の同等の呼び出しにマップします。 (付録 G: 下位互換性のためのドライバガイドラインの[SQLBindParam マッピング](../../../odbc/reference/appendixes/sqlbindparam-mapping.md)を参照してください。  
  
-   ISO CLI に合わせて、ODBC *3.x*ヘッダー ファイルには **、SQLGetInfo**の呼び出しで使用される情報型のエイリアスが含まれています。 標準に準拠したアプリケーションでは、ODBC *3.x*情報型の代わりにこれらの別名を使用できます。 詳細については、次のトピック[「ヘッダー ファイル](../../../odbc/reference/develop-app/header-files.md)」を参照してください。  
  
-   標準に準拠したアプリケーションは、サポートするすべての機能が、動作するドライバーでサポートされていることを確認する必要があります。 SQL_ATTR_CURSOR_SCROLLABLEステートメント属性をSQL_SCROLLABLEに設定し、SQL_ATTR_CURSOR_SENSITIVITYステートメント属性をSQL_INSENSITIVEまたはSQL_SENSITIVEに設定することは、標準ではオプション機能として使用できますが、ODBC *3.x* Core レベルには含まれていないため、すべての ODBC *3.x*ドライバでサポートされない可能性があります。 標準準拠のアプリケーションがこれらの機能を使用する場合は、そのアプリケーションで動作するドライバーがサポートしていることを確認する必要があります。
