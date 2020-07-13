---
title: ステートメントハンドルを解放する ODBC |Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305617"
---
# <a name="freeing-a-statement-handle-odbc"></a>ステートメント ハンドルの解放 (ODBC)
既に説明したように、ステートメントを再利用して新しいステートメントを割り当てるよりも効率的です。 ステートメントで新しい SQL ステートメントを実行する前に、アプリケーションで現在のステートメントの設定が適切であることを確認する必要があります。 確認する設定には、ステートメント属性、パラメーター バインド、結果セットのバインドがあります。 通常、古い SQL ステートメントのパラメーターと結果セットは、(SQL_RESET_PARAMS と SQL_UNBIND のオプションを指定して**SQLFreeStmt**を呼び出し、新しい sql ステートメントに対して再バインドすることによって) バインド解除する必要があります。  
  
 ステートメントを使用してアプリケーションが終了すると、 **Sqlfreehandle**を呼び出してステートメントを解放します。 ステートメントを解放すると、ODBC 関数の呼び出しでステートメントのハンドルを使用するアプリケーションプログラミングエラーになります。この操作を行うと、未定義になりますが、致命的な結果になります。  
  
 **Sqlfreehandle**が呼び出されると、ドライバーはステートメントに関する情報を格納するために使用される構造体を解放します。  
  
 **Sqldisconnect**は、接続上のすべてのステートメントを自動的に解放します。
