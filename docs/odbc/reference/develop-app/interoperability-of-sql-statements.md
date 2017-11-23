---
title: "SQL ステートメントの相互運用性 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC]
- interoperability of SQL statements [ODBC], about interoperability
ms.assetid: 3b24c499-829c-4e65-90cf-a3a0f6d0a186
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 991208c26beba1167d083785a19c1e64ecaeaba6
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="interoperability-of-sql-statements"></a>SQL ステートメントの相互運用性
SQL ステートメントには、アプリケーションの残りの部分と同様に、相互運用可能なまたは DBMS 固有を指定できます。 アプリケーションの残りの部分と同様にどのように相互運用可能な SQL ステートメントを選択する必要があるアプリケーションの種類によって異なります。 カスタム アプリケーションは、1 つまたは可能性のある 2 つの Dbms の機能を利用する通常設計されているために、相互運用可能な SQL ステートメントを使用する可能性は低くします。 汎用アプリケーションは、さまざまな Dbms を使用するよう設計されていますので、相互運用可能な SQL ステートメントを使用します。 垂直アプリケーション通常代替の場所間に、特定のレベルの機能を確認要求が、それ以外の場合 相互運用可能な SQL ステートメントを使用しています。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [SQL 文法の選択](../../../odbc/reference/develop-app/choosing-an-sql-grammar.md)  
  
-   [相互運用可能な SQL ステートメントの構築](../../../odbc/reference/develop-app/constructing-interoperable-sql-statements.md)
