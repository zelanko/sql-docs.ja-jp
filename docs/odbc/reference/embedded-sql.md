---
title: "埋め込まれた SQL |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL [ODBC], embedded SQL
- sending SQL statements to DBMS [ODBC]
- SQL statements [ODBC], embedded SQL
- ODBC [ODBC], SQL
- embedded SQL [ODBC]
ms.assetid: 8eee3527-f225-4aa2-bd18-a16bd3ab0fb7
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7e27c80832143ff9907878ffc35c9479ce39ce1e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="embedded-sql"></a>Embedded SQL
DBMS に SQL ステートメントを送信するための最初の手法が埋め込まれた SQL です。 SQL は、変数および流れ制御ステートメントは使用しないので、多くの場合、C または COBOL などの従来のプログラミング言語で書かれたプログラムを追加できるデータベース サブ言語として使用されます。 これは、embedded SQL の中心: ホスト プログラミング言語で書かれたプログラムで SQL ステートメントを配置することです。 簡単に、ホスト言語で SQL ステートメントを埋め込むには、次の手法が使用されます。  
  
-   埋め込まれた SQL ステートメントは、特別な SQL プリによって処理されます。 すべての SQL ステートメントは、紹介子で始まる、終端記号は、どちらも、SQL ステートメントにフラグを設定、またはプリコンパイル済みで終わります。 紹介子と終端記号は、ホスト言語によって異なります。 たとえば、C の"EXEC SQL"は、紹介子と"(& a) SQL ("MUMPS で、終端記号は、セミコロン (;) と C および MUMPS に右かっこでします。  
  
-   ホストの変数と呼ばれる、アプリケーション プログラムからの変数は、定数が許可されている場所に埋め込まれた SQL ステートメントで使用できます。 これらは、特定の状況と、クエリの結果を受け取るための出力には、SQL ステートメントを調整するための入力で使用できます。  
  
-   1 行のデータを返すクエリは、単一の SELECT ステートメントでは; を処理します。このステートメントは、クエリとデータを返す対象となる内のホスト変数の両方を指定します。  
  
-   複数行のデータを返すクエリは、カーソルで処理されます。 カーソルは、結果セット内の現在の行の追跡します。 クエリを定義する DECLARE CURSOR ステートメント、OPEN ステートメントは、クエリ処理を開始、FETCH ステートメントは、連続する行のデータを取得および CLOSE ステートメントは、クエリ処理を終了します。  
  
-   カーソルが開いているときに、位置指定更新と位置指定の delete ステートメントは、更新またはカーソルから現在選択されている行の削除に使用できます。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [Embedded SQL の使用例](../../odbc/reference/embedded-sql-example.md)  
  
-   [埋め込み SQL プログラムのコンパイル](../../odbc/reference/compiling-an-embedded-sql-program.md)  
  
-   [静的 SQL](../../odbc/reference/static-sql.md)  
  
-   [動的 SQL](../../odbc/reference/dynamic-sql.md)

