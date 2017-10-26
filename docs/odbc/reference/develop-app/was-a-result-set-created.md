---
title: "結果セットの作成にありましたか。 | Microsoft Docs"
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
- result sets [ODBC], determining if created
ms.assetid: 4a83b8cb-2d57-4e64-b497-80bd587ee1f9
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 4c38b613ed4c2e6efb5737118030905ab9de60b1
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="was-a-result-set-created"></a>結果セットの作成にありましたか。
ほとんどの状況では、アプリケーション プログラマは、アプリケーションが実行するステートメントが結果セットを作成するかどうかを知る。 これは、アプリケーション プログラマによって書き込まれたハード コーディングされた SQL ステートメントを使用している場合に、ケースです。 通常は、大文字と小文字、アプリケーションが実行時に SQL ステートメントを構築するときに: プログラマは、フラグを設定するコードを簡単に追加できるかどうか、**を選択**ステートメントまたは**挿入**ステートメントの中構成されます。 いくつかの状況で、プログラマ可能性がありますが認識できない、ステートメントが結果セットを作成するかどうか。 これは、アプリケーションはユーザーを入力して SQL ステートメントを実行する方法を提供する場合は true です。 これは、アプリケーションがプロシージャを実行する実行時にステートメントを構築するときにも当てはまります。  
  
 このような場合、アプリケーションで**SQLNumResultCols**結果セット内の列数を決定します。 ステートメントが結果セットを作成できません 0 の場合は、を他の任意の数がある場合、ステートメントは結果セットを作成しました。  
  
 アプリケーションが呼び出すことができます**SQLNumResultCols**ステートメントが準備または実行後にします。 ただし、一部のデータ ソースは、準備されたステートメントによって作成される結果セットを簡単に記述できない、ためパフォーマンスが低下する場合は**SQLNumResultCols**は、ステートメントを準備した後が実行される前に呼び出されます。  
  
 一部のデータ ソースは、SQL ステートメントが返す結果セット内の行の数を決定するもサポートします。 そのためには、アプリケーション呼び出し**SQLRowCount**です。 (カーソルの種類) に応じて SQL_DYNAMIC_CURSOR_ATTRIBUTES2、SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2、SQL_KEYSET_CURSOR_ATTRIBUTES2、または SQL_STATIC_CURSOR_ATTRIBUTES2 オプションの設定で示される正確にどのような行の数を表します呼び出しによって返される**SQLGetInfo**です。 このビットマスクは、各種類のカーソルに対して返される行の数が、概数、正確なであるかどうかを示しますか、まったく使用可能なではありません。 静的行をカウントするかどうか、またはキーセット ドリブン カーソルがを通じて行われた変更によって影響を受ける**SQLBulkOperations**または**SQLSetPos**、位置指定更新または delete ステートメントでは、によってその他のビットに依存します。前の表に、同じオプション引数が返されます。 詳細については、次を参照してください。、 [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)関数の説明。

