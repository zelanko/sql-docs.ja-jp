---
title: 組み込み SQL の例 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL [ODBC], embedded SQL
- SQL statements [ODBC], embedded SQL
- embedded SQL [ODBC]
ms.assetid: b8a26e05-3c82-4c5f-8f01-9de0edb645e9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 39ec504c423817c6a3e11bc954555b201b8b09c6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81294173"
---
# <a name="embedded-sql-example"></a>埋め込み SQL の例
次のコードは、C で記述された単純な組み込み SQL プログラムです。このプログラムは、組み込み SQL 技法の多くを示していますが、すべてではありません。 プログラムは、注文番号の入力を求めるプロンプトを表示し、顧客番号、営業担当者、および注文の状態を取得し、取得した情報を画面に表示します。  
  
```cpp  
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
  
 このプログラムについて、以下の点に注意してください。  
  
-   **ホスト変数**ホスト変数は **、BEGIN DECLARE SECTION**キーワードおよび END DECLARE **SECTION**キーワードで囲まれたセクションで宣言されます。 各ホスト変数名には、コロン (:)組み込み SQL ステートメントに表示される場合。 コロンを使用すると、プリコンパイラーは、ホスト変数と、同じ名前のデータベース・オブジェクト (表や列など) を区別できます。  
  
-   **データ型**DBMS とホスト言語でサポートされるデータ型は、まったく異なる場合があります。 ホスト変数は二重の役割を果たすため、これはホスト変数に影響を与えます。 一方で、ホスト変数はプログラム変数であり、ホスト言語ステートメントによって宣言および操作されます。 一方、データベース・データを取り出すために、組み込み SQL ステートメントで使用されます。 DBMS データ型に対応するホスト言語タイプがない場合、DBMS は自動的にデータを変換します。 ただし、各 DBMS には変換プロセスに関連付けられた独自のルールと特異性があるため、ホスト変数の型は慎重に選択する必要があります。  
  
-   **エラー処理**DBMS は、SQL 通信域 (SQLCA) を介して、ランタイム・エラーをアプリケーション・プログラムに報告します。 上記のコード例では、最初の組み込み SQL ステートメントは INCLUDE SQLCA です。 これにより、プリコンパイラーは SQLCA 構造をプログラムに組み込むように指示します。 これは、プログラムが DBMS によって返されるエラーを処理する場合に必要です。 常に..GOTO ステートメントは、エラーが発生したときに特定のラベルに分岐するエラー処理コードを生成するようにプリコンパイラーに指示します。  
  
-   **シングルトン選択**データを返すために使用されるステートメントは、シングルトンの SELECT ステートメントです。つまり、1 行のデータのみを返します。 したがって、コード例ではカーソルを宣言または使用しません。
