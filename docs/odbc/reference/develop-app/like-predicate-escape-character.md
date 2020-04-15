---
title: LIKE 述語エスケープ文字 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- LIKE predicate [ODBC]
- escape sequences [ODBC], LIKE predicate
ms.assetid: 185d6109-48cf-4981-bc40-ec2a4a90cafc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2e4f04b12911145eede3354532736cb92f1ae413
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306153"
---
# <a name="like-predicate-escape-character"></a>LIKE 述語のエスケープ文字
**LIKE**述語では、パーセント記号 (%)は 0 個以上の文字に一致し、アンダースコア (_) は任意の 1 文字に一致します。 **LIKE**述部の実際のパーセント記号またはアンダースコアを照合するには、パーセント記号またはアンダースコアの前にエスケープ文字を指定する必要があります。 **LIKE**述部エスケープ文字を定義するエスケープ・シーケンスは、次のとおりです。  
  
 **{エスケープ '** *エスケープ文字* **'}**  
  
 *エスケープ文字*は、データ ソースでサポートされる任意の文字です。  
  
 LIKE エスケープ シーケンスの詳細については、「付録 C: SQL 文法」の[LIKE エスケープ シーケンス](../../../odbc/reference/appendixes/like-escape-sequence.md)を参照してください。  
  
 たとえば、次の SQL ステートメントは、"%AAA" という文字で始まる同じ顧客名の結果セットを作成します。 最初のステートメントでは、エスケープ シーケンス構文を使用します。 2 番目のステートメントは、Access のネイティブ構文®使用します。 各**LIKE**述部の 2 番目のパーセント文字は、0 個以上の文字に一致するワイルドカード文字であることに注意してください。  
  
```  
SELECT Name FROM Customers WHERE Name LIKE '\%AAA%' {escape '\'}  
  
SELECT Name FROM Customers WHERE Name LIKE '[%]AAA%'  
```  
  
 **LIKE**述部エスケープ文字がデータ ソースでサポートされているかどうかを確認するために、アプリケーションは SQL_LIKE_ESCAPE_CLAUSE オプションを指定して**SQLGetInfo**を呼び出します。
