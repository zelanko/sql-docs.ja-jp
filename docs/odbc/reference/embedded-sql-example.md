---
title: "SQL の使用例を埋め込み |Microsoft ドキュメント"
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
- SQL [ODBC], embedded SQL
- SQL statements [ODBC], embedded SQL
- embedded SQL [ODBC]
ms.assetid: b8a26e05-3c82-4c5f-8f01-9de0edb645e9
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 13890248b3e724f2a41db5a3425c62dc7635b63a
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="embedded-sql-example"></a>Embedded SQL の使用例
次のコードは c 言語で記述された単純な埋め込み SQL プログラムです。プログラムは、埋め込みのすべてではありませんが、ほとんどの SQL 方法を示しています。 プログラムは、注文番号の入力を求めます、顧客番号、販売員、および、注文ステータスを取得し、画面で取得した情報を表示します。  
  
```  
int main() {  
   EXEC SQL INCLUDE SQLCA;  
   EXEC SQL BEGIN DECLARE SECTION;  
      int OrderID;         /* Employee ID (from user)         */  
      int CustID;            /* Retrieved customer ID         */  
      char SalesPerson[10]   /* Retrieved salesperson name      */  
      char Status[6]         /* Retrieved order status        */  
   EXEC SQL END DECLARE SECTION;  
  
   /* Set up error processing */  
   EXEC SQL WHENEVER SQLERROR GOTO query_error;  
   EXEC SQL WHENEVER NOT FOUND GOTO bad_number;  
  
   /* Prompt the user for order number */  
   printf ("Enter order number: ");  
   scanf_s("%d", &OrderID);  
  
   /* Execute the SQL query */  
   EXEC SQL SELECT CustID, SalesPerson, Status  
      FROM Orders  
      WHERE OrderID = :OrderID  
      INTO :CustID, :SalesPerson, :Status;  
  
   /* Display the results */  
   printf ("Customer number:  %d\n", CustID);  
   printf ("Salesperson: %s\n", SalesPerson);  
   printf ("Status: %s\n", Status);  
   exit();  
  
query_error:  
   printf ("SQL error: %ld\n", sqlca->sqlcode);  
   exit();  
  
bad_number:  
   printf ("Invalid order number.\n");  
   exit();  
}  
```  
  
 このプログラムについては、次に注意してください。  
  
-   **ホスト変数**で囲まれているセクションで、ホスト変数が宣言されている、**宣言セクションの開始**と**宣言セクションの最後**キーワード。 埋め込まれた SQL ステートメントで表示される各ホストの変数名のコロン (:) が付きます。 コロンは、ホスト変数とテーブルと同じ名前を持つ列などのデータベース オブジェクトを識別するプリを使用できます。  
  
-   **データ型**DBMS とホスト言語でサポートされているデータ型は大きく異なる場合します。 これは、デュアルの役割を果たします原因で、ホスト変数に影響します。 一方で、ホスト変数は、プログラム変数を宣言し、ホスト言語のステートメントによって操作です。 その一方で、データベースのデータの取得に埋め込まれた SQL ステートメントで、使用されます。 DBMS のデータ型に対応するホスト言語の型がない場合、DBMS でデータが自動的に変換します。 ただし、各 DBMS には、独自のルールと変換プロセスに関連付けられている特異性があるために、慎重にホストの変数の型が選択する必要があります。  
  
-   **エラー処理**DBMS が、SQL 通信領域、または SQLCA によるアプリケーションのプログラムを実行時のエラーを報告します。 前のコード例では、最初の埋め込まれた SQL ステートメントは、含める SQLCA がします。 これは、プログラムに含める SQLCA 構造体、またはプリコンパイル済みを示しています。 これは、機能は、プログラムは、DBMS によって返されたエラーを処理するたびに必要です。 WHENEVER しています.GOTO ステートメントは、特定のラベルを使用しているときにエラーを分岐に発生するエラー処理コードを生成するプリを指示します。  
  
-   **単一選択**データを返すために使用するステートメントは単一の SELECT ステートメントです。 つまり、1 行のデータのみを返します。 そのため、コード例を宣言したり、しないカーソルを使用します。
