---
title: "トランザクション ODBC |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transactions [ODBC], about transactions
- transactions [ODBC]
ms.assetid: b4ca861a-c164-4e87-8672-d5de15e3823c
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d11b681fa324c2c0b514bfb43aa67d51ce19a1ba
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="transactions-odbc"></a>ODBC トランザクション
A*トランザクション*作業の単位ですが、1 つのアトミック操作として完了する以外の場合は、操作として成功または失敗全体です。 たとえば、間の 1 つの銀行口座の money を転送します。 これは、2 つの手順: 参加お金を最初のアカウントと 2 番目にデポジットです。 重要です。 両方の手順が成功します。1 つのステップが成功して失敗する余裕がないです。 トランザクションをサポートするデータベースは、これを保証できません。  
  
 いずれかが原因でトランザクションを完了できる*コミット*中または*ロールバック*です。 トランザクションがコミットされた場合、トランザクションを永続的なものに加えられた変更します。 トランザクションがロールバックされたときに、トランザクションの開始前に、の状態に影響を受けた行が返されます。 アカウントの転送の例を拡張するには、アプリケーションは、最初の口座に 1 つの SQL ステートメントおよびクレジットの 2 番目のアカウントを別の SQL ステートメントを実行します。 両方のステートメントが成功した場合、その後、アプリケーションは、トランザクションをコミットします。 どちらかのステートメントは、何らかの理由で失敗した場合、アプリケーション トランザクションをロールバックします。 どちらの場合は、アプリケーションは、トランザクションの終了時の一貫性のある状態を保証します。  
  
 1 つのトランザクションには、異なるタイミングで複数のデータベース操作が含まれていることができます。 他のトランザクションに完全なアクセスに中間結果がある場合は、トランザクションが互いに干渉可能性があります。 たとえば、1 つのトランザクションでは、行を挿入したと仮定しますその行と、最初のトランザクションがロールバック 2 番目のトランザクションを読み取ります。 2 番目のトランザクションを今すぐには、存在しない行のデータがあります。  
  
 この問題を解決するには、いずれかの別のトランザクションを分離するさまざまなパターンがあります。 *トランザクションの分離*は一般にによって実装される、行をロックを同時に同じ行を使用して 1 つ以上のトランザクションを除外します。 一部のデータベースで行をロックには他の行をロック可能性がありますはもできます。  
  
 トランザクション分離は削減*同時実行性、*または同時に同じデータを使用する 2 つのトランザクションの機能です。 詳細については、次を参照してください。[設定 Transaction Isolation Level](../../../odbc/reference/develop-app/setting-the-transaction-isolation-level.md)です。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [ODBC でのトランザクション](../../../odbc/reference/develop-app/transactions-in-odbc-odbc.md)  
  
-   [トランザクションの分離](../../../odbc/reference/develop-app/transaction-isolation.md)  
  
-   [同時実行制御](../../../odbc/reference/develop-app/concurrency-control.md)

