---
title: SQL 文法を選択する |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], SQL grammar
- SQL grammar [ODBC], selecting
ms.assetid: 4e0d189b-e407-47e0-92a9-f9982230dd0e
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f571ee10abc26d5de0fb0ff35fc0c931b759f2b4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32911487"
---
# <a name="choosing-an-sql-grammar"></a>SQL 文法を選択します。
使用するには、どの文法は、SQL ステートメントを構築するときに最初に決定します。 Open Group、ANSI、ISO など、さまざまな標準機関から使用可能な文法に加えては、ほぼすべて DBMS ベンダーは、それぞれが多少異なります、標準の独自の文法を定義します。  
  
 [付録 c: SQL 文法](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md)、すべての ODBC ドライバーのサポートが必要な SQL 文法を説明します。 この文法では、SQL 92 エントリ レベルのサブセットです。 ドライバーは、中間、Full、または SQL 92 によって FIPS 127-2 の移行中レベルの定義に準拠するように追加の文法をサポートできます。 詳細については、次を参照してください。 [SQL 最小文法](../../../odbc/reference/appendixes/sql-minimum-grammar.md)付録 c: SQL 文法と sql-92 にします。  
  
 付録 C も定義*エスケープ シーケンス*一般利用可能な言語などの機能、外部結合は、標準的な文法を含むことで対応されていない SQL 92 文法します。 詳細については、次を参照してください。 [ODBC エスケープ シーケンス](../../../odbc/reference/appendixes/odbc-escape-sequences.md)付録 c: SQL 文法と[エスケープ シーケンス](../../../odbc/reference/develop-app/escape-sequences.md)、このセクションで後述します。  
  
 選択されている文法では、ドライバーが、ステートメントを処理する方法に影響します。 ドライバーは、SQL 92 SQL と DBMS に固有の SQL に ODBC で定義されたエスケープ シーケンスを変更する必要があります。 ほとんどの SQL 文法は、1 つ以上のさまざまな標準に基づいているために、ほとんどのドライバーはこの要件を満たす操作をほとんどまたはまったくないを行います。 多くの場合の定義のエスケープ シーケンスの検索のみで構成されます ODBC と DBMS 固有の文法で置き換えることができます。 ドライバーには、認識できない文法が検出されると、文法は DBMS 固有であり、SQL ステートメントの実行のデータ ソースを変更せずに渡しますが前提とします。  
  
 したがってが本当に文法を使用する 2 つの選択肢: SQL 92 文法 (およびエスケープ シーケンス ODBC)、DBMS に固有の文法とします。 2 つの SQL 92 文法のみは、相互運用可能なすべての相互運用可能なアプリケーションで使用する必要があります。 相互運用可能なアプリケーションには、SQL 92 文法または DBMS 固有の文法を使用できます。 DBMS に固有の文法がある 2 つの利点: sql-92 に含まれないすべての機能を利用して、ドライバーに修正することがあるないために若干速くはします。 後者の機能は、ドライバーの検索と置換のエスケープ シーケンスを停止する、SQL_ATTR_NOSCAN ステートメント属性を設定して、部分的に適用できます。  
  
 SQL 92 文法を使用する場合、アプリケーションがわかる修正方法、ドライバーによって呼び出すことによって**SQLNativeSql**です。 これは、アプリケーションのデバッグ時に多くの場合に便利です。 **SQLNativeSql** SQL ステートメントを受け取り、ドライバーが変更された後にそれを返します。 この関数は、コア インターフェイスへの準拠レベルにあるため、すべてのドライバーでサポートされています。
