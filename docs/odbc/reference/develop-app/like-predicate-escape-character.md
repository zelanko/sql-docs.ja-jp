---
title: 述語のエスケープ文字のような |Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 30547551cc1793622eaa981c07bbc002d07a094d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63312921"
---
# <a name="like-predicate-escape-character"></a>LIKE 述語のエスケープ文字
**など**述語、パーセント記号 (%)一致する 0 個以上の任意の文字、およびアンダー スコア (_) では、任意の 1 文字と一致します。 実際のパーセント記号の一致またはでアンダー スコア、**など**述語、エスケープ文字はアンダー スコアまたはパーセント記号の前に取得する必要があります。 エスケープ シーケンスを定義する、**など**述語のエスケープ文字とは。  
  
 **{エスケープ '** *エスケープ文字* **'}**  
  
 場所*エスケープ文字*はデータ ソースでサポートされる任意の文字。  
  
 などの詳細についてはエスケープ シーケンスを参照してください[エスケープ シーケンスのような](../../../odbc/reference/appendixes/like-escape-sequence.md)付録 c:SQL 文法。  
  
 たとえば、次の SQL ステートメントは、「AAA %」文字で始まる名前、同じ結果セットの顧客の作成します。 最初のステートメントでは、エスケープ シーケンス構文を使用します。 2 番目のステートメントでは、Microsoft® access 固有の構文を使用して、相互運用可能なではありません。 2 番目のパーセントが各文字に注意してください**など**述語は、0 個以上の任意の文字に一致するワイルドカード文字です。  
  
```  
SELECT Name FROM Customers WHERE Name LIKE '\%AAA%' {escape '\'}  
  
SELECT Name FROM Customers WHERE Name LIKE '[%]AAA%'  
```  
  
 確認するかどうか、**など**述語のエスケープ文字がデータ ソースでサポートされている、アプリケーションを呼び出す**SQLGetInfo** SQL_LIKE_ESCAPE_CLAUSE オプションを使用します。
