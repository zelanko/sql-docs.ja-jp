---
title: "手順 4 a: 結果をフェッチ |Microsoft ドキュメント"
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
- application process [ODBC], fetching results
- fetches [ODBC], fetching results
ms.assetid: 77d30142-c774-473c-96fb-b364bb92ac60
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f706364735794aea773847431a9d42d0a09c8183
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="step-4a-fetch-the-results"></a>手順 4 a: 結果のフェッチ
次の手順は、次の図に示すように、結果を取得するは。  
  
 ![ODBC アプリケーションで結果のフェッチ](../../../odbc/reference/develop-app/media/pr14.gif "pr14")  
  
 「ステップ 3:: ビルドと、SQL ステートメントの実行」で実行されるステートメントの場合、**選択**ステートメントまたはカタログ関数では、まずを呼び出して**SQLNumResultCols**列の数を決定するには結果セットです。 この手順は、アプリケーションが既にセットの列の SQL ステートメントを垂直方向またはカスタム アプリケーションにハードコーディングする場合など、結果の数を把握している場合に必要ではありません。  
  
 次に、アプリケーション名、データ型、有効桁数、および取得に各結果セット列の小数点以下桁数**SQLDescribeCol**です。 ここでも、この垂直方向およびカスタム アプリケーションをこの情報が既にわかっているなどのアプリケーションの必要はありません。 アプリケーションは、この情報を渡す**SQLBindCol**、アプリケーション変数、結果セット内の列にバインドします。  
  
 アプリケーションの現在の呼び出し**SQLFetch**データの最初の行を取得し、その行のデータにバインドされた変数内に配置する**SQLBindCol**です。 呼び出して、行に長いデータがある場合**SQLGetData**データを取得します。 アプリケーションの呼び出しを継続**SQLFetch**と**SQLGetData**追加データを取得します。 これには、データのフェッチが終了したらを呼び出す**SQLCloseCursor**カーソルを閉じます。  
  
 結果の取得の詳細については、次を参照してください。[を取得する結果 (基本)](../../../odbc/reference/develop-app/retrieving-results-basic.md)と[(詳細) を取得する結果](../../../odbc/reference/develop-app/retrieving-results-advanced.md)です。  
  
 今すぐアプリケーションを返します"手順 3:: ビルドと実行、SQL ステートメントに"を同じトランザクションで別のステートメントを実行するにはまたは、"手順 5:: Commit Transaction"をコミットまたはトランザクションをロールバックしてに進みます。
