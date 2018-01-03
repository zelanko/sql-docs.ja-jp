---
title: "スカラー関数の呼び出し |Microsoft ドキュメント"
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
helpviewer_keywords: escape sequences [ODBC], scalar function calls
ms.assetid: 10cb4dcf-4cd8-4a56-8725-d080bd3ffe47
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4e69cc7382c73aaedda31a902cc8ed8daff5cff8
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="scalar-function-calls"></a>スカラー関数の呼び出し
スカラー関数は、各行の値を返します。 たとえば、絶対値スカラー関数は数値列を引数としてし、列の各値の絶対値を返します。 スカラー関数を呼び出すためのエスケープ シーケンスは、します。  
  
 **{fn***スカラー関数* **}**   
  
 ここで*スカラー関数*はでは、関数の 1 つ[付録 e: のスカラー関数](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md)です。 スカラー関数エスケープ シーケンスの詳細については、次を参照してください。[スカラー関数エスケープ シーケンス](../../../odbc/reference/appendixes/scalar-function-escape-sequence.md)付録 c: SQL の文法でします。  
  
 たとえば、次の SQL ステートメントを作成大文字の顧客の同じ結果セット名。 最初のステートメントでは、エスケープ シーケンスの構文を使用します。 2 番目のステートメントでは、OS/2 の Ingres のネイティブの構文を使用して、相互運用可能ではありません。  
  
```  
SELECT {fn UCASE(Name)} FROM Customers  
  
SELECT uppercase(Name) FROM Customers  
```  
  
 アプリケーションは、ネイティブの構文を使用するスカラー関数の呼び出しと ODBC 構文を使用するスカラー関数の呼び出しに混在させることができます。 たとえば、Employee テーブルの名前は、姓、コンマ、および姓として格納されていることを想定しています。 次の SQL ステートメントは、Employee テーブルの従業員の姓の結果セットを作成します。 ステートメントは、ODBC スカラー関数を使用して**SUBSTRING**と SQL Server のスカラー関数**CHARINDEX**し、SQL Server でのみ正常に実行されます。  
  
```  
SELECT {fn SUBSTRING(Name, 1, CHARINDEX(',', Name) – 1)} FROM Customers  
```  
  
 相互運用性を最大にするため、アプリケーションを使用する必要があります、**変換**スカラー関数、スカラー関数の出力が必要な型であるかどうかを確認します。 **変換**関数は、1 つの SQL データ型のデータを指定した SQL データ型に変換します。 構文、**変換**関数  
  
 **変換 (** *value_exp* **、** *data_type***)**  
  
 ここで*value_exp*列名、もう 1 つのスカラー関数、またはリテラルの値の結果と*data_type*キーワードと一致する、 **#define**によって使用される名前、定義されている、SQL データ型識別子[付録 d: データ型](../../../odbc/reference/appendixes/appendix-d-data-types.md)です。 たとえば、次の SQL ステートメントを使用して、**変換**ことを確認する関数の出力、 **CURDATE**関数は、タイムスタンプ列または文字データではなく、日付。  
  
```  
INSERT INTO Orders (OrderID, CustID, OpenDate, SalesPerson, Status)  
   VALUES (?, ?, {fn CONVERT({fn CURDATE()}, SQL_DATE)}, ?, ?)  
```  
  
 アプリケーションが呼び出す調べるには、データ ソースがサポートするスカラー関数、 **SQLGetInfo** SQL_CONVERT_FUNCTIONS、SQL_NUMERIC_FUNCTIONS、SQL_STRING_FUNCTIONS、SQL_SYSTEM_FUNCTIONS、SQL_TIMEDATE_ と関数のオプションです。 どの変換操作によってサポートされますを決定する、**変換**関数の場合、アプリケーションを呼び出す**SQLGetInfo** SQL_CONVERT でを起動するオプションのいずれかとします。
