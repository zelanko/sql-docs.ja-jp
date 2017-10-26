---
title: "コミットとロールバックの動作 |Microsoft ドキュメント"
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
- interoperability [ODBC], transaction support
- transactions [ODBC], DBMS support
ms.assetid: 2ac8f012-e46d-41ca-81bb-e4a3246e3241
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7bf7e756c77ceef96502fdacc078b4780f01ce86
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="commit-and-rollback-behavior"></a>コミットとロールバックの動作
サーバーの Dbms の間で共通の動作は、カーソルを閉じるし、ステートメントがコミットまたはロールバック時に、準備されたステートメントを破棄するのにです。 デスクトップのデータベースは、カーソルを開いたままにして、準備されたステートメントを保持する可能性が高くなります。 詳細については、SQL_CURSOR_COMMIT_BEHAVIOR と SQL_CURSOR_ROLLBACK_BEHAVIOR のオプションを参照してください、 [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)関数の説明と[と準備されたステートメントのカーソルのトランザクションの効果](../../../odbc/reference/develop-app/effect-of-transactions-on-cursors-and-prepared-statements.md).

