---
title: 同時実行制御 |Microsoft ドキュメント
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
- transactions [ODBC], concurrency control
- concurrency control [ODBC]
ms.assetid: 75e4adb3-3d43-49c5-8c5e-8df96310d912
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2fd05a84e70b601180ce67a94cbdc4caabf7e37e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="concurrency-control"></a>同時実行制御
*同時実行*同時に同じデータを使用する 2 つのトランザクションの機能は、トランザクション分離通常は同時実行が少なくします。 これはトランザクションの分離は通常、行をロックで実装が、ロックされた行が少なくとも一時的にブロックされることがなく少ないトランザクションを完了できる複数の行がロックされている、です。 トランザクション分離レベルが高いデータベースの整合性を維持するために必要なのトレードオフとして同時実行が少なく、一般的に、中にカーソルを使用してを高い読み取り/書き込み活動で、インタラクティブなアプリケーションで問題になります。  
  
 たとえば、アプリケーションは、SQL ステートメントを実行**選択\*から注文**です。 呼び出す**SQLFetchScroll**結果をスクロールする設定し、ユーザーを更新するには、削除、または注文を挿入します。 ユーザーは、更新、削除、または注文の挿入、後に、アプリケーションは、トランザクションをコミットします。  
  
 分離レベルが Repeatable Read の場合は、トランザクション可能性があります: の実装方法に応じて — によって返される行ごとのロック**SQLFetchScroll**です。 トランザクションは分離レベルが Serializable の場合は、全体の Orders テーブルをロックする可能性があります。 どちらの場合は、トランザクションは、コミットまたはロールバックされた場合にのみそのロックを解放します。 したがって、ユーザーが、多くの注文と更新、削除、わずかな時間の読み取り時間を費やすまたはそれらを挿入するには、トランザクションが簡単に場合は、他のユーザーに利用できないように、行の数が多いをロックします。  
  
 これは、カーソルは読み取り専用と、アプリケーションにより、ユーザーは既存の注文だけを読み取る場合でもの問題です。 この場合、アプリケーションは、トランザクションをコミットしを呼び出すときに、ロックを解放**SQLCloseCursor** (自動コミット モードで) または**SQLEndTran** (手動コミット モードで)。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [同時実行の種類](../../../odbc/reference/develop-app/concurrency-types.md)  
  
-   [オプティミスティック同時実行制御](../../../odbc/reference/develop-app/optimistic-concurrency.md)
