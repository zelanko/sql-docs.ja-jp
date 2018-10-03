---
title: '手順 4 a: 結果が得られない |Microsoft Docs'
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
manager: craigg
ms.openlocfilehash: cad33f1ccf798a08ef1f11667e59b4d5fb4888d8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47730650"
---
# <a name="step-4a-fetch-the-results"></a>ステップ 4a: 結果のフェッチ
次の手順は、次の図に示すように、結果を取得します。  
  
 ![ODBC アプリケーションで結果のフェッチ](../../../odbc/reference/develop-app/media/pr14.gif "pr14")  
  
 「手順 3:: 構築と、SQL ステートメントの実行」で実行されるステートメントの場合、**選択**ステートメントまたはカタログ関数の場合は、アプリケーションを呼び出す最初**SQLNumResultCols**列の数を決定するには結果セット。 この手順は、アプリケーションが既に SQL ステートメントを垂直方向またはカスタム アプリケーションにハードコーディングする場合など、列の設定の結果の数を把握している場合は、必要ではありません。  
  
 次に、アプリケーションは、名前、データ型、有効桁数、および各結果セット列の小数点以下桁数を取得**SQLDescribeCol**します。 ここでも、この情報を知っている垂直方向およびカスタムのアプリケーションなどのアプリケーションの必要はありません。 アプリケーションは、この情報を渡す**SQLBindCol**、アプリケーション変数、結果セット内の列にバインドします。  
  
 アプリケーションの現在の呼び出し**SQLFetch**データの最初の行を取得し、その行からデータにバインドされた変数内に配置する**SQLBindCol**します。 行に、長い形式のデータがある場合を呼び出して**SQLGetData**データを取得します。 アプリケーションの継続を呼び出す**SQLFetch**と**SQLGetData**追加データを取得します。 これには、データのフェッチが完了したら、後に呼び出す**SQLCloseCursor**カーソルを閉じます。  
  
 結果の取得の詳細については、次を参照してください。 [(Basic) を取得する結果](../../../odbc/reference/develop-app/retrieving-results-basic.md)と[(詳細) を取得する結果](../../../odbc/reference/develop-app/retrieving-results-advanced.md)します。  
  
 "手順 3:: ビルドと実行する SQL ステートメントに"同じトランザクションで別のステートメントを実行するアプリケーションを今すぐを返しますまたは、「手順 5::、トランザクションをコミット」にコミットまたはトランザクションをロールバックに進みます。
