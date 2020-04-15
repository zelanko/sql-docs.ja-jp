---
title: SQL 文法の選択 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], SQL grammar
- SQL grammar [ODBC], selecting
ms.assetid: 4e0d189b-e407-47e0-92a9-f9982230dd0e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2ca9911d3c88f2f540ff1332d77a2e1ebc6a4942
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299162"
---
# <a name="choosing-an-sql-grammar"></a>SQL 文法の選択
SQL ステートメントを構築する際に最初に決定するのは、どの文法を使用するかを決定することです。 オープングループ、ANSI、ISO などのさまざまな標準機関から利用できる文法に加えて、ほとんどすべての DBMS ベンダーが独自の文法を定義します。  
  
 [付録 C: SQL 文法](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md)では、すべての ODBC ドライバーがサポートする必要がある最小の SQL 文法について説明します。 この文法は、SQL-92 のエントリ レベルのサブセットです。 ドライバーは、SQL-92 で定義された中間、完全、または FIPS 127-2 の移行レベルに準拠する追加の文法をサポートする場合があります。 詳細については、「付録 C: [SQL 文法](../../../odbc/reference/appendixes/sql-minimum-grammar.md)」および「SQL-92」の「SQL 最小文法」を参照してください。  
  
 付録 C では、SQL-92 文法でカバーされない、外部結合など、一般的に使用できる言語機能の標準文法を含む*エスケープ シーケンス*も定義します。 詳細については、後の「付録 C: SQL 文法」および「[エスケープ シーケンス](../../../odbc/reference/develop-app/escape-sequences.md)」の[「ODBC エスケープ シーケンス](../../../odbc/reference/appendixes/odbc-escape-sequences.md)」を参照してください。  
  
 選択された文法は、ドライバーがステートメントを処理する方法に影響します。 ドライバーは、SQL-92 SQL と ODBC 定義のエスケープ シーケンスを DBMS 固有の SQL に変更する必要があります。 ほとんどの SQL 文法はさまざまな標準に基づいているため、ほとんどのドライバーはこの要件を満たすためにほとんどまたはまったく作業を行いません。 通常、ODBC で定義されたエスケープ シーケンスを検索し、DBMS 固有の文法に置き換えることだけを目的として構成されます。 ドライバーは、認識しない文法を検出すると、文法は DBMS 固有であると見なし、実行のためにデータ ソースに変更を加えずに SQL ステートメントを渡します。  
  
 したがって、実際には、SQL-92 文法 (および ODBC エスケープ シーケンス) と DBMS 固有の文法の 2 つの文法の選択肢があります。 2 つのうち、相互運用可能な SQL-92 文法のみが可能であるため、相互運用可能なすべてのアプリケーションで使用する必要があります。 相互運用できないアプリケーションでは、SQL-92 文法または DBMS 固有の文法を使用できます。 DBMS 固有の文法には、SQL-92 でカバーされていない機能を利用できるという 2 つの利点があり、ドライバーが変更する必要がないため、わずかに高速です。 後者の機能は、SQL_ATTR_NOSCANステートメント属性を設定することで部分的に強制できます。  
  
 SQL-92 文法を使用する場合、アプリケーションは**SQLNativeSql**を呼び出すことによって、ドライバーによって変更される方法を検出できます。 これは、アプリケーションをデバッグするときに役立ちます。 **SQL ステートメント**を受け入れ、ドライバーが変更した後、それを返します。 この関数は、コア インターフェイス準拠レベルであるため、すべてのドライバーでサポートされます。
