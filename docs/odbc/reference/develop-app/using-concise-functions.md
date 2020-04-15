---
title: 簡潔関数の使用 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- concise functions [ODBC]
- functions [ODBC], concise functions
- descriptors [ODBC], concise functions
ms.assetid: 31ac070f-8c59-4fd5-bd5a-466bb27dbca0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 63313e3dfaec8dbcd91f3bb084bbaab46da40c6e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306783"
---
# <a name="using-concise-functions"></a>簡潔な関数の使用
一部の ODBC 関数は、記述子への暗黙的なアクセスを取得します。 アプリケーションの作成者は **、SQLSetDescField**または**SQLGetDescField**を呼び出すよりも便利な場合があります。 これらの関数は、記述子フィールドの設定や取得など、多くの関数を実行するため、*簡潔*関数と呼ばれます。 一部の簡潔な関数では、アプリケーションが 1 回の関数呼び出しで複数の関連する記述子フィールドを取得したり、取得したりできます。  
  
 簡潔関数は、引数として使用する記述子ハンドルを最初に取得せずに呼び出すことができます。 これらの関数は、呼び出されるステートメント ハンドルに関連付けられた記述子フィールドを処理します。  
  
 SQLBindCol と**SQLBindParameter** **SQLBindParameter**の簡潔な関数は、引数に対応する記述子フィールドを設定することによって、列またはパラメーターをバインドします。 これらの関数は、単に記述子を設定するよりも多くのタスクを実行します。 **SQLBindCol**と**SQLBind パラメーターは**、データ列または動的パラメーターのバインディングの完全な仕様を提供します。 ただし、アプリケーションは**SQLSetDescField**または**SQLSetDescRec**を呼び出すことによってバインディングの個々の詳細を変更でき、これらの関数に対して一連の適切な呼び出しを行うことによって、列またはパラメーターを完全にバインドできます。  
  
 簡潔な関数**SQLCol 属性****、SQLDescribeCol、SQLDescribeParam** **、SQLNumParams**、および**SQLNumResultCols は**記述子フィールドの値を取得します。 **SQLDescribeParam**  
  
 **SQLSetDescRec**と**SQLGetDescRec**は、1 回の呼び出しで、列またはパラメーター データのデータ型とストレージに影響を与える複数の記述子フィールドを設定または取得する簡潔な関数です。 **SQLSetDescRec**は、列またはパラメーター・データのバインディングを 1 ステップで変更する効果的な方法です。  
  
 **場合**によっては、簡潔な関数として機能**します**。 ([記述子フィールドを](../../../odbc/reference/develop-app/descriptor-fields.md)参照してください。
