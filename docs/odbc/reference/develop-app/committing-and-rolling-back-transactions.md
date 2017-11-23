---
title: "コミットして、トランザクションをロールバックしています |Microsoft ドキュメント"
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
helpviewer_keywords:
- rolling back transactions [ODBC]
- committing transactions [ODBC]
- transactions [ODBC], rolling back
- transactions [ODBC], committing
ms.assetid: 800f2c1a-6f79-4ed1-830b-aa1a62ff5165
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5ddf51903e3c6f8f58be1ccf0fcf5f037e4adb8c
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="committing-and-rolling-back-transactions"></a>コミットして、トランザクションをロールバックしています
アプリケーションが呼び出すをコミットまたは手動コミット モードでのトランザクションをロールバック、 **SQLEndTran**です。 通常のトランザクションをサポートする Dbms 用のドライバーを実行してこの関数を実装する、**コミット**または**ロールバック**ステートメントです。 ドライバー マネージャーは呼び出しません**SQLEndTran**場合でも、アプリケーションが、トランザクションをロールバックしようとしています。 SQL_SUCCESS、単純に返します接続が自動コミット モードであるとします。 いずれかを実装できるため、トランザクションをサポートしない Dbms 用のドライバーは、自動コミット モードでは常に、 **SQLEndTran**を何もせずに関係なく SQL_SUCCESS を返しますまたは、まったく実装しません。  
  
> [!NOTE]  
>  アプリケーションをコミットするかを実行して、トランザクションをロールバックできません**コミット**または**ロールバック**ステートメントと**SQLExecute**または**SQLExecDirect**. これを行う場合の影響は、定義されていません。 考えられる問題には、不要になったトランザクションがアクティブなを知ること、ドライバーとトランザクションをサポートしないデータ ソースに対して失敗したこれらのステートメントが含まれます。 これらのアプリケーションを呼び出す必要があります**SQLEndTran**代わりにします。  
  
 アプリケーションに、環境ハンドルをパスした場合**SQLEndTran**が概念的には、ドライバー マネージャー、接続ハンドルに渡さないを呼び出す**SQLEndTran**ドライバーごとに、環境ハンドルを使用します。環境内の 1 つまたは複数のアクティブな接続があります。 ドライバーは、環境内の各接続に対してトランザクションをコミットします。 ただしは、ドライバーでも、ドライバー マネージャーが、環境では、接続で 2 フェーズ コミットを実行することに注意これは、プログラミングの便宜を同時に呼び出す単**SQLEndTran**環境内のすべての接続。  
  
 (A *2 フェーズ コミット*は通常、複数のデータ ソース間で分散しているトランザクションのコミットを使用します。 最初の段階には、データ ソースは、トランザクションの一部をコミットできるかどうかに関するポーリングされます。 2 番目のフェーズでは、トランザクションは、すべてのデータ ソースに実際にコミットされます。 すべてのデータ ソースの最初のフェーズで返信はトランザクションをコミットすることはできない場合、2 番目のフェーズは発生しません。)
