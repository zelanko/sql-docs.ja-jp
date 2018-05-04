---
title: SQL ステートメントの相互運用性 |Microsoft ドキュメント
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
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC]
- interoperability of SQL statements [ODBC], about interoperability
ms.assetid: 3b24c499-829c-4e65-90cf-a3a0f6d0a186
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bb9f4ec6fbc2e6aecff8d78ff562f35f9a546405
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="interoperability-of-sql-statements"></a>SQL ステートメントの相互運用性
SQL ステートメントには、アプリケーションの残りの部分と同様に、相互運用可能なまたは DBMS 固有を指定できます。 アプリケーションの残りの部分と同様にどのように相互運用可能な SQL ステートメントを選択する必要があるアプリケーションの種類によって異なります。 カスタム アプリケーションは、1 つまたは可能性のある 2 つの Dbms の機能を利用する通常設計されているために、相互運用可能な SQL ステートメントを使用する可能性は低くします。 汎用アプリケーションは、さまざまな Dbms を使用するよう設計されていますので、相互運用可能な SQL ステートメントを使用します。 垂直アプリケーション通常代替の場所間に、特定のレベルの機能を確認要求が、それ以外の場合 相互運用可能な SQL ステートメントを使用しています。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [SQL 文法の選択](../../../odbc/reference/develop-app/choosing-an-sql-grammar.md)  
  
-   [相互運用可能な SQL ステートメントの構築](../../../odbc/reference/develop-app/constructing-interoperable-sql-statements.md)
