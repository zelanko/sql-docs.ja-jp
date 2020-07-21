---
title: ステートメントハンドルを解放する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- reusing statement handles
- freeing statement handles
- statements [ODBC], statement handles
- SQLFreeStmt function
- ODBC applications, statements
- statement handles [ODBC]
ms.assetid: 96fdff84-0ca7-460a-a240-94ee826ea41c
author: rothja
ms.author: jroth
ms.openlocfilehash: 8d7a1e93d222e2b87058bc878f7eca85313b4108
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85018341"
---
# <a name="freeing-a-statement-handle"></a>ステートメント ハンドルの解放
  ステートメント ハンドルは、削除して新しいハンドルを割り当てるよりも、再利用する方が効率的です。 アプリケーションでは、任意のステートメント ハンドルで新しい SQL ステートメントを実行する前に、現在のステートメント設定が適切であることを確認する必要があります。 確認する設定には、ステートメント属性、パラメーター バインド、結果セットのバインドがあります。 通常、古い SQL ステートメントのパラメーターと結果セットは、SQL_RESET_PARAMS と SQL_UNBIND のオプションで[SQLFreeStmt](../native-client-odbc-api/sqlfreestmt.md)を呼び出し、新しい sql ステートメントに対して再バインドすることによって、バインドを解除する必要があります。  
  
 ステートメントを使用してアプリケーションが終了すると、 [Sqlfreehandle](../native-client-odbc-api/sqlfreehandle.md)を呼び出してステートメントを解放します。 **Sqldisconnect**は、接続上のすべてのステートメントを自動的に解放することに注意してください。  
  
## <a name="see-also"></a>参照  
 [ODBC&#41;&#40;クエリの実行](executing-queries-odbc.md)  
  
  
