---
title: ステートメント ハンドル ODBC を解放する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- statement handles [ODBC]
- handles [ODBC], statement
- freeing statement handles [ODBC]
ms.assetid: ee18e2f1-2690-4cc1-9e5c-e20244e5d480
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 01e4cb46edf1b1a0f1c6dfaa0273c1dd5b392686
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305617"
---
# <a name="freeing-a-statement-handle-odbc"></a>ステートメント ハンドルの解放 (ODBC)
前述のように、ステートメントを削除して新しいステートメントを割り当てるよりも、ステートメントを再利用する方が効率的です。 ステートメントに対して新しい SQL ステートメントを実行する前に、アプリケーションは現在のステートメント設定が適切であることを確認する必要があります。 確認する設定には、ステートメント属性、パラメーター バインド、結果セットのバインドがあります。 一般に、古い SQL ステートメントのパラメーターと結果セットは、(SQL_RESET_PARAMSおよびSQL_UNBINDオプションを指定して**SQLFreeStmt**を呼び出して) バインド解除し、新しい SQL ステートメントに対して再バインドする必要があります。  
  
 アプリケーションは、ステートメントの使用を終了すると、ステートメントを解放する**SQLFreeHandle**を呼び出します。 ステートメントを解放した後、ODBC 関数の呼び出しでステートメントのハンドルを使用するのは、アプリケーション プログラミング エラーです。そうすることは、未定義だが、おそらく致命的な結果をもたらす。  
  
 **SQLFreeHandle**が呼び出されると、ドライバーは、ステートメントに関する情報を格納するために使用される構造体を解放します。  
  
 **SQLDisconnect は**、接続上のすべてのステートメントを自動的に解放します。
