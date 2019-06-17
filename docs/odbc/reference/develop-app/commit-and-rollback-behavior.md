---
title: コミットとロールバックの動作 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], transaction support
- transactions [ODBC], DBMS support
ms.assetid: 2ac8f012-e46d-41ca-81bb-e4a3246e3241
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bad1706e7283c0b0a5111e93c9dfd7ae494c8ef4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63125498"
---
# <a name="commit-and-rollback-behavior"></a>動作のコミットとロールバック
Server Dbms の間で共通の動作では、カーソルを閉じるし、ステートメントがコミットまたはロールバック時に、準備されたステートメントを破棄します。 デスクトップ データベースは、カーソルを開いたままにして、準備されたステートメントを保持する可能性が高くなります。 詳細については、SQL_CURSOR_COMMIT_BEHAVIOR と SQL_CURSOR_ROLLBACK_BEHAVIOR のオプションを参照してください、 [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)関数の説明と[カーソルと準備されたステートメントでトランザクションの効果](../../../odbc/reference/develop-app/effect-of-transactions-on-cursors-and-prepared-statements.md).
