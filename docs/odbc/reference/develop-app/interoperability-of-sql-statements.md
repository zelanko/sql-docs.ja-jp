---
title: SQL ステートメントの相互運用性 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC]
- interoperability of SQL statements [ODBC], about interoperability
ms.assetid: 3b24c499-829c-4e65-90cf-a3a0f6d0a186
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d3d7a76c67096d2e76fe1cd3d4b15f73122699e7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302803"
---
# <a name="interoperability-of-sql-statements"></a>SQL ステートメントの相互運用性
他のアプリケーションと同様に、SQL ステートメントは相互運用可能または DBMS 固有の場合があります。 また、アプリケーションの他の部分と同様に、相互運用可能な SQL ステートメントの種類は、アプリケーションの種類によって異なります。 カスタム アプリケーションは、通常、1 つまたは 2 つの DBMS の機能を利用するように設計されているため、相互運用可能な SQL ステートメントを使用する可能性は低くなります。 汎用アプリケーションは、さまざまな DBMS で動作するように設計されているため、相互運用可能な SQL ステートメントを使用します。 また、垂直アプリケーションは通常、その中間に位置し、一定のレベルの機能を要求しますが、それ以外の場合は相互運用可能な SQL ステートメントを使用します。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [SQL 文法の選択](../../../odbc/reference/develop-app/choosing-an-sql-grammar.md)  
  
-   [相互運用可能な SQL ステートメントの構築](../../../odbc/reference/develop-app/constructing-interoperable-sql-statements.md)
