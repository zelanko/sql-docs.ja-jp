---
title: '手順 4a: 結果をフェッチする |Microsoft Docs'
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3ab0bdabe8b2d66bf054f07ea51056a4044b4ae8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68114185"
---
# <a name="step-4a-fetch-the-results"></a>ステップ 4a: 結果のフェッチ
次の手順では、次の図に示すように結果を取得します。  
  
 ![ODBC アプリケーションでの結果のフェッチ](../../../odbc/reference/develop-app/media/pr14.gif "pr14")  
  
 "手順 3: SQL ステートメントをビルドして実行する" で実行されたステートメントが**SELECT**ステートメントまたはカタログ関数であった場合、アプリケーションはまず**Sqlnumresultcols**を呼び出して、結果セット内の列の数を決定します。 この手順は、アプリケーションが、SQL ステートメントが垂直またはカスタムアプリケーションにハードコーディングされている場合など、結果セットの列の数を既に認識している場合は必要ありません。  
  
 次に、 **SQLDescribeCol**を使用して、各結果セット列の名前、データ型、有効桁数、および小数点以下桁数を取得します。 ここでも、この情報を既に把握しているアプリケーション (垂直アプリケーションやカスタムアプリケーションなど) には必要ありません。 アプリケーションは、この情報を**SQLBindCol**に渡します。これにより、アプリケーション変数が結果セットの列にバインドされます。  
  
 これで、アプリケーションは**Sqlfetch**を呼び出してデータの最初の行を取得し、その行のデータを**SQLBindCol**にバインドされた変数に配置するようになりました。 行に長いデータがある場合は、 **SQLGetData**を呼び出してそのデータを取得します。 アプリケーションは引き続き**Sqlfetch**と**SQLGetData**を呼び出して、追加データを取得します。 データのフェッチが完了したら、 **Sqlcloを**呼び出してカーソルを閉じます。  
  
 結果の取得の詳細については、「[結果の取得 (基本)](../../../odbc/reference/develop-app/retrieving-results-basic.md) 」および「[結果の取得 (詳細)](../../../odbc/reference/develop-app/retrieving-results-advanced.md)」を参照してください。  
  
 これで、アプリケーションは、同じトランザクション内で別のステートメントを実行するために、"手順 3: SQL ステートメントをビルドして実行する" に戻ります。または、トランザクションをコミットまたはロールバックするために、「手順 5: トランザクションをコミットする」に進みます。
