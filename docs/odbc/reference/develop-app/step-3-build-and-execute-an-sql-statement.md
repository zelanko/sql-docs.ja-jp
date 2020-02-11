---
title: '手順 3: SQL ステートメントをビルドして実行する |Microsoft Docs'
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
ms.openlocfilehash: f0e369b74ef629c5fd7136b9098f579b5ad2b1b4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68114259"
---
# <a name="step-3-build-and-execute-an-sql-statement"></a>ステップ 3: SQL ステートメントのビルドと実行
3番目の手順では、次の図に示すように、SQL ステートメントをビルドして実行します。 この手順の実行に使用する方法は、大きく異なる可能性があります。 アプリケーションでは、SQL ステートメントを入力したり、ユーザー入力に基づいて SQL ステートメントを作成したり、ハードコーディングされた SQL ステートメントを使用したりするようユーザーに求めることができます。 詳細については、「 [SQL ステートメントの構築](../../../odbc/reference/develop-app/constructing-sql-statements.md)」を参照してください。  
  
 ![SQL ステートメントのビルドと実行](../../../odbc/reference/develop-app/media/pr13.gif "pr13")  
  
 SQL ステートメントにパラメーターが含まれている場合、アプリケーションは、各パラメーターに対して**SQLBindParameter**を呼び出すことによって、これらのパラメーターをアプリケーション変数にバインドします。 詳細については、「[ステートメントパラメーター](../../../odbc/reference/develop-app/statement-parameters.md)」を参照してください。  
  
 SQL ステートメントが作成され、すべてのパラメーターがバインドされると、 **SQLExecDirect**を使用してステートメントが実行されます。 ステートメントが複数回実行される場合は、 **SQLPrepare**で準備し、 **sqlexecute**を使用して実行できます。 詳細については、「[ステートメントの実行](../../../odbc/reference/develop-app/executing-a-statement.md)」を参照してください。  
  
 また、アプリケーションでは、SQL ステートメントを完全に実行し、代わりに関数を呼び出して、使用可能な列やテーブルなどのカタログ情報を含む結果セットを返すことも済ませるます。 詳細については、「[カタログデータの使用](../../../odbc/reference/develop-app/uses-of-catalog-data.md)」を参照してください。  
  
 アプリケーションの次のアクションは、実行された SQL ステートメントの種類によって異なります。  
  
|SQL ステートメントの種類|続行|  
|---------------------------|----------------|  
|**SELECT**または catalog 関数|[ステップ 4a: 結果のフェッチ](../../../odbc/reference/develop-app/step-4a-fetch-the-results.md)|  
|**更新**、**削除**、または**挿入**|[ステップ 4b: 行数のフェッチ](../../../odbc/reference/develop-app/step-4b-fetch-the-row-count.md)|  
|その他のすべての SQL ステートメント|手順 3: SQL ステートメントをビルドして実行する (このトピック)、または[手順 5: トランザクションをコミットする](../../../odbc/reference/develop-app/step-5-commit-the-transaction.md)|
