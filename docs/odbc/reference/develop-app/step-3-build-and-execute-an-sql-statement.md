---
title: 'ステップ 3: SQL ステートメントを作成して実行する |マイクロソフトドキュメント'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- application process [ODBC], building and executing statements
- SQL statements [ODBC], building and executing
ms.assetid: 133b8bd4-a3c8-4f7e-93c5-c05283c8e96f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e8322cf5e7b4a91bfc5f5f0204cfb25fa4bdad92
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306833"
---
# <a name="step-3-build-and-execute-an-sql-statement"></a>手順 3:SQL ステートメントのビルドと実行
3 番目の手順では、次の図に示すように、SQL ステートメントを作成して実行します。 この手順を実行するために使用される方法は、大きく異なる可能性があります。 アプリケーションは、ユーザーに対して、SQL ステートメントの入力、ユーザー入力に基づく SQL ステートメントの作成、またはハードコーディングされた SQL ステートメントの使用を求めるメッセージを表示する場合があります。 詳細については、 [SQL ステートメントの作成を](../../../odbc/reference/develop-app/constructing-sql-statements.md)参照してください。  
  
 ![SQL ステートメントのビルドと実行](../../../odbc/reference/develop-app/media/pr13.gif "pr13")  
  
 SQL ステートメントにパラメーターが含まれている場合、アプリケーションは各パラメーターに対して**SQLBindParameter**を呼び出して、パラメーターをアプリケーション変数にバインドします。 詳細については、「ステートメント[パラメータ](../../../odbc/reference/develop-app/statement-parameters.md)」を参照してください。  
  
 SQL ステートメントが作成され、パラメーターがバインドされると **、SQLExecDirect**を使用してステートメントが実行されます。 ステートメントが複数回実行される場合は、 **SQLPrepare を**使用して準備し、 **SQLExecute**を使用して実行できます。 詳細については、「[ステートメントの実行](../../../odbc/reference/develop-app/executing-a-statement.md)」を参照してください。  
  
 また、アプリケーションは SQL ステートメントの実行を完全に見送り、代わりに関数を呼び出して、使用可能な列やテーブルなどのカタログ情報を含む結果セットを返す場合があります。 詳細については、「カタログ[データの使用](../../../odbc/reference/develop-app/uses-of-catalog-data.md)」を参照してください。  
  
 アプリケーションの次のアクションは、実行される SQL ステートメントのタイプによって異なります。  
  
|SQL ステートメントのタイプ|に進む|  
|---------------------------|----------------|  
|**SELECT**またはカタログ関数|[手順 4a: 結果をフェッチする](../../../odbc/reference/develop-app/step-4a-fetch-the-results.md)|  
|**更新**、**削除**、または**挿入**|[手順 4b: 行数をフェッチする](../../../odbc/reference/develop-app/step-4b-fetch-the-row-count.md)|  
|その他のすべての SQL ステートメント|ステップ 3: SQL ステートメントを作成して実行する (このトピック) または[ステップ 5: トランザクションをコミットする](../../../odbc/reference/develop-app/step-5-commit-the-transaction.md)|
