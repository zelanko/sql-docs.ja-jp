---
title: 同時実行制御 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- transactions [ODBC], concurrency control
- concurrency control [ODBC]
ms.assetid: 75e4adb3-3d43-49c5-8c5e-8df96310d912
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2e54298e9c25777f10b92f322f1b1e6a3d94c243
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63191759"
---
# <a name="concurrency-control"></a>コンカレンシー制御
*同時実行*と同時に、同じデータを使用する 2 つのトランザクションの機能は、トランザクション分離は、通常は同時実行が少なくします。 これは、トランザクション分離は、通常、行をロックによって実装が少ないトランザクションがロックされている行によって、少なくとも一時的にブロックされることがなく行うことができます複数の行がロックされている、ためです。 同時実行の制限は、データベースの整合性を維持するために必要な高いトランザクション分離レベルのトレードオフとして受け入れますが一般に、カーソルを使用して高い読み取り/書き込みアクティビティを含む対話型アプリケーションの問題になることができます。  
  
 たとえば、アプリケーションは、SQL ステートメントを実行します。**選択\*から注文**します。 呼び出す**SQLFetchScroll**結果をスクロールする設定し、ユーザーを更新するには、削除、または注文を挿入します。 ユーザーは、更新、削除、または注文の挿入、後に、アプリケーションは、トランザクションをコミットします。  
  
 分離レベルが Repeatable Read の場合は、トランザクションの実装の方法によってのロックによって返される各行**SQLFetchScroll**します。 分離レベルが Serializable の場合は、トランザクション全体の Orders テーブルのロック。 いずれの場合も、トランザクションはコミットまたはロールバックされた場合にのみロックを解放します。 したがって、ユーザーは、多くの注文と更新、削除、ごくわずかな時間の読み取り時間を費やすまたはそれらを挿入するには、トランザクションが簡単に場合は、多くの他のユーザーに使用できないように、行をロックします。  
  
 これは、カーソルは読み取り専用と、アプリケーションにより、ユーザーは既存の注文だけを読み取る場合でも問題です。 この場合、アプリケーションは、トランザクションをコミットしを呼び出すときに、ロックを解放**SQLCloseCursor** (自動コミット モード) でまたは**SQLEndTran** (手動コミット モード) では。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [コンカレンシーの種類](../../../odbc/reference/develop-app/concurrency-types.md)  
  
-   [オプティミスティック コンカレンシー](../../../odbc/reference/develop-app/optimistic-concurrency.md)
