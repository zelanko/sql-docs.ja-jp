---
title: LIKE 述語エスケープ文字 |Microsoft Docs
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
ms.openlocfilehash: 20310c60759aea17d61b9252fd73d226567a7a54
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68027231"
---
# <a name="like-predicate-escape-character"></a>LIKE 述語のエスケープ文字
**LIKE**述語では、パーセント記号 (%)0個以上の任意の文字と一致し、アンダースコア (_) は任意の1文字と一致します。 **LIKE**述語の実際のパーセント記号またはアンダースコアを一致させるには、パーセント記号またはアンダースコアの前にエスケープ文字を指定する必要があります。 **LIKE**述語エスケープ文字を定義するエスケープシーケンスは次のとおりです。  
  
 **{escape '** *エスケープ文字* **'}**  
  
 ここで、*エスケープ文字*はデータソースでサポートされている任意の文字です。  
  
 LIKE エスケープシーケンスの詳細については、「付録 C: SQL 文法」の「[エスケープシーケンス](../../../odbc/reference/appendixes/like-escape-sequence.md)」を参照してください。  
  
 たとえば、次の SQL ステートメントでは、文字 "% AAA" で始まる顧客名と同じ結果セットが作成されます。 最初のステートメントでは、エスケープシーケンス構文を使用します。 2番目のステートメントでは Microsoft® Access のネイティブ構文を使用し、相互運用することはできません。 各述語の2番目のパーセント文字は、0個以上の任意の文字と一致するワイルドカード文字であることに注意し**てください。**  
  
```  
SELECT Name FROM Customers WHERE Name LIKE '\%AAA%' {escape '\'}  
  
SELECT Name FROM Customers WHERE Name LIKE '[%]AAA%'  
```  
  
 データソースで**LIKE**述語エスケープ文字がサポートされているかどうかを判断するために、アプリケーションは SQL_LIKE_ESCAPE_CLAUSE オプションを指定して**SQLGetInfo**を呼び出します。
