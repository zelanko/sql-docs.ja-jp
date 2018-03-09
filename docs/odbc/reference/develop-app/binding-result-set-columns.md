---
title: "バインドの結果セットの列 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- result sets [ODBC], binding columns
- binding columns [ODBC]
ms.assetid: 4bc9c30f-83ae-4766-a746-032953c187ad
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 156d7a4fa40e28f2526b5ab3f5fd1a5bef19c003
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="binding-result-set-columns"></a>バインドの結果セットの列
アプリケーションがない列をバインドしないを含む結果セットを選択する際の多くまたは少数の列としてバインドできます。 データの行がフェッチしたときに、ドライバーは、アプリケーションにバインドされた列のデータを返します。 かどうか、結果セット内のアプリケーション バインドのすべての列は、アプリケーションによって異なります。 たとえば、通常のレポートを生成するアプリケーションにある固定形式です。このようなアプリケーションは、すべてのレポートで使用する列を含む結果セットを作成し、バインドし、これらの列のすべてのデータを取得します。 表示する列を決定することもありますデータでいっぱい画面を表示するアプリケーション アクセス許可します。このようなアプリケーションでは、ユーザー可能性がありますが、バインドし、ユーザーが選択した列のみをデータの取得のすべての列を含む結果セットを作成します。  
  
 呼び出して非バインド列からデータを取得できる**SQLGetData**です。 これは、一般的な呼びれ多くの場合、1 つのバッファーの長さを超えています部分で取得する必要があります、長いデータを取得します。  
  
 列は、いつでも、行がフェッチされた後にもバインドできます。 ただし、新しいバインドは有効になりませんは行をフェッチします。 次の時間までいない既にフェッチされた行からデータに適用されます。  
  
 呼び出して、列がバインド解除されるまでの列に、別の変数がバインドされるまで、変数が列にバインドされていない**SQLBindCol**を null ポインター変数のアドレス、を呼び出すことによってすべての列がバインドされていないまでとして**SQLFreeStmt** SQL_UNBIND オプションを使用して、または、ステートメントが解放されるまでです。 このため、アプリケーションがバインドされている限り、すべてのバインドされた変数が有効なままことを確認する必要があります。 詳細については、次を参照してください。[割り当てと解放バッファー](../../../odbc/reference/develop-app/allocating-and-freeing-buffers.md)です。  
  
 列のバインドは、ステートメントの構造に関連付けられているだけの情報であるために、任意の順序で設定することができます。 また、結果セットから独立しています。 たとえば、アプリケーションは、次の SQL ステートメントによって生成される結果セットの列をバインドします。  
  
```  
SELECT * FROM Orders  
```  
  
 その後、アプリケーションは、SQL ステートメントを実行する場合  
  
```  
SELECT * FROM Lines  
```  
  
 同じステートメント ハンドルでは、最初の結果セットの列バインドはまだ有効なため、これらのステートメントの構造体に格納されているバインディング。 ほとんどの場合、これが低いプログラミング手法、避ける必要があります。 代わりに、アプリケーションを呼び出す必要があります**SQLFreeStmt**古いすべての列のバインドを解除し、新しいものをバインドする SQL_UNBIND オプションを使用します。
