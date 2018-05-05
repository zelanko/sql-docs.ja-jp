---
title: '手順 3: ビルドし、SQL ステートメントを実行 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- application process [ODBC], building and executing statements
- SQL statements [ODBC], building and executing
ms.assetid: 133b8bd4-a3c8-4f7e-93c5-c05283c8e96f
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3f972fb5a0edfbbf492860e3421d5985d5e4edcc
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="step-3-build-and-execute-an-sql-statement"></a>手順 3: ビルドし、SQL ステートメントを実行
3 番目の手順は、次の図に示すようにビルドし、SQL ステートメントを実行するです。 この手順を実行するために使用するメソッドは、大幅に異なる可能性があります。 アプリケーションは、SQL ステートメントを入力して、ユーザー入力に基づいて SQL ステートメントを作成するように求めるか、ハード コーディングされた SQL ステートメントを使用する可能性があります。 詳細については、次を参照してください。 [SQL ステートメントを構築する](../../../odbc/reference/develop-app/constructing-sql-statements.md)です。  
  
 ![構築と SQL ステートメントの実行を示しています](../../../odbc/reference/develop-app/media/pr13.gif "pr13")  
  
 SQL ステートメントにパラメーターが含まれている場合、アプリケーションにアプリケーションを変数にバインドを呼び出して**SQLBindParameter**パラメーターごとにします。 詳細については、次を参照してください。[ステートメント パラメーター](../../../odbc/reference/develop-app/statement-parameters.md)です。  
  
 使用して、ステートメントを実行後は、SQL ステートメントに構築され、すべてのパラメーターがバインドされている、 **SQLExecDirect**です。 ステートメントが複数回を実行できる場合に準備できます**SQLPrepare**およびで実行される**SQLExecute**です。 詳細については、次を参照してください。[ステートメントを実行する](../../../odbc/reference/develop-app/executing-a-statement.md)です。  
  
 アプリケーションもせず、SQL ステートメントの実行を完全し、代わりに使用可能な列やテーブルなどのカタログ情報を含む結果セットを返す関数を呼び出すことがあります。 詳細については、次を参照してください。[カタログ データの使用](../../../odbc/reference/develop-app/uses-of-catalog-data.md)です。  
  
 アプリケーションの次のアクションは、実行される SQL ステートメントの種類によって異なります。  
  
|SQL ステートメントの種類|続行するには|  
|---------------------------|----------------|  
|**選択**またはカタログに関数|[ステップ 4a: 結果のフェッチ](../../../odbc/reference/develop-app/step-4a-fetch-the-results.md)|  
|**更新**、**削除**、または**挿入**|[ステップ 4b: 行数のフェッチ](../../../odbc/reference/develop-app/step-4b-fetch-the-row-count.md)|  
|その他のすべての SQL ステートメント|手順 3: ビルドし、(このトピックの) SQL ステートメントを実行または[手順 5: トランザクションをコミットします](../../../odbc/reference/develop-app/step-5-commit-the-transaction.md)|
