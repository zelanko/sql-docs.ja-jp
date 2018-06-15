---
title: コミットとロールバックの動作 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], transaction support
- transactions [ODBC], DBMS support
ms.assetid: 2ac8f012-e46d-41ca-81bb-e4a3246e3241
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d859dcaad175ce7f340ecbf8ad8e08492d22b63c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32908797"
---
# <a name="commit-and-rollback-behavior"></a>コミットとロールバックの動作
サーバーの Dbms の間で共通の動作は、カーソルを閉じるし、ステートメントがコミットまたはロールバック時に、準備されたステートメントを破棄するのにです。 デスクトップのデータベースは、カーソルを開いたままにして、準備されたステートメントを保持する可能性が高くなります。 詳細については、SQL_CURSOR_COMMIT_BEHAVIOR と SQL_CURSOR_ROLLBACK_BEHAVIOR のオプションを参照してください、 [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)関数の説明と[と準備されたステートメントのカーソルのトランザクションの効果](../../../odbc/reference/develop-app/effect-of-transactions-on-cursors-and-prepared-statements.md).
