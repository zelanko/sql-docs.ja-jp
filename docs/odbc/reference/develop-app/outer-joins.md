---
title: 外部結合 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- outer join escape sequences [ODBC]
- escape sequences [ODBC], outer join
ms.assetid: be1a0203-5da9-4871-9566-4bd3fbc0895c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 81988d34dca38d5c041ff9f87e9674d7c97d76cc
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81282449"
---
# <a name="outer-joins"></a>外部結合
ODBC は、SQL-92 の左、右、および完全外部結合構文をサポートします。 外部結合のエスケープシーケンスは、  
  
 **{oj** _外部結合_**}**  
  
 *外部結合が存在する*場所  
  
 *テーブル参照*{**左 &#124; right &#124; FULL} OUTER JOIN** { 外部結合 { 外部*結合*&#124;*テーブル参照*}**検索条件**_search-condition_  
  
 *テーブル参照*はテーブル名を指定し、*検索条件は**テーブル参照*間の結合条件を指定します。  
  
 外部結合要求は **、FROM**キーワードの後、および**WHERE**句の前に指定する必要があります (存在する場合)。 構文の詳細については、「付録 C: SQL 文法」の[「外部結合エスケープ シーケンス](../../../odbc/reference/appendixes/outer-join-escape-sequence.md)」を参照してください。  
  
 たとえば、次の SQL ステートメントは、すべての顧客を一覧表示し、オープン注文を示す同じ結果セットを作成します。 最初のステートメントでは、エスケープ シーケンス構文を使用します。 2 番目のステートメントは、Oracle のネイティブ構文を使用しますが、相互運用できません。  
  
```  
SELECT Customers.CustID, Customers.Name, Orders.OrderID, Orders.Status  
   FROM {oj Customers LEFT OUTER JOIN Orders ON Customers.CustID=Orders.CustID}  
   WHERE Orders.Status='OPEN'  
  
SELECT Customers.CustID, Customers.Name, Orders.OrderID, Orders.Status  
   FROM Customers, Orders  
   WHERE (Orders.Status='OPEN') AND (Customers.CustID= Orders.CustID(+))  
```  
  
 データ ソースとドライバーがサポートする外部結合の種類を決定するには、アプリケーションは、SQL_OJ_CAPABILITIES フラグを使用して**SQLGetInfo**を呼び出します。 サポートされる外部結合のタイプは、左、右、完全、またはネストされた外部結合です。**ON**句の列名が**OUTER JOIN**句のそれぞれのテーブル名と同じ順序でない外部結合。外部結合と組み合わせた内部結合。および ODBC 比較演算子を使用して外部結合を行います。 SQL_OJ_CAPABILITIES情報型が 0 を返す場合、外部結合句はサポートされません。
