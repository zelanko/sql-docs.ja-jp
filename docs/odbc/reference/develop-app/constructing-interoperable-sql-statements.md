---
title: 相互運用可能な SQL ステートメントの作成 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], constructing statements
ms.assetid: dee6f7e2-bcc4-4c74-8c7c-12aeda8a90eb
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1eccdef63b7d06a456a07f5f1a9ccad987d2de29
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81282519"
---
# <a name="constructing-interoperable-sql-statements"></a>相互運用可能な SQL ステートメントの構築
前のセクションで説明したように、相互運用可能なアプリケーションでは ODBC SQL 文法を使用する必要があります。 ただし、この文法を使用する以外にも、相互運用可能なアプリケーションでは、いくつかの問題が発生します。 たとえば、すべてのデータ ソースでサポートされていない外部結合などの機能を使用する場合、アプリケーションは何をしますか。  
  
 この時点で、アプリケーション作成者は、どの言語機能が必要か、どの言語機能がオプションであるかについていくつかの決定を行う必要があります。 ほとんどの場合、特定のドライバーがアプリケーションで必要な機能をサポートしていない場合、アプリケーションはそのドライバーで実行することを拒否します。 ただし、この機能がオプションの場合、アプリケーションは機能を回避できます。 たとえば、ユーザーが機能を使用できるようにするインターフェイスのこれらの部分を無効にする場合があります。  
  
 サポートされている機能を特定するために、アプリケーションは、SQL_SQL_CONFORMANCE オプションを指定して**SQLGetInfo**を呼び出すことによって開始します。 SQL 準拠レベルは、アプリケーションに SQL がサポートされている幅広いビューを提供します。 このビューを絞り込むために、アプリケーションは**SQLGetInfo**を呼び出し、その他のオプションを使用します。 これらのオプションの完全な一覧については[、SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)関数の説明を参照してください。 最後に **、SQLGetTypeInfo は**、データ ソースでサポートされているデータ型に関する情報を返します。 次のセクションでは、相互運用可能な SQL ステートメントを構築する際にアプリケーションが注意すべきいくつかの要因を示します。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [カタログとスキーマの使用状況](../../../odbc/reference/develop-app/catalog-and-schema-usage.md)  
  
-   [カタログの位置](../../../odbc/reference/develop-app/catalog-position.md)  
  
-   [引用符で囲まれた識別子](../../../odbc/reference/develop-app/quoted-identifiers.md)  
  
-   [識別子の大文字と小文字の区別](../../../odbc/reference/develop-app/identifier-case.md)  
  
-   [エスケープ シーケンス](../../../odbc/reference/develop-app/escape-sequences.md)  
  
-   [リテラル プレフィックスおよびサフィックス](../../../odbc/reference/develop-app/literal-prefixes-and-suffixes.md)  
  
-   [プロシージャ呼び出しのパラメーター マーカー](../../../odbc/reference/develop-app/parameter-markers-in-procedure-calls.md)  
  
-   [DDL ステートメント](../../../odbc/reference/develop-app/ddl-statements.md)
