---
title: カーソルおよび準備文に対するトランザクションの影響 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- rolling back transactions [ODBC]
- committing transactions [ODBC]
- transactions [ODBC], rolling back
- cursors [ODBC], transaction commits or roll backs
- prepared statements [ODBC]
- transactions [ODBC], cursors
ms.assetid: 523e22a2-7b53-4c25-97c1-ef0284aec76e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ef3cb4095410b8ccb03b0a138f65b8df2cfb1a4b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300472"
---
# <a name="effect-of-transactions-on-cursors-and-prepared-statements"></a>カーソルと準備されたステートメントでのトランザクションの影響
トランザクションをコミットまたはロールバックすると、カーソルおよびアクセス・プランに対して以下の影響があります。  
  
-   すべてのカーソルがクローズされ、その接続上の準備済みステートメントのアクセス・プランが削除されます。  
  
-   すべてのカーソルがクローズされ、その接続上の準備済みステートメントのアクセス・プランはそのまま残ります。  
  
-   すべてのカーソルはオープンしたままで、その接続上の準備済みステートメントのアクセス・プランはそのまま残ります。  
  
 たとえば、データ ソースが、このリストの最初の動作を示し、これらの動作の中で最も制限が厳しい場合を考えます。 ここで、アプリケーションが次のように行っているとします。  
  
1.  コミット モードを手動コミットに設定します。  
  
2.  明細書 1 に対して販売注文の結果セットを作成します。  
  
3.  ユーザーがその注文を強調表示したときに、明細書 2 の販売注文の明細行の結果セットを作成します。  
  
4.  ユーザーが行を更新するときに、ステートメント 3 で準備された位置指定更新ステートメントを実行するために**SQLExecute**を呼び出します。  
  
5.  位置指定更新ステートメントをコミットするために**SQLEndTran**を呼び出します。  
  
 データ・ソースの動作のために、ステップ 5 で**SQLEndTran**を呼び出すと、ステートメント 1 および 2 のカーソルがクローズされ、すべてのステートメントのアクセス・プランが削除されます。 アプリケーションは、ステートメント 1 と 2 を再実行して結果セットを再作成し、ステートメント 3 でステートメントを再準備する必要があります。  
  
 自動コミット・モードでは **、SQLEndTran**以外の関数は、以下のトランザクションをコミットします。  
  
-   **SQL 実行**または**SQLExecDirect**前の例では、手順 4 の**SQLExecute**の呼び出しは、トランザクションをコミットします。 これにより、データ・ソースはステートメント 1 および 2 のカーソルをクローズし、その接続上のすべてのステートメントのアクセス・プランを削除します。  
  
-   **SQLBulkOperations**前の**例では、** 手順 4 で、アプリケーションがステートメント 3 で位置指定更新ステートメントを実行するのではなく、ステートメント 2 の SQL_UPDATE オプションを指定して**SQLSetPos**を呼び出したとします。 これにより、トランザクションがコミットされ、データ・ソースはステートメント 1 と 2 のカーソルをクローズし、その接続上のすべてのアクセス・プランが廃棄されます。  
  
-   **カーソルを閉じる**前の例では、ユーザーが別の販売注文を強調表示したときに、アプリケーションがステートメント 2 で**SQLCloseCursor**を呼び出してから、新しい販売注文の明細行の結果を作成するとします。 **SQLCloseCursor**の呼び出しは、行の結果セットを作成した**SELECT**ステートメントをコミットし、データ ソースがステートメント 1 のカーソルを閉じ、その接続上のすべてのアクセス プランを破棄します。  
  
 アプリケーション、特にユーザーが結果セットをスクロールして行を更新または削除する画面ベースのアプリケーションは、この動作を回避するコードに注意する必要があります。  
  
 トランザクションがコミットまたはロールバックされたときにデータ ソースがどのように動作するかを判断するために、アプリケーションは**sqlGetInfo**を呼び出してSQL_CURSOR_COMMIT_BEHAVIORオプションとSQL_CURSOR_ROLLBACK_BEHAVIOR オプションを指定します。
