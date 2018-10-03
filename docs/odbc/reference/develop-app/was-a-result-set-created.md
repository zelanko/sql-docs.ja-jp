---
title: 結果セットは作成されましたか? | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], determining if created
ms.assetid: 4a83b8cb-2d57-4e64-b497-80bd587ee1f9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: db287e729678f54aaf637950c89c724724678f08
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47650302"
---
# <a name="was-a-result-set-created"></a>結果セットは作成されましたか?
ほとんどの場合は、アプリケーション プログラマは、アプリケーションが実行するステートメントが結果セットを作成するかどうかを把握します。 これは、アプリケーション プログラマによって書き込まれたハード コーディングされた SQL ステートメントを使用している場合、大文字と小文字です。 多くの場合、アプリケーションが実行時に SQL ステートメントを構築したときに: プログラマがフラグを設定するコードを簡単に含めるかどうかを**選択**ステートメントまたは**挿入**ステートメントの中構築します。 いくつかの状況で、プログラマが知ることはできません可能性があるステートメントが結果セットを作成するかどうか。 これは、アプリケーションが、ユーザーを入力して、SQL ステートメントを実行するための手段を提供する場合に当てはまります。 これは、アプリケーションは、プロシージャを実行する実行時に、ステートメントを構築したときにも当てはまります。  
  
 このような場合は、アプリケーションが呼び出す**SQLNumResultCols**結果セット内の列の数を決定します。 ステートメントが結果セットを作成できません 0 の場合は、他の任意の数である場合、ステートメントが結果セットを作成します。  
  
 アプリケーションを呼び出して、 **SQLNumResultCols**ステートメントが準備または実行後、いつでもできます。 ただし、一部のデータ ソースは、準備されたステートメントによって作成される結果セットを簡単に記述できない、ため、パフォーマンスが低下する場合は**SQLNumResultCols**ステートメントが準備された後は、実行される前に呼び出されます。  
  
 一部のデータ ソースは、SQL ステートメントが返す結果セット内の行の数を決定するもサポートします。 そのためをアプリケーション呼び出しを**SQLRowCount**します。 行の数を表すと正確には (カーソルの種類) に応じて SQL_DYNAMIC_CURSOR_ATTRIBUTES2、SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2、SQL_KEYSET_CURSOR_ATTRIBUTES2、または SQL_STATIC_CURSOR_ATTRIBUTES2 オプションの設定によって示されます呼び出しによって返される**SQLGetInfo**します。 このビットマスクは、各種類のカーソルに対して返される行の数が正確なおおよそ、かどうかを示しますか、すべての利用可能なです。 静的な行をカウントするかどうか、またはキーセット ドリブン カーソルがを通じて行われた変更によって影響を受ける**SQLBulkOperations**または**SQLSetPos**、位置指定の update または delete ステートメント、その他のビットに依存します。前の表に、同じオプション引数が返されます。 詳細については、次を参照してください。、 [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)関数の説明。
