---
title: "バインディング パラメーター ODBC |Microsoft ドキュメント"
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
helpviewer_keywords: binding parameters [ODBC]
ms.assetid: 7538a82b-b08b-4c8f-9809-e4ccea16db11
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e0994006c2e99c8f1e454eaf07b74fffcee70e9f
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="binding-parameters-odbc"></a>ODBC のパラメーターのバインド
SQL ステートメントの各パラメーターが関連付けられている、する必要がありますまたは*バインドされると、*ステートメントが実行される前に、アプリケーション内の変数にします。 アプリケーションは、パラメーターに変数をバインドしたときにその変数について説明: アドレス、C データ型: ドライバーにします。 パラメーター自体についても説明: SQL データ型、有効桁数、およびなです。 ドライバーでは、そのステートメントを保持し、ステートメントを実行すると、変数から値を取得する情報を使用して、構造のこの情報を格納します。  
  
 パラメーターのバインドまたはステートメントが実行される前にいつでも再バインドできます。 パラメーターは、ステートメントの実行後に再バインドは、ステートメントをもう一度実行するまで、バインドは適用されません。 パラメーターを別の変数をバインドするには、アプリケーションだけでの再バインド数です。 新しい変数を持つパラメーター以前のバインドが自動的に解放します。  
  
 までを呼び出してすべてのパラメーターがバインドされていない、パラメーターに、別の変数がバインドされるまで、変数がパラメーターにバインドされていない**SQLFreeStmt** SQL_RESET_PARAMS オプションを使用して、または、ステートメントが解放されるまでです。 このため、アプリケーションはバインドされた変数がまで解放されないことを確認する必要があります。 詳細については、次を参照してください。[割り当てと解放バッファー](../../../odbc/reference/develop-app/allocating-and-freeing-buffers.md)です。  
  
 パラメーターのバインドは、ステートメントのドライバーによって管理される構造に格納されているだけの情報であるために、任意の順序で設定することができます。 実行される SQL ステートメントの独立したにもです。 たとえば、アプリケーションは、3 つのパラメーターをバインドし、次の SQL ステートメントを実行します。  
  
```  
INSERT INTO Parts (PartID, Description, Price) VALUES (?, ?, ?)  
```  
  
 その後、アプリケーションがすぐに、SQL ステートメントを実行する場合  
  
```  
SELECT * FROM Orders WHERE OrderID = ?, OpenDate = ?, Status = ?  
```  
  
 次のように同じステートメント ハンドルのパラメーター バインディング、**挿入**のため、これらのステートメントの構造体に格納されているバインディングにステートメントを使用します。 ほとんどの場合、これが低いプログラミング手法、避ける必要があります。 代わりに、アプリケーションを呼び出す必要があります**SQLFreeStmt**古いすべてのパラメーターのバインドを解除し、新しいものをバインドする SQL_RESET_PARAMS オプションを使用します。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [バインディング パラメーター マーカー](../../../odbc/reference/develop-app/binding-parameter-markers.md)  
  
-   [名前によるパラメーターのバインド (名前付きパラメーター)](../../../odbc/reference/develop-app/binding-parameters-by-name-named-parameters.md)  
  
-   [パラメーター バインディングのオフセット](../../../odbc/reference/develop-app/parameter-binding-offsets.md)  
  
-   [パラメーターの記述](../../../odbc/reference/develop-app/describing-parameters.md)
