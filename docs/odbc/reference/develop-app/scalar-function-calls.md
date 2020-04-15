---
title: スカラー関数呼び出し |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- escape sequences [ODBC], scalar function calls
ms.assetid: 10cb4dcf-4cd8-4a56-8725-d080bd3ffe47
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 349599a51b2996f419e6c8656a71bc9e30146542
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304263"
---
# <a name="scalar-function-calls"></a>スカラー関数の呼び出し
スカラー関数は、各行の値を返します。 たとえば、絶対値スカラー関数は数値列を引数として受け取り、列の各値の絶対値を返します。 スカラー関数を呼び出すエスケープシーケンスは、  
  
 **{fn**  _スカラー関数_ **}**  
  
 *ここでスカラー関数*は[付録 E: スカラー関数](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md)に記載されている関数の 1 つです。 スカラー関数エスケープ シーケンスの詳細については、「付録 C: SQL 文法」の[スカラー関数エスケープ シーケンス](../../../odbc/reference/appendixes/scalar-function-escape-sequence.md)を参照してください。  
  
 たとえば、次の SQL ステートメントは、大文字の顧客名の同じ結果セットを作成します。 最初のステートメントでは、エスケープ シーケンス構文を使用します。 2 番目のステートメントは、OS/2 用 Ingres のネイティブ構文を使用しますが、相互運用できません。  
  
```  
SELECT {fn UCASE(Name)} FROM Customers  
  
SELECT uppercase(Name) FROM Customers  
```  
  
 アプリケーションは、ネイティブ構文を使用するスカラー関数の呼び出しと、ODBC 構文を使用するスカラー関数の呼び出しを混在させることができます。 たとえば、Employee テーブルの名前が姓、コンマ、および名として格納されているとします。 次の SQL ステートメントは、Employee テーブルに従業員の姓の結果セットを作成します。 このステートメントは、ODBC スカラー関数**SUBSTRING**と SQL Server スカラー関数**CHARINDEX**を使用し、SQL Server でのみ正しく実行されます。  
  
```  
SELECT {fn SUBSTRING(Name, 1, CHARINDEX(',', Name) - 1)} FROM Customers  
```  
  
 相互運用性を最大限に高めるには、アプリケーションは**CONVERT**スカラー関数を使用して、スカラー関数の出力が必要な型であることを確認する必要があります。 **CONVERT**関数は、1 つの SQL データ型から指定した SQL データ型にデータを変換します。 **変換**関数の構文は次のとおりです。  
  
 **変換(** _value_exp_ **,** _data_type_**)**  
  
 *value_exp*は、列名、別のスカラー関数の結果、またはリテラル値で *、data_type*は[、「付録 D: データ型](../../../odbc/reference/appendixes/appendix-d-data-types.md)」で定義されている SQL データ型識別子で使用される **#define**名と一致するキーワードです。 たとえば、次の SQL ステートメントは**CONVERT**関数を使用して **、CURDATE**関数の出力がタイムスタンプや文字データではなく日付であることを確認します。  
  
```  
INSERT INTO Orders (OrderID, CustID, OpenDate, SalesPerson, Status)  
   VALUES (?, ?, {fn CONVERT({fn CURDATE()}, SQL_DATE)}, ?, ?)  
```  
  
 データ ソースでサポートされるスカラー関数を特定するために、アプリケーションは、SQL_CONVERT_FUNCTIONS、SQL_NUMERIC_FUNCTIONS、SQL_STRING_FUNCTIONS、SQL_SYSTEM_FUNCTIONS、およびSQL_TIMEDATE_FUNCTIONSオプションを指定して**SQLGetInfo**を呼び出します。 **CONVERT**関数でサポートされる変換操作を確認するために、アプリケーションは、SQL_CONVERTで始まるオプションを使用して**SQLGetInfo**を呼び出します。
