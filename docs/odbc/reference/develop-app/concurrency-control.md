---
title: 同時実行制御 | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8afba3b3b8c8fee1307473c790186d509b37d982
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81294852"
---
# <a name="concurrency-control"></a>同時実行制御
*同時実行と*は、2 つのトランザクションが同時に同じデータを使用する能力であり、トランザクションの分離が増加すると、通常は同時実行性が低下します。 これは、通常、トランザクション分離は行のロックによって実装され、ロックされる行が増えるほど、ロックされた行によって少なくとも一時的にブロックされることなく完了できるトランザクションが少なくなるためです。 一般に、データベースの整合性を維持するために必要なトランザクション分離レベルの高い場合は、並行性の低下がトレードオフとして受け入れられますが、カーソルを使用する読み取り/書き込みアクティビティが高い対話式アプリケーションでは問題になる可能性があります。  
  
 たとえば、アプリケーションが SQL ステートメント**SELECT \* FROM Orders**を実行するとします。 **SQLFetchScroll**を呼び出して結果セットをスクロールし、ユーザーが注文を更新、削除、または挿入できるようにします。 ユーザーが更新、削除、または注文を挿入した後、アプリケーションはトランザクションをコミットします。  
  
 分離レベルが反復可能読み取りである場合、トランザクションは、実装方法に応じて **、 SQLFetchScroll**によって返される各行をロックする可能性があります。 分離レベルが [シリアル化可能] の場合、トランザクションは Orders テーブル全体をロックする可能性があります。 どちらの場合も、トランザクションは、コミットまたはロールバックされたときにのみロックを解放します。 したがって、ユーザーが注文の読み取りに時間を費やし、注文の更新、削除、挿入にほとんど時間を費やさなければ、トランザクションは大量の行を簡単にロックし、他のユーザーが利用できなくなる可能性があります。  
  
 これは、カーソルが読み取り専用で、アプリケーションがユーザーに既存の注文のみを読み取ることができる場合でも問題になります。 この場合、アプリケーションは**SQLCloseCursor** (自動コミット モード) または**SQLEndTran** (手動コミット モード) を呼び出すと、トランザクションをコミットし、ロックを解放します。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [コンカレンシーの種類](../../../odbc/reference/develop-app/concurrency-types.md)  
  
-   [オプティミスティック コンカレンシー](../../../odbc/reference/develop-app/optimistic-concurrency.md)
