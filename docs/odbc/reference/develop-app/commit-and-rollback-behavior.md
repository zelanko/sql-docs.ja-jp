---
title: コミットとロールバックの動作 |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c67c29b295160a2908152b22c7a349ce4c0f9f50
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299132"
---
# <a name="commit-and-rollback-behavior"></a>動作のコミットとロールバック
サーバー Dbms 間で一般的な動作は、カーソルをクローズし、ステートメントがコミットまたはロールバックされたときに準備済みステートメントを破棄することです。 デスクトップ データベースは、カーソルを開いたままにして、準備されたステートメントを保持する可能性が高くなります。 詳細については、 [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)関数の説明および[カーソルおよび準備されたステートメントに対するトランザクションの影響](../../../odbc/reference/develop-app/effect-of-transactions-on-cursors-and-prepared-statements.md)の SQL_CURSOR_COMMIT_BEHAVIOR およびSQL_CURSOR_ROLLBACK_BEHAVIORオプションを参照してください。
