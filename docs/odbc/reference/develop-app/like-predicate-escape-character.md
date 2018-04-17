---
title: 述語のエスケープ文字のような |Microsoft ドキュメント
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
- LIKE predicate [ODBC]
- escape sequences [ODBC], LIKE predicate
ms.assetid: 185d6109-48cf-4981-bc40-ec2a4a90cafc
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6b47a12dbb25eaea1455a928892d6a1cd4f380c9
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="like-predicate-escape-character"></a>述語のエスケープ文字のように
**など**述語、パーセント記号 (%) と一致する 0 個以上の任意の文字と一致する任意の 1 文字をアンダー スコア (_)。 実際のパーセント記号に一致またはでアンダー スコア、**など**述語、エスケープ文字は、パーセント記号またはアンダー スコアの前にする必要があります。 エスケープ シーケンスを定義する、**など**述語のエスケープ文字とは。  
  
 **{エスケープ '** *エスケープ文字* **'}**  
  
 ここで*エスケープ文字*は、データ ソースによってサポートされる任意の文字です。  
  
 詳細については、LIKE エスケープ シーケンスを参照してください[エスケープ シーケンスと同様に](../../../odbc/reference/appendixes/like-escape-sequence.md)付録 c: SQL の文法でします。  
  
 たとえば、次の SQL ステートメントは、"%AAA"の文字で始まる名前を同じ結果セットの顧客の作成します。 最初のステートメントでは、エスケープ シーケンスの構文を使用します。 2 番目のステートメントでは、Microsoft® Access のネイティブの構文を使用して、相互運用可能ではありません。 2 番目の割合が各文字に注意してください**など**述語は、0 個以上の任意の文字に一致するワイルドカード文字です。  
  
```  
SELECT Name FROM Customers WHERE Name LIKE '\%AAA%' {escape '\'}  
  
SELECT Name FROM Customers WHERE Name LIKE '[%]AAA%'  
```  
  
 決定するかどうか、**と同様に**述語のエスケープ文字がデータ ソースによってサポートされている、アプリケーションが呼び出す**SQLGetInfo** SQL_LIKE_ESCAPE_CLAUSE オプションを使用します。
