---
title: '手順 3: ビルドし、SQL ステートメントの実行 |Microsoft Docs'
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a3427057e70ee27fe1108fde71c833f0c511836b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47801370"
---
# <a name="step-3-build-and-execute-an-sql-statement"></a>ステップ 3: SQL ステートメントのビルドと実行
3 番目の手順は、次の図に示すようをビルドして、SQL ステートメントを実行します。 この手順を実行するために使用するメソッドは、非常に異なる可能性があります。 アプリケーションは、SQL ステートメントを入力し、ユーザーの入力に基づいて、SQL ステートメントを作成するように求めるか、ハード コーディングされた SQL ステートメントを使用して可能性があります。 詳細については、次を参照してください。 [SQL ステートメントを構築する](../../../odbc/reference/develop-app/constructing-sql-statements.md)します。  
  
 ![構築と、SQL ステートメントの実行を示しています](../../../odbc/reference/develop-app/media/pr13.gif "pr13")  
  
 SQL ステートメントにパラメーターが含まれている場合、アプリケーションにバインド アプリケーション変数を呼び出して**SQLBindParameter**パラメーターごとにします。 詳細については、次を参照してください。[ステートメント パラメーター](../../../odbc/reference/develop-app/statement-parameters.md)します。  
  
 ステートメントの実行後、SQL ステートメントは組み込まれており、すべてのパラメーターがバインドされている、 **SQLExecDirect**します。 用意することができる場合、ステートメントが複数回を実行する**SQLPrepare**で実行されると**SQLExecute**します。 詳細については、次を参照してください。[ステートメントを実行して](../../../odbc/reference/develop-app/executing-a-statement.md)します。  
  
 アプリケーションもせず、SQL ステートメントの実行を完全し、代わりに使用可能な列やテーブルなどのカタログ情報を含む結果セットを返す関数を呼び出す可能性があります。 詳細については、次を参照してください。[カタログ データの使用](../../../odbc/reference/develop-app/uses-of-catalog-data.md)します。  
  
 アプリケーションの次のアクションは、実行された SQL ステートメントの種類によって異なります。  
  
|SQL ステートメントの種類|続行するには|  
|---------------------------|----------------|  
|**選択**またはカタログに関数|[ステップ 4a: 結果のフェッチ](../../../odbc/reference/develop-app/step-4a-fetch-the-results.md)|  
|**UPDATE**、**削除**、または**挿入**|[ステップ 4b: 行数のフェッチ](../../../odbc/reference/develop-app/step-4b-fetch-the-row-count.md)|  
|その他のすべての SQL ステートメント|手順 3: ビルドして (このトピックの) SQL ステートメントを実行または[手順 5: トランザクションをコミットします](../../../odbc/reference/develop-app/step-5-commit-the-transaction.md)|
