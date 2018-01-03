---
title: "エラーとバッチ |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- batches [ODBC], errors
- sql_success_with_info [ODBC]
- sql_success [ODBC]
- SQL statements [ODBC], batches
- sql_error [ODBC]
ms.assetid: 6debd41d-9f4c-4f4c-a44b-2993da5306f0
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6bdb04f60a6f7a981fd5869f7c74c4741df05f3a
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="errors-and-batches"></a>エラーとバッチ
SQL ステートメントのバッチの実行中にエラーが発生したときに次の 4 つの結果のいずれかが可能です。 (各考えられる結果はデータ ソース固有は、バッチに含まれるステートメントにも依存している)。  
  
-   バッチ内のステートメントは実行されません。  
  
-   バッチ内のステートメントが実行されないと、トランザクションがロールバックされます。  
  
-   すべてのエラー ステートメントの前にステートメントが実行されます。  
  
-   すべてのエラー ステートメントを除くステートメントが実行されます。  
  
 最初の 2 つの場合、 **SQLExecute**と**SQLExecDirect** SQL_ERROR を返します。 後者の 2 つのケースが返される SQL_SUCCESS_WITH_INFO または SQL_SUCCESS、実装によってです。 すべての場合、さらにエラー情報を取得すると**SQLGetDiagField**、 **SQLGetDiagRec**、または**SQLError**です。 ただし、性質とこの情報の深さはデータ ソース固有です。 さらに、この情報は、エラーでステートメントを正確に特定する可能性はありません。
