---
title: SQL ステートメントの実行時に構築 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- run time constructed SQL statements [ODBC]
- SQL statements [ODBC], constructing
- SQL statements [ODBC], building at run time
ms.assetid: f6554486-d49c-436a-82e3-4c158d26acd8
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 74ac852c583a45d0ccf15f80cbbaf29c0cad4292
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sql-statements-constructed-at-run-time"></a>実行時に構築される SQL ステートメント
よくアド ホック分析を実行するアプリケーションでは、実行時に SQL ステートメントを構築します。 たとえば、スプレッドシートでは、データを取得する対象の列を選択するユーザーを使用する可能性があります。  
  
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
  
 通常 SQL ステートメントの実行時に作成するアプリケーションの別のクラスは、アプリケーションの開発環境です。 作成するステートメントがここで、通常最適化およびテスト可能、ビルド、アプリケーションにハードコーディングします。  
  
 実行時に SQL ステートメントを構築するアプリケーションでは、ユーザーに多大な柔軟性を提供できます。 サポートしていませんでしたなどの一般的な操作の前の例からわかるように**場所**句、 **ORDER BY**句、または実行時に SQL ステートメントの作成、結合が大幅により複雑なハード コーディング ステートメント。 さらに、このようなアプリケーションのテストは問題のある任意の数の SQL ステートメントを構築するためです。  
  
 実行時に SQL ステートメントを構築する場合の潜在的な欠点は、ハード コーディングされたステートメントを使用してよりも、ステートメントを構築するために非常に多くの時間がかかることです。 幸いにも、問題ではほとんどありません。 このようなアプリケーションの傾向があります、大量のユーザー インターフェイス アプリケーションに費やす時間 SQL ステートメントの作成は通常小さく、ユーザー入力の条件に費やす時間と比較しています。
