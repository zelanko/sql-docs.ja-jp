---
title: 簡潔な関数を使用して |Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1d70d3ca60a046a355549260406edba261f805e4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63312478"
---
# <a name="using-concise-functions"></a>簡潔な関数の使用
一部の ODBC 関数では、記述子への暗黙のアクセスを取得します。 アプリケーションの作成者があります呼び出しよりも便利な**SQLSetDescField**または**SQLGetDescField**します。 これらの関数を呼び出す*簡潔な*多くの機能、設定、記述子フィールドの取得などを実行するために機能します。 一部の簡潔な関数では、アプリケーションが 1 つの関数の呼び出しでいくつかの関連する記述子フィールドを取得または設定できるようにします。  
  
 簡潔な関数は、最初の引数として使用するための記述子ハンドルを取得することがなく呼び出すことができます。 これらの関数で呼び出されるステートメント ハンドルに関連付けられた記述子フィールドを使用します。  
  
 簡潔な関数**SQLBindCol**と**SQLBindParameter**引数に対応する記述子フィールドを設定して、列またはパラメーターをバインドします。 これらの各関数は、単に記述子を設定するよりも多くのタスクを実行します。 **SQLBindCol**と**SQLBindParameter**データ列または動的パラメーターのバインディングの完全な仕様を提供します。 アプリケーションは、呼び出すことでバインディングの個別詳細を変更ただし、 **SQLSetDescField**または**SQLSetDescRec**と一連の適切な呼び出しのことで列またはパラメーターをバインドできる完全にこれらの関数。  
  
 簡潔な関数**SQLColAttribute**、 **SQLDescribeCol**、 **SQLDescribeParam**、 **SQLNumParams**、および**SQLNumResultCols**記述子フィールドの値を取得します。  
  
 **SQLSetDescRec**と**SQLGetDescRec**簡潔な関数は、1 つの呼び出しでデータ型および列またはパラメーターのデータの記憶域に影響する複数の記述子フィールドを取得または設定します。 **SQLSetDescRec**を 1 つの手順で列またはパラメーターのデータのバインドを変更する効果的な方法です。  
  
 **SQLSetStmtAttr**と**SQLGetStmtAttr**場合によっては、簡潔な関数として機能します。 (を参照してください[記述子フィールド](../../../odbc/reference/develop-app/descriptor-fields.md))。
