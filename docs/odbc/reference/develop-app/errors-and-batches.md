---
title: エラーとバッチ |Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 36a402686a695a08748df24a7b40a228d7a2ca7f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300432"
---
# <a name="errors-and-batches"></a>エラーおよびバッチ
SQL ステートメントのバッチの実行中にエラーが発生すると、次の4つのいずれかの結果が得られます。 (考えられる各結果はデータソース固有であり、バッチに含まれるステートメントにも依存する可能性があります)。  
  
-   バッチ内のステートメントは実行されません。  
  
-   バッチ内のステートメントは実行されず、トランザクションはロールバックされます。  
  
-   Error ステートメントの前にあるすべてのステートメントが実行されます。  
  
-   Error ステートメントを除くすべてのステートメントが実行されます。  
  
 最初の2つのケースでは、 **Sqlexecute**と**SQLExecDirect**は SQL_ERROR を返します。 後者の2つのケースでは、実装によっては SQL_SUCCESS_WITH_INFO または SQL_SUCCESS が返されることがあります。 どのような場合でも、 **SQLGetDiagField**、 **SQLGetDiagRec**、または**SQLError**を使用してさらにエラー情報を取得できます。 ただし、この情報の性質と深さは、データソース固有のものです。 また、この情報は、エラーのステートメントを正確に特定することはほとんどありません。
