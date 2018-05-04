---
title: 相互運用性 |Microsoft ドキュメント
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
- interoperability [ODBC]
- interoperability [ODBC], about interoperability
ms.assetid: 43b7c849-9d59-4002-9977-9e2c8730b859
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c7a3d49e3e537cdb0c11bfbc37bd9c5ce56bd130
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="interoperability"></a>相互運用性
*相互運用性*多くのさまざまな Dbms で動作する 1 つのアプリケーションの機能です。 ジェネリック、相互運用可能なアプリケーションを記述する必要では、ODBC の開発につながる主な要因の 1 つでした。 ただし、相互運用性はありません「いない相互運用可能な」からの続き、単純なパスを「完全に相互運用可能な」。 パスは、多数の分岐を持ち、それぞれの機能、速度、コードの複雑性、および開発時間の間のトレードオフを必要とします。  
  
 相互運用可能なアプリケーションを作成するプロセスでは、いくつかの手順に従います。  
  
1.  アプリケーションで ODBC を使用しているかどうかを決定します。  
  
2.  上のトレードオフはそのレベルに到達するために必要な決定する相互運用性のレベルを選択します。  
  
3.  相互運用可能なコードを記述し、可能な限りすべてのテストします。  
  
 相互運用性が、主に、アプリケーション作成者のドメインであることに注意してください。 ドライバーは、1 つの DBMS を使用するよう設計されていて、定義上は相互運用可能なされません。 相互運用性に正しく実装と、1 つの DBMS 経由で ODBC を公開することによって、役割を果たします。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [ODBC が正解ですか?](../../../odbc/reference/develop-app/is-odbc-the-answer.md)  
  
-   [相互運用性のレベルの選択](../../../odbc/reference/develop-app/choosing-a-level-of-interoperability.md)  
  
-   [ターゲット DBMS とドライバーの決定](../../../odbc/reference/develop-app/determining-the-target-dbmss-and-drivers.md)  
  
-   [使用するデータベース機能の検討](../../../odbc/reference/develop-app/considering-database-features-to-use.md)  
  
-   [製品サイクルの長さ](../../../odbc/reference/develop-app/length-of-the-product-cycle.md)  
  
-   [相互運用可能なアプリケーションの作成](../../../odbc/reference/develop-app/writing-an-interoperable-application.md)  
  
-   [相互運用可能なアプリケーションのテスト](../../../odbc/reference/develop-app/testing-interoperable-applications.md)
