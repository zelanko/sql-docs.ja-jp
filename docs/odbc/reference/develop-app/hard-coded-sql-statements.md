---
title: SQL ステートメントがハードコード |Microsoft ドキュメント
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
ms.topic: article
helpviewer_keywords:
- SQL statements [ODBC], hard-coded
- hard-coded SQL statements [ODBC]
- SQL statements [ODBC], constructing
ms.assetid: e355f5f1-4f1a-4933-8c74-ee73e90d2d19
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 50239c5a593c45e4f89b779787181451d44b7ac1
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="hard-coded-sql-statements"></a>ハード コーディングされた SQL ステートメント
通常、固定のタスクを実行するアプリケーションでは、ハード コーディングされた SQL ステートメントを含んでいます。 たとえば、注文入力システムがオープンの販売注文の一覧を次の呼び出しを使用する可能性があります。  
  
```  
SQLExecDirect(hstmt, "SELECT OrderID FROM Orders WHERE Status = 'OPEN'", SQL_NTS);  
```  
  
 SQL ステートメントのハードコーディングにいくつかの利点がありますアプリケーションが書き込まれます。 ときにテストする。ステートメントの実行時に構築するよりも実装する方が簡単にはアプリケーションが簡素化します。  
  
 ステートメント パラメーターを使用して、ステートメントの準備は、ハード コーディングされた SQL ステートメントを使用してさらに優れた方法を提供します。 たとえば、部品テーブルには、PartID、説明、および価格の列が含まれています。 このテーブルに新しい行を挿入する方法の 1 つ作成および実行すること、**挿入**ステートメント。  
  
```  
#define DESC_LEN 51  
#define STATEMENT_LEN 51  
  
SQLUINTEGER   PartID;  
SQLCHAR       Desc[DESC_LEN], Statement[STATEMENT_LEN];  
SQLREAL       Price;  
  
// Set part ID, description, and price.  
GetNewValues(&PartID, Desc, &Price);  
  
// Build INSERT statement.  
sprintf_s(Statement, 100, "INSERT INTO Parts (PartID, Description,  Price) "  
         "VALUES (%d, '%s', %f)", PartID, Desc, Price);  
  
// Execute the statement.  
SQLExecDirect(hstmt, Statement, SQL_NTS);  
```  
  
 さらに優れた方法では、ハード コーディングされた、パラメーター化されたステートメントを使用します。 これは、ハード コードされたデータ値を持つステートメントの上の 2 つの利点です。 最初に、整数および浮動小数点数ではなく文字列への変換など、ネイティブ型のデータ値を送信できるため、パラメーター化されたステートメントを構築するために簡単です。 パラメーター値を変更し、それをしてだけで、このようなステートメントを複数回使用する 2 番目に、再構築する必要はありません。  
  
```  
#define DESC_LEN 51  
  
SQLCHAR * Statement = "INSERT INTO Parts (PartID, Description,  Price) "  
         "VALUES (?, ?, ?)";  
SQLUINTEGER   PartID;  
SQLCHAR       Desc[DESC_LEN];  
SQLREAL       Price;  
SQLINTEGER    PartIDInd = 0, DescLenOrInd = SQL_NTS, PriceInd = 0;  
  
// Bind the parameters.  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_ULONG, SQL_INTEGER, 5, 0,  
                  &PartID, 0, &PartIDInd);  
SQLBindParameter(hstmt, 2, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR, DESC_LEN - 1, 0,  
                  Desc, sizeof(Desc), &DescLenOrInd);  
SQLBindParameter(hstmt, 3, SQL_PARAM_INPUT, SQL_C_FLOAT, SQL_REAL, 7, 0,  
                  &Price, 0, &PriceInd);  
  
// Set part ID, description, and price.  
GetNewValues(&PartID, Desc, &Price);  
  
// Execute the statement.  
SQLExecDirect(hstmt, Statement, SQL_NTS);  
```  
  
 このステートメントが複数回実行されると仮定した場合、それを準備できますより効率を上げるのため。  
  
```  
#define DESC_LEN 51  
  
SQLCHAR *Statement = "INSERT INTO Parts (PartID, Description,  Price) "  
         "VALUES (?, ?, ?)";  
SQLUINTEGER   PartID;  
SQLCHAR       Desc[DESC_LEN];  
SQLREAL       Price;  
SQLINTEGER    PartIDInd = 0, DescLenOrInd = SQL_NTS, PriceInd = 0;  
  
// Prepare the INSERT statement.  
SQLPrepare(hstmt, Statement, SQL_NTS);  
  
// Bind the parameters.  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_ULONG, SQL_INTEGER, 5, 0,  
                  &PartID, 0, &PartIDInd);  
SQLBindParameter(hstmt, 2, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR, DESC_LEN - 1, 0,  
                  Desc, sizeof(Desc), &DescLenOrInd);  
SQLBindParameter(hstmt, 3, SQL_PARAM_INPUT, SQL_C_FLOAT, SQL_REAL, 7, 0,  
                  &Price, 0, &PriceInd);  
  
// Loop to continually get new values and insert them.  
while (GetNewValues(&PartID, Desc, &Price))  
   SQLExecute(hstmt);  
```  
  
 おそらく、ステートメントを使用して最も効率的な方法は、次のコード例に示すように、ステートメントを含むプロシージャを構築するためにです。 プロシージャを開発時に構築されたデータ ソースに格納されているため、実行時に準備する必要はありません。 この方法の欠点は、プロシージャを作成する構文は DBMS によって異なり、アプリケーションが実行される各 DBMS 用に、プロシージャを個別に構築する必要があります。  
  
```  
#define DESC_LEN 51  
  
SQLUINTEGER   PartID;  
SQLCHAR       Desc[DESC_LEN];  
SQLREAL       Price;  
SQLINTEGER    PartIDInd = 0, DescLenOrInd = SQL_NTS, PriceInd = 0;  
  
// Bind the parameters.  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_ULONG, SQL_INTEGER, 5, 0,  
                  &PartID, 0, &PartIDInd);  
SQLBindParameter(hstmt, 2, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR, DESC_LEN - 1, 0,  
                  Desc, sizeof(Desc), &DescLenOrInd);  
SQLBindParameter(hstmt, 3, SQL_PARAM_INPUT, SQL_C_FLOAT, SQL_REAL, 7, 0,  
                  &Price, 0, &PriceInd);  
  
// Loop to continually get new values and insert them.  
while (GetNewValues(&PartID, Desc, &Price))  
   SQLExecDirect(hstmt, "{call InsertPart(?, ?, ?)}", SQL_NTS);  
```  
  
 パラメーター、準備されたステートメント、およびプロシージャの詳細については、次を参照してください。[ステートメントを実行する](../../../odbc/reference/develop-app/executing-a-statement.md)です。
