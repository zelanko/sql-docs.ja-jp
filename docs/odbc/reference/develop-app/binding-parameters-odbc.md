---
title: バインド パラメータ ODBC |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- binding parameters [ODBC]
ms.assetid: 7538a82b-b08b-4c8f-9809-e4ccea16db11
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6e314bb9e3a1a979976a450e2a45a286ec54dfe7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306383"
---
# <a name="binding-parameters-odbc"></a>パラメーターのバインド (ODBC)
SQL ステートメントの各パラメーターは、ステートメントの実行前にアプリケーション内の変数に関連付けるか *、バインド*されている必要があります。 アプリケーションは、変数をパラメーターにバインドするときに、その変数 (アドレス、C データ型など) をドライバーに記述します。 また、SQL データ型、精度など、パラメータ自体についても説明します。 ドライバーは、そのステートメントの保持する構造体にこの情報を格納し、ステートメントの実行時に変数から値を取得する情報を使用します。  
  
 パラメータは、ステートメントが実行される前にいつでもバインドまたはリバウンドできます。 ステートメントの実行後にパラメーターが再バインドされた場合、ステートメントが再度実行されるまでバインディングは適用されません。 パラメーターを別の変数にバインドするには、アプリケーションは単にパラメーターを新しい変数に再バインドします。前のバインドは自動的に解放されます。  
  
 変数は、別の変数がパラメーターにバインドされるまで、すべてのパラメーターが SQL_RESET_PARAMS オプションを指定して**SQLFreeStmt**を呼び出してバインド解除されるまで、またはステートメントが解放されるまで、パラメーターにバインドされたままになります。 このため、アプリケーションは、変数がバインド解除されるまで、変数が解放されないようにする必要があります。 詳細については、「[バッファの割り当てと解放](../../../odbc/reference/develop-app/allocating-and-freeing-buffers.md)」を参照してください。  
  
 パラメーターのバインドは、ステートメントのドライバーによって保持されている構造体に格納されている情報だけなので、任意の順序で設定できます。 また、実行される SQL ステートメントからも独立しています。 たとえば、アプリケーションが 3 つのパラメータをバインドし、次の SQL ステートメントを実行するとします。  
  
```  
INSERT INTO Parts (PartID, Description, Price) VALUES (?, ?, ?)  
```  
  
 アプリケーションが SQL ステートメントを直ちに実行する場合  
  
```  
SELECT * FROM Orders WHERE OrderID = ?, OpenDate = ?, Status = ?  
```  
  
 同じステートメント・ハンドルでは **、INSERT**ステートメントのパラメーター・バインディングが使用されます。 ほとんどの場合、これはプログラミングの習慣が悪いため、避けるべきです。 代わりに、アプリケーションは、すべての古いパラメーターをバインド解除し、新しいパラメーターをバインドするSQL_RESET_PARAMS オプションを使用して**SQLFreeStmt**を呼び出す必要があります。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [バインディング パラメーター マーカー](../../../odbc/reference/develop-app/binding-parameter-markers.md)  
  
-   [名前によるパラメーターのバインド (名前付きパラメーター)](../../../odbc/reference/develop-app/binding-parameters-by-name-named-parameters.md)  
  
-   [パラメーター バインディングのオフセット](../../../odbc/reference/develop-app/parameter-binding-offsets.md)  
  
-   [パラメーターの記述](../../../odbc/reference/develop-app/describing-parameters.md)
