---
title: 実行時に SQL ステートメントを構築する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- run time constructed SQL statements [ODBC]
- SQL statements [ODBC], constructing
- SQL statements [ODBC], building at run time
ms.assetid: f6554486-d49c-436a-82e3-4c158d26acd8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 795335be2a2a3aab1be6dac26bf6d213161fe42e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301973"
---
# <a name="sql-statements-constructed-at-run-time"></a>実行時に構築された SQL ステートメント
アドホック分析を実行するアプリケーションは、通常、実行時に SQL ステートメントを作成します。 たとえば、スプレッドシートを使用して、データを取得する列を選択できます。  
  
```  
// SQL_Statements_Constructed_at_Run_Time.cpp  
#include <windows.h>  
#include <stdio.h>  
#include <sqltypes.h>  
  
int main() {  
   SQLCHAR *Statement = 0, *TableName = 0;  
   SQLCHAR **TableNamesArray, **ColumnNamesArray = 0;  
   BOOL *ColumnSelectedArray = 0;  
   BOOL  CommaNeeded;  
   SQLSMALLINT i = 0, NumColumns = 0;  
  
   // Use SQLTables to build a list of tables (TableNamesArray[]). Let the  
   // user select a table and store the selected table in TableName.  
  
   // Use SQLColumns to build a list of the columns in the selected table  
   // (ColumnNamesArray). Set NumColumns to the number of columns in the  
   // table. Let the user select one or more columns and flag these columns  
   // in ColumnSelectedArray[].  
  
   // Build a SELECT statement from the selected columns.  
   CommaNeeded = FALSE;  
   Statement = (SQLCHAR*)malloc(8);  
   strcpy_s((char*)Statement, 8, "SELECT ");  
  
   for (i = 0 ; i = NumColumns ; i++) {  
      if (ColumnSelectedArray[i]) {  
         if (CommaNeeded)  
            strcat_s((char*)Statement, sizeof(Statement), ",");  
         else  
            CommaNeeded = TRUE;  
         strcat_s((char*)Statement, sizeof(Statement), (char*)ColumnNamesArray[i]);  
      }  
   }  
  
   strcat_s((char*)Statement, 15, " FROM ");  
   // strcat_s((char*)Statement, 100, (char*)TableName);  
  
   // Execute the statement . It will be executed once, do not prepare it.  
   // SQLExecDirect(hstmt, Statement, SQL_NTS);  
}  
```  
  
 実行時に SQL ステートメントを通常作成するアプリケーションの別のクラスは、アプリケーション開発環境です。 ただし、作成するステートメントは、構築するアプリケーションでハードコーディングされており、通常は最適化およびテストできます。  
  
 実行時に SQL ステートメントを作成するアプリケーションは、ユーザーに大きな柔軟性を提供します。 前の例からわかるように **、WHERE**句 **、ORDER BY**句、または結合などの一般的な操作をサポートしていなかったので、実行時に SQL ステートメントを構築することは、ハードコーディングステートメントよりも非常に複雑です。 さらに、このようなアプリケーションのテストは、任意の数の SQL ステートメントを作成できるため、問題があります。  
  
 実行時に SQL ステートメントを作成する場合の潜在的な欠点は、ハードコーディングされたステートメントを使用するよりも、ステートメントの作成に時間がかかるということです。 幸いなことに、これはめったに問題ではありません。 このようなアプリケーションはユーザー・インターフェースを集中的に使用する傾向があり、アプリケーションが SQL ステートメントの作成に費やす時間は、ユーザーが基準を入力する時間に比べて一般に小さくなります。
