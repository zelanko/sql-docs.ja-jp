---
title: 外部結合 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- outer join escape sequences [ODBC]
- escape sequences [ODBC], outer join
ms.assetid: be1a0203-5da9-4871-9566-4bd3fbc0895c
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 15ab82f5623bad7d3c82729dfd9077ac967301e5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="outer-joins"></a>外部結合
ODBC には、sql-92 左、右、および完全外部結合の構文がサポートされています。 外部結合のエスケープ シーケンスは、します。  
  
 **{oj** *outer で結合 * * *}**  
  
 ここで*外部結合*は  
  
 *テーブル参照*{**左 &#124; です。右 &#124; です。FULL} OUTER JOIN** {*テーブル参照*&#124; です。*外部結合*} **ON** *検索条件*  
  
 *テーブル参照*テーブル名を指定し、*検索条件*間の結合条件を指定します、*テーブル参照*です。  
  
 外部結合要求は後に表示する必要があります、 **FROM**キーワードとの前に、**場所**句 (が存在する場合)。 完全な構文については、次を参照してください。[外部結合エスケープ シーケンス](../../../odbc/reference/appendixes/outer-join-escape-sequence.md)付録 c: SQL の文法でします。  
  
 たとえば、次の SQL ステートメントは、すべての顧客を一覧表示していますオープン注文を表示するのと同じ結果セットを作成します。 最初のステートメントでは、エスケープ シーケンスの構文を使用します。 2 番目のステートメントでは、for Oracle 固有の構文を使用して、相互運用可能ではありません。  
  
```  
SELECT Customers.CustID, Customers.Name, Orders.OrderID, Orders.Status  
   FROM {oj Customers LEFT OUTER JOIN Orders ON Customers.CustID=Orders.CustID}  
   WHERE Orders.Status='OPEN'  
  
SELECT Customers.CustID, Customers.Name, Orders.OrderID, Orders.Status  
   FROM Customers, Orders  
   WHERE (Orders.Status='OPEN') AND (Customers.CustID= Orders.CustID(+))  
```  
  
 データ ソースとドライバーをサポートする外部結合の種類を判断するには、アプリケーションが呼び出す**SQLGetInfo** SQL_OJ_CAPABILITIES でフラグを設定します。 サポートされる可能性がある外部結合の種類、left、right、完全処理、または外部結合は; 入れ子になった外部結合で名前の列で、 **ON**句内のそれぞれのテーブル名と同じ順序がない、 **OUTER JOIN**句; 外部結合とを使用して外部結合と組み合わせて内部結合任意の ODBC 比較演算子です。 SQL_OJ_CAPABILITIES 情報の種類では、0 を返します、外部結合句はサポートされません。
