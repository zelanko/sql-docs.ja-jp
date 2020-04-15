---
title: 相互運用性 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC]
- interoperability [ODBC], about interoperability
ms.assetid: 43b7c849-9d59-4002-9977-9e2c8730b859
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 31b20a696c601ff91c591e4c717f468beca34e36
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306223"
---
# <a name="interoperability"></a>相互運用性
*相互運用性*とは、1 つのアプリケーションが多くの異なる Dbms で動作する機能です。 汎用的で相互運用可能なアプリケーションを作成する必要性は、ODBC の開発につながる主要な要因の 1 つでした。 しかし、相互運用性は「相互運用できない」から「完全に相互運用可能」への単純なパスではありません。 パスには多くの分岐があり、各パスには機能間のトレードオフ、速度、コードの複雑さ、開発時間が必要です。  
  
 相互運用可能なアプリケーションを作成するプロセスは、次の手順に従います。  
  
1.  アプリケーションが ODBC を使用するかどうかを決定します。  
  
2.  相互運用性のレベルを選択し、そのレベルに到達するために必要なトレードオフを決定します。  
  
3.  相互運用可能なコードを記述し、可能な限り完全にテストします。  
  
 相互運用性は主にアプリケーション作成者のドメインです。 ドライバは、単一の DBMS で動作するように設計されており、定義上、相互運用可能ではありません。 1 つの DBMS で ODBC を正しく実装し、公開することで、相互運用性の役割を果たします。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [ODBC が正解ですか?](../../../odbc/reference/develop-app/is-odbc-the-answer.md)  
  
-   [相互運用性のレベルの選択](../../../odbc/reference/develop-app/choosing-a-level-of-interoperability.md)  
  
-   [ターゲット DBMS とドライバーの決定](../../../odbc/reference/develop-app/determining-the-target-dbmss-and-drivers.md)  
  
-   [使用するデータベース機能の検討](../../../odbc/reference/develop-app/considering-database-features-to-use.md)  
  
-   [製品サイクルの長さ](../../../odbc/reference/develop-app/length-of-the-product-cycle.md)  
  
-   [相互運用可能なアプリケーションの作成](../../../odbc/reference/develop-app/writing-an-interoperable-application.md)  
  
-   [相互運用可能なアプリケーションのテスト](../../../odbc/reference/develop-app/testing-interoperable-applications.md)
