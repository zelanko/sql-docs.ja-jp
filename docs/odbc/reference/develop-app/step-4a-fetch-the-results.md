---
title: 'ステップ 4a: 結果を取得する |マイクロソフトドキュメント'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- application process [ODBC], fetching results
- fetches [ODBC], fetching results
ms.assetid: 77d30142-c774-473c-96fb-b364bb92ac60
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c4f810e5c42b54ec871c233ab498936abae610dc
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302973"
---
# <a name="step-4a-fetch-the-results"></a>手順 4a: 結果をフェッチする
次の手順では、次の図に示すように、結果を取得します。  
  
 ![ODBC アプリケーションでの結果のフェッチ](../../../odbc/reference/develop-app/media/pr14.gif "pr14")  
  
 「ステップ 3: SQL ステートメントの作成と実行」で実行されたステートメントが**SELECT**ステートメントまたはカタログ関数であった場合、アプリケーションは最初に**SQLNumResultCols**を呼び出して結果セット内の列数を決定します。 この手順は、SQL ステートメントが垂直アプリケーションやカスタム アプリケーションでハードコーディングされている場合など、アプリケーションが結果セット列の数を既に認識している場合には必要ありません。  
  
 次に、アプリケーションは **、SQLDescribeCol**を使用して、各結果セット列の名前、データ型、有効桁数、および小数点以下桁数を取得します。 このことは、既にこの情報を知っている垂直アプリケーションやカスタム アプリケーションなどのアプリケーションでは必要ありません。 アプリケーションは、この情報を**SQLBindCol**に渡し、アプリケーション変数を結果セット内の列にバインドします。  
  
 アプリケーションは**SQLFetch**を呼び出して、データの最初の行を取得し、その行のデータを**SQLBindCol**でバインドされた変数に配置します。 行に長いデータがある場合は **、SQLGetData**を呼び出してそのデータを取得します。 アプリケーションは、追加のデータを取得するために**SQLFetch**と**SQLGetData**を呼び出し続けます。 データのフェッチが完了すると、カーソルを閉じるための**SQLCloseCursor**が呼び出されます。  
  
 結果の取得の詳細については、「[結果の取得 (基本)」](../../../odbc/reference/develop-app/retrieving-results-basic.md)および「[結果の取得 (詳細)」](../../../odbc/reference/develop-app/retrieving-results-advanced.md)を参照してください。  
  
 アプリケーションは、同じトランザクション内の別のステートメントを実行する「ステップ 3: SQL ステートメントをビルドして実行する」に戻ります。または「ステップ 5: トランザクションをコミットする」に進み、トランザクションをコミットまたはロールバックします。
