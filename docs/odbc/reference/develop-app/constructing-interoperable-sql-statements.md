---
title: "相互運用可能な SQL ステートメントの作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], constructing statements
ms.assetid: dee6f7e2-bcc4-4c74-8c7c-12aeda8a90eb
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 34636d9ead963cf9548d8ff1345424f4283fd1fb
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="constructing-interoperable-sql-statements"></a>相互運用可能な SQL ステートメントの作成
前述の前のセクションで、相互運用可能アプリケーションは、ODBC SQL 文法を使用してください。 ただし、この文法を使用して、以外は他の問題の数が相互運用可能なアプリケーションが直面しています。 たとえば、アプリケーションのはたらきすべてのデータ ソースによってサポートされていない機能、外部結合などを使用する必要がある場合。  
  
 この時点で、アプリケーション作成者必要がありますいくつか方法に関する意思言語機能が必要か、省略可能。 ほとんどの場合、特定のドライバーは、アプリケーションで必要な機能をサポートしていない場合、アプリケーションだけで退出をそのドライバーを使用して実行します。 ただし、機能が省略可能な場合は、アプリケーションできます回避機能。 たとえば、これは機能を使用するユーザーに許可するインターフェイスの一部を無効に可能性があります。  
  
 サポートされる機能を決定するには、アプリケーションの開始を呼び出して**SQLGetInfo** SQL_SQL_CONFORMANCE オプションを使用します。 SQL への準拠レベルは、SQL はサポートされているさまざまなビューをアプリケーションに提供します。 このビューでは、アプリケーションの呼び出しを設定し直す**SQLGetInfo**いくつかの他のオプションのいずれかとします。 これらのオプションの一覧については、次を参照してください。、 [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)関数の説明。 最後に、 **SQLGetTypeInfo**データ ソースによってサポートされるデータ型に関する情報を返します。 次のセクションでは、相互運用可能な SQL ステートメントを構築するときにアプリケーションを監視する必要があります潜在的な要素の数を一覧表示します。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [カタログとスキーマの使用状況](../../../odbc/reference/develop-app/catalog-and-schema-usage.md)  
  
-   [カタログの位置](../../../odbc/reference/develop-app/catalog-position.md)  
  
-   [引用符で囲まれた識別子](../../../odbc/reference/develop-app/quoted-identifiers.md)  
  
-   [識別子の大文字と小文字の区別](../../../odbc/reference/develop-app/identifier-case.md)  
  
-   [エスケープ シーケンス](../../../odbc/reference/develop-app/escape-sequences.md)  
  
-   [リテラル プレフィックスおよびサフィックス](../../../odbc/reference/develop-app/literal-prefixes-and-suffixes.md)  
  
-   [プロシージャ呼び出しのパラメーター マーカー](../../../odbc/reference/develop-app/parameter-markers-in-procedure-calls.md)  
  
-   [DDL ステートメント](../../../odbc/reference/develop-app/ddl-statements.md)
