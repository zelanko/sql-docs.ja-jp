---
title: エラーとバッチ |マイクロソフトドキュメント
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300432"
---
# <a name="errors-and-batches"></a>エラーおよびバッチ
SQL ステートメントのバッチの実行中にエラーが発生した場合、次の 4 つの結果のいずれかが可能です。 (考えられる結果はデータ ソース固有であり、バッチに含まれるステートメントに依存する可能性もあります)。  
  
-   バッチ内のステートメントは実行されません。  
  
-   バッチ内のステートメントは実行されず、トランザクションはロールバックされます。  
  
-   エラーステートメントの前のすべてのステートメントが実行されます。  
  
-   エラーステートメント以外のすべてのステートメントが実行されます。  
  
 最初の 2 つのケースでは **、SQL 実行**と**SQLExecDirect** SQL_ERROR返します。 後者の 2 つのケースでは、実装に応じて、SQL_SUCCESS_WITH_INFOまたはSQL_SUCCESSが返されることがあります。 いずれの場合も、さらにエラー情報を取得するには、 **SQLGetDiagField**、 **SQLGetDiagRec**、または**SQLError**を使用します。 ただし、この情報の性質と深さはデータ ソースに固有のものです。 さらに、この情報が、誤ったステートメントを正確に識別する可能性は低くなります。
