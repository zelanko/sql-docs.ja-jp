---
title: カーソルと準備されたステートメントでのトランザクションの効果 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- rolling back transactions [ODBC]
- committing transactions [ODBC]
- transactions [ODBC], rolling back
- cursors [ODBC], transaction commits or roll backs
- prepared statements [ODBC]
- transactions [ODBC], cursors
ms.assetid: 523e22a2-7b53-4c25-97c1-ef0284aec76e
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a454fd9fe82171685b267b24af37d562ff497ae9
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="effect-of-transactions-on-cursors-and-prepared-statements"></a>カーソルと準備されたステートメントでのトランザクションの影響
コミットまたはロールバックのカーソルとアクセスの計画に影響は次がトランザクションには。  
  
-   すべてのカーソルが閉じられ、され、その接続で準備されたステートメント用のアクセス プランが削除されます。  
  
-   すべてのカーソルが閉じられ、その接続で準備されたステートメント用のアクセス プランがそのまま残ります。  
  
-   すべてのカーソルは開いたままし、その接続で準備されたステートメント用のアクセス プランがそのまま残ります。  
  
 たとえば、データ ソースはこの一覧で、これらの動作の中で最も限定的な最初の動作を示します。 これで、次の処理をアプリケーションと仮定します。  
  
1.  手動コミットするには、コミット モードを設定します。  
  
2.  1 のステートメントでは、販売注文の結果セットを作成します。  
  
3.  ユーザーがその順序を強調表示したとき、第 2 のステートメントで販売注文の行の結果セットを作成します。  
  
4.  呼び出し**SQLExecute**ユーザーが行を更新したとき、第 3 のステートメントで準備されている位置指定更新ステートメントを実行します。  
  
5.  呼び出し**SQLEndTran**を位置指定の update ステートメントをコミットします。  
  
 データ ソースの動作への呼び出しにより**SQLEndTran**手順 5 は、1 と 2 のステートメントでカーソルを閉じると、すべてのステートメントにアクセス プランを削除します。 アプリケーションは、1 と 2 を結果を再作成するステートメントのセットを再実行し、3 のステートメントでステートメントを再び準備する必要があります。  
  
 自動コミット モードでは、機能以外の**SQLEndTran**トランザクションをコミットします。  
  
-   **SQLExecute**または**SQLExecDirect**への呼び出し、前の例で**SQLExecute**手順 4 がトランザクションをコミットします。 これにより、1 と 2 のステートメントでカーソルを閉じるし、その接続ですべてのステートメントでアクセス プランを削除するには、データ ソースです。  
  
-   **SQLBulkOperations**または**SQLSetPos**前の例では、たとえば、手順 4. で、アプリケーションを呼び出す**SQLSetPos**で実行する代わりにステートメント 2、SQL_UPDATE オプションを使用して、3 のステートメントで update ステートメントを配置します。 これは、トランザクションをコミットおよび 1 と 2 のステートメントでカーソルをクローズするデータ ソースとその接続ですべてのアクセスのプランを破棄します。  
  
-   **SQLCloseCursor**前の例では、たとえば、ユーザーは、別の販売注文を強調表示、アプリケーションが呼び出すこと**SQLCloseCursor**新しい売上の線の結果を作成する前にステートメント 2 で順序です。 呼び出し**SQLCloseCursor**コミット、**選択**行の結果セットを作成し、データ ソースが 1 のステートメントでカーソルを閉じるにし、上のすべてのアクセス プランを破棄するステートメント接続です。  
  
 アプリケーション、特にスクリーン ベースのアプリケーションでユーザーが結果セットと更新プログラムの周囲をスクロールまたは行の削除は、コードがこの問題を回避するように注意する必要があります。  
  
 データ ソースでのトランザクションがコミットまたはロールバックされたときの動作方法を決定するには、アプリケーションを呼び出す**SQLGetInfo** SQL_CURSOR_COMMIT_BEHAVIOR と SQL_CURSOR_ROLLBACK_BEHAVIOR オプションを使用します。
