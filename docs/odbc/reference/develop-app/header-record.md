---
title: ヘッダー レコード |Microsoft ドキュメント
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
ms.topic: article
helpviewer_keywords:
- diagnostic information [ODBC], diagnostic records
- header records [ODBC]
- diagnostic records [ODBC]
ms.assetid: d0fff1ed-5616-422a-a394-7ea1d2486f89
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: becebb5a48c06ae16c00fb72e9db5474f876dcf1
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="header-record"></a>ヘッダー レコード
ヘッダー レコード内のフィールドには、リターン コード、行の数、実行されるステートメントの状態レコードの数と種類など、関数の実行に関する一般的な情報が含まれています。 ヘッダー レコードは、関数 SQL_INVALID_HANDLE が返されない限り、常に作成します。 ヘッダー レコード内のフィールドの完全な一覧については、 [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)関数の説明。
