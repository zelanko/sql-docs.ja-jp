---
title: エラーおよびバッチ |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- batches [ODBC], errors
- sql_success_with_info [ODBC]
- sql_success [ODBC]
- SQL statements [ODBC], batches
- sql_error [ODBC]
ms.assetid: 6debd41d-9f4c-4f4c-a44b-2993da5306f0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 97179574407dca56026f9d5216e4978069cffc1e
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2018
ms.locfileid: "52527329"
---
# <a name="errors-and-batches"></a>エラーおよびバッチ
SQL ステートメントのバッチの実行中にエラーが発生したときに次の 4 つの結果の 1 つは可能です。 (可能な各結果はデータ ソースに固有では、バッチ内に含まれるステートメントにも依存)。  
  
-   バッチ内のステートメントは実行されません。  
  
-   バッチ内のステートメントが実行されないと、トランザクションをロールバックします。  
  
-   すべてのエラー ステートメントの前にステートメントが実行されます。  
  
-   すべてのエラー ステートメント以外のステートメントが実行されます。  
  
 最初の 2 つの場合、 **SQLExecute**と**SQLExecDirect** SQL_ERROR を返します。 後者の 2 つのケースで SQL_SUCCESS_WITH_INFO または SQL_SUCCESS、実装によって返す場合があります。 どの場合も、さらにエラー情報を取得すると**SQLGetDiagField**、 **SQLGetDiagRec**、または**SQLError**します。 ただし、性質と、この情報については、データ ソースに固有です。 さらに、この情報がエラーでステートメントを正確に識別するために可能性があります。
