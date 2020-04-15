---
title: 組み込み SQL |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL [ODBC], embedded SQL
- sending SQL statements to DBMS [ODBC]
- SQL statements [ODBC], embedded SQL
- ODBC [ODBC], SQL
- embedded SQL [ODBC]
ms.assetid: 8eee3527-f225-4aa2-bd18-a16bd3ab0fb7
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9ad6fd2753d026f026d72a7aa8f68d5d48ce03cb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306675"
---
# <a name="embedded-sql"></a>埋め込み SQL
SQL ステートメントを DBMS に送信する最初の手法は、組み込み SQL です。 SQL は変数やフロー制御ステートメントを使用しないため、C や COBOL などの従来のプログラミング言語で記述されたプログラムに追加できるデータベース・サブ言語として使用されることがよくあります。 これは、組み込み SQL の中心的な考え方です: ホスト・プログラミング言語で記述されたプログラムに SQL ステートメントを配置します。 簡単に説明すると、ホスト言語に SQL ステートメントを組み込むには、次の手法を使用します。  
  
-   組み込み SQL ステートメントは、特殊な SQL プリコンパイラーによって処理されます。 すべての SQL ステートメントは、導入者で始まり、終了文字で終わり、どちらもプリコンパイラーの SQL ステートメントにフラグを付けます。 紹介とターミネータはホスト言語によって異なります。 たとえば、紹介者は C の "EXEC SQL" と "&SQL(") は MUMPS で、ターミネータはセミコロン (;)C で、右括弧は MUMPS で囲みます。  
  
-   ホスト変数と呼ばれるアプリケーション・プログラムの変数は、定数が許容される場所であれば、組み込み SQL ステートメントで使用できます。 これらは、入力時に使用して、SQL ステートメントを特定の状況に合わせ、出力時にクエリの結果を受け取ることができます。  
  
-   単一行のデータを返すクエリは、シングルトン SELECT ステートメントで処理されます。このステートメントは、データを返すクエリとホスト変数の両方を指定します。  
  
-   複数行のデータを返すクエリは、カーソルを使用して処理されます。 カーソルは、結果セット内の現在の行を追跡します。 DECLARE CURSOR ステートメントは、照会を定義し、OPEN ステートメントは照会処理を開始し、FETCH ステートメントは連続したデータ行を検索し、CLOSE ステートメントは照会処理を終了します。  
  
-   カーソルがオープンされている間、位置指定更新ステートメントおよび位置指定削除ステートメントを使用して、カーソルによって現在選択されている行を更新または削除できます。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [埋め込み SQL の例](../../odbc/reference/embedded-sql-example.md)  
  
-   [埋め込み SQL プログラムのコンパイル](../../odbc/reference/compiling-an-embedded-sql-program.md)  
  
-   [静的 SQL](../../odbc/reference/static-sql.md)  
  
-   [動的 SQL](../../odbc/reference/dynamic-sql.md)
